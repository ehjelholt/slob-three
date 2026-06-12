# Seed evolution mixes die count and Die Type into the Session Seed

The Session Seed evolves after each Roll by mixing the prior seed with the roll's die count and Die Type using Mulberry32's integer advancement combined with a XOR-mix: `new_seed = mulberry32_advance(seed ^ (count * 31 + sides))`. This means rolling 2d6 then 1d8 produces different outcomes than rolling 1d8 then 2d6 from the same starting seed — the *what* of each roll is baked into the seed history.

## Considered Options

- **Pure PRNG state** — advance the PRNG by N steps per roll regardless of die config. Simpler, but loses the property that the roll sequence is tied to the specific dice chosen.
- **Cryptographic hash (SHA-256)** — stronger collision resistance, but overkill for tabletop reproducibility and requires the Web Crypto API.

The hash-mixing approach was chosen because it makes the Session Seed a fingerprint of the exact sequence of decisions made, which is the semantically correct behaviour for a reproducible tabletop session.
