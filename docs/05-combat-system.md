# 5. Combat System

## Core Intent
Combat should be readable, timing-focused, and centered on meaningful offensive and defensive decisions.

The current direction combines the readable enemy intent of *Slay the Spire* with active-defense/timing inspiration from *Clair Obscur: Expedition 33* and the constrained interaction model of *Infinity Blade* / *Crossed Swords*.

The goal is **not** to make combat a pure reaction test. The player should make meaningful decisions about offense, defense, position, and build resources before and during enemy resolution.

## Current Combat Direction
**Turn-based combat with active offense, visible enemy intent, randomized defensive opportunities, and positional defense.**

The player always has offensive agency. Defensive options are constrained by a hidden deck, creating controlled randomness similar to drawing cards in *Slay the Spire* without requiring the player-facing system to literally be a card game.

## Basic Turn Flow
1. Enemy intent is visible/declared.
2. Player starts their turn and gains Energy.
3. Player chooses how to spend the turn's Energy on attacks and/or repositioning.
4. The player's combo/action sequence resolves.
5. Enemy performs its previously declared intent.
6. The player's current position determines which enemy attacks can hit.
7. Available defensive opportunities can be used to mitigate or avoid applicable attacks.
8. Unused defensive opportunities may be retained according to the hand rules.
9. Next turn begins.

Exact timing/animation ordering remains implementation-level TBD.

---

## Energy

Energy is the primary temporary offensive resource and is intentionally spent or lost each turn.

### Energy and combos
Energy determines the player's available slash count for a combo.

Example:
- Start the turn with **5 Energy**.
- Start an attack combo.
- The combo can contain up to **5 slashes**.
- The entire Energy amount committed to the combo is consumed/committed when the combo begins rather than being spent one slash at a time.

The player can execute the combo slowly or rapidly. The final input is currently simply the **end-of-combo / finisher marker**; the baseline final slash has no inherent special bonus.

A short input lockout after the final slash may be used to prevent accidental input leakage/mashing (exact duration TBD).

### Energy does not carry over
Unused Energy is lost at the end of the turn.

If the player has 5 Energy:
- Use 5 → 5 slashes available.
- Use 3 → the remaining 2 Energy is lost.
- Do not attack → all 5 Energy is lost.
- The player cannot save 5 Energy and then gain 5 more next turn to create a 10-Energy turn.

Energy is therefore a **temporary offensive opportunity**, not a bankable resource.

### Repositioning cost
Changing position costs **1 Energy regardless of the distance moved** within the three-position combat space.

This creates a direct tradeoff between mobility and offensive combo length.

---

## Offensive Interaction

### Directional slashes
The player attacks through directional slash inputs. Current conceptual directions include:
- ↑ Up
- ↓ Down
- ← / → Horizontal directions
- Diagonal directions may exist where useful

The exact complete input vocabulary is TBD.

The player can learn or acquire effects that make particular slash directions more valuable.

### Sequence-based build mechanics
Build effects can care about the sequence of slashes rather than merely total damage.

Examples:
- Every 2 Down Slashes → gain a free Uppercut.
- ↑ attacks deal increased damage.
- ↘ followed by ↗ causes Bleed.
- After 3 horizontal slashes → gain a free heavy attack.
- ↓ → ↓ triggers a special effect.
- ↑ → ↘ grants a defensive benefit.
- 3 different directions → empower the next attack.
- Repeating the same direction → creates a stronger hit.

These are examples of the desired design space, not a final list of effects.

The important distinction is:
- **Player skill:** physically executing the desired slash sequence.
- **Build logic:** determining why that sequence is valuable during the current run.

### Combo modifiers
Run rewards/powerups may modify the combo system by:
- Extending the combo.
- Granting free slashes.
- Refunding Energy.
- Altering the next slash.
- Repeating a previous slash.
- Forcing a follow-up.
- Rewarding or restricting particular sequences.
- Giving the final slash a special effect.

A final slash is not inherently special unless a build effect explicitly makes it special.

---

# Positioning

Combat uses exactly three player positions:

```text
LEFT - CENTER - RIGHT
```

The position system is a core part of both offense and defense.

## Position as defense
The player's current position determines where they physically are and therefore which enemy attack zones can hit them.

An enemy attack covers one or more positions.

Example:

```text
15 | 3 | 3
 L   C   R
```

If the player is on RIGHT, the 15-damage LEFT attack and the CENTER attack miss automatically; the RIGHT attack can hit.

If multiple enemy attacks cover the player's current position, all applicable attacks can hit and must be dealt with.

Wide attacks are therefore supported naturally:
- Single-position attack: covers one position.
- Two-position attack: covers two adjacent positions.
- Potentially three-position attack: covers the whole combat space.

The exact visual notation is implementation/presentation TBD.

## Dodge is repositioning
The old concept of Dodge as a generic tap-to-dodge reaction is replaced by the position model.

**Dodge means changing position.**

- Repositioning costs 1 Energy.
- The player chooses where to move.
- The new position persists as a state.
- There is no separate generic "tap dodge" reaction in the baseline system.

