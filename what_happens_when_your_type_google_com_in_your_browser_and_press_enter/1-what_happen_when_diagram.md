┌─────────────────────────────────────────────────────────────────────────────┐
│                            CLIENT SIDE                                      │
└─────────────────────────────────────────────────────────────────────────────┘
         │
         ▼
1.  https://www.google.com
         │
         ▼ DNS Resolution
┌─────────────────────────────────────────────────────────────────────────────┐
│  DNS LOOKUP PROCESS:                                                        │
│  • Browser Cache → OS Cache → Router → ISP DNS → Root → TLD → Authoritative │
│  • Returns: 142.251.32.196                                                  │
└─────────────────────────────────────────────────────────────────────────────┘
         │
         ▼
2.  TCP/IP Connection on Port 443
    ┌─ SYN ──────────────────────────────────────────────────────────────────┐
    ├─ SYN-ACK ──────────────────────────────────────────────────────────────┤
    └─ ACK ──────────────────────────────────────────────────────────────────┘
         │
         ▼
3.  🔒 Firewall Check
    ┌─────────────────────────────────────────────────────────────────────────┐
    │ ✓ Verify Port 443                                                       │
    │ ✓ Check Security Rules                                                  │
    │ ✓ Allow Encrypted Traffic                                               │
    └─────────────────────────────────────────────────────────────────────────┘
         │
         ▼
4.  HTTPS/SSL Handshake
    ┌─────────────────────────────────────────────────────────────────────────┐
    │ • Certificate Exchange                                                  │
    │ • Key Generation                                                        │
    │ • Encrypted Tunnel Established                                          │
    └─────────────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────────────────┐
│                          GOOGLE INFRASTRUCTURE                              │
└─────────────────────────────────────────────────────────────────────────────┘
         │
         ▼
5.  ⚖️ Load Balancer
    ┌─────────────────────────────────────────────────────────────────────────┐
    │ • Health Checks                                                         │
    │ • Traffic Distribution                                                  │
    │ • Route to Available Server                                             │
    └─────────────────────────────────────────────────────────────────────────┘
         │
         ▼
6.  🖥️ Web Server (Nginx/Apache)
    ┌─────────────────────────────────────────────────────────────────────────┐
    │ • Receive Request                                                       │
    │ • Serve Static Assets? ─Yes─→ Return HTML/CSS/JS                       │
    │ • Need Dynamic Content? ─Yes─→ Pass to Application Server               │
    └─────────────────────────────────────────────────────────────────────────┘
         │
         ▼ (Dynamic Content Path)
7.  🚀 Application Server
    ┌─────────────────────────────────────────────────────────────────────────┐
    │ • Execute Business Logic                                                │
    │ • Process User Data                                                     │
    │ • Generate Dynamic Content                                              │
    └─────────────────────────────────────────────────────────────────────────┘
         │
         ▼
8.  🗄️ Database Query
    ┌─────────────────────────────────────────────────────────────────────────┐
    │ • Connect to Database                                                   │
    │ • Execute Queries                                                       │
    │ • Return Results                                                        │
    └─────────────────────────────────────────────────────────────────────────┘
         │
         ▼
    ┌────────────────┐
    │   DATABASE     │
    │  • Google      │
    │  • Bigtable    │
    │  • Spanner     │
    └────────────────┘
         │
         ▼
    Return Journey: Database → Application Server → Web Server → Load Balancer → Client

┌─────────────────────────────────────────────────────────────────────────────┐
│                            RESPONSE JOURNEY                                 │
└─────────────────────────────────────────────────────────────────────────────┘
         │
         ▼
9.  🔄 Return Path (Reverse Flow)
    Database Results → Application Logic → Web Page Generation → Encryption → Network
         │
         ▼
10. 📨 Client Receives Response
    ┌─────────────────────────────────────────────────────────────────────────┐
    │ • SSL Decryption                                                        │
    │ • HTML Parsing                                                          │
    │ • DOM Construction                                                      │
    │ • CSS Rendering                                                         │
    │ • JavaScript Execution                                                  │
    └─────────────────────────────────────────────────────────────────────────┘
         │
         ▼
11. 🌐 Google Homepage Displayed
