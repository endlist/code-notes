---
{"publish":true,"created":"2025-07-08T20:03:21.962-06:00","modified":"2025-07-08T23:04:19.551-06:00","tags":["a11y"],"cssclasses":""}
---


This often comes up when we get a ticket that says we need readable text available on an icon-only button.  There are a few other places tooltips commonly get used, like additional information on usage with little help icon popovers, chart data, and sometimes also as an attempt to avoid reflow issues caused by truncation by adding a tooltip instead.

## The Problem

Tooltips are difficult to support properly, people often forget to make them accessible by keyboard or touch, not adding an announcement so they are surfaced to screen readers, they may disappear and prevent hovering/copying text from them making them difficult to read, they can get positioned cutoff offscreen, not support zoom or window resizing to reposition, among other things.  We often use 3rd party libraries to offload maintenance of this headache, but that comes with the issue of potentially poor support for a11y.

## The Solution

If you can avoid a tooltip, do avoid a tooltip.  This often stems from a UX problem that wasn't addressed, either trying to save space by using icon-only buttons, not considering need for help text, etc.  As a developer, push back on UX that calls for a tooltip.  If it's absolutely unavoidable make sure you are supporting the full spec of accessibility.