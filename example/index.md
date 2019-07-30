
# New Bootstrap v5 forms

A quick look at some of the major changes coming to form controls in Bootstrap 5.

## Checks

<hr class="mt-2 mb-3">

Taking a fresh pass at custom checkboxes and radios without psuedo-elements, thus replacing our previous native form control styles. By resetting the `appearance`, we should be able to style the inputs across Edge, Chrome, Firefox, and Safari.

**Differences from v4:**

- Custom form controls are the new native.
- No more custom HTML is required for the new form controls. They're 100% styled from the `<input>` itself with `appearance: none;`.
- Form controls are 25% larger, moving from `1rem` (`16px`) to `1.25em` (`20px`).
- Form controls are now built with `em`s instead of `rem`s for easy sizing.
- Instead of `position: absolute;`, `<input>`s are aligned with `float` and `margin-top` to help align and scale with sizing options.
- No more `.custom-checkbox-inline` modifier class—instead, use utilities for way more flexibility in your layouts.

These new checks and their text are aligned the same way as v4—with `padding-left` on the outer container. This is so any and all siblings to the `<input>` (like the `<label>`, help text, or validation feedback) is easily aligned.

Flexbox styles were originally attempted, but they're unnecessary and were abandoned early in favor of a `float`ed `<input>`.

### Default styles

<div class="flex-check">
  <input class="flex-check-input" type="checkbox" id="check1" checked>
  <label class="flex-check-label" for="check1">This is the new custom checkbox</label>
  <small class="text-muted d-block">Some additional help text could appear right here.</small>
</div>

<div class="flex-check">
  <input class="flex-check-input" type="checkbox" id="checkindeterminate">
  <label class="flex-check-label" for="checkindeterminate">This is an indeterminate custom checkbox</label>
  <small class="text-muted d-block">Indeterminate checkboxes must be toggled via JavaScript—there's no HTML attribute for this.</small>
</div>

<div class="flex-check">
  <input class="flex-check-input" type="checkbox" id="longcheck">
  <label class="flex-check-label" for="longcheck">This is the new custom checkbox with text that wraps to multiple lines because of a super long label that I keep adding text to so that it does that whole wrapping thing easily enough.</label>
</div>

<div class="flex-check">
  <input class="flex-check-input" type="checkbox" id="disabledcheck" disabled>
  <label class="flex-check-label" for="disabledcheck">This is the new disabled custom checkbox</label>
</div>

<br>

<div class="flex-check">
  <input class="flex-check-input" type="radio" id="radio1" name="radios" checked>
  <label class="flex-check-label" for="radio1">Custom radio that's checked</label>
</div>

<div class="flex-check">
  <input class="flex-check-input" type="radio" id="radio2" name="radios">
  <label class="flex-check-label" for="radio2">Custom radio that isn't</label>
</div>

<div class="flex-check">
  <input class="flex-check-input" type="radio" id="radio3" name="radios" disabled>
  <label class="flex-check-label" for="radio3">Custom radio that's disabled</label>
</div>

<br>

<div class="flex-check flex-switch">
  <input class="flex-check-input" type="checkbox" id="switch1">
  <label class="flex-check-label" for="switch1">Custom switch checkbox input</label>
</div>

<div class="flex-check flex-switch">
  <input class="flex-check-input" type="checkbox" id="switch2" disabled>
  <label class="flex-check-label" for="switch2">Disabled custom switch checkbox input</label>
</div>

<br>

<div class="flex-check flex-switch">
  <input class="flex-check-input" type="radio" id="switchradio1" name="switchradio">
  <label class="flex-check-label" for="switchradio1">Custom switch radio that's checked</label>
</div>

<div class="flex-check flex-switch">
  <input class="flex-check-input" type="radio" id="switchradio2" name="switchradio">
  <label class="flex-check-label" for="switchradio2">Second custom switch radio</label>
</div>

### Without label

And without labels inside the wrapper:

<div class="form-group row">
  <label class="col-md-3" for="check-no-label">External label</label>
  <div class="col-md-9">
    <div class="flex-check">
      <input class="flex-check-input" type="checkbox" id="check-no-label" checked>
    </div>
  </div>
</div>

<div class="form-group row">
  <label class="col-md-3" for="switch-no-label">External label</label>
  <div class="col-md-9">
    <div class="flex-check flex-switch">
      <input class="flex-check-input" type="checkbox" id="switch-no-label" checked>
    </div>
  </div>
</div>

### Inline

Make any checkbox, radio, or switch appear "inline" with utility classes. We recommend `.d-inline-block` and `margin` utilities (e.g., `.mr-3`) as needed.

<div class="flex-check d-inline-block mr-3">
  <input class="flex-check-input" type="checkbox" id="checkInline1" checked>
  <label class="flex-check-label" for="checkInline1">Inline checkbox</label>
</div>
<div class="flex-check d-inline-block mr-3">
  <input class="flex-check-input" type="checkbox" id="checkInline2">
  <label class="flex-check-label" for="checkInline2">Another one</label>
