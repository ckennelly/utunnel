utunnel - A TCP over UDP Multiplexer
(c) 2013 - Chris Kennelly (chris@ckennelly.com)

Overview
========

`utunnel` provides TCP proxying services over an underlying UDP-based transport.  This approach allows for (eventually) reliable data delivery, even over poor network connections.  Unreliable connections, such as those found on trains and airplanes, complicates the use of SSH's built-in SOCKS proxy.  Excessive packet drops and outages can cause the failure of the underlying SSH connection, ultimately killing any TCP sessions using the tunnel.  This abrupt failure requires the SSH connection to be reestablished and only then, the proxied TCP connections to be restarted.

`utunnel` maintains buffers at each end of the tunnel, allowing proxied TCP connections to be maintained (albeit without data transfer) even during network outages.  The contents of these buffers are only flushed as full round-trip acknowledgments are received.  Data and acknowledgments are transmitted with encrypted UDP packets.

`utunnel` is open source software, licensed under the GPLv3.  For more information, see COPYING.

Building
========

`utunnel` depends on boost and cmake at compile time.

Limitations
===========

For security-sensitive applications, the tried-and-true approach of using SSH to transport data may be more secure than using `utunnel`.

Future Work
===========

* Presently, proxy services are provided with SOCKS.  In the future, support for additional protocols should be added.
