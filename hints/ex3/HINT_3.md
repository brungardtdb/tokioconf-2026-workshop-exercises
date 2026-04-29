In `turn`, start by blocking on the OS:
`self.poll.poll(&mut self.events, None).unwrap()`. The `None` timeout means
"wait forever." When it returns, iterate `self.events.iter()` and handle
each event by its `event.token()`.
