# ComfyUI-Manager: Frontend (js)

This directory contains the JavaScript frontend implementation for ComfyUI-Manager, providing the user interface components that interact with the backend API.

## Core Components

- **comfyui-manager.js**: Main entry point that initializes the manager UI and integrates with ComfyUI.
- **custom-nodes-manager.js**: Implements the UI for browsing, installing, and managing custom nodes. Includes local hide/unhide toggling capabilities via TurboGrid row interception.
- **model-manager.js**: Handles the model management interface for downloading and organizing AI models. Features a local hide/unhide state manager matching the custom nodes architecture.
- **components-manager.js**: Manages reusable workflow components system.
- **snapshot.js**: Implements the snapshot system for backing up and restoring installations.

### Local Filtering Features (Hide/Unhide)

The frontend features a client-side item hiding mechanism implemented in both `custom-nodes-manager.js` and `model-manager.js`:
- **State Persistence**: Hidden item hashes are retained locally in the browser using `localStorage` keys (`cmm_hidden_nodes_list` and `cmm_hidden_models_list`).
- **TurboGrid Visibility Interception**: Triggered inside the `rowFilter` callback configuration to dynamically remove rows from view unless explicitly overridden.
- **Master UI Override**: Provides a global "Show Hidden Items" checkbox wrapper in the dialog header section to reveal hidden items temporarily. Forced-visible rows are dimmed visually for easy recognition.

## Sharing Components

- **comfyui-share-common.js**: Base functionality for workflow sharing features.
- **comfyui-share-copus.js**: Integration with the ComfyUI Copus sharing platform.
- **comfyui-share-openart.js**: Integration with the OpenArt sharing platform.
- **comfyui-share-youml.js**: Integration with the YouML sharing platform.

## Utility Components

- **cm-api.js**: Client-side API wrapper for communication with the backend.
- **common.js**: Shared utilities and helper functions used across the frontend.
- **node_fixer.js**: Utilities for fixing disconnected links and repairing malformed nodes by recreating them while preserving connections.
- **popover-helper.js**: UI component for popup tooltips and contextual information.
- **turbogrid.esm.js**: Grid component library - https://github.com/cenfun/turbogrid
- **workflow-metadata.js**: Handles workflow metadata parsing, validation and cross-repository compatibility including versioning, dependencies tracking, and resource management.

## Architecture

The frontend follows a modular component-based architecture:

1. **Integration Layer**: Connects with ComfyUI's existing UI system
2. **Manager Components**: Individual functional UI components (node manager, model manager, etc.)
3. **Sharing Components**: Platform-specific sharing implementations
4. **Utility Layer**: Reusable UI components and helpers

## Implementation Details

- The frontend integrates directly with ComfyUI's UI system through `app.js`
- Dialog-based UI for most manager functions to avoid cluttering the main interface
- Asynchronous API calls to handle backend operations without blocking the UI

## Styling

CSS files are included for specific components:
- **custom-nodes-manager.css**: Styling for the node management UI
- **model-manager.css**: Styling for the model management UI. Contains matching style properties for dimming and highlighing local `tg-row-is-hidden` state rows.

This frontend implementation provides a comprehensive yet user-friendly interface for managing the ComfyUI ecosystem.
