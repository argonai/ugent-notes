### Telnet
TCP-connection, exchanges ascii between endpoint
### SSH
Securer than Telnet
# Telnet for other application
## Mail protocols
### SMTP
[Command list here](https://www.samlogic.net/articles/smtp-commands-reference.htm)
port 25, example
```bash
telnet mail.example.net 25
```
#### Example flow
```telnet
C: HELO example.net
S: 250 OK
C: MAIL FROM:<test@example.net>
S: 250 OK
C: RCPT TO: <recipient@example.com>
S: 250 OK
C: DATA
S: 354 Send message content; end with <CRLF>.<CRLF>
C: Date: Thu, 21 May 2008 05:33:29 -0700
C: From: User <test@example.net>
C: Subject: The Next Meeting
C: To: recipient@example.com
C:
C: Hi John,
C: The next meeting will be on Friday.
C: /Anna.
C: .
S: 250 OK
```
### POP
POP can be used to retreive the sent email
```bash
telnet mail.example.com 110
```
```telnet
USER test
PASS t3st
STAT (shows mails)
RETR 1 (retreive 1 mail)
QUIT
```
### HTTP
Send HTTP requests
```bash
telnet portquiz.net 80
```
```telnet
GET / HTPP/1.0
```
# Labo
## Telnet labo
1. make file -> use standard linux commands, `touch`, `vi`
2. Connection refused
3. How to test FTP -> telnet naar ftp port (21) [Instructions here](https://www.filestash.app/2021/08/07/ftp-with-telnet/)
4. Send mail -> see [SMTP](#SMTP)
5. Read mail -> see [POP](#POP)
5. Server ligt plat at time of writing, not possible
6. idem nr5
7. Geeft enkel positive response, om timeouts te vermijden bij testen
## Wireshark part
wireshark labo meer comprehensive
## DNS
1. Welk ip adres heeft <url> -> gebruik `dig`, answer section
2. Reverse lookup geeft `portlvs.ugent.be` -> via `dig -x <ip>`
3. Verschillende IP-adressen -> een bedrijf zoals tinder gebruikt een CDN, is sneller, ook door EU, US, en Asia servers kunnen ip-adressen verschillen
