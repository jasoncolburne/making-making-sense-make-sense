# [Making Making Sense Make Sense](./Making%20Making%20Sense%20Make%20Sense.md)

# [READ THE WRITING](./Making%20Making%20Sense%20Make%20Sense.md)

# [LISTEN TO THE AUDIO](https://github.com/jasoncolburne/making-making-sense-make-sense/raw/main/assets/Making%20Making%20Sense%20Make%20Sense.mp3)

This repository is a verifiably authentic archive, issued by the KERI AID
`EHhnRAdKqaF4ux-J4CZD5gXmnh45OQO13cFOdbcmCXNB`.

Rules:

1. Jason Andrew Colburne is not liable for damages or losses resulting from the use of this archive.
2. License: CC BY-NC-ND 4.0

## How to verify

I used my own code to construct this data, but there is a command-line utility I have built based on
[KERIpy](https://github.com/WebOfTrust/keripy) to verify this kind of archive. You can find it
[here](https://github.com/jasoncolburne/verify-markdown-archive).

### Manual Steps (for the curious)

If you want to do the verification yourself without the above script, read the KERI and ACDC
specifications to understand how the verifiable data was constructed. The `.ceg` file is a graph of
verifiable data. The most compact form of the expanded `.acdc` file is contained at the end of the
`.ceg` file. To verify this data:

1. Using the [KERI protocol](https://github.com/trustoverip/tswg-keri-specification) and
[ACDC specification](https://github.com/trustoverip/tswg-acdc-specification), verify the graph in
the `.ceg` file - which consists of KERI and ACDC messages ordered for direct mode consumption.

2. Compact the expanded ACDC and compare its SAID to that of the compacted variant to ensure they
are based on the same data (the expanded ACDC).

    > It's worth noting that the current implementation of KERIpy doesn't automatically compact the
ACDC being verified. You can't sign the most compact version, ingest an expanded version and expect
it to function seamlessly. To work around this, I used a schema that does not permit chaining and
has no issuee. This allows us to compact the expanded ACDC and compare SAIDs without needing to
verify other properties of the expanded ACDC. For future purposes, I can simply embed references to
other archive SAIDs in markdown contents itself, which is signed via digest, rather than chaining -
since these kind of works do not really benefit from the cryptographic assurances that chaining
provides. The issuer AID is really all that I am concerned with in this use case.

3. Finally, verify the license, each markdown document, and each asset, when hashed, matches the
appropriate CESR digest as recorded in the attributes of the expanded ACDC (I used the typical
CESR-encoded Blake3 hashing mechanism).

In this manner, you can be sure that if the identifier described at the top of this document is used
in the future, it is me, **Jason Andrew Colburne**, communicating. I control that identifier (AID).
