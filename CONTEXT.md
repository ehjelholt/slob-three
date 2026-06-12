# Dice Roller

A client-side dice rolling tool for Basic Fantasy tabletop sessions. Rolls are reproducible via a seed encoded in the URL.

## Language

**Session Seed**:
A 32-bit unsigned integer in the URL that encodes the full history of rolls made so far.
_Avoid_: hash, state, nonce

**Roll**:
A single user-initiated action specifying a number of dice and a die type, producing one result per die and a total.
_Avoid_: throw, cast

**Die Type**:
The number of sides on a die. Valid values: 4, 6, 8, 12, 20.
_Avoid_: sides, faces, d-value

**Roll Result**:
The outcome of a Roll: the individual values for each die and their total.
_Avoid_: outcome, result set

**Roll Log**:
The in-memory, in-page list of all Rolls and their Roll Results made during the current page session.
_Avoid_: history, audit log

## Relationships

- A **Roll** consumes the current **Session Seed** and produces a **Roll Result**
- A **Roll** produces a new **Session Seed** by mixing the old seed with the Roll's die count and Die Type
- A **Roll Result** is appended to the **Roll Log**
- The **Session Seed** is reflected in the URL after every Roll via `replaceState`

## Example dialogue

> **Dev:** "When the user presses Roll, do we update the Session Seed before or after generating the Roll Result?"
> **Domain expert:** "After. We use the current Session Seed to generate the Roll Result, then evolve it using the die count and Die Type to produce the next Session Seed."

## Flagged ambiguities

- "seed" could refer to the initial URL parameter or the current evolved value — resolved: **Session Seed** always means the *current* value; the initial value is just the starting Session Seed.
