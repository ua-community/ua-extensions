# Obsidian

An analysis of [plugins](https://obsidian.md/plugins) in the interactive note taking tool called [Obsidian](https://obsidian.md).


## Positives

- Easy to install through the [community plugin index](https://obsidian.md/plugins).
- Easy to add custom plugins from elsewhere by adding them to a directory presented through the app's settings.
- Plugins need to be activated manually after installation.
- Settings pages for the plugin.
- Automatic updates for plugins that are not in the main community index through the [BRAT](https://github.com/TfTHacker/obsidian42-brat) plugin.
- Obsidian runs in restricted mode by default to prevent third-party code execution.


## Negatives

- Automatic updates of community plugins, legitimate extensions can turn malicious.
- Vulnerable to [injection](https://docs.obsidian.md/Plugins/Releasing/Plugin+guidelines#Avoid+%60innerHTML%60%2C+%60outerHTML%60+and+%60insertAdjacentHTML%60) attacks.
- No permission system.
- [No sandboxing](https://help.obsidian.md/plugin-security#Plugin+capabilities), plugins have access to whatever the parent app has access to.


## Impediments

These may be positive or negative, depending on the way you look at it.

- All community plugins go through an [initial review](https://help.obsidian.md/plugin-security#Plugin+review+process).
- Core plugins cannot be disabled.


## Threat models

If the user is not careful and is convinced to disable the restricted mode, a plugin can gain access to the device and/or web; depending on the access levels of the Obsidian app it is executed in.


## Use cases & numbers

Most popular plugins:

- 4.8M: **Excalidraw**, canvas files in your notes.
- 3.4M: **Dataview**, a query language for your Obsidian vault (Obsidian Bases, a core plugin, supersedes this most likely)
- 3.2M: **Templater**, executes arbitrary JavaScript code and system commands (potentially dangerous).
- 2.8M: **Tasks**, task tracking.

More: tables, calendar, kanban.

Some other notable ones:
- 1.9M: **Git**, version control.
- 184K: **Local REST API**
- 163K: **Google Calendar**
- Various (unofficial) sync plugins.
- Importing data plugins.
