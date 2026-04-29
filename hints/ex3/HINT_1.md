In `register`: `Token` is a newtype around `usize`. Build one from
`self.next_token`, increment the counter, then call
`self.poll.registry().register(source, token, interest)` and return the token.
