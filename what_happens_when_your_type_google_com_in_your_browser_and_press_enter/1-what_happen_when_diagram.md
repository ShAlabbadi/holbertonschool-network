# What Happens When You Type https://www.google.com in Your Browser and Press Enter?
## The Complete Journey - Request Flow Diagram :
graph TD
    A[User Types<br/>https://www.google.com] --> B{DNS Resolution}
    B --> C[Check Browser Cache]
    C --> D[Check OS Cache]
    D --> E[Check Router Cache]
    E --> F[Query ISP DNS]
    F --> G[Root DNS Server]
    G --> H[.com TLD Server]
    H --> I[Google Name Server]
    I --> J[Get IP: 142.251.32.196]
    
    J --> K[TCP/IP Connection<br/>Port 443]
    K --> L[SYN]
    L --> M[SYN-ACK]
    M --> N[ACK]
    N --> O[Connection Established]
    
    O --> P[Firewall Check]
    P --> Q{Port 443 Allowed?}
    Q -->|Yes| R[HTTPS/SSL Handshake]
    Q -->|No| S[Connection Blocked]
    
    R --> T[SSL Certificate Exchange]
    T --> U[Key Generation]
    U --> V[Encrypted Tunnel Created]
    
    V --> W[Load Balancer]
    W --> X[Server Health Check]
    X --> Y[Traffic Distribution]
    Y --> Z[Route to Web Server]
    
    Z --> AA[Web Server<br/>Nginx/Apache]
    AA --> AB{Serve Static Content?}
    AB -->|Yes| AC[Return HTML/CSS/JS]
    AB -->|No| AD[Pass to Application Server]
    
    AD --> AE[Application Server]
    AE --> AF[Business Logic]
    AF --> AG[Database Query]
    
    AG --> AH[(Database<br/>MySQL/PostgreSQL)]
    AH --> AI[Query Results]
    AI --> AE
    
    AE --> AJ[Generate Dynamic Content]
    AJ --> AA
    AC --> AK[HTTP Response]
    
    AK --> AL[Encrypt Response]
    AL --> AM[Send Through Firewall]
    AM --> AN[Transmit to Client]
    
    AN --> AO[Browser Receives Response]
    AO --> AP[SSL Decryption]
    AP --> AQ[Render Web Page]
    AQ --> AR[Google Homepage Displayed]
    
    %% Styling
    classDef dns fill:#e1f5fe
    classDef network fill:#f3e5f5
    classDef security fill:#fff3e0
    classDef infrastructure fill:#e8f5e8
    classDef database fill:#ffebee
    classDef client fill:#fce4ec
    
    class B,C,D,E,F,G,H,I,J dns
    class K,L,M,N,O,P,Q network
    class R,S,T,U,V security
    class W,X,Y,Z,AA,AB,AD,AE infrastructure
    class AH,AI database
    class A,AO,AP,AQ,AR client
