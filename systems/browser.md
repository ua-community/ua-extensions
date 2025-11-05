## Pros

- Easy to install.
- Easy to discover.
- Asks the user for high level permissions. (https://developer.chrome.com/docs/extensions/develop/concepts/declare-permissions)
- Ability to improve the user's agency and security.
- Ability to customise a page to a person's liking.
- Ability to slightly tweak the browser's behaviour (eg. vertical tabs) depending on the browser.
- Provides convenience.


## Cons

- Can be modified without the user's consent, missing auditing/ visibility cpabilites. Legitimate extensions can turn malicious.
- May do more than assumed/intended by asking for more permissions than it should.
- Vague privacy-policies and handling of user data.
- Ability to hide third-party code.
- Susceptible to phishing, spying, email spamming, affiliate fraud, malvertising, and payment fraud.
- Gatekept by centralised extension stores.
- Actions of an extension may be obscured.
- No full control over the browsing experience, still subjected to the container and tabs model.
- potentially huge performance impact
- no fine grined, subscoped permissions
- limited runtime permissions
- very limited control over ad hoc/ surgical activation (usually either always on or enabled per tab)

## On the fence

These may be positive or negative, depending on the way you look at it.

- State partitioning
- CORS


## Threat models

Malicious intent in order to gain access to a user's data, financial info, activities, etc. Done through the methods described above.


## Sources

- A Study on Malicious Browser Extensions in 2025: https://arxiv.org/html/2503.04292v2