This makes Dodge a spatial decision rather than simply a better version of Block or Parry.

## Position as offense
Position also determines attack reach.

The player's position represents their current location and therefore where their attacks can reach.

The baseline rule is:
> **A player's attack can reach their current position plus the adjacent position toward the enemy.**

Therefore:
- Player on LEFT → attacks can reach LEFT + CENTER.
- Player on RIGHT → attacks can reach CENTER + RIGHT.
- Player on CENTER → attacks can reach CENTER plus one adjacent side; the exact directional choice/grammar is TBD.

Position therefore affects both:
1. **Defense:** which enemy attack zones can hit the player.
2. **Offense:** which enemy positions the player can attack.

Moving can make the player safer while simultaneously changing which enemy areas are reachable, and moving consumes Energy that could otherwise extend the offensive combo.

---

# Defensive System

## Design problem
A purely deterministic defense system creates an obvious optimal response: if the player can always perform the best defense, they simply spam it.

Random enemy patterns alone do not solve this because a fixed optimal response can still emerge.

The intended solution is **controlled randomness in the player's available defensive choices** while preserving agency over which available option to use.

> RNG should constrain the player's available choices, not remove meaningful agency.

Randomness should create situations/problems to solve, not decide whether the player is allowed to play well.

## Hidden defensive deck
The player has an internal defensive deck/pool.

The deck is not necessarily displayed as literal cards. It is the probability engine that determines which defensive opportunities are available.

Example starting composition:
- Parry ×2
- Block ×3
- Dodge ×1
- Nothing ×2

Probabilities are determined directly by the relative number of entries.

There is **no separate Parry % stat**. The deck itself defines the probability distribution.

### Deck dilution
Adding a card inherently increases the size of the deck and therefore changes the relative probability of every card.

Example:
- Adding another Parry increases the number of Parry entries.
- It also increases the total deck size.
- Therefore simply spamming one desired card is never automatically optimal.

This dilution is intentional and is a core part of the deckbuilding tradeoff.

---

## Defensive hand / opportunities
At the start of a turn, defensive opportunities are drawn from the hidden deck up to the player's hand-size capacity.

The **hand size is itself a manipulable stat**.

The system behaves similarly to *Slay the Spire*'s retained hand in one important way:
- Unused opportunities can be retained between turns.

But the underlying deck behaves differently from a normal finite draw pile:
- Having an opportunity in hand does **not** remove that card from the drawable deck.
- Using a Parry/Block/Dodge opportunity consumes that current opportunity from the hand.
- The underlying deck remains the probability source for future draws.

This means the player can accumulate useful defensive options while still receiving new opportunities each turn, subject to hand capacity.

The exact draw timing, redraw behavior, and hand-size defaults remain TBD.

---

# Defensive Values

The defensive types represent different things rather than simple variants of the same reaction.

| Defense | Meaning |
|---|---|
| 🧱 Block | Stored damage absorption |
| 🛡️ Parry | Ability to satisfy Parry requirements |
| 💨 Dodge | Spatial repositioning / ability to satisfy Dodge requirements |
| 💀 Nothing | Choosing/not having a defense and taking the consequence |

## Block value
Block has a numeric value and can stack.

Example:
- Gain 15 Block.
- Gain 10 Block.
- Gain 8 Block.
- Total = 33 Block.

A 20-damage hit removes 20 Block, leaving 13 Block and dealing 0 HP damage.

A later 25-damage hit consumes the remaining 13 Block and deals 12 HP damage.

Block is therefore persistent within the relevant combat window rather than being a one-use "Block opportunity".

## Parry value / requirement
Parry is also value-based rather than purely binary.

Some enemy attacks may require more than one Parry unit/value to be fully parried.

Example:
- Enemy attack requires **Parry 3**.
- Player has **Parry 2**.
- The player cannot fully satisfy that Parry requirement with the available value.

The exact behavior of partial Parry, combining Parry with other defenses, and what a successful Parry grants remains TBD.

## Dodge value / requirement
The conceptual value-based Dodge model is retained as a possible additional layer, but the primary Dodge mechanic is now **positioning**.

The key established rule is that position determines whether an attack can hit the player at all. If attacks later use explicit Dodge requirements, those requirements must coexist with the spatial position rules rather than replacing them.

Exact value interactions remain TBD.

---

# Nothing / Taking the Hit

"Nothing" is a real tactical outcome, not a failed draw.

If the player has no suitable defense—or deliberately chooses not to spend one—the attack hits them.

The current proposed rule is:
> **Taking a blow with Nothing deals double damage.**

Example:
- Enemy intent = 20 damage.
- Nothing → 40 HP damage.

The exact multiplier is still subject to playtesting, but the design intent is settled: **Nothing should be especially scary.**

This creates a clear tradeoff:
- Spend a defensive opportunity now.
- Preserve it for a future threat.
- Or accept a severe HP cost.

---

# Defensive Deck Progression

