# Networking Fundamentals — Practical

## Objective

Practice basic networking commands, inspect network configuration, test connectivity, resolve domain names, and understand network routes and listening ports.

## Task 1: Practice from DevOps-Heroes

Repository: [DevOps-Heroes](https://github.com/NamanKajla/DevOps-Heroes)

Reviewed the networking session material and practiced the networking commands covered in the repository.

## Task 2: Networking Commands and Observations

### 1. `ifconfig` — Network Interfaces

**Command (macOS):**

```bash
ifconfig
```

**Observation:** Displays network interfaces, IP addresses, MAC addresses, and interface status.

**Output/Screenshot:** Add terminal screenshot here.

### 2. `ping` — Connectivity Testing

**Command:**

```bash
ping -c 4 google.com
```

**Observation:** Sends four packets to test connectivity and displays response times and packet-loss statistics.

**Output/Screenshot:** Add terminal screenshot here.

### 3. `nslookup` — DNS Resolution

**Command:**

```bash
nslookup google.com
```

**Observation:** Queries DNS to find the IP addresses associated with a domain name.

**Output/Screenshot:** Add terminal screenshot here.

### 4. `traceroute` — Network Route

**Command:**

```bash
traceroute google.com
```

**Observation:** Shows the network hops taken toward a destination. Some routers may not respond to traceroute probes.

**Output/Screenshot:** Add terminal screenshot here.

### 5. `curl` — HTTP Request

**Command:**

```bash
curl -I https://example.com
```

**Observation:** Sends an HTTP HEAD request and displays response headers, including the HTTP status code when a response is received.

**Output/Screenshot:** Add terminal screenshot here.

### 6. `netstat` — Network Connections

**Command (macOS):**

```bash
netstat -an
```

**Observation:** Displays network connections and listening sockets, including their addresses and ports.

**Output/Screenshot:** Add terminal screenshot here.

### 7. `ipconfig` — Local IP Address

**Command (macOS):**

```bash
ipconfig getifaddr en0
```

**Observation:** Displays the IPv4 address assigned to the `en0` interface when it has one. The active interface may differ depending on the system.

**Output/Screenshot:** Add terminal screenshot here.

### 8. `route` — Default Gateway

**Command (macOS):**

```bash
route -n get default
```

**Observation:** Displays information about the default route, including the gateway used for destinations without a more specific route.

**Output/Screenshot:** Add terminal screenshot here.

## Additional Linux Commands

The following commands are useful when practicing in Ubuntu:

```bash
ip addr
ip route
ss -tuln
```

- `ip addr`: Displays network interfaces and their IP addresses.
- `ip route`: Displays the routing table.
- `ss -tuln`: Displays listening TCP and UDP sockets with numeric addresses and ports.

## Conclusion

Practiced networking commands to inspect local interfaces, test connectivity, resolve DNS names, trace network routes, examine HTTP responses, and view connections and routing information.