</div>
<div class="flex-check flex-switch d-inline-block">
  <input class="flex-check-input" type="checkbox" id="switchInline1">
  <label class="flex-check-label" for="switchInline1">Inline switch</label>
</div>

### Sizing

Built with `em` units, custom checks, radios, and switches will scale to their own `font-size`, or their containing element's (explicit or inherited) `font-size`. Here we're using a modifier class to set `font-size: 1.5rem` on the container.

<div class="flex-check flex-check-lg">
  <input class="flex-check-input" type="checkbox" id="sizingcheck1">
  <label class="flex-check-label" for="sizingcheck1">Resized custom check</label>
</div>

<div class="flex-check flex-check-lg">
  <input class="flex-check-input" type="radio" id="sizingradio1" name="sizingradios">
  <label class="flex-check-label" for="sizingradio1">Resized custom radio</label>
</div>

<div class="flex-check flex-switch flex-check-lg mb-3">
  <input class="flex-check-input" type="checkbox" id="sizingswitch1">
  <label class="flex-check-label" for="sizingswitch1">Resized custom switch checkbox</label>
</div>

Note that you could scope the sizing to the `<input>` itself, but you'll need additional styles to change the indentation of the `<label>`'s text. Alternatively, you could set a `font-size` on the wrapper and then override the `<label>`'s `font-size`.

<div class="flex-check flex-switch" style="font-size: 1.5rem;">
  <input class="flex-check-input" type="checkbox" id="sizingSwitch2">
  <label class="flex-check-label" for="sizingSwitch2" style="font-size: 1rem;">Large switch, normal label text</label>
</div>

## Selects

<hr class="mt-2 mb-3">

Without the `.form-select`, the previous `.custom-select` is going to become the default styling, providing a unified look across all platforms.

### Default styles

Below are the default and disabled selects. Disabled styles are the same as our checks—no `pointer-events` and an `opacity` change.

<select class="flex-select mb-3">
  <option selected>Open this select menu</option>
  <option value="1">One</option>
  <option value="2">Two</option>
  <option value="3">Three</option>
</select>

<select class="flex-select" disabled>
  <option selected>Disabled select menu</option>
  <option value="1">One</option>
  <option value="2">Two</option>
  <option value="3">Three</option>
</select>

### Inline

Similar to the new checks, make selects inline with a modifier class: `.w-auto`. Selects are `inline-block` to begin with, so no need to change their `display`.

<div class="mb-3">
  <select class="flex-select w-auto mr-3">
    <option selected>Open this select menu</option>
    <option value="1">One</option>
    <option value="2">Two</option>
    <option value="3">Three</option>
  </select>
  <div class="flex-check d-inline-block">
    <input class="flex-check-input" type="checkbox" id="selectInlineCheck">
    <label class="flex-check-label" for="selectInlineCheck">Inline checkbox</label>
  </div>
</div>

Vertical alignment may become an issue, so consider wrapping your inline form controls in some flex and margin utilities. The example below features a wrapper with `.d-flex` and `.align-items-center`, plus `.mb-0` on the inline checkbox.

<div class="d-flex align-items-center">
  <select class="flex-select w-auto mr-3">
    <option selected>Open this select menu</option>
    <option value="1">One</option>
    <option value="2">Two</option>
    <option value="3">Three</option>
  </select>
  <div class="flex-check d-inline-block mb-0">
    <input class="flex-check-input" type="checkbox" id="selectInlineCheck2">
    <label class="flex-check-label" for="selectInlineCheck2">Inline checkbox</label>
  </div>
</div>

### Sizing

Sizing should become similar to the new checks and switches as they're now built with `em`s. Below is the same select as above, but with an increased `font-size` of `1.5rem`.

<select class="flex-select mb-3" style="font-size: 1.5rem;">
  <option selected>Open this select menu</option>
  <option value="1">One</option>
  <option value="2">Two</option>
  <option value="3">Three</option>
</select>

And making it smaller with `font-size: .875rem;`.

<select class="flex-select mb-3" style="font-size: .875rem;">
  <option selected>Open this select menu</option>
  <option value="1">One</option>
  <option value="2">Two</option>
  <option value="3">Three</option>
</select>

### Multiple and size attributes

Adding `multple` or `size` should render the select as expected, though with (expected) limited styling of the `<option>`s.

<select class="flex-select mb-3" multiple>
  <option value="1">One</option>
  <option value="2">Two</option>
  <option value="3">Three</option>
  <option value="4">Four</option>
  <option value="5">Five</option>
</select>

<select class="flex-select mb-3" size="3">
  <option value="1">One</option>
  <option value="2">Two</option>
  <option value="3">Three</option>
  <option value="4">Four</option>
  <option value="5">Five</option>
</select>

## File

<hr class="mt-2 mb-3">

<div class="flex-file">
  <input type="file" class="flex-file-input" id="customFile">
  <label class="flex-file-label" for="customFile" data-browse="Browse">Choose file</label>
</div>
