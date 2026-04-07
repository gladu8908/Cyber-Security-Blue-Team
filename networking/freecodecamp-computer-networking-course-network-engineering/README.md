# freeCodeCamp Computer Networking Course - Network Engineering

Platform: freeCodeCamp

## 📚 What I learned today

### 2026-04-07 — What I understood (Computer Networking basics)
Today I mainly focused on how common network devices map to the first 3 layers of the OSI model, and why that matters in real networks.

- **Layer 1 (Physical)** is about signals and the physical media. A **modem** is basically translating signals (digital ↔ analog). A **hub** is a simple repeater that blasts traffic out to every port (no real “decision-making”).
- **Layer 2 (Data Link)** is where **MAC addresses** matter. A **switch** learns MAC addresses and forwards frames only where they should go (instead of everywhere). A **wireless access point (WAP)** bridges Wi‑Fi (802.11) clients into the wired Ethernet (802.3) world.
- **Layer 3 (Network)** is where **IP addresses and routing** happen. A **router** connects different networks and makes routing decisions. A **multi-layer switch** can do switching but also perform Layer 3 routing.

I also got a clearer picture of “security/traffic-handling” devices:
- A **firewall** can filter traffic at multiple layers, and the big difference I understood is **stateless** (checks packets individually) vs **stateful** (tracks connection state and allows return traffic for connections initiated internally).
- **IDS vs IPS:** IDS is more like “detect and alert,” while IPS is inline and can actively block/drop.
- A **load balancer** spreads traffic across multiple servers, and a **proxy** makes requests on behalf of a client (can hide internal IPs, cache, and filter).

For VPNs, I understood the main connection patterns:
- **Site-to-site** (network ↔ network), **remote access** (user ↔ office network), and **host-to-host / SSL VPN** (browser/TLS-based style).
- **IPsec** protects at Layer 3 (AH for auth without encryption, ESP adds encryption), and **GRE** is useful for tunneling things like broadcast/multicast (often carried inside IPsec).

Finally, on access/authentication:
- A **NIC** is basically the interface at Layer 1 (physical connection) and Layer 2 (MAC identity).
- **RADIUS** does AAA but only encrypts the password (rest is cleartext).
- **TACACS+** encrypts the entire payload, so it’s stronger from a confidentiality standpoint
