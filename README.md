[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/-jWdCFXs)
## Project 00
### NeXTCS
### Period: 
## Thinker0: Mohammed Ullah mohammedu74@nycstudents.net
## Thinker1: Franklin Li franklinl28@nycstudents.net
---

This project will be completed in phases. The first phase will be to work on this document. Use github-flavoured markdown. (For more markdown help [click here](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) or [here](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax) )

All projects will require the following:
- Researching new forces to implement.
- Method for each new force, returning a `PVector`  -- similar to `getGravity` and `getSpring` (using whatever parameters are necessary).
- A distinct demonstration for each individual force (including gravity and the spring force).
- A visual menu at the top providing information about which simulation is currently active and indicating whether movement is on or off.
- The ability to toggle movement on/off
- The ability to toggle bouncing on/off
- The user should be able to switch _between_ simluations using the number keys as follows:
  - `1`: Gravity
  - `2`: Spring Force
  - `3`: Drag
  - `4`: Custom Force
  - `5`: Combination


## Phase 0: Force Selection, Analysis & Plan
---------- 

#### Custom Force: Megalophobia

### Custom Force Formula
What is the formula for your force? Including descriptions/definitions for the symbols. (You may include a picture of the formula if it is not easily typed.)
f = s_a - s_b/d * ab * p
f is the force exerted on orb b
s_a is the bsize of orb a
s_b is the bsize of orb b
d is the distance between orb a and orb b
ab is the normalized vector between orb a and orb b
p is a constant that will be used to change the magnitude of the force, it will be 2, and then for each orb that exists, 0.1 will be subtracted from it
### Custom Force Breakdown
- What information that is already present in the `Orb` or `OrbNode` classes does this force use?
  - The PVector center
  - The bsize values

- Does this force require any new constants, if so what are they and what values will you try initially?
  - Possibly, a scaling constant may be needed to keep the force stable and prevent extreme values, it will depend on the number of orbs currently present, scaling down, as orbs are removed.

- Does this force require any new information to be added to the `Orb` class? If so, what is it and what data type will you use?
  - All necessary values are in Orb already or can be calculated using values in Orb

- Does this force interact with other `Orbs`, or is it applied based on the environment?
  - This force interacts with other orbs. Orb b feels a force based on the size difference between orb a and orb b.

- In order to calculate this force, do you need to perform extra intermediary calculations? If so, what?
  - Yes, compute distance between orb centers, compute normalized direction vector, and compute s_a - s_b

--- 

### Simulation 1: Gravity
Describe how you will attempt to simulate orbital motion.

A large orb stays near the center while a smaller orb moves around it. Gravity pulls the smaller orb inward, creating an orbit‑like path.

--- 

### Simulation 2: Spring
Describe what your spring simulation will look like. Explain how it will be setup, and how it should behave while running.

Two orbs are connected by a spring with a chosen rest length. Both orbs start slightly away from that rest length. The spring pulls the orbs toward the rest length. They overshoot, bounce back, and continue oscillating. 

--- 

### Simulation 3: Drag
Describe what your drag simulation will look like. Explain how it will be setup, and how it should behave while running.

An orb begins with some initial velocity. A drag force is applied that should always oppose the direction of motion. The orb slows down over time. Its movement becomes smaller and smaller until it eventually comes to a stop as drag removes its energy.

--- 

### Simulation 4: Custom force
Describe what your Custom force simulation will look like. Explain how it will be setup, and how it should behave while running. 

A large orb and a smaller orb are placed in the space. The custom force uses the size difference and distance between them to calculate a repelling effect. The smaller orb moves away from the larger one. A bigger size difference creates a stronger push, causing the small orb to flee more dramatically. Aditionally, when 2 orbs completely overlap, the smaller orb will be removed and the size and mass will be added to the larger orb. The fixed orb will not be affected by this.

--- 

### Simulation 5: Combination
Describe what your combination simulation will look like. Explain how it will be setup, and how it should behave while running.

Multiple orbs are placed in the space, and all forces are active at the same time. Because all forces act on all orbs simultaneously, the motion is complicated. Orbs curve when they’re orbiting, bounce by springs, slow down from drag, and move away from the nearest larger orb due to the megalophobia force.

