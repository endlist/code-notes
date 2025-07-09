---
{"publish":true,"created":"2025-07-08T20:03:21.962-06:00","modified":"2025-07-08T21:58:51.069-06:00","tags":["a11y"],"cssclasses":""}
---

## The Problem
```html
<h2>{{ label }} Section</h2>
<div [attr.aria-label]="'Sort by ' + column.label">{{ column.label }}</div>
```

Very commonly I see people do this sort of thing, perhaps as a placeholder or perhaps not thinking about it too hard, but it is an issue for translation for two reasons:

1) Every text a user can see or hear should be translated through the translation system, otherwise someone who has set their settings to Mandarin is suddenly hearing an out of place English word or phrase.
2) You can't string-together strings like this. Word order changes in different languages. Some languages may require things like articles to be attached to words, so this only makes sense in English any other languages that have similar sentence structure.  

## The Solution

It is much better to pass in a string with interpolation i.e. name a translation key something like `Core_TableSort` which is translated as a phrase: `Sort by {{column.label}}`.

## Edge Cases

A unique case is if you are using `aria-labelledby` or `aria-describedby` to apply additional context:

```html
<table>
  <tr id="table-row-1" aria-label="John Smith">
    <td>[...]</td>
    <td>
      <button aria-labelledby="button-label table-row-1"><span id="button-label">More options.</span></button>
    </td>
  </tr>
</table>
```

> [!Caution]
> Using `aria-describedby` on a button label may seem like a good idea but it does remove the context from things like VoiceOver's Rotor or NVDA's form control navigation.  `aria-labelledby` is a better choice in that scenario.  But if you want to make the screen reader pause to separate the action from the context you can add a period to your screen reader labels.

