# sonner-js

sonner-js is a dependency-free, vanilla JavaScript version of the [Sonner](https://sonner.emilkowal.ski/) toast component originally built for React. This version maintains almost the same functionality but is built to be used in any JavaScript project without the need for React.

## Usage

To start using the library, include it in your project:

```html
<script src="path/to/sonner.js"></script>
<link rel="stylesheet" href="path/to/sonner.css" />
```

Then, initialize and start showing toasts:

```javascript
Sonner.init();
Sonner.show("My first toast");
```

```html
<button onclick="Sonner.show('Here\'s a toast')">Give me a toast</button>
```

## Roadmap

Some of the features of the original Sonner component are not available in this version. These include:

1. Implement missing features
   1. Custom toast components
   2. Promise toast
   3. TypeScript definitions
2. Improve the example
3. Add tests
4. Add CI/CD

The intention is to implement these features in the future.

The example also needs some love. It's a bit rough around the edges.

For now, if you want to run the example, all you need to do is clone the repository and open the `example/index.html` file in your browser.

The existing implementation serves as a proof of concept. However, we anticipate a few enhancements in the near future to refine the project:

1. Transition to Web Components: We plan to adopt Web Components to enhance the modularity and reusability of our code.
2. Refactor API Exposure: Currently, the API is exposed via the `window` object. We aim to revise this approach for a more encapsulated and secure method of API exposure.

## Sonner API

The Sonner API is very simple and consists of a few methods:

- `init`
- `success`
- `error`
- `info`
- `warning`
- `show`
- `remove`

### `init(options)`

Initializes the toasters in the DOM.

**Parameters:**

- `options` (Object)
  - `closeButton` (boolean): Controls the visibility of the close button on the toasts.
  - `richColors` (boolean): Controls the use of rich colors for the toasts.
  - `position` (string): Controls the position of the toasts. Possible values are `top-left`, `top-center`, `top-right`, `bottom-left`, `bottom-center`, and `bottom-right`.
  - `theme` (string): The color theme for the toasts. Possible values are `"light"`, `"dark"`, and `"system"` (default: `"system"`). When set to `"system"`, the theme is detected from the user's `prefers-color-scheme` media query and automatically updates when the system preference changes.
  - `duration` (number): Global default toast duration in milliseconds. Overrides the built-in default of 4000ms. Individual toasts can still override this with a per-toast `duration`.

**Example:**

```javascript
Sonner.init({
  closeButton: true,
  richColors: true,
  position: "bottom-right",
  theme: "dark",
  duration: 5000,
});
```

### `success(msg, descriptionOrOptions)`

Shows a new success toast with a specific message.

**Parameters:**

- `msg` (string): The message to display in the toast.
- `descriptionOrOptions` (string | Object): A description string, or an options object with `description`, `duration`, etc.

**Returns:** `string` — the toast id.

**Examples:**

```javascript
Sonner.success("Saved!");
Sonner.success("Saved!", "Your changes have been saved.");
Sonner.success("Saved!", { description: "Your changes have been saved.", duration: 8000 });
```

### `error(msg, descriptionOrOptions)`

Shows a new error toast with a specific message.

**Parameters:**

- `msg` (string): The message to display in the toast.
- `descriptionOrOptions` (string | Object): A description string, or an options object.

**Returns:** `string` — the toast id.

### `info(msg, descriptionOrOptions)`

Shows a new info toast with a specific message.

**Parameters:**

- `msg` (string): The message to display in the toast.
- `descriptionOrOptions` (string | Object): A description string, or an options object.

**Returns:** `string` — the toast id.

### `warning(msg, descriptionOrOptions)`

Shows a new warning toast with a specific message.

**Parameters:**

- `msg` (string): The message to display in the toast.
- `descriptionOrOptions` (string | Object): A description string, or an options object.

**Returns:** `string` — the toast id.

### `show(msg, options)`

Shows a new toast with a specific message, description, and type.

**Parameters:**

- `msg` (string): The message to display in the toast.
- `options` (Object)
  - `type` (string): The type of the toast.
  - `description` (string): The description to display in the toast.
  - `duration` (number): Per-toast duration in milliseconds. Overrides the global `duration` set in `init()`.

**Returns:** `string` — the toast id.

**Example:**

```javascript
const id = Sonner.show("Processing…", { type: "info", duration: 10000 });
// Later, remove it programmatically:
Sonner.remove(id);
```

### `remove(id)`

Removes an element with a specific id from the DOM after a delay.

**Parameters:**

- `id` (string): The data-id attribute of the element to remove.

## Thanks

This is a fork of [sonner-js](https://github.com/ofps/sonner-js) by [Fernando Pina dos Santos](https://github.com/ofps) — thank you for the excellent vanilla JS port!

I would also like to thank [Emil Kowalski](https://emilkowal.ski/) for creating the original Sonner component and for the inspiration behind this project.

## License

This library is licensed under the MIT license. See the [LICENSE](LICENSE) file for more information.
