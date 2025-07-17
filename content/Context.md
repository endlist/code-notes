---
{"publish":true,"created":"2025-07-08T20:03:21.962-06:00","modified":"2025-07-17T15:07:09.054-06:00","tags":["a11y"],"cssclasses":""}
---


Button and other form control labels, link text, landmark sections, tables, and anything else that is actionable particularly if it is **not unique** on a page should provide context as well as a generic label.  We want to try to be the least verbose we can be while still providing all the information necessary to utilize a link or button.

Screen readers like VO and NVDA and JAWS provide users with the ability to navigate lists of form controls or headers or landmarks.  It looks something like this in VO (with the visuals turned on-- use `Ctrl+Opt+U` to open the rotor):

![[img/table-form-controls-named.png|Screencap of the VoiceOver Rotor Form Controls display of a table with checkboxes and buttons on every row showing they have the row context and read out like "More Options Nitrogen"]]

This table has many rows that have similar interactive controls to select/see more options etc.  If we don't provide both the generic label (e.g. "select row" "More Options" etc) and the context ("2 Hydrogen"), tools like the rotor will be useless for users.

> [!Tip]
> You can use the period or comma to force the screen reader to pause which will allow us to bypass using phrase translation on every aria label-- recommended to utilize `aria-labelledby` where possible, linked with unique `id` values.  Do not use `aria-describedby` for context or it will not be available in tools like the rotor.

![[img/table-links-named.png|Screencap of the VoiceOver Rotor Links display on a table with links visually displaying only the name of the element i.e. "Lithium" but the rotor lists the link as "Lithium Details"]]

Links do not need to have "Open" as part of their text as screen readers notify the user they are on a link so they understand it will be opening a new page.  But the label should have text that gives the user an idea of where they are navigating to.  This may include adding screen-reader-only text like "details" to explain what kind of page the link will take them to as opposed to "buy lithium" or similar.