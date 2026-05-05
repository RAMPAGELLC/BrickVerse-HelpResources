# Understanding Game Servers & Matchmaking

BrickVerse automatically manages game servers and infrastructure for developers. You do not need to manually provision machines, scale capacity, or clean up idle servers — the platform handles this dynamically based on player activity and server demand.

### Overview

When a player joins a world:

1. BrickVerse attempts to find an existing available server
2. If no server capacity exists, the platform automatically provisions a new VM node
3. A world server container is started on that node
4. The server is registered for discovery and matchmaking
5. Players are routed into the available server automatically

This entire process is managed by the BrickVerse orchestration system and Azure-backed infrastructure.

***

## Infrastructure Model

### VM Nodes

A **VM Node** is a cloud virtual machine that hosts one or more game server instances.

Current platform limits:

* Maximum servers per VM node: **3**

Nodes run:

* Ubuntu 22.04
* Docker
* BrickVerse Node Daemon
* Game server containers pulled from the platform container registry

***

## Server Lifecycle

### Server Creation

When a world requires a new server:

* The platform checks for existing VM nodes with remaining capacity
* If no node has room, a new VM node is automatically provisioned
* The node daemon becomes available
* A free network port is assigned
* The game server container is launched
* The server becomes discoverable by matchmaking

The orchestration layer includes retry handling and exponential-style recovery logic to deal with:

* Nodes still booting
* Temporary daemon outages
* Port exhaustion
* Transient infrastructure failures

***

## Matchmaking Behavior

BrickVerse matchmaking is capacity-aware.

The platform:

* Prefers already-running servers when capacity exists
* Spins up new servers only when needed
* Automatically distributes servers across VM nodes
* Handles node selection internally

Developers do not need to:

* Reserve ports
* Allocate machines
* Configure Docker manually
* Handle autoscaling logic
* Manage orchestration infrastructure

***

## Idle Server Shutdowns

To reduce infrastructure waste and keep the platform healthy, BrickVerse automatically removes idle servers and nodes.

### Idle World Servers

A world server is automatically terminated when:

* It has **zero active players**
* It has existed for longer than **3 minutes**

This means:

* Empty servers are temporary
* Servers are not intended to stay alive forever
* Developers should not rely on servers persisting after players leave

Cleanup runs every **10 minutes** via CRON scheduling, theoretically allowing inactive servers for up to 10 minutes.

***

## Idle VM Node Shutdowns

VM nodes are automatically removed when:

* They contain **no active world servers**
* They have existed for longer than **3 minutes**

This helps:

* Reduce unnecessary cloud costs
* Keep infrastructure scalable
* Avoid idle compute waste

Cleanup runs every **15 minutes**.

***

## Node Rotation & Fleet Health

BrickVerse also rotates infrastructure automatically.

Any VM node older than:

* **24 hours** will be automatically destroyed and reprovisioned.

This improves:

* Fleet stability
* Security hygiene
* Long-term daemon reliability
* Infrastructure consistency

Rotation cleanup runs every **30 minutes**.

***

## Important Developer Notes

### Do Not Depend on Permanent Servers

World servers are considered ephemeral infrastructure.

You should:

* Persist important data externally
* Save player state continuously
* Avoid relying on in-memory state surviving indefinitely

Servers may shut down due to:

* Player inactivity
* Infrastructure rotation
* Node health issues
* Fleet cleanup operations

***

### Server Startup Delays

New servers may take a short time to start if:

* A new VM node must first be provisioned
* Docker images need pulling
* Infrastructure is scaling up

The orchestration system retries automatically during startup failures or temporary daemon issues.

***

## Fault Tolerance

The system includes automatic recovery behavior for:

* Offline node daemons
* Failed server creation
* Missing ports
* Temporary communication failures
* Unhealthy nodes

If a server creation fails:

* The database registration is rolled back
* Another attempt is made automatically

***

## Health Monitoring

BrickVerse continuously checks node daemon health. If a daemon becomes unreachable or unhealthy, the orchestration layer can mark the node offline and replace it.
