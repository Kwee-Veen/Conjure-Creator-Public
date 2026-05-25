# Conjure Creator

Conjure Creator is an internal Android tooling application used to create and manage structured data for the Conjure tabletop card game system.

Rather than manually authoring large JSON files, the application provides a UI-driven workflow for configuring cards, moves, effects, modifiers, and related rules data. The generated output is then consumed directly by Conjure Dex, the companion encyclopaedia application for browsing and unlocking cards.

This project is designed as a development utility rather than a consumer-facing product. Functionality and speed of iteration were prioritised over production-level UX polish.

## Routes & Navigation
<img width="1169" height="1340" alt="Conjure Creator Routes Map" src="https://github.com/user-attachments/assets/1faee4d1-d686-4811-9e77-b341ffead787" />

## Purpose

Conjure Creator exists to solve three core problems in the Conjure ecosystem:

- Provide a UI-driven interface to rapidly create complex Conjure cards 
- Output structured JSON data consumable by the public-facing Conjure Dex
- Generate individual QR codes that link to that card’s listing on Conjure Dex

## Features

- UI-based card creation and editing
- Card data JSON export 
- QR code generation & scanning

## Data Structure

The data created by this application mirrors the structure consumed by Conjure Dex.

### Card Hierarchy

```text
Card
├── DamageModifiers[]
├── Moves[]
│   ├── Effects[]
```

### Card

Each card contains identifying, descriptive, and rules-related metadata, including:

- Card type
- Unique ID
- Core parameters
- Description text
- Image reference

### Damage Modifiers

Cards can contain multiple `DamageModifier` objects which define:

- Vulnerabilities
- Resistances
- Associated damage types
- Modifier values

These modifiers are referenced throughout rules calculations and card detail rendering.

### Moves

Moves are the most detailed nested structure in the application.  
Each `Move` object encapsulates card actions and associated rules metadata, including:

- Cost
- Targeting rules
- Damage values & type
- Range
- Area of effect

Moves may also contain multiple nested `Effect` objects.

### Effects

Effects provide conditional or persistent rule interactions attached to moves.

An `Effect` may define:

- Description text
- Effect duration
- Trigger probability
- Status effects
- Traits
- Additional damage modifiers

This layered structure allows complex card interactions while keeping the data model modular and extensible.

## Integration with Conjure Dex

Conjure Creator serves as the content pipeline for Conjure Dex.

Generated JSON data and QR codes are imported directly into Dex, where the underlying structured data is dynamically interpreted to render:

- Card information
- Rules text
- Contextual tooltips
- Interaction descriptions
- Unlockable card data

This approach keeps gameplay logic and explanatory text data-driven rather than manually authored within the Dex application itself.

##
Copyright © 2025, 2026 Caoimhín Arnott and Jack Mehegan. All rights reserved.
