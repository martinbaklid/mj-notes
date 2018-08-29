# Content Accessibility ("Universell utforming")

## Standards
### W3C 
www.w3.org (HTML, Xml, Css)

### WAI
www.w3.org/wai (ATAG)

### WCAG (Web Content Accessibility Guidelines) 
www.w3.org/WAI/intro/wcag.php 

05.06.18 -> version 2.1

Levels:
- A 
- AA
- AAA

Erupopean standards (EU):
- WCAG 2.0: EN 301 549
- WCAG 2.1: HEN 301 549

## Technical requirements
Always complement icons with a text (e.g. hamburger icon with text "Menu")

Illustrations is important to complement text (e.g. description of parking). Many people have problems understanding what they read.

### Screen readers
Examples: 
- Jaws (free for developers)
- VoiceOver (IOS)
- TalkBack, Brailleback (Android)

### WCAG 2.0
- Links need to be explicit (e.g. if all are listed, which are which)
- Don't use Java-applets and flash
- Add labels to describe e.g. forms
- No HTML errors (validate: http://validator.w3.org), e.g.:
    * Use start and end tags.
    * Unique ids
    * Etc.
- Validate CSS
- Set char set (`<meta charset="utf-8"/>`)
- Set title
- All presentation done with CSS (not html)
- Don't use layout tables
- Test if content is readable without CSS
- Layout should work on all screen sizes
- Icon should be complemented with text
- Try to keep menu also for iPad (smaller can use mobile type menu)
- Page will work up to 200% zoom, and with bigger text size
- Don't set maximum scale
- If using iFrames always set title
- In general don't use title tags (`<title>`)
- Add noscript tag (`<noscript>`) if page needs script. This tag will only show if scripts are disabled.
- Modals:
    * Lock user within modals (so not possible to tab out of open modal)
    * Don't start modals randomly (should be opened with user action)
- Use wai-aria attributes to show hidden information. E.g. `<button aria-expanded="true">Expand<button/>`.
    * Use aria-live for fields that update automatically (off, polite, assertive).
    * Don't use where not needed
    * `aria-describedby` can be used if you have a text describing a field.
- Make it possible to navigate with mouse, touch, and keyboard.
    * Think about mouse over
    * `tabindex` is a possibility if default order is bad, but may cause weird behaviour. So only use if needed.
- Keep clickables big enough
- Use structural tags as `nav` and `body`, and attributes as `role`
- Let first tab be "go to main content"
- Set links to current page as not clickable (e.g. `span`).
- Keep consequent order on menu options.
- Clearly show which clickable object is active while tabbing/mouse over.
- Only use timing (e.g. logout from bank) where needed
- If automatically updated/logged out/etc, keep unsaved changes (e.g. forms)
- Use tags correctly (e.g. links are `<a>`, buttons are `<button>`, etc)
- Use `label` for label texts. Will also expand areas.
    * E.g.: `<label for="text">Name</label><input id="text" required type="text" />`
- Use `<fieldset>` and `<legend>`. 
- Validation of forms
    * Show list with errors, and connect errors to correct fields. E.g. show error in `<label>` as a `<span>`
    * Don't use only colors to show state. E.g. for errors, also add icon and text
    * Don't submit actions before validated, and don't clear any fields.
- Structure
    * Header text should be in a `<h1>`, `<h2>`, etc.
    * Text in `<p>` tags
    * Cites in `<blockqoute>` tags
    * Abbreviations in `<abbr>` tags (works for mouse over)
- Tables:
    * use `<caption>`
    * use `<th scope="<col|row>">`
    * must show without scroll on smaller screen. Could e.g. show each row by itself.
- Images:
    * set `alt` text. Be explicit, e.g. "A person writes on a laptop. Photo."
    * images just for design (e.g. a line separator) should be set as background image in CSS.
- Multimedia
    * Background music should be easy to disable/automatically turn of in 3 sec
    * Use description in links to files. What is it, file type, size, etc.
    * Quality picker for at least two qualities
- Colors and texts (choosing color contrasts: Color Contrast Analyzer)
    * Use clear contrast between text and background.
    * Set text on images, not in.
- Pages
    * Pages needs unique, relevant titles. Should be used in URL (slug)
    * Add meta data
    * Use lang attribute (E.g. `<html lang='en'>`). Could still have e.g. quotes with other language.
- Links
    * Should be clear, also out of context.
    * If opens in new window/is a document/redirect to other page, show this clearly
    * Create a relevant and nice 404 page
    * Show that actions are working with loading icon

### WCAG 2.1
14 additional technical requirements 
3 design requirements

Also adds requirements to apps.

Technical requirements:
- 2.1.4 Character key shortcuts (A)
    * Must be with ctrl, alt, shift
    * Must be able to disable or personalize
    * Can use attribute `accesskey` (e.g. `<a accesskey="t" href="">Something</a>`)
- 2.5.4 Label in Name (A)
    * Name shown must also be accessible for help tools. Visual should mirror code.
    * E.g. `<button>Close</button>`, not `<button aria-label="close">X</button>`
- 2.5.4 Pointer Cancellation (A)
    * If one uses mouse down, one should be able to abort action.
    * One should use standard behaviour (e.g. abort click by releasing mouse away from button).
- 2.5.7 Motion actuation (A)
    * All that can be done with motion should be able to do with mouse (e.g. 360-degree movie).
    * Can be exceptions e.g. leveler
- 1.3.4 Orientation (AA)
    * Should work in both vertical/horizontal mode
- 1.3.5 Identify Input Purpose (AA)
    * Makes it easier to use `autofill`.
    * Use `autocomplete` attribute (e.g. `<input type="email" autocomplete="work email" name="E-post, jobb" />`).
- 1.4.10 Reflow (AA)
    * No scroll for 320px width, or 256px height
    * Should not loose any information on smaller screen.
- 1.4.12 Text Spacing (AA)
    * Should be able to use tools to decide text spacing (e.g. stylish (chrome app))
    * Should not hide any information (e.g. for overflow=hidden)
- 1.4.13 Content on Hover or Focus (AA)
    * Mainly meant for sub menus and programmatically created tooltips (not `title`).
    * Mouse must be able to move to expanded area
    * Expanded area must not disappear by itself
    * Must be closable with ESC
    * Does not include `Modal`
- 4.1.3 Status Messages (AA)
    * Use `aria-live`
    * If reload of page (some request done)
    * If live validation of form
- 2.5.5 Target Size (AAA)
    * Clickable objects must be minimum 44x44 px.
    * Not anchor links
- 1.3.6 Identify Purpose (AAA)
    * Set purpose of fields, functions, etc.
    * Could be done with:
        - meta data (e.g. `itemtype`)
        - text (e.g. "Phone number 12345678")
- 2.5.6 Concurrent Input Mechanisms (AAA)
    * Should work with touch, mouse, keyboard
- 2.2.6 Timeouts (AAA)
    * Save data for 20 hours (auto save)
    * Warn user about timeouts
    * Does not count if computer turns off/web browser closes 

Design requirements:
- Contrast
- Animations
- Pointer gestures
