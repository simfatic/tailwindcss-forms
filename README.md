# @simfatic/tailwindcss-forms 

Forked from @tailwindcss/forms and added some alternate styles

A plugin that provides a basic reset for form styles that makes form elements easy to override with utilities.

## Installation

> Note that @tailwindcss/forms is designed for Tailwind CSS v2.0.

Install the plugin from npm:

```sh
# Using npm
npm install @tailwindcss/forms

# Using Yarn
yarn add @tailwindcss/forms
```

Then add the plugin to your `tailwind.config.js` file:

```js
// tailwind.config.js
module.exports = {
  theme: {
    // ...
  },
  plugins: [
    require('@tailwindcss/forms'),
    // ...
  ],
}
```

## Basic usage

[**View the live demo**](https://tailwindcss-forms.vercel.app/)

All of the basic form elements you use will now have some simple default styles that are easy to override with utilities.

Currently we add basic utility-friendly form styles for the following form element types:

- `input[type='text']`
- `input[type='password']`
- `input[type='email']`
- `input[type='number']`
- `input[type='url']`
- `input[type='date']`
- `input[type='datetime-local']`
- `input[type='month']`
- `input[type='week']`
- `input[type='time']`
- `input[type='search']`
- `input[type='tel']`
- `input[type='checkbox']`
- `input[type='radio']`
- `select`
- `select[multiple]`
- `textarea`

**Note that for text inputs, you must add the `type="text"` attribute for these styles to take effect.** This is a necessary trade-off to avoid relying on the overly greedy `input` selector and unintentionally styling elements we don't have solutions for yet, like `input[type="range"]` for example.

Every element has been normalized/reset to a simple visually consistent style that is easy to customize with utilities, even elements like `<select>` or `<input type="checkbox">` that normally need to be reset with `appearance: none` and customized using custom CSS:

```html
<!-- You can actually customize padding on a select element now: -->
<select class="px-4 py-3 rounded-full">
  <!-- ... -->
</select>

<!-- Or change a checkbox color using text color utilities: -->
<input type="checkbox" class="rounded text-pink-500" />
```

More customization examples and best practices coming soon.

### Using classes instead of element selectors

Although we recommend thinking of this plugin as a "form reset" rather than a collection of form component styles, in some cases our default approach may be too heavy-handed, especially when integrating this plugin into existing projects.

For situations where the default strategy doesn't work well with your project, you can use the `class` strategy to make all form styling _opt-in_ instead of applied globally:

```js
// tailwind.config.js
plugins: [
 require("@tailwindcss/forms")({
   strategy: 'class',
 }),
],
```

When using the `class` strategy, form elements do not receive any reset styles by default, and reset styles are added per element using a new set of `form-*` classes generated by the plugin:

```html
<input type="email" class="form-input px-4 py-3 rounded-full">

<select class="form-select px-4 py-3 rounded-full">
  <!-- ... -->
</select>

<input type="checkbox" class="form-checkbox rounded text-pink-500" />
```

Here is a complete table of the provided `form-*` classes for reference:

| Base                      | Class              |
| ------------------------- | ------------------ |
| `[type='text']`           | `form-input`       |
| `[type='email']`          | `form-input`       |
| `[type='url']`            | `form-input`       |
| `[type='password']`       | `form-input`       |
| `[type='number']`         | `form-input`       |
| `[type='date']`           | `form-input`       |
| `[type='datetime-local']` | `form-input`       |
| `[type='month']`          | `form-input`       |
| `[type='search']`         | `form-input`       |
| `[type='tel']`            | `form-input`       |
| `[type='time']`           | `form-input`       |
| `[type='week']`           | `form-input`       |
| `textarea`                | `form-textarea`    |
| `select`                  | `form-select`      |
| `select[multiple]`        | `form-multiselect` |
| `[type='checkbox']`       | `form-checkbox`    |
| `[type='radio']`          | `form-radio`       |
