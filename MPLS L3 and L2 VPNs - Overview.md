(28-Feb-2026)

[MPLS L3 and L2 VPNs - YouTube] 
(https://www.youtube.com/watch?v=662iDLZDepQ)

MPLS L3 and L2 VPNs

![](/home/knight/snap/marktext/9/.config/marktext/images/2026-02-28-20-37-04-image.png)

MPLS L3 and L2 VPNs

IGP convergence is a prerequisite in mpls core and LDP

VRFs w/ RDs and RTs - Route Distinguishers (RD) and Route Targets (RT)

Virtual Routing & Forwarding Table

BGP VPNv4 PE to PE

VRF Aware PE-CE

L3 vpn > IP rtd 

L2 vpn > Bridged > Ethernet over Mpls > EoMPLS

Link State Routing > LSR > IS-IS or OSPF > SPF (Shortest path first)

Transport Label > MPLS core change a lot > on top

VPN Label > Customer traffic label > doesn't change a lot > significant to a customer traffic > on bottom  

[Penultimate Hop Popping](https://www.google.com/search?q=Penultimate+Hop+Popping&sca_esv=26102ee7b85ee816&biw=1920&bih=949&sxsrf=ANbL-n44uRHmj2msv741lFprCj88Ur8s8A%3A1772453112606&ei=-HylafLaJJbv4-EPuseBiAQ&ved=2ahUKEwiI5dP0l4GTAxVuxDgGHU4BB2cQgK4QegQIARAC&uact=5&oq=mpls+php+&gs_lp=Egxnd3Mtd2l6LXNlcnAiCW1wbHMgcGhwIDIGEAAYFhgeMgYQABgWGB4yBhAAGBYYHjIGEAAYFhgeMgYQABgWGB4yBhAAGBYYHjILEAAYgAQYhgMYigUyCxAAGIAEGIYDGIoFMgsQABiABBiGAxiKBTILEAAYgAQYhgMYigVIlsUYUN2XGFiVrxhwAXgAkAEAmAG7AaAB8AeqAQM0LjW4AQPIAQD4AQGYAgqgAqQIwgIIEAAYsAMY7wXCAgsQABiwAxiiBBiJBcICCxAAGIAEGLADGKIEwgILEAAYgAQYkQIYigXCAggQABiABBixA8ICCxAuGIAEGLEDGIMBwgILEAAYgAQYsQMYgwHCAg4QABiABBixAxiDARiKBcICDhAuGIAEGLEDGIMBGIoFwgIKEC4YgAQYQxiKBcICChAAGIAEGEMYigXCAhEQABiABBiRAhixAxiDARiKBcICBRAuGIAEwgIHEAAYgAQYCsICBRAAGIAEwgIPEAAYgAQYsQMYgwEYChgLwgIJEC4YgAQYChgLwgIJEAAYgAQYChgLmAMAiAYBkAYEkgcDNC42oAewSLIHAzMuNrgHoAjCBwQyLTEwyAcogAgA&sclient=gws-wiz-serp&mstk=AUtExfDMC14KL2D52Z4ywJ1QixfV1xfHuIvMiLzXMpRqlVD1uni6ZX-kFDfKPqOuNQPm2HEGmD1aOpDLgi1JK1DDuD3giRlmpygSWKtsB3S5541hLAfcn6OZjqGbRH9mlLfwcSVQk2O2yJBv1nxdl1-2cX8Ikmq9upTawDpIgGREFthI7D86TCHiYF2vfjg2EpAbaB6MZ0O1-V9_Fj6mp66DHyePgI-kBXProwtUQB_DTiqQ49ywp1KyCCchigMrwpFBFcvI_x7ONrsRYwNCHMehxIlp&csui=3) (PHP)

VRF = Routing 

VLAN = Switching 

RD = X:X:X.X.X.X , RD = 65002: 10: 10.1.0.0/16 (show run vrf)

RT = IMPORT , EXPORT, BOTH





### Summary of MPLS Layer 3 and Layer 2 VPNs Overview

This video provides a **comprehensive high-level explanation of MPLS (Multiprotocol Label Switching) Layer 3 (L3) and Layer 2 (L2) VPNs**, focusing on their components, differences, and operational principles. The content is tailored for networking professionals preparing for certifications like CCNP, CCIE, or specifically Service Provider tracks such as CCIP/CCDP or CCNP Service Provider.

---

### Core Concepts and Definitions

- **MPLS ()** is not a protocol but a **service** that facilitates efficient packet forwarding using labels.
- **Layer 3 VPN (L3VPN):** IP-routed VPN where customer routes are advertised and forwarded across the provider network using MPLS labels.
- **Layer 2 VPN (L2VPN):** VPN that operates at Layer 2, effectively bridging customer sites as if connected by a large provider switch, without IP routing across the provider backbone.
- **VRF (Virtual Routing and Forwarding):** Virtual routing tables per customer to isolate routing domains.
- **Route Distinguisher (RD):** A unique 96-bit prefix prepended to customer routes to ensure uniqueness across overlapping private IP spaces.
- **Route Target (RT):** BGP extended community attribute used to control import/export of routes between VRFs on PE devices.
- **PE (Provider Edge) and P (Provider) routers:** PE routers connect to customer sites and run MPLS VPN functions; P routers operate in the MPLS core, forwarding based on labels.
- **IGP (Interior Gateway Protocol):** Typically OSPF or ISIS, used for routing within the MPLS core.
- **LDP (Label Distribution Protocol):** Distributes labels for forwarding packets within the MPLS network.
- **BGP VPNv4:** Multiprotocol BGP address family used to advertise VPN routes between PE routers.

---

### Layer 3 vs. Layer 2 VPNs

| Feature                        | Layer 3 VPN (L3VPN)                                | Layer 2 VPN (L2VPN)                                            |
| ------------------------------ | -------------------------------------------------- | -------------------------------------------------------------- |
| Operation layer                | Layer 3 (IP Routed)                                | Layer 2 (Bridged)                                              |
| Routing between sites          | Routes advertised and exchanged via BGP VPNv4      | No routing; acts as a giant switch                             |
| IP addressing on PE interfaces | PE interfaces towards CE have IP addresses         | PE interfaces bridging customer sites do not have IP addresses |
| Customer traffic handling      | IP packets forwarded with VPN and transport labels | Frames bridged transparently across MPLS core                  |
| Typical use case               | Connecting customer sites with separate IP subnets | Extending Layer 2 domains across sites                         |
| Key configuration command      | BGP VPNv4 address family, VRFs, RD, RT             | Xconnect command to establish Layer 2 tunnel                   |

---

### Key Technical Details and Configuration Components

- **IGP and LDP Setup:**
  
  - OSPF or ISIS is used as the IGP in the MPLS core.
  - PE routers must have **/32 loopback interfaces** advertised in IGP for MPLS LDP sessions.
  - The command `mpls ldp autoconfig` can simplify LDP deployment by enabling LDP on interfaces running OSPF.
  - P routers do **not** require /32 loopbacks as they do not interface with customer networks.
  - IGP convergence is critical for correct MPLS forwarding.

- **Label Operations:**
  
  - MPLS uses **two types of labels:**
    - **Transport label:** Changes hop-by-hop inside the MPLS core, guiding packet forwarding.
    - **VPN label:** Assigned per customer route, remains constant end-to-end.
  - Label values are locally significant per link and may overlap in different interfaces.
  - PHP (Penultimate Hop Popping) removes the transport label one hop before the PE to forward the packet using the VPN label.

- **VRFs, Route Distinguishers, and Route Targets:**
  
  - VRFs enable multiple isolated routing tables on the same PE device for different customers.
  - Route Distinguishers ensure uniqueness of overlapping private IP address spaces by prepending a unique 96-bit value.
  - Route Targets control route import/export policies between PE routers.
  - VRFs are applied on interfaces using commands like `ip vrf forwarding <VRF_NAME>`.
  - VRF Light is a simpler form of VRF without MPLS VPN, useful in some isolated environments.

- **BGP VPNv4:**
  
  - Runs between PE routers to exchange VPN routes.
  - Requires a **full mesh or route reflector setup** for PE-to-PE BGP sessions.
  - VPNv4 address family is separate from IPv4, allowing independent operation.
  - Extended community attributes carry Route Target info.
  - Configuration involves activating `address-family vpnv4` under BGP and establishing neighbor relationships.

- **VRF-Aware PE-to-CE Routing:**
  
  - PE routers support **VRF-aware routing protocols** for customer connections.
  - Multiple routing protocols (BGP, OSPF, EIGRP, RIP, static) are supported between PE and CE.
  - Redistribution between routing protocols inside the VRF may be necessary.
  - OSPF in VRFs can be complex and might require separate process IDs and sham links for discontiguous areas.

- **Layer 2 VPN Specifics:**
  
  - Uses the `xconnect` command on PE interfaces to establish Layer 2 tunnels.
  - Forms **targeted LDP sessions** for signaling Layer 2 circuits across the MPLS core.
  - Customer sites appear connected on the same Layer 2 broadcast domain.
  - No VRF-aware routing needed for L2VPN.

---

### Summary Table of MPLS VPN Components and Functions

| Component                     | Function/Description                                                    |
| ----------------------------- | ----------------------------------------------------------------------- |
| MPLS (NLS)                    | Label-based packet forwarding service, not a protocol                   |
| IGP (OSPF/ISIS)               | Provides routing inside MPLS core and advertises loopbacks              |
| LDP                           | Distributes MPLS labels for forwarding paths                            |
| PE Router                     | Connects to customer sites, runs VRFs, applies VPN labels               |
| P Router                      | MPLS core routers, label switch packets, no customer connection         |
| VRF                           | Virtual routing table per customer                                      |
| Route Distinguisher (RD)      | Makes customer routes globally unique                                   |
| Route Target (RT)             | Controls route import/export between VRFs                               |
| BGP VPNv4                     | Exchanges VPN routes between PE routers                                 |
| Xconnect                      | Creates Layer 2 VPN tunnels between PE devices                          |
| PHP (Penultimate Hop Popping) | Removes transport label one hop before PE device to simplify forwarding |

---

### Key Insights and Best Practices

- **Understanding the distinction between Layer 2 and Layer 3 VPNs is fundamental.** Layer 3 VPNs route IP traffic with VRFs and BGP VPNv4; Layer 2 VPNs bridge traffic without IP routing.
- **IGP and LDP must be properly configured and converged** for MPLS forwarding to work; loopback interfaces with /32 masks on PE routers are critical.
- **BGP VPNv4 is the backbone technology enabling PE-to-PE route exchange,** and route reflectors can simplify peering in large networks.
- **VRFs isolate customer routing domains and handle overlapping IP spaces** via route distinguishers and route targets.
- **Layer 2 VPNs require xconnect and targeted LDP tunnels** for bridging customer Layer 2 segments.
- **VRF-aware routing protocols allow customer routing protocols to function over MPLS VPNs;** multiple protocols are supported.
- **Route leaking and advanced features like EVN (Easy Virtual Networking) and multi-topology routing exist** but are beyond the basic scope.
- **Operational troubleshooting often involves checking IGP/LDP status, loopback reachability, MPLS forwarding tables, and BGP VPNv4 peerings.**

---

### Additional Notes

- The instructor emphasizes this overview is theoretical; configuration and demos are planned for future content.
- The content is oriented toward service provider environments but applies to enterprise MPLS VPN deployments.
- The speaker shares personal certification experience and study approach, encouraging deep understanding over memorization.
- Some advanced topics such as inter-AS VPNs, multicast, traffic engineering, and L2TPv3 are *Not specified/Uncertain* in this overview.

---

This summary encapsulates the detailed conceptual and operational breakdown of MPLS Layer 3 and Layer 2 VPNs as presented in the video, providing a solid foundation for further study or practical implementation.
