# Controller Skin White + Blue Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Restyle the PS4 controller skin to a white body with medium blue d-pad, sticks, and accents using CSS filters.

**Architecture:** Add `filter` declarations to the three existing selector groups in `edit.css`. No new files. The purple sprite sheets are recolored at render time: base body gets desaturated and brightened to white; d-pad and sticks get hue-rotated ~-70° to shift purple (~280°) to blue (~210°).

**Tech Stack:** CSS filters (`saturate`, `brightness`, `hue-rotate`)

---

### Task 1: Apply filters to `edit.css`

**Files:**
- Modify: `edit.css`

- [ ] **Step 1: Update the base body selectors**

Replace the contents of the two base selectors in `edit.css`:

```css
.edit .controller.ds4 {
    background: url(https://schoettner.github.io/skins/base-custom.png);
    filter: saturate(0) brightness(2.5);
}


.controller.edit {
    background: url(https://schoettner.github.io/skins/base-custom.png);
    filter: saturate(0) brightness(2.5);
}
```

- [ ] **Step 2: Update the d-pad selectors**

Replace the two d-pad selectors:

```css
.edit .face .ds4 {
    background: url(https://schoettner.github.io/skins/dpad-custom.png);
    filter: hue-rotate(-70deg) saturate(1.3) brightness(1.1);
}


.edit .face {
    position: absolute;
    background: url(https://schoettner.github.io/skins/dpad-custom.png);
    filter: hue-rotate(-70deg) saturate(1.3) brightness(1.1);
}
```

- [ ] **Step 3: Update the stick selectors**

Replace the two stick selectors:

```css
.edit .stick .ds4 {
    background: url(https://schoettner.github.io/skins/sticks-custom.png);
    filter: hue-rotate(-70deg) saturate(1.3) brightness(1.1);
}


.edit .stick {
    position: absolute;
    background: url(https://schoettner.github.io/skins/sticks-custom.png);
    filter: hue-rotate(-70deg) saturate(1.3) brightness(1.1);
}
```

- [ ] **Step 4: Verify visually**

Open the Gamepad Viewer link in a browser (push to GitHub Pages first or serve locally):

```
https://gamepadviewer.com/?p=1&s=5&editcss=https%3A%2F%2Fschoettner.github.io%2Fedit.css
```

Expected result:
- Controller body appears **white**
- D-pad appears **medium blue** (~#1E6BB8)
- Analog sticks appear **medium blue**

If blue is too dark → increase `brightness` value (try `1.2`–`1.4`)
If blue is too desaturated → increase `saturate` value (try `1.5`–`1.8`)
If hue is off (too purple or too cyan) → adjust `hue-rotate` (range: `-60deg` to `-80deg`)
