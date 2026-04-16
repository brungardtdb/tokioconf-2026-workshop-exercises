After draining the queue, check two things in order:

1. Is `done` set? -> return (success). Spawned tasks that haven't finished
   are simply dropped.
2. Otherwise -> `thread::park()` (wait for a waker).

When you wake up from park, loop back to the top and drain the queue again.
