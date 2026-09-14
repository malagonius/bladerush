# Dump of Ideas

> A deliberately messy idea dump for BladeRush.
>
> This file is **not** authoritative design documentation. Ideas can be contradictory, half-baked, redundant, or later moved into the proper GDT document once we decide they belong there.
>
> The goal is to avoid losing interesting ideas simply because we don't yet know where they fit.

## Idea Status

- **[APPRECIATED]** — We like the idea and want to keep it in consideration.
- **[TBD]** — Interesting enough to keep, but we have not decided whether it belongs in the game.
- **[DISCARDED]** — Explicitly rejected. Keep the record so we don't accidentally reinvent the same idea later.
- **[PROMOTED]** — The idea was accepted and moved into an authoritative GDT document. Keep a short reference here if useful.

---

## High Concept / Identity

### [APPRECIATED] Crossed Swords presentation + Infinity Blade progression
Use the readable, constrained arcade staging of *Crossed Swords* as the presentation inspiration, while taking inspiration from *Infinity Blade* for mobile-friendly timing-based interaction and character/build progression.

This combination is currently one of the strongest directions for BladeRush.

### [APPRECIATED] Production-conscious fantasy
The game should deliberately choose a visual/gameplay format that a small team or solo developer can actually produce. We should not design a game that requires AAA animation, huge environments, dozens of unique rigs, or cinematic storytelling to feel good.

### [APPRECIATED] Original game, not a remake
The inspirations should inform the design language, not become a recreation of either game. BladeRush needs its own mechanics, content, assets, terminology, and identity.

### [TBD] Stronger identity hook
We may eventually need one immediately recognizable BladeRush-specific hook beyond "mobile action roguelite with arcade sword combat." TBD.

---

## Combat

### [TBD] Mostly 1v1 combat
A strong possibility is keeping the player focused on one meaningful opponent at a time. Additional enemies could exist as special encounters, but the baseline interaction remains readable and personal.

### [TBD] Enemy approach through depth
Enemies could begin farther away and enter the player's combat range, creating a sense of progression and anticipation without requiring large environments.

### [TBD] Directional attacks
Attacks could have a directional component, potentially inspired by classic arcade sword games. The exact input and number of directions are TBD.

### [TBD] Parry as a major skill expression
Parry could be one of the most satisfying high-skill actions: recognize the attack, respond during a narrow timing window, and gain a strong advantage.

### [TBD] Block as the forgiving defensive option
Block could be easier and safer than parry, but less rewarding. This creates a natural risk/reward relationship between reliable defense and mastery.

### [TBD] Dodge as a different defensive language
Dodge could coexist with block/parry if it creates a genuinely different decision rather than simply being "the better defense." It might emphasize positioning, timing, or avoiding specific attack types.

### [TBD] Combat should be readable before it is complex
A small number of actions with clear enemy telegraphs is preferable to a large action list that becomes difficult to understand on a phone.

### [TBD] Timing over button-combo mastery
The game may be better served by recognizing *when* to act than by requiring long fighting-game-style combinations.

### [TBD] Player attacks should have meaningful commitment
Attacks should probably not be completely free/reactive. Committing to an attack can create tension and make defensive timing more important.

### [TBD] Stagger / interruption
Successful attacks, parries, or particular builds might interrupt enemies. TBD whether stagger is a core combat system or merely a consequence of certain attacks.

### [TBD] Combat build identities
Possible build directions include:
- Fast attacks / bleed
- Heavy attacks / stagger
- Parry / counterattack
- Defensive / retaliation
- Dodge / mobility / back attack
- Status-effect focused

---

## Roguelite / Progression

### [APPRECIATED] Every run should create a build
The player should make meaningful decisions during a run that change how the character fights, rather than simply accumulating larger numbers.

### [TBD] Build synergies
Individual upgrades should ideally interact. The interesting moment is not just "+10% damage" but "this changes what my character wants to do."

### [TBD] Temporary run upgrades
Possible categories:
- Weapon modifications
- Attack changes
- Defensive/parry changes
- Dodge/mobility changes
- Status effects
- Passive relic-like effects
- Risk/reward effects
- Resource manipulation

