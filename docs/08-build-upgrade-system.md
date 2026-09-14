# 8. Build and Upgrade System

## Purpose
Build choices should alter the player's preferred combat behavior and create recognizable synergies rather than simply increasing numbers.

The current build model has two interacting layers:

1. **Combat build effects** — modify attacks, slash sequences, Energy, defense, positioning, or other combat rules.
2. **Defensive deck building** — determines which defensive opportunities are available during combat.

## Defensive Deck
The player builds a hidden defensive deck during a run.

A deck can contain entries such as:
- Parry
- Block
- Dodge
- Nothing

The relative counts of these entries determine their probabilities. There is no separate percentage stat.

Adding a card increases the deck size and therefore dilutes the relative probability of every card. This is intentional: simply adding more copies of a desired defense is never automatically optimal.

### Encounter reward
After winning an encounter:
- Present 3 card choices.
- Player chooses 1.
- Add the chosen card to the run's deck.

### Training
Training removes one non-Nothing card from the deck.

Training cannot remove Nothing. This provides a route toward specialization while preserving a permanent risk floor.

## Defensive Hand
Defensive opportunities are drawn from the hidden deck into a hand whose size is itself a buildable stat.

Unused opportunities can be retained between turns.

Having an opportunity in hand does not remove that entry from the underlying drawable deck. The hand is the player's currently available options; the deck remains the probability source.

## Slash Sequence Builds
Offensive builds can care about **what sequence the player physically performs**, not only the amount of damage dealt.

Example effects:
- Every 2 Down Slashes → free Uppercut.
- ↑ attacks deal increased damage.
- ↘ followed by ↗ causes Bleed.
- After 3 horizontal slashes → free heavy attack.
- ↓ → ↓ triggers a special effect.
- ↑ → ↘ grants a defensive benefit.
- 3 different directions → empowers the next attack.
- Repeating the same direction → creates a stronger hit.

These examples illustrate the intended design space rather than a final upgrade list.

The key distinction is:
- **Player skill:** executing the sequence.
- **Build:** making certain sequences valuable.

## Energy / Combo Modifiers
Build effects may:
- Extend a combo.
- Grant free slashes.
- Refund Energy.
- Alter the next slash.
- Repeat a previous slash.
- Force follow-ups.
- Reward or restrict particular sequences.
- Give the final slash a special effect.

The final slash is not inherently special. Any special finisher behavior must come from an explicit build effect.

Energy does not carry over between turns, so Energy-related upgrades should interact with the current turn's offensive opportunity rather than enabling indefinite banking.

## Positioning Builds
Position is both an offensive and defensive build axis.

There are three positions:
`LEFT - CENTER - RIGHT`

Repositioning costs 1 Energy regardless of distance.

Position determines:
- Which enemy attacks can hit the player.
- Which enemy positions the player's attacks can reach.

The baseline attack reach is the player's current position plus the adjacent position toward the enemy.

This means a mobility-related upgrade can change both survivability and offensive access, while also competing with combo Energy.

## Candidate Upgrade Families
- Slash-direction modifiers.
- Combo/sequence modifiers.
- Energy modifiers.
- Defensive deck modifiers.
- Block modifiers.
- Parry modifiers.
- Position/mobility modifiers.
- Status effects.
- Passive Relics.
- Risk/reward effects.
- Resource economy modifiers.

## Build Philosophy
The player should choose a broad direction without receiving a perfectly controlled build.

Controlled randomness should produce interesting problems and unexpected synergies while preserving meaningful agency.

Build effects should encourage different combat behavior rather than create a single dominant numerical path.

## Examples of Build Directions
- Directional combo / bleed.
- Heavy attacks / stagger.
- Parry-focused counterattack.
- Block-heavy attrition.
- Mobility / positional attacks.
- Sequence-combo specialist.
- High-risk Nothing manipulation.
- Hybrid defense with strong retained hand.

## TBD
- Rarity system.
- Exact upgrade pool.
- Upgrade stacking rules.
- Exact Relic system.
- Build size/slot limits, if any.
- Exact synergy discovery/presentation.
- Exact numerical values.
