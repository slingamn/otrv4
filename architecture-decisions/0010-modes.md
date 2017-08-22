## ADR 10: OTRv4 Modes

### Context

Otrv4 is a protocol that aims to:

1. Be an alternative to current messaging applications that work in synchronous
   and asynchronous messaging environments.
2. Be a comprehensive and up-to-date specification: update cryptographic
   primitives and increase the security level of the whole protocol to 224 bits.
3. Provide better deniability properties.
4. Be compatible with OTRv3 and be useful for instant messaging protocols
   (e.g. XMPP).

In order to be an alternative to current messaging applications and to be
compatible with OTRv3, OTRv4 protocol must define two modes that can be
implemented: a only OTRv4 mode and a OTRv3-compatible OTRv4. These are the two
modes enforced by the protocol, but, it must be taken into account, that OTRv4
can also be implemented in other modes.

### Decision

To attain all of the purposes of OTRv4, the specification will describe
two modes:

1. OTRv4 only: a always encrypted mode. This mode will not know how to handle
   any kind of plain text, including query messages and whitespace tags).
2. OTRv3-Compatible OTRv4: a mode that keep backwards compatibility with OTRv3.
   This mode will know, therefore, how to handle plaintext messages.

### Consequences

As a result, OTRv4' state machine will need to know the mode is working on when
initialized. It will also need to take this mode into account everytime it
makes a decision on how to transition from every state. This increases the
complexity of the specification and implementation.