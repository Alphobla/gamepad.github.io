---
title: Controller Skin Redesign — White + Blue
date: 2026-04-24
status: approved
---

## Goal

Restyle the PS4 controller skin from the current purple theme to a bright white body with medium blue details (d-pad, analog sticks, all accents). Target blue is a medium saturated web blue (~#1E6BB8, matching the reference screenshot).

## Approach

CSS filters applied to the existing element groups in `edit.css`. No new PNG files are created — the existing purple sprite sheets are recolored at render time.

## Changes

**File:** `edit.css`

Add a `filter` property to each selector group:

| Element | Filter value | Effect |
|---|---|---|
| Base body (`.controller.edit`, `.edit .controller.ds4`) | `saturate(0) brightness(2.5)` | Strips purple, boosts to white |
| D-pad (`.edit .face`, `.edit .face .ds4`) | `hue-rotate(-70deg) saturate(1.3) brightness(1.1)` | Shifts purple (~280°) to blue (~210°) |
| Sticks (`.edit .stick`, `.edit .stick .ds4`) | `hue-rotate(-70deg) saturate(1.3) brightness(1.1)` | Same blue as d-pad |

## Out of scope

- Replacing the PNG sprite files
- Changing button labels or layout
- Any changes to `index.html` or other CSS files