## Encounter rewards
After winning an encounter:
1. The player receives **3 card choices**.
2. The player chooses **1**.
3. That card is added to the defensive deck for the current run.

This is settled behavior.

## Training
Training provides a separate way to specialize the deck.

**Training removes one non-Nothing card from the deck.**

Training cannot remove Nothing.

This is important because normal card addition can never make a card reach true 100% probability: adding cards also bloats the deck. Training allows the player to prune unwanted defensive options and eventually specialize heavily in a particular defense.

The distinction is intentional:
- **Rewards add possibilities.**
- **Training removes non-Nothing possibilities.**
- **Nothing remains a permanent part of the risk floor.**

---

# Roguelite System Vocabulary

For discussion purposes, the current structure uses *Slay the Spire* vocabulary:

### Deck — player controlled
The player builds the hidden defensive deck through encounter rewards and training.

### Path — Relics
The chosen route/path determines which Relics the player can acquire.

Relics modify broader combat/deck rules rather than simply being another copy of a deck card.

Example concepts:
- Every 3rd Parry grants 1 Energy.
- Maximum hand size +2.
- The first Nothing each combat deals reduced damage.

These examples are illustrative, not final content.

### Events — deck strength
Events are a place where the game can manipulate deck quality/strength.

Possible examples:
- Remove a Nothing.
- Upgrade a Block into a stronger form.
- Replace 2 Nothings with 1 Parry.
- Add 2 Parry and 3 Nothing as a risky deal.

The exact boundary between Events and Training remains TBD, but Events are explicitly intended to be a meaningful source of deck manipulation.

---

# Combat Decision Model

Every turn should create several interacting decisions:

1. **How much Energy should be committed to the combo?**
2. **Should Energy be spent repositioning?**
3. **Which slash sequence best supports the current build?**
4. **Where should the player stand to avoid dangerous enemy attack zones?**
5. **Which enemy positions remain reachable from that location?**
6. **Which defensive opportunities should be spent now?**
7. **Which useful opportunities should be retained for a future turn?**
8. **Is it worth accepting the dangerous Nothing outcome?**

The intended result is that no single defensive option is universally best.

---

# Encounter Model

- Primarily 1v1 encounters remain favored.
- Enemies present readable, visible attack intents.
- Enemy attacks can target one or multiple positions.
- Player positioning determines whether those attacks can hit.
- Player positioning also determines attack reach.
- Energy creates a direct tradeoff between offense and repositioning.
- Defensive opportunities are randomized through the hidden deck.
- Player chooses among the opportunities actually available.
- Successful defense may prevent damage, create openings, enable counters, or interact with build effects.
- Enemy behavior should create distinct combat problems rather than only increasing HP/damage.

---

# Design Principles

- **Defense is a decision, not a free reaction.**
- **Energy creates tension between offense and mobility.**
- **Energy is temporary; unused Energy is lost.**
- **Enemy intent provides information.**
- **RNG constrains choices without removing agency.**
- **The player chooses a direction, but does not receive a perfectly controlled build.**
- **Position matters for both attack and defense.**
- **Deck dilution prevents blindly stacking one defensive option.**
- **Training enables specialization without making additions free.**
- **Nothing must remain a genuinely frightening outcome.**
- **Player skill should matter more than grinding.**
- **Build effects should create new combat behavior, not only larger numbers.**

---

# Confirmed vs TBD

### Confirmed direction
- Turn-based structure with active combat decisions.
- Visible enemy intent.
- Energy determines combo length.
- Entire committed Energy amount is consumed when starting the combo.
- Unused Energy does not carry over.
- Slash sequences are a build axis.
- Three persistent positions: LEFT / CENTER / RIGHT.
- Repositioning costs 1 Energy regardless of distance.
- Position determines which enemy attack zones can hit the player.
- Attacks can cover multiple positions.
- Position determines attack reach toward the enemy.
- Hidden defensive deck.
- Defensive hand/opportunities can be retained.
- Holding an opportunity does not remove it from the underlying deck.
- Block uses stacking numeric value.
- Parry can have numeric requirements.
- Nothing is a real outcome and is intended to be especially dangerous.
- Encounter reward = 3 card choices, choose 1, add it to the deck.
- Training removes one non-Nothing card.
- Path provides Relics.
- Events manipulate deck strength.

### Still TBD
- Exact Energy starting value and maximum.
- Exact combo input/timing rules.
- Complete slash-direction vocabulary.
- Center-position attack reach grammar.
- Exact enemy attack notation/presentation.
- Exact defensive draw timing.
- Default hand size and hand-size progression.
- Whether defensive opportunities have numeric values or counts in all cases.
- Exact Parry resolution.
- Whether Parry can interact with attacks outside the player's current position.
- Partial Parry behavior.
- Whether defensive options can be combined against one attack.
- Exact Block persistence/reset rules.
- Exact Nothing damage multiplier after playtesting.
- HP/damage/healing model.
- Stagger/counterattack rules.
- Exact relationship between position and enemy attack animation.
- Exact multi-enemy rules.
- Exact Relic and Event pools.