### [TBD] Persistent progression
Possible permanent progression:
- New weapons
- New upgrade pools
- Permanent unlocks
- Characters/loadouts
- Small permanent stat progression
- Difficulty modifiers

### [TBD] Avoid grind as the primary progression
Persistent progression should ideally unlock possibilities rather than simply making the player numerically stronger forever.

### [TBD] Runs should be short enough for mobile
Exact target is TBD, but the game should support sessions that can reasonably fit around mobile play rather than assuming long uninterrupted play sessions.

---

## Presentation / Camera

### [APPRECIATED] Constrained staging
A limited combat space is a feature, not a weakness. It reduces art requirements and lets us spend production effort on combat readability, characters, effects, and polish.

### [APPRECIATED] Reusable arenas
A small number of modular environments can support many encounters if lighting, enemy combinations, camera treatment, and encounter structure create enough variation.

### [TBD] 2.5D / hybrid presentation
A hybrid approach may give us the best compromise: 2D/arcade-like staging and readability with modern 3D characters/effects where useful.

### [TBD] Silhouette-first enemy readability
Enemies should be recognizable from shape, posture, weapon, and attack preparation before the player needs detailed textures.

### [TBD] Effects can provide visual polish cheaply
Lighting, hit flashes, particles, trails, impact effects, and camera feedback could provide a large amount of perceived polish without requiring elaborate environments.

---

## Enemy Design

### [APPRECIATED] Each enemy should ask a different combat question
Enemies should not primarily differ by having different HP pools. A new enemy should introduce a new timing, positioning, defensive, or build-related problem.

### [TBD] Basic enemy archetypes
Potential archetypes:
- Basic / teaches the core loop
- Fast / tests reaction
- Heavy / tests patience and defense
- Defensive / punishes careless attacks
- Ranged / pressures positioning
- Counter/parry enemy / tests attack selection
- Elite / combines mechanics
- Boss / creates a larger encounter pattern

### [TBD] Enemy modifiers
Elite enemies could gain modifiers that alter their behavior rather than simply increasing their stats.

### [TBD] Enemy combinations
Once multiple enemies can be present, combinations could create new problems without requiring many enemy types. This depends heavily on whether simultaneous enemies fit the combat model.

---

## Production / Scope

### [APPRECIATED] Small MVP
A possible first complete playable target:
- 1 player character
- 1 weapon
- 1 arena
- 3 enemy types
- 1 boss
- ~10 upgrades
- 1 complete run structure

This is a scope target, not yet a final production plan.

### [APPRECIATED] Reuse before variety
Prefer systems that allow one asset to serve multiple gameplay purposes over creating large quantities of unique content.

### [TBD] Data-driven content
Enemies, upgrades, encounters, and progression should ideally be represented as data rather than hard-coded one-offs. This should make experimentation cheap.

### [TBD] Avoid content that multiplies animation cost
Any feature that requires every enemy to have many unique animations should be treated with suspicion during design.

---

## Random Thoughts / Loose Ideas

### [TBD] Roguelite paths as encounter choices
Instead of a giant map, the player could choose between a small number of next encounters, with icons communicating risk/reward.

### [TBD] Elite encounters as build checks
Elite fights could deliberately test whether the player's current build has a coherent identity.

### [TBD] Bosses as rules changes
A boss could be more interesting if it temporarily changes how combat works rather than being merely a larger enemy with more HP.

### [TBD] Risk/reward upgrades
Some upgrades could make the player significantly stronger while imposing a real behavioral drawback, encouraging interesting build decisions.

### [TBD] "One more run" structure
The run should ideally end at a natural point that makes restarting immediately attractive rather than exhausting the player.

### [TBD] Build discovery
Some of the strongest synergies could be discoverable rather than explicitly advertised, rewarding experimentation.

### [TBD] Controlled randomness
Randomness should create variety and decision pressure, not determine whether the player wins despite playing well.

---

## Discarded Ideas

> Nothing is permanently discarded yet unless we explicitly say so. This section is intentionally empty at the start.

---

## Promoted Ideas

> Ideas that become authoritative design decisions should eventually be moved into the relevant GDT document. This section can retain a short trail of where the idea came from.

---
