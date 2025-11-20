# Zed

An extensibility review of [Zed](https://zed.dev), the code editor.


## Positives

- Fine-grained [capabilities](https://zed.dev/docs/extensions/capabilities)! Appears to be introduced quietly very recently.
- Easy to install extensions from inside the app.
- Many areas to extend.


## Negatives

- Automatic updates, legitimate extensions can turn malicious.
- Extensions by default appear to not restrict their capabilities. [Unclear documentation](https://github.com/zed-industries/zed/issues/42473).
- [No sandboxing](https://github.com/zed-industries/zed/issues/12358) for language servers.


## Threat models

Unclear from the extension store which extensions have restricted capabilities (if at all). So an extension may have access to everything Zed has access to.
