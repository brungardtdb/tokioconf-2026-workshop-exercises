`set_waker` is one line: `self.io_wakers.insert(token, waker);`. The reactor
owns the waker until an event for that token fires inside `turn()`.
