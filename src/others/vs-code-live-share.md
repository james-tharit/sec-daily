# Analysis of VS Code Live share

## What is VS Code Live Share?

VS Code Live Share is a collaborative development tool that enables real-time code sharing and editing among multiple developers. It allows users to work together on the same codebase, with each participant able to see and edit the code simultaneously. Live Share also supports features like debugging and terminal sharing, fostering a seamless collaborative coding experience within the Visual Studio Code editor. It's particularly useful for pair programming and remote collaboration.

## What happening during the Peer Authentication

```mermaid
sequenceDiagram
    participant Host
    participant LiveShare
    participant Guest

    Host->>LiveShare: Initiates Live Share session with peer authentication
    Host->>Host: Generates unique RSA key-pair for the session
    Host-->>Host: Host private key kept in memory
    Host->>LiveShare: Host public key published to Live Share service

    Note over LiveShare: Host's public key and session details are stored

    LiveShare->>LiveShare: Generate invitation link with the session details, include the host public key
    LiveShare->>Host: Receives invitation link

    Host->>Guest: Share invitation link to Guest

    Guest->>LiveShare: Authenticate with Live Share, got back Live Share token(sign JWT)


    Guest->>Host: Open invitation link
    Host-->>Host: Validates token and checks claims

    Note over Host: Token includes user identity and session access claims

    Host-->>Guest: Establishes secure connection
    Note over LiveShare: Real-time collaboration begins
```

### Steps explanation

1. **Host Initiates Live Share Session**:
   The Host initiates a Live Share session with peer authentication.
2. **RSA Key-Pair Generation**:
   The Host generates a unique RSA key-pair specifically for this Live Share session.
   The Host's private key is kept in memory and not written to disk for security reasons.
3. **Host Publishes Public Key**:
   The Host publishes the generated public key to the Live Share service, along with session details such as IP address or relay endpoint.
4. **LiveShare Generates Invitation Link**:
   LiveShare generates an invitation link, incorporating the session details and including the Host's public key.
5. **Host Shares Invitation Link**:
   The Host shares the invitation link, containing the Live Share session details and the public key, with the Guest.
6. **Guest Authentication with Live Share**:
   The Guest authenticates with the Live Share service, obtaining a Live Share token (signed JWT) as a result.
7. **Guest Opens Invitation Link**:
   The Guest opens the invitation link, initiating the connection process
8. **Host Validates Token**:
   The Host validates the Live Share token received from the Guest, checking its claims, including user identity and session access permissions.
9. **Establishment of Secure Connection**:
   Upon successful validation, the Host and Guest establish a secure connection, marking the beginning of real-time collaboration through Live Share.

### What's about wire encryption?

After initiate the session with RAS Key-Pair, Host and Guest uses a Diffie-Hellman key-exchange to establish a shared secret for the session, and derives from that a key for **AES symmetric encryption**.

The encryption key is rotated periodically throughout the duration of the session. The shared session secret and all encryption keys are only maintained in-memory by both sides, and are only valid for the duration of the session. They are never written to disk or sent to any service (including Live Share).

..

---

Reference:

- [VS Code Live Share Security Document](https://learn.microsoft.com/en-us/visualstudio/liveshare/reference/security)
