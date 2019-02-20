# posix_quic.
QUIC (Quick UDP Internet Connections)

QUIC is an early-stage network protocol [Jim Roskind <jag@google.com>]
is experimenting with that runs a stream multiplexing protocol over a
new flavor of Transport Layer Security (TLS) on top of UDP instead of
TCP. QUIC combines a carefully selected collection of techniques to
reduce the number of round trips we need as we surf the Internet. You
can learn more in the design document, but here are some of the
highlights:

  * High security similar to TLS
  * Fast (often 0-RTT) connectivity similar to TLS Snapstart combined
    with TCP Fast Open
  * Packet pacing to reduce packet loss
  * Packet error correction to reduce retransmission latency
  * UDP transport to avoid TCP head-of-line blocking
  * A connection identifier to reduce reconnections for mobile clients
  * A pluggable congestion control mechanism

This is "libquic", a user-space library that re-uses/packages/purposes
the QUIC code from the Chromium browser project so that other software
can use this new protocol for Internet layer-4 communications.  QUIC
is a general purpose protocol built primarily with HTTP in mind, but
there is no reason not to use it as a replacement for TCP in other
non-HTTP based connections.

QUIC Discussions:
 proto-quic@chromium.org
 https://groups.google.com/a/chromium.org/d/forum/proto-quic


[1] http://blog.chromium.org/2013/06/experimenting-with-quic.html
[2] https://docs.google.com/document/d/1RNHkx_VvKWyWg6Lr8SZ-saqsQx7rFV-ev2jRFUoVD34/preview?sle=true
[3] https://docs.google.com/document/d/1lmL9EF6qKrk7gbazY8bIdvq3Pno2Xj_l_YShP40GLQE/edit#heading=h.h3jsxme7rovm
