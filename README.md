# Local Hide/Unhide System (Fork Feature Outline)

Since this fork is frozen in its current state and will no longer receive upstream updates, the **Local Hide/Unhide System** is the core defining feature that sets it apart from the original ComfyUI-Manager. 

This architecture allows you to clean up your workspace by muting unwanted nodes or models completely on the client side without altering the backend database channels.

---

## Architecture & Implementation Breakdown

### 1. Persistent Client-Side State
Rather than relying on backend server migrations, the hide status is managed instantly in the browser.
* **Storage Keys:** Tracks hidden items using `cmm_hidden_nodes_list` (for custom nodes) and `cmm_hidden_models_list` (for models) inside the browser's `localStorage`.
* **Persistence:** Because it uses local storage, your muted preferences persist seamlessly across page reloads, browser tabs, and ComfyUI server restarts.

### 2. TurboGrid Pipeline Interception
The feature is deeply integrated into the `turbogrid.esm.js` component engine inside both `custom-nodes-manager.js` and `model-manager.js`:
* **Interactive Column:** A new action column (`id: 'hide_item'`) displaying an eye (`👁`) icon is prepended to the grid layout schema. Clicking it instantly toggles the item's hidden state.
* **Row Filtration Pass:** The grid’s core `rowFilter` method is hooked to cross-reference every item's unique hash against the local hidden list. If a match is found, TurboGrid suppresses the row from being rendered in the DOM.

### 3. Master Global Override UI
To ensure hidden items are never permanently lost, a master toggle switch is injected directly into the manager dialog headers next to the search filter input.

* **"Show Hidden Items" Checkbox:** Checking this box forces the `rowFilter` to bypass the hiding restriction, bringing all muted rows back into view instantly.
* **Visual Muting Classes (`tg-row-is-hidden`):** For clear context, rows that are meant to be hidden are assigned a custom CSS modifier class when forced visible. This applies an `opacity: 0.45` filter and a soft red background tint, making it effortless to identify muted items at a glance so you can click `❌` to unhide them.

---

## Summary of Code Injections
