title: MicroServices
author:
  name: Tom Wilson
  twitter: twilson63
  url: http://jackrussellsoftware.com
output: index.html
controls: true

--

# MicroServices

--

### WHOAMI

* Tom Wilson (@twilson63)
* Lead Technologist for Jack Russell Software, A Tabula Rasa Healthcare Division
* <3 JavaScript/ES
* <3 NodeJS/IO.JS
* <3 CouchDB/PouchDB
* <3 Angular1/Mercury

--

### Terms

* Monolithic Application
* MicroServices

--

# Monolithic Application
An application that is built as a single unit

--

### Monolithic Application

    +---------------+           +-----------------+
    |               |           |                 |
    |               |           |                 |
    |  Application  +---------->|   Database      |
    |               |           |                 |
    |               |           |                 |
    |               |           |                 |
    +---------------+           +-----------------+

--

### Monolithic Application



    +---------------+           +-----------------+
    |               |           |                 |
    |               |           |                 |
    |  Application  +---------->|   Database      |
    |               +           |                 |
    |               |           |                 |
    |               |           |                 |
    +------+--------+           +-----------------+
          +
    +---------------+           +-----------------+
    |               |           |   Services      |
    |  Caching      |           |-----------------|
    |               +-----------+                 |
    |               |           |                 |
    |               |           |                 |
    +---------------+           +-----------------+

--

### In Process Components


    +-------------------------------------------------------------------+
    | Application                                                       |
    |                   +----------+                +--------------+    |
    | +----------+      |          |                |              |    |
    | |          |      | Component|                | Component    |    |
    | | Component|      |          |                |              |    |
    | |          |      |          |                |              |    |
    | |          |      +----------+                |              |    |
    | +----------+                                  |              |    |
    |                                               +--------------+    |
    |                                                                   |
    |  +-------------+         +-------------+                          |
    |  |             |         |             |                          |
    |  | Component   |         |             |                          |
    |  |             |         | Component   |                          |
    |  |             |         |             |                          |
    |  |             |         |             |      +--------------+    |
    |  +-------------+         |             |      |              |    |
    |                          |             |      | Component    |    |
    |                          +-------------+      |              |    |
    |                                               |              |    |
    |                                               |              |    |
    |                                               +--------------+    |
    |                                                                   |
    +-------------------------------------------------------------------+

--

### MicroServices


    +------------+        +--------------+
    |            |        |              |     +----------------+
    | Application|        | Component    |     |                |
    |            |        |              |     | Component      |
    |            |        |              |     |                |
    |            |        |              |     |                |
    +------------+        +--------------+     |                |
                                               |                |
        +------------+                         +----------------+
        |            |
        |            |
        |  Component |      +---------------+
        |            |      |               |
        |            |      |  Component    |
        |            |      |               |   +-----------------+
        +------------+      |               |   |                 |
                            |               |   |  Component      |
                            |               |   |                 |
                            +---------------+   |                 |
        +----------------+                      |                 |
        |                |                      |                 |
        |  Component     |                      +-----------------+
        |                |
        |                |
        |                |
        |                |
        +----------------+

--

## MicroServices is about Team Organization too

--

### Conway's Law

> Any organization that designs a system (defined broadly) will produce a design whose
> structure is a copy of the organization's communication structure.

--

### Technical Domains



    +---------------+ +---------------+ +----------------+ +----------------+ +---------------+
    |               | |               | |                | |                | |               |
    |               | |               | |                | |                | |               |
    |               | |               | |                | |                | |               |
    |               | |               | |                | |                | |               |
    |               | |               | |                | |                | |               |
    |               | |               | |                | |                | |               |
    |   Designers   | | Front End     | | Backend Devs   | | DevOps         | | DBA's         |
    |               | |               | |                | |                | |               |
    |               | |               | |                | |                | |               |
    |               | |               | |                | |                | |               |
    |               | |               | |                | |                | |               |
    |               | |               | |                | |                | |               |
    |               | |               | |                | |                | |               |
    |               | |               | |                | |                | |               |
    |               | |               | |                | |                | |               |
    |               | |               | |                | |                | |               |
    |               | |               | |                | |                | |               |
    |               | |               | |                | |                | |               |
    |               | |               | |                | |                | |               |
    |               | |               | |                | |                | |               |
    +---------------+ +---------------+ +----------------+ +----------------+ +---------------+

--

### Business Domains


    +----------------+
    |                |       +-----------------+
    |  Product A     |       |                 |
    |                |       |                 |       +-----------------------------------+
    |                |       |  Product C      |       | Services                          |
    |                |       |                 |       |-----------------------------------|
    +----------------+       |                 |       |                                   |
                             |                 |       |  * Service 1                      |
    +----------------+       +-----------------+       |  * Service 2                      |
    |                |                                 |  * Service 3                      |
    |  Product B     |                                 |  * Service 4                      |
    |                |                                 |                                   |
    |                |   +------------------+          |                                   |
    |                |   |                  |          |                                   |
    |                |   |                  |          |                                   |
    +----------------+   |  Product D       |          |                                   |
                         |                  |          |                                   |
                         |                  |          |                                   |
                         |                  |          |                                   |
                         |                  |          |                                   |
                         +------------------+          |                                   |
                                                       |                                   |
                                                       |                                   |
                                                       |                                   |
                                                       +-----------------------------------+

--

### Addressing the Need for Complexity

http://12factor.net/

* Multiple Presentation Layers
* Cross-Functional Features
* Multiple Persistent Models
* Multi-Site Replication
* Central Logging
* Multiple Languages
* Feature Experiementation

--

### MicroServices Platform


    +-----------------------+                     +------------------------+ +-------------------+
    | Platform as a Service |                     |  Platform as a Service | | Data Containers   |
    |-----------------------|                     |------------------------| |-------------------|
    | * App 1               |      xxxxxxxx       |  * Service 1           | | +-------+         |
    | * App 2               |    xxx      xxx     |  * Service 2           | | | SQL   |         |
    | * App 3               |   xx          xx    |  * Service 3           | | |       |         |
    | * App 4               |   x            x    |  * Service 4           | | +-------+         |
    |                       |  xx            x    |                        | | +-------+         |
    |                       |  xx            x    |                        | | | NoSQL |         |
    |                       |   xx          xx    |                        | | |       |         |
    |                       |    xxx      xxx     |                        | | +-------+         |
    |                       |      xxxxxxxx       |                        | | +-------+         |
    |                       |                     |                        | | | Redis |         |
    |                       |    Pub/Sub/Log      |                        | | |       |         |
    |                       |                     |                        | | +-------+         |
    |                       |                     |                        | |                   |
    |                       |                     |                        | |                   |
    +-----------------------+                     +------------------------+ +-------------------+

--

### Pushes Complexity to Automation

* Components
* Services

--

# Product Based, not Project Based

--

# Smart endpoints and dumb pipes

--

# Decentralized Governance

--

# Decentralized Data Management

--

# Infrastructure Automation

--

# Design for failure

--

# Evolutionary Design

--

### Resources

http://martinfowler.com/articles/microservices.html
https://github.com/twilson63/palmettoflow

