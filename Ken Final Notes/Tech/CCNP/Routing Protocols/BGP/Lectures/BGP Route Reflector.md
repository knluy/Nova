## BGP Route Reflector


Route reflectors (RR) are one method to get rid of the full-mesh of IBGP peers in your network. The other method is BGP confederations.

The route reflector allows all IBGP speakers within your autonomous network to learn about the available routes without introducing loops. 

>![[ibgp-6-routers-full-mesh.png]]

Above we have a network with 6 IBGP routers. Using the full mesh formula we can calculate the number of IBGP peerings:

$$N(N-1)/2$$

So that will be:

$$6(6-1=5) / 2 = 15 IBGP peerings.$$

When we use a route reflector our network could look like this:

>![[ibgp-route-reflector-example.png]]


We still have 6 routers but each router only has an IBGP peering with the route reflector on top. When one of those IBGP routes advertises a route to the route reflector, it will be “reflected” to all other IBGP routers:

>![[ibgp-route-reflector-route-update.png]]

This simplifies our IBGP configuration a lot but there’s also a downside. What if the route reflector crashes? It’s a single point of failure when it comes to IBGP peerings. Of course there’s a solution to this, we can have multiple route reflectors in our network. I’ll give you some examples later.

The route reflector can have three type of peerings:

1. EBGP neighbor
2. IBGP client neighbor
3. IBGP non-client neighbor

When you configure a route reflector you have to tell the router whether the other IBGP router is a client or non-client. A client is an IBGP router that the route reflector will “reflect” routes to, the non-client is just a regular IBGP neighbor.

## Rules

When a route reflector forwards a route, there are a couple of rules:

1.  A route learned from a non-RR client is advertised to RR clients but not to non-RR clients.
2.  A route learned from a RR client is advertised to both RR clients and non-RR clients. Even the RR client that advertised the route will receive a copy and discards it because it sees itself as the originator.
3.  A route learned from an EBGP neighbor is advertised to both RR clients and non-RR clients.

Here are three illustrations to see these rules in action.

### Rule 1

>![[bgp-route-reflector-rule1.png]]

### Rule 2
>![[bgp-route-reflector-rule2.png]]

### Rule 3

>![[bgp-route-reflector-rule3.png]]






---
tags: #ccnp #routing #bgp
links: https://networklessons.com/bgp/bgp-route-reflector
see also:
created on: 2022-01-18 13:27