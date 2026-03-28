# nostkey.org

Alternative WebAuthn passkey gateway for [keytr](https://github.com/sovITxyz/keytr). Hosted on Hostinger.

## What this is

- **Landing page** explaining the multi-gateway decentralization model for keytr
- **WebAuthn gateway** — serves `/.well-known/webauthn` so Nostr clients can register passkeys under the `nostkey.org` rpId via [Related Origin Requests](https://w3c.github.io/webauthn/#sctn-related-origins)

No server logic. No backend. Just static files.

## Why a second gateway?

WebAuthn passkeys are bound to the domain (rpId) they were created on. If `keytr.org` goes down or Cloudflare has an outage, passkeys registered against it can't authenticate. By registering passkeys against **both** `keytr.org` and `nostkey.org`, users maintain access even if one provider fails.

- `keytr.org` — Cloudflare Pages
- `nostkey.org` — Hostinger

Different domains, different registrars, different hosting providers. Each gateway produces a separate `kind:30079` event on the user's relays.

## Gateway

To add your Nostr client as an authorized origin, open a PR adding your domain to `.well-known/webauthn`.

## Related

- [keytr](https://github.com/sovITxyz/keytr) — the library (`@sovit.xyz/keytr` on npm)
- [keytr.org](https://github.com/sovITxyz/keytr.org) — primary gateway on Cloudflare
- [NIP-K1](https://github.com/sovITxyz/keytr/blob/main/nip/nip-k1.md) — the protocol spec

## License

AGPL-3.0-or-later
