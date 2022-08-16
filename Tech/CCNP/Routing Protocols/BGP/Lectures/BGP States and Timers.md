## BGP States and Timers

### BGP IDLE state
- BGP start event detected
- Actively trying to establish TCP connection with peer
- Listens for a new connect from peer

### BGP Connect State
- Waiting for TCP Three-way Handshake to complete
- 120 Second ConnectRetry timer
- Connet state failure (ConnectRetry timer reaches zero) moves BGP to Active State

### BGP Active State:
- New TCP connection with peer is attempted
- Failure moves BGP back to Connect state, resets ConnectRetry timer
- Success moves BGP to OpenState state

### "TCP Phase" of States
- _Idle_ State
- _Connect_ State
- _Active_ State

- Failure in these states indicates a TCP connection issue

### BGP _OpenSent_ State
- BGP - related messages are exchanged
- Originating router sends *Open* message
- Waits for similar *Open* message from peer
- Compares BGP version, source IP addressing, AS number, BGP RID, and security parameters
- If parameters match, KEEPLIVE messages keep session active and reset the Hold Time
- If error are found, a notification message is sent and BGP moves back to _Idle_ state

### BGP _OpenConfirm_ State
- _Open_ messages match and session is established
- Waiting for **KEEPALIVE** messages
- if no **KEEPALIVE** is received, BGP moves to _Idle_ state
- Receipt of **KEEPALIVE** moves BGP to _Established_ state


### BGP _Established_ State:
- Routes exchanged via Update messaged
- **KEEPALIVE** messages exchanged between peers to reset Hold Time
- **KEEPALIVE** default value is 60 seconds
- Hold Time default value is 180 seconds


### "BGP Phase" of States
- *OpenSent* State
- *OpenConfirm* State
- *Established* State

- Failure in these states indicates a BGP configuration issue

---
tags: #ccnp #routing #bgp
links: https://www.linkedin.com/learning/cisco-ccnp-enarsi-300-410-cert-prep-2-vpn-technologies/bgp-states-and-timers?autoAdvance=true&autoSkip=true&autoplay=true&contextUrn=urn%3Ali%3AlyndaLearningPath%3A5f88923f498edf8b778e9879&resume=false&u=46118444
see also:
created on: 2022-01-18 10:53