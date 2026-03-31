# Climb & Fight

Climb & Fight is a gameplay prototype exploring chaotic vertical traversal and player interaction in a competitive climbing environment.

The project was designed as a short-scope experiment to explore gameplay systems, code architecture, and rapid prototyping under tight constraints.

---

## Motivation

Climb & Fight started as a small experiment to test my ability to standardize gameplay architecture, design a complete prototype, and document the process within a limited scope.

The guiding question behind the project was:

**“What is the best game I can build today using only the tools and assets I already have?”**

Rather than planning a large project that might never reach completion, I  constrained the scope to a prototype that could become playable very quickly.

The initial goal was extremely ambitious: **a playable prototype in seven days.**

During development I completed most of the planned systems in the first two days. However, after spending nearly six hours adjusting the camera behavior on the third day, it became clear that the full prototype would require more time than originally planned.

Despite that, the project progressed steadily and became a valuable exercise in scope control and rapid iteration.

Another motivation behind the project was returning to **game design thinking**. After spending a long period focusing on programming fundamentals and learning Unity systems, I wanted to return to designing gameplay experiences now that I could implement my own systems directly.

---

## Design Constraints

The project was developed under several constraints:

- Limited asset set
- Solo development
- Very short prototype timeline
- Focus on gameplay systems rather than content

Because of these limitations, the design focuses on a **single environment concept** where variation comes from gameplay systems rather than visual variety.

---

## Core Gameplay Loop

1. Climb upward through a vertical environment  
2. Navigate trap zones  
3. Recover from push or stun disruptions  
4. Maintain momentum while climbing  
5. Reach the top before other players  

The gameplay emphasizes **disruption and recovery** instead of lethal failure.

Mistakes push the player downward rather than restarting the level.

---

## Environment Structure

Although visually framed as a tower, the environment is actually a **procedural climbing path** that extends upward.

Early prototypes used a static tower with random traps. Within seconds of testing it became clear that the experience felt repetitive.

To improve replayability, the environment was redesigned as **procedural scaffold-like paths suspended in empty space**.

Players navigate dynamically generated routes filled with traps and movement challenges.


---

## Player Interaction

During early testing another design question emerged:

**“What if players could push each other?”**

Instead of implementing a full combat system, the prototype focuses on **movement disruption between players**.

Players can briefly push or displace each other while navigating traps.

This creates chaotic interactions without introducing a complex combat system.


---

## Key Systems

### Movement System

The player controller uses Unity's **CharacterController** for deterministic movement.

Features include:

- directional movement
- jump mechanics
- dash / evasion
- stun response
- push displacement

Movement prioritizes **control responsiveness over physical realism**.


---

### Trap System

Traps apply environmental pressure instead of damage.

Examples include:

- falling hammers
- rotating hazards
- moving obstacles

Their purpose is to interrupt player movement and create recovery moments.



---

### Camera System

The camera uses an orbit / follow configuration designed to maintain visibility during vertical traversal.

Maintaining readability in a dense vertical environment was one of the main technical challenges.

---

### Input Abstraction

Player input is abstracted through an interface (`IInputSource`).

This allows the gameplay systems to remain independent from the input device.

Different implementations can plug into the same character controller, including:

- PC keyboard input
- mobile joystick controls
- local test controls inside Unity

This made testing and iteration significantly easier.

---

## Key Technical Decisions

### CharacterController vs Rigidbody

The movement system uses **CharacterController instead of Rigidbody physics**.

This decision was made to maintain precise control while navigating narrow climbing paths.

---

### Gameplay and Presentation Separation

Gameplay logic is separated from presentation systems.

The character motor controls gameplay state while animation and facing systems follow the motor state.

This prevents animation logic from affecting gameplay behavior.

---

## Challenges

### Input System Integration

Adapting to Unity’s new Input System required rethinking how player input should be structured.

The interface-based input system was introduced to keep gameplay code independent from specific input devices.

---

### Camera Readability

Camera behavior in vertical traversal environments proved difficult to balance.

The camera must keep the player visible while also providing enough context to anticipate upcoming traps.

---

### Balancing Chaos vs Fairness

Trap strength had to be carefully tuned.

If traps were too strong, players lost control too often.  
If traps were too weak, the climb lacked tension.

The final approach emphasizes **short disruptions followed by quick recovery**.

---

## Outcome

The prototype resulted in a stable gameplay loop focused on disruption and recovery.

Players are constantly pushed off balance but can quickly regain control and continue climbing.

This creates a rhythm of **movement → disruption → recovery → progress**.

---

## Lessons Learned

Small, focused prototypes are extremely valuable for testing gameplay ideas.

By constraining scope early and focusing on a few core systems, the project was able to reach a playable state while still exploring meaningful gameplay mechanics.

The experience also reinforced the importance of designing systems that allow rapid iteration during early gameplay testing.

---

## Current Status

Prototype in development.

Gameplay systems are functional, while visuals and level variation are still being expanded.

Additional gameplay footage and screenshots will be added as the prototype progresses.