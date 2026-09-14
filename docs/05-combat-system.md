# 5. Combat System

## Core Intent
Combat should be readable, timing-focused, and centered on meaningful offensive and defensive decisions.

The current direction combines the readable enemy intent of *Slay the Spire* with the active defense/timing feel of *Clair Obscur: Expedition 33* and the constrained interaction model of *Infinity Blade* / *Crossed Swords*.

## Current Combat Direction
**Turn-based combat with active defense.**

At the start of the player's turn, they gain **Energy**. Energy is a shared resource for both offense and defense.

The player therefore has to decide:

> How much Energy do I spend attacking now, and how much do I preserve so I can defend against the enemy's declared attack?

### Basic Turn Flow
1. Enemy declares its next attack/intention.
2. Player starts their turn and gains Energy.
3. Player spends Energy on attacks, abilities, and/or preparation.
4. Enemy attack resolves.
5. Player uses their defensive skill/timing when appropriate.
6. Next turn begins.

The exact ordering of attack and defense resolution is TBD.

## Enemy Intent
Enemies should clearly communicate what they intend to do before the action resolves.

Examples:
- Attack direction.
- Attack type.
- Potential damage/effect.
- Other meaningful combat intent.

The goal is not to make combat purely about memorizing enemy patterns. The player should have enough information to make an informed decision, while still needing to execute that decision well.

## Shared Energy
Energy is intentionally shared between offense and defense.

Example:
- Spend most Energy on a powerful attack → less available for defense.
- Attack conservatively → retain Energy for a stronger defensive response.
- Spend very little → potentially preserve resources for a larger future turn.

This creates a recurring **risk/reward decision every turn**, rather than making defense a free reaction layered on top of attacking.

Exact Energy generation, maximum Energy, costs, regeneration, and carry-over are TBD.

## Active Defense
Two defensive interaction styles are currently being explored.

### Directional Defense
The player chooses the correct direction for the incoming attack.

- Correct direction = **Perfect Defense**.
- Incorrect direction = weaker/failed defense.
- Inspired by the directional/readable defense of Crossed Swords / Infinity Blade.

### Timing Defense
The player performs a timed defensive input against the incoming attack.

- Precise timing = **Perfect Defense**.
- Poor timing = weaker/failed defense.
- Inspired by the active timing mechanics of Expedition 33.

Both approaches should consume Energy using the same underlying defensive resource model.

It is TBD whether both systems coexist as separate options, are used by different abilities/builds, or whether one becomes the primary defense system.

## Offensive Interaction
The player should have meaningful ways to spend Energy offensively.

Candidate actions:
- Basic attack.
- Directional attack.
- Heavy attack.
- Special/run-specific abilities.
- Other build-dependent attacks.

Exact attack structure, combos, attack direction, and Energy costs are TBD.

## Encounter Model
- Primarily 1v1 encounters are currently favored.
- Enemies present readable attack intents.
- Player decisions determine how aggressively they can attack while maintaining enough Energy to defend.
- Successful defense can create advantages such as damage prevention, stagger, counterattack opportunities, or other openings.
- Enemy behavior should create distinct combat problems rather than only increasing health/damage.

## Design Principles
- **Defense is a decision, not a free reaction.**
- **Energy creates tension between aggression and safety.**
- **Enemy intent provides information; execution still matters.**
- **Player skill should matter more than grinding.**
- **Combat should remain readable even as builds and enemy behavior become more complex.**

## Core TBD Questions
- Exact turn ordering: when does enemy intent appear and when does defense resolve?
- Exact Energy model: starting amount, gain, maximum, costs, carry-over.
- Whether attacks consume Energy individually or use fixed action costs.
- Whether Directional Defense and Timing Defense coexist.
- Whether defense can be performed only after committing Energy or as part of the enemy's resolution.
- Exact Perfect Defense benefits.
- Failure consequences for defensive actions.
- Health, armor, stagger, wounds, and healing rules.
- Whether dodge exists alongside the defensive system.
- Number of simultaneous enemies.
- Movement and positional mechanics.
- Attack chaining/combos.
- Whether enemy attacks can be interrupted.
