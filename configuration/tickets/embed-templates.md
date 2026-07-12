---
title: Ticket Manager UI
description: Panel and option managers use select menus, buttons, and forms, not embeds.
icon: code
---

Manager screens from `,ticket panel` and `,ticket option` are **components only** (select menus + buttons). Configuration opens Discord **modals/forms**. Embeds are for member-facing ticket messages only.

**Color for ephemeral success/warn replies:** `#558184` (`color.default`)

---

## `,ticket panel`

No embed. Select + **Add** + **Done**.

**Select:** `Select a ticket panel...`  
Option title = panel name · description = `button` or `dropdown`

### Add panel form

```
Add panel
├─ Panel Name
├─ Channel - Where the ticket panel message should be posted
└─ Mode - Buttons / Dropdown
```

### Panel selected

No embed. Disabled select shows the panel name. Buttons:

| Row | Buttons |
| --- | ------- |
| 1 | **Behavior** · **Categories** · **Display** · **Messages** (all blue) |
| 2 | **Remove** (red) · **Back** (grey) |

### Panel forms

**Behavior • {panel}**

- Delete Delay
- Max Open
- Autopin (checkbox) - pin ticket control message
- Claims (checkbox) - allow staff to claim

**Categories • {panel}**

- Default Category
- Overflow Category

**Display • {panel}**

- Panel Name
- Default Channel Name Format
- Padding
- Tickets Mode - Buttons / Dropdowns

**Edit Panel Message • {panel}**

- Panel Message (embed code)

---

## `,ticket option`

No embed. Select + **Add** + **Done**.

**Select:** `Select a ticket panel...`  
Then manage that panel's options (select option + **Add** + **Back**).

Shortcut: `,ticket option support` opens that panel's options directly.

### Option selected

| Row | Buttons |
| --- | ------- |
| 1 | **Behavior** · **Forms** · **Messages** · **Style** (blue) |
| 2 | **Remove** (red) · **Back** (grey) |

### Behavior

**Button UX** - Claim 📥 · Close 🔒 · Delete ⛔ · Reopen 🔓  
Each opens a form: Label, Emoji (`none` to clear), Color (Blurple/Gray/Green/Red)

**Categories** - Category / Claim Category / Close Category

**Naming** - Channel Name Format · Claim Rename · Close Rename (blank = inherit/clear)

**Permissions** - **Members** · **Support** · **Trainees** + **Back**

### Style

- **Button mode:** Label, Emoji, Color, Disable button (checkbox)
- **Dropdown mode:** Dropdown label, description, emoji, Disable dropdown option (checkbox)

### Messages

Dropdown of message types (no overview embed). Each form uses a **checkbox** to enable/disable.

---

## Default member-facing embeds

Defined in `adore/commands/server/ticket/_constants.py`.

### Panel message

```javascript
{embed}
$v{author: adore}
$v{title: adore}
$v{description: Click the button below to open a ticket. A private ticket channel will be created for you when you open one.}
$v{field: Max Open Tickets && 1 && true}
$v{field: What To Include && Be clear about your issue, include screenshots or links when helpful, and wait for a staff response. && false}
```

### Greeting / Close / Claim / …

See `_constants.py` for `DEFAULT_GREETING_MESSAGE`, `DEFAULT_CLOSE_MESSAGE`, `DEFAULT_CLAIM_MESSAGE`, `DEFAULT_REOPEN_MESSAGE`, `DEFAULT_AUTOCLOSE_MESSAGE`, `DEFAULT_AUTODELETE_MESSAGE`, `DEFAULT_INACTIVITY_MESSAGE`, `DEFAULT_MOVE_MESSAGE`, `DEFAULT_REQUIRE_ROLES_MESSAGE`.
