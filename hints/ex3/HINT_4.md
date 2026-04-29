For each event in `turn`: if `event.token() == NOTIFY_TOKEN`, `continue`.
Those events only mean "a task was queued," and the executor handles those
by draining its queue. Otherwise, `self.io_wakers.remove(&event.token())`
returns `Option<Waker>`; if `Some(waker)`, call `waker.wake()`. Use
`remove` (not `get`) so the waker is consumed. The I/O future will
re-register a fresh one on its next poll if it still needs to wait.
