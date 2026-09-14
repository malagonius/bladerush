# 13. Combat Actions

This document records the player action types discussed for the turn-based combat system. It complements `05-combat-system.md`, which focuses on the core combat, Energy, positioning, and defense rules.

## Player Phase

At the start of the player's turn, they gain Energy. During the Player Phase, they choose how to use their available actions and resources.

The current action categories are:

### ⚔️ Attack

The basic offensive action.

- Uses Energy.
- Energy determines the available slash/combo length.
- The player performs directional slash inputs.
- Build effects can care about the exact slash sequence.
- The full committed Energy amount is consumed when the combo begins.
- Unused Energy is lost at the end of the turn.

### 🔥 Cast Spell

Spells are a separate offensive/action category from the basic slash combo.

- **Casting a spell does not use Energy.**
- Spells use a separate resource.
- The exact spell resource is still TBD.
- Spells therefore compete with other spell-resource decisions rather than directly reducing the player's available slash count.

This distinction is intentional: Energy is primarily the temporary resource governing melee combo opportunity and repositioning, while spells should have their own economy.

### 🧪 Use Potion

Potion use is another possible Player Phase action.

- Potions are not part of the basic slash combo.
- Their exact resource/availability and whether potion use consumes another action are TBD.

### Other Actions

The system may support additional Player Phase actions as the design develops.

The exact action economy outside attacks, spells, potions, and repositioning remains TBD.

## Action Economy Principle

The current direction is **not** to force every player action into Energy.

Energy has a specific role:

> **Energy represents the player's temporary offensive opportunity and mobility budget for the turn.**

This allows different action systems to coexist without making every mechanic simply compete for the same resource.

## Current Turn Model

The broad turn structure is therefore:

1. Enemy intent is visible/declared.
2. Player starts the turn and gains Energy.
3. Player uses available actions, including attacks, spells, potions, and repositioning as appropriate.
4. The player's offensive/action sequence resolves.
5. Enemy performs its previously declared intent.
6. Position determines which enemy attacks can hit.
7. Defensive opportunities can be used where applicable.
8. Unused defensive opportunities may be retained.
9. Next turn begins.

Exact action ordering, whether multiple non-attack actions can be performed in one turn, spell-resource rules, potion rules, and animation timing remain TBD.
