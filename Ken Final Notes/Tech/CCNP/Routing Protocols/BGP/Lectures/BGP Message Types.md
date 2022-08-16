## BGP Message Types

BGP Message Types:
- OPEN
- UPDATE
- NOTIFICATION
- KEEPALIVE


### OPEN Message:
- Establishes initial BGP adjacency
- BGP version, ASN of originating router, BGP identifier, hold time, and other optional parameters
- BGP identifier - 32 bit Router ID (RID)
- Hold time determines when session is torn down (180 second default)

### KEEPALIVE Message
- Heartbeaat that keeps hold time from expiring
- Exchanged at a rate of 1/3 of the hold time
- Default value is 60 seconds (1/3 of 180 second hold time)

### UPDATE Message
- Updates known routes 
- Advertises feasible routes and removing routes
- NLRI exchanged within the UPDATE messages

### NOTIFICATION message
- Alert about error detection within a BGP session
- Expired hold timers, neighbor changes, request for BGP session reset



---
tags:  #ccnp #routing #bgp
links:
see also:
created on: 2022-01-18 10:43