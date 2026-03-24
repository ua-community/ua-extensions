# Observations

Some random observations related to the various discussed extension systems.

* Sandboxing and narrow permissions are rare, especially for desktop software and small teams.
* Many popular extension systems opt for automatic updates and centralised stores.


## Extension structure

### Peek

- The structure of `background.js` is similar to that of an Obsidian plugin. They both have `init` and `uninit` callbacks (called `onload` and `onunload` in Obsidian).
- Peek and Raycast work quite differently in terms of defining their commands and UI. Raycast manages its UI in the plugin commands and Peek has a settings UI schema.
