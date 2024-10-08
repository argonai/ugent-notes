# Wireshark Lab
## 1.1 Basic HTTP/GET response interaction
1. **Client version: `http 1.1`, visible in GET request, packet nr. 6, Server version also `http/1.1`, visible in response, packet nr 6.**
2. part of accept-language, packet nr 6, `en` and `nl`
3. Computer ip: `157.193.215.200`, Server-ip: `128.119.245.12`
4. Status code `200 OK`, packet 8
5. Content-length: `128`, packet 8 -> probably wrong, not tcp payload length, may go back and fix
6. No clue, get solution
## 1.2 The HTTP CONDITIONAL GET/response interaction
**DO LATER, NOT REQUIRED/YELLOW QUESTIONS SO DO OTHER ONES FIRST**
## 1.3 Retrieving Long Documents
11. Only one GET request message, packet 6
12. Response in packet 14
13. Status code 200 OK
14. 4 packets
15. **1488 bytes in TCP payload for the in-between frames (between Req and Resp), final frame with response has 480 bytes, the last bytes remaining to complete the page**
## 1.4 HTML Documents with embedded objects.
16. **4 GET requests, sent to two different ip's, `128.119.245.12` and `128.119.240.90`**
17. **Looks sequentially, but might be parallell, as the second image download makes a `SYN` request before the first image makes it `ACK`, second image (kurose) responded first time with code 302 found, then redownloaded**
This is more viewable using [this method](https://networkengineering.stackexchange.com/a/52896)
## 1.5 HTTP Authentication
18. `401 Unauthorized`
19. `Authorization: Basic`
`Authorization: Basic` header content en not encrypted but base64 encoded, this is not secure and can be reversed
## 2.1 First look at captured trace
Top filter (not CTRL+F) can be used to filter protocol, http filters on HTTP Req and Response.
1. IP: `192.168.1.187`, Port: `61689`
2. IP: `128.119.245.12`, Port: `80`
## 2.2 TCP Basics
3. Sequence number: `0` (Seq=0), SYN identified with flag (hex bitmask)
4. Sequence number: `0`, SYN and ACK set with flag (hex bitmask)
5. Seq=1, **TCP payload: 711 bytes, did not fit into single TCP segment**
6. **Total length: `1500`, payload has `1460` bytes**
Easily find Total length: first part of frame
7. Window increases by about `8800 bytes` (calculated window size) every other frame -> idk im tired
