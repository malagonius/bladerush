# 7. Roguelite Structure

## Run Progression
A run should create a changing combat build through player choices constrained by controlled randomness.

The current progression vocabulary intentionally uses *Slay the Spire* terms for discussion:

- **Deck:** the player's hidden defensive deck. The player shapes it through encounter rewards and Training.
- **Path:** the route through the run; the path determines access to Relics.
- **Relics:** broader passive/rule modifiers that interact with combat and the deck.
- **Events:** opportunities to manipulate deck strength/quality and create unusual tradeoffs.

## Deck Progression
After winning an encounter:
1. The player sees 3 card choices.
2. The player chooses 1.
3. The chosen card is added to the defensive deck for the current run.

Adding cards inherently bloats the deck. This means adding a desired defense also changes the relative probabilities of the other cards, preventing simple spam of one card from being automatically optimal.

### Training
Training removes one **non-Nothing** card from the deck.

Training cannot remove Nothing. This gives the player a separate route toward specialization and can eventually make a particular defensive option extremely likely without allowing the player to erase the game's baseline risk entirely.

## Controlled Randomness
The player should be able to choose a broad direction without receiving a perfectly controlled build.

> RNG should constrain the player's available choices while preserving meaningful agency.

Good randomness creates situations/problems to solve. It should not decide whether the player is allowed to play well.

The hidden defensive deck is the main expression of this principle: the game determines which defensive opportunities are available, while the player chooses how to use the opportunities currently in hand.

## Path / Relics
The chosen path determines the Relics available during a run.

Relics should generally modify broader rules rather than simply acting as additional defensive cards.

Illustrative examples:
- Every 3rd Parry grants 1 Energy.
- Maximum defensive hand size +2.
- The first Nothing each combat deals reduced damage.

These are examples of the design space, not final content.

## Events
Events are a place where the game can manipulate deck strength/quality.

Illustrative examples:
- Remove a Nothing.
- Upgrade a Block into a stronger form.
- Replace 2 Nothings with 1 Parry.
- Add 2 Parry and 3 Nothing as a risky deal.

The exact boundary between Events and Training remains TBD.

## Temporary Run Elements
Potential temporary elements include:
- Defensive deck composition.
- Defensive hand size.
- Relics.
- Weapons or weapon modifications.
- Slash/combo modifiers.
- Status effects.
- Synergy components.
- Resource modifiers.

## Meta Progression
Potential persistent elements:
- Unlockable weapons.
- New upgrade pools.
- New defensive cards or card pools.
- New Relics.
- New characters or starting loadouts.
- Difficulty modifiers.

Persistent progression should ideally expand possibilities rather than simply making the player numerically stronger forever.

## Design Principle
A run should differ because of decisions and synergies, not only because enemy numbers are randomized.

The player should discover build interactions during a run rather than simply selecting a pre-written build from a menu.

## TBD
- Roguelike vs roguelite balance.
- What resets on death.
- What persists after death.
- Meta currency.
- Exact path/map structure.
- Exact Event pool.
- Exact Relic pool.
- Run length.
- Exact randomness level.
- Whether all content is eventually unlockable or skill-gated.
