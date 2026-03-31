# Tales of Pirates Server – Gameplay Systems Refactoring & MMO Design

## Project Context

This project represents a heavily customized gameplay scripting layer for a Tales of Pirates MMORPG server.

The server uses Lua as its primary scripting language to control most gameplay logic including combat behavior, item interactions, world events, NPC services, and player progression.

Most of the development took place inside the `GameServer/Custom` directory, which functions as an extension layer that overrides and improves the original server scripts.

Originally, the project started as a personal hobby focused on experimenting with gameplay mechanics and understanding how MMORPG servers operate internally. Over time, the scope expanded significantly as the project evolved into a potential long-term server capable of generating revenue if successfully launched.

Although the server never became publicly available, the project became a long-term technical learning environment that helped develop programming skills, system design thinking, and persistence when dealing with large and complex systems.

Development lasted approximately **three years**, during which nearly every gameplay mechanic of the original game was analyzed, tested, iterated, and documented.

---

## Development Philosophy

A large portion of the work focused not on adding completely new systems, but on **refactoring and restructuring existing gameplay mechanics** in order to make them clearer, scalable, and easier to maintain.

Many original scripts were difficult to read, tightly coupled, or duplicated logic across multiple files.

The goal of the refactoring process was to reorganize the scripting layer using modern programming principles such as:

- **SOLID** – separating responsibilities across modules
- **KISS** – simplifying overly complex logic
- **DRY** – avoiding duplicated code and reusable patterns

Instead of constantly introducing new mechanics, the focus shifted toward improving the internal structure of the existing gameplay systems so they could be safely expanded and balanced over time.

---

## Gameplay Systems

### NPC Interaction Systems

Custom NPC scripts provide several services used by players throughout the game world.

Examples include:

- teleportation services between cities and maps
- service NPCs related to progression systems
- event-related NPC interactions

These systems rely on modular dialogue scripts and conditional logic based on player state, items, or progression status.

📷 Screenshot suggestion  
`screenshot-here: custom NPC interaction window`

---

### Combat and Damage Calculations

The combat pipeline was reorganized into a clearer calculation structure.

Instead of scattered formulas across multiple scripts, damage calculations were consolidated into dedicated modules responsible for:

- base damage computation
- map-specific modifiers
- set bonuses
- pet skills mechanics
- Player skill interactions
- item usage

This restructuring allowed combat balancing to be performed in a controlled and centralized manner.

---

### Experience and Progression

Experience gain and progression rules were adjusted to provide better control over server pacing.

Examples include:

- level-based experience scaling
- configurable experience limits
- map-specific experience modifiers
- improved party experience distribution

These changes helped ensure progression remained consistent while highly customizable.

---

### Item Systems

The server includes a modular item-effect system where each item type defines its behavior through a dedicated Lua handler.

Examples of item functionality include:

- reward chests
- crafting materials
- experience boosters
- progression items
- reset and utility items

The goal of the refactoring process was to make item behaviors reusable and easier to extend.

---

### World Events

Several automated world events are implemented through server scripts.

These include:

- scheduled drop events
- level progression contests
- battleground-style map events
- automated server announcements

A cron-style timer system is used to trigger events based on time schedules.

📷 Screenshot suggestion  
`screenshot-here: event announcement or drop event`

---

### Battleground and Map Systems

Custom map scripts define the behavior of competitive maps and event maps.

These scripts manage:

- player entry conditions
- team balancing
- event timers
- reward distribution
- map-specific rules

The scripting structure allows each map to implement its own rule system without interfering with other gameplay areas.

📷 Screenshot suggestion  
`screenshot-here: battleground event map`

---

## Script Architecture

The scripting layer uses a modular loader structure.

### Loader System

The primary loader is located at:
GameServer/Custom/index.lua


This script loads the various subsystems in a deterministic order.

Each module contains its own `index.lua` loader that registers the scripts belonging to that subsystem.

This architecture allows features to be enabled, disabled, or modified without affecting unrelated gameplay systems.

---

### Hook System

The project uses a hook-based system to intercept existing server behavior.

Hooks allow scripts to attach to original server functions using:

- replacement hooks
- pre-execution hooks
- post-execution hooks

This approach makes it possible to extend or override default game behavior while maintaining compatibility with the underlying server engine.

---

### Command System

A chat-command system allows administrators to execute commands directly inside the game client.

Commands support:

- argument parsing
- permission validation
- command dispatching

This system provides operational control over server behavior without requiring direct server access.

---

## Game Economy Design

Designing a stable in-game economy proved to be one of the most complex challenges of the project.

A healthy MMORPG economy requires constant interaction between players through trading and resource exchange.

A common principle used during development was:

> *A server where nobody buys or sells items is a dead server.*

Two economic extremes were avoided:

**Resource inflation**

If valuable resources become too easy to obtain, they quickly lose value and player trading activity collapses.

**Resource scarcity**

If resources are too rare, new players cannot compete with veterans, creating a large power gap and discouraging player retention.

To balance this system, the design focused on **diversifying resource acquisition**.

Different activities generate different types of resources:

- PvE hunting activities
- dungeon rewards
- world events
- item-based progression systems

This diversification encourages player-to-player trading and helps maintain a dynamic in-game economy.

---

## Security Research

During development it became clear that many publicly distributed MMORPG server sources contain serious vulnerabilities.

Examples include:

- SQL injection vulnerabilities
- hidden backdoors
- item duplication exploits
- client asset manipulation
- lack of protection against automated attacks

A considerable amount of time was spent researching these vulnerabilities and implementing mitigations.

However, security in MMORPG servers is never a one-time solution. It requires continuous monitoring and adaptation as new exploits are discovered.

---

## Development Challenges

One of the biggest challenges during development was learning how to work with large legacy systems.

Many original scripts were difficult to understand due to poor organization or lack of documentation.

The development process involved:

- analyzing existing scripts
- reorganizing systems
- simplifying complex logic
- ensuring compatibility with the server engine

Another major challenge was learning **C++** in order to modify parts of the original server and client source code when scripting limitations were encountered.

This experience reinforced an important lesson:

> There are no magic solutions in programming.

Large systems require patience, persistence, and repeated iteration to improve over time.

---

## Outcome

Although the server never launched publicly due to the operational challenges of running and monetizing a private MMORPG server, the project provided extensive practical experience.

Over roughly **three years of development**, the project involved:

- editing and refactoring around **50 Lua scripts**
- contributing to the design and testing of **150+ gameplay scripts**
- testing and iterating nearly every gameplay mechanic in the game

More importantly, the project provided experience across multiple disciplines:

- programming and scripting
- multiplayer game systems
- game economy design
- server security
- tooling and infrastructure
- long-term system maintenance

The project ultimately demonstrated that large systems evolve through continuous iteration rather than sudden breakthroughs.

---

## Technologies Used

- **Lua**
- Tales of Pirates server scripting engine
- C++ (server/client modifications)
- Sql 