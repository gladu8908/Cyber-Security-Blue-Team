# Wireshark – Quick Reference

> Commonly used display filters, workflow tips, and shortcuts for network traffic analysis in a SOC context.

---

## Basic Syntax

| Operator | Meaning | Example |
|---|---|---|
| `==` | Equals | `ip.addr == 192.168.1.1` |
| `!=` | Not equal | `ip.addr != 10.0.0.1` |
| `&&` or `and` | AND | `ip.src == 10.0.0.1 && tcp.port == 443` |
| `\|\|` or `or` | OR | `tcp.port == 80 \|\| tcp.port == 443` |
| `!` or `not` | NOT | `!arp` |
| `contains` | Contains string | `http.host contains "evil"` |
| `matches` | Regex match | `dns.qry.name matches ".*pastebin.*"` |

---

## Useful Display Filters

### IP-based filters

```wireshark
ip.addr == 192.168.1.100          # Any traffic to/from this IP
ip.src == 10.0.0.5                # Traffic FROM this IP
ip.dst == 8.8.8.8                 # Traffic TO this IP
ip.addr == 192.168.0.0/24         # Entire subnet
```

### Protocol filters

```wireshark
tcp                               # All TCP traffic
udp                               # All UDP traffic
dns                               # DNS queries and responses
http                              # HTTP (plain text)
tls                               # TLS/HTTPS (encrypted)
icmp                              # Ping / ICMP traffic
arp                               # ARP broadcasts
```

### Port-based filters

```wireshark
tcp.port == 80                    # HTTP
tcp.port == 443                   # HTTPS
tcp.port == 22                    # SSH
tcp.port == 3389                  # RDP
tcp.port == 445                   # SMB
udp.port == 53                    # DNS
```

### HTTP-specific filters

```wireshark
http.request                      # HTTP requests only
http.response                     # HTTP responses only
http.request.method == "POST"     # POST requests (look for data exfil)
http.response.code == 200         # Successful responses
http.response.code == 404         # Not found
http.host contains "example"      # Filter by hostname
```

### DNS-specific filters

```wireshark
dns.qry.name                      # All DNS queries
dns.qry.name == "malicious.com"   # Specific domain lookup
dns.flags.rcode != 0              # DNS errors (NXDOMAIN etc.)
```

### TCP handshake / flags

```wireshark
tcp.flags.syn == 1 && tcp.flags.ack == 0   # SYN (connection initiation)
tcp.flags.reset == 1                        # RST (connection reset — possible scan/reject)
tcp.flags.fin == 1                          # FIN (connection teardown)
```

---

## SOC Investigation Workflow

1. **Apply a source IP filter** to focus on the suspicious host.
2. **Follow TCP/HTTP streams** (`Right-click → Follow → TCP/HTTP Stream`) to read session content.
3. **Look at DNS queries** from the host — unexpected domains are a red flag.
4. **Check for large data transfers** — use Statistics → Conversations to see byte counts.
5. **Export objects** (`File → Export Objects → HTTP`) to extract transferred files for hashing.
6. **Check TLS SNI** (`tls.handshake.extensions_server_name`) to see destination hostnames in encrypted traffic.

---

## Useful Menu Shortcuts

| Action | Menu path |
|---|---|
| Filter by selected field | Right-click field → Apply as Filter → Selected |
| Follow TCP stream | Right-click packet → Follow → TCP Stream |
| Export HTTP objects | File → Export Objects → HTTP |
| Endpoint statistics | Statistics → Endpoints |
| Conversation statistics | Statistics → Conversations |
| Protocol hierarchy | Statistics → Protocol Hierarchy |
| I/O graph | Statistics → I/O Graph |

---

> **Tip:** Combine Wireshark display filters with Statistics views to quickly spot unusual volumes, beaconing patterns, or data exfiltration.
