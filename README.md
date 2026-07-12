# midtale-auth

Static login relay for the MidTale game (see the game repo's
`docs/SERVER_PLAN.md`).

SpacetimeAuth only accepts `https://` redirect URIs, but mobile apps need
the OAuth result delivered via a custom URL scheme (`midtale://`) because
the OS suspends backgrounded apps. `callback.html` bridges the two: it
receives the redirect and forwards the query string to `midtale://callback`,
which reopens the game.

No secrets live here — the authorization code in the query is single-use
and bound to a PKCE verifier that never leaves the game.

Registered in the SpacetimeAuth client as:
`https://redredret.github.io/midtale-auth/callback.html`
