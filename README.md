# 👁 Hide Items — ComfyUI Manager MOD

A quality-of-life patch for **ComfyUI Manager** that lets you hide custom nodes and models from their respective lists — keeping your workspace clean without uninstalling anything.

files modified: 
- model-manager.js
  custom-nodes-manager.js


---

## ✨ Features

- 🟢 **Green cell** = item is visible (click to hide)
- 🔴 **Red cell** = item is hidden (click to unhide)
- 👻 **Show Hidden** toggle — reveal hidden items as dimmed rows without removing them from the list permanently
- 💾 **Persistent** — hidden lists are saved to disk via the ComfyUI API and survive restarts
- 🧩 Works independently for **Custom Nodes** and **Models**


<img width="1324" height="816" alt="image" src="https://github.com/user-attachments/assets/90982994-4eae-4977-99a0-966cfb6c0ccb" />

<img width="1361" height="836" alt="image" src="https://github.com/user-attachments/assets/00e4d22f-5b91-4850-b730-469962ed1e03" />


---

## 📁 Files

| File | Description |
|------|-------------|
| `custom-nodes-manager.js` | Patched custom nodes manager with hide support |
| `model-manager.js` | Patched model manager with hide support |

just overwrite the files and refresh browser ! 

---

## 💾 Storage

Hidden items are saved to your ComfyUI user data folder:

```
ComfyUI/user/default/hidden_nodes.json   ← custom nodes
ComfyUI/user/default/hidden_models.json  ← models
```

These are plain JSON arrays of item hashes. You can delete them at any time to reset.

---

## 🚀 Usage

1. Drop the patched files into your `ComfyUI-Manager` custom node folder, replacing the originals
2. Restart ComfyUI
3. Open **Custom Nodes Manager** or **Model Manager**
4. Click the coloured cell in the first column to toggle visibility
5. Use the **Show Hidden Items** checkbox in the header to peek at hidden entries

---

---

## 📝 Notes

> Hidden items are **not** uninstalled — they're just filtered from view. Re-enable anytime by clicking the red cell or using the Show Hidden toggle.
