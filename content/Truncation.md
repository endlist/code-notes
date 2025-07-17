---
{"publish":true,"created":"2025-07-08T20:03:21.962-06:00","modified":"2025-07-17T15:04:25.787-06:00","tags":["a11y"],"cssclasses":""}
---

## The Problem
Text truncation is a violation of [WCAG SC 1.4.10 Reflow](https://www.w3.org/WAI/WCAG22/Understanding/reflow) which also commonly violates [WCAG SC 1.4.12 Text Spacing](https://www.w3.org/WAI/WCAG22/Understanding/text-spacing.html) and [WCAG SC 1.4.4 Resize Text](https://www.w3.org/WAI/WCAG22/Understanding/resize-text.html).

Text should not be cut off vertically (typically by `overflow: hidden` on the container or an overlapping element) or horizontally (this is still an issue if you use `text-overflow: ellipsis`) as this causes a loss of information.  Text needs to be readable not only at default size/zoom on every device, but adapt to a user setting browser settings to increase the text size or kerning or increasing the zoom.
## The Solution

You can mostly think about it as a priority list:

1) **Simply wrap the text.**  This is the best option, it scales for any browser size, any zoom size, and it is always readable.  Ideally the UX team will be able to come up with a way to make this look good as well.
2) **Set a maximum character limit.**  This is only usable if you know where the text is coming from and can still run into problems such as with translation so make sure to test in various languages.  But for things like a list option it might be reasonable to set a character limit for people who will be creating the options internally or even for clients for item titles to ensure the text will not be cut off by the UI.
3) **Provide a way to expand the text so it is readable inline.**  Not ideal, but can work in some scenarios where text is not available on initial load but can be made to expand.  Be careful to ensure that the mechanism for doing this is clear to users and follows all other accessibility guidelines.
4) **Floating tooltip.**  Last resort.  If there is no other option or if you are under a crunch, a properly accessible tooltip can be used to show the full text.  Remember this needs to be mobile-friendly, keyboard-friendly, mouse-friendly, screen-reader-friendly, and readable.

## Inadequate Fixes

### text-overflow: ellipsis

This sometimes seems like a good solution as a built-in truncation.  It does visually indicate text is truncated in a way it might not if only `overflow: hidden` is applied, but it does not fundamentally fix the issue as information is still lost.

![[img/example-of-ellipsis-ambiguity.png|Example of button truncated to read "Experi..." with code showing the full title reads "Experience Life or Experiment Links?"]]

Obviously this is extreme and not likely to be a real world example, but without additional information would you guess correctly on what the text on the buttons were?
### title attribute

Sometimes people think to use a `title` attribute as a replacement for an accessible tooltip, and this is one case where native html is not the better option.  See [[Bad Aria and Attributes#title\|Bad Aria and Attributes: title]] for more details.

![[img/example-of-title-truncation.png|Example of button with a long title that is cut off the full title being shown with the title attribute only on mouse hover.]]

This is still violating horizontal cutoff because there's no way to read this title text on mobile.

