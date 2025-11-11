# Browser

The good, the bad and the ugly about extension on mainstream browsers (Chrome, Safari, Firefox, etc).


## Pros

- Easy to install.
- Easy to discover.
- Asks the user for high level [permissions](https://developer.chrome.com/docs/extensions/develop/concepts/declare-permissions) (not fine-grained).
- Ability to improve the user's agency and security.
- Ability to customise a page to a person's liking.
- Ability to slightly tweak the browser's behaviour (eg. vertical tabs) depending on the browser.
- Provides convenience.


## Cons

- Can be modified without the user's consent, missing auditing/visibility capabilities. Legitimate extensions can turn malicious.
- May do more than assumed/intended by asking for more permissions than it should.
- Vague privacy-policies and handling of user data.
- Ability to hide third-party code.
- Susceptible to phishing, spying, email spamming, affiliate fraud, malvertising, and payment fraud.
- Gatekept by centralised extension stores.
- Actions of an extension may be obscured.
- No full control over the browsing experience, still subjected to the container and tabs model.
- Potentially large performance impact.
- Limited control over activation (usually either always on or enabled per tab)
- No fine-grained, subscoped permissions.
- No cross extension interop.
- Does not enable tighter integrations with local-first or cloud data solutions.


## On the fence

These may be positive or negative, depending on the way you look at it.

- State partitioning
- CORS


## Threat models

Malicious intent in order to gain access to a user's data, financial info, activities, etc. Done through the methods described above in the cons section.


## Use cases & numbers

The most popular Chrome extension categories¹ are:

* Productivity (56%)
* Lifestyle (33%)
* Make Chrome yours (11%)

Most popular extensions:

* Adobe Acrobat
* "a bunch of ad blockers"
* Grammarly
* Google Translate
* "remote desktop tools"
* Honey (scam)
* MetaMask
* Teleparty (watch together)
* Tampermonkey (userscripts).

The latter has 11 million users on Chrome, of its total estimated 3.8 billion installs (2025). That's 0.28% of users that installs this extension. Compared to Adobe Acrobat's 327 million users, which is 8.6%.

Bit hard to say what the ad blocking portion is because there's a bunch of different extensions here. But summing up the three most popular ones: Adblock (62 mil), Adblock Plus (41 mil), uBlock (hard to say because ..., some older stats say 37 mil). Which would be roughly 140 mil, 3.7%. That's only the biggest three, so suffice to say, people hate ads and are willing to install an extension for that.

### Some quotes from a research article²

> Only about 0.2% of extensions (roughly 242) have achieved more than one million installations, and a mere 13 extensions have surpassed the 10 million user mark (Backlinko, 2024). This “long tail” phenomenon indicates that while Chrome offers the most extensive selection, actual usage is concentrated among a relatively small number of highly popular extensions.

> Mozilla Firefox, despite holding a smaller market share of between 2.5% and 6.4% depending on the platform, hosts over 36,000 extensions in its Firefox Add-ons store (AMO).

> Despite its modest market share, Firefox users demonstrate the highest demonstrated propensity to install extensions on a per-user basis. According to the Firefox Public Data Report, over 40% of Firefox desktop users worldwide have at least one user-installed add-on (Firefox Public Data Report, 2025). This figure varies regionally, reaching nearly 60% in countries like Russia and Canada, while being lower (around 19%) in India.

> While Chrome dominates in terms of absolute numbers due to its massive user base, the average Chrome user may install fewer extensions than Firefox users. The concentration of installations among a small percentage of extensions suggests that most Chrome users stick to common, widely-adopted extensions like ad blockers, productivity tools, and shopping assistants rather than exploring the depths of what’s available.

> Safari users likely install the fewest extensions on average among the major browsers. The App Store distribution model, smaller selection, and more stringent multi-step permission process prioritize security and quality over quantity and ease of installation. Safari’s approach to extensions involves a more controlled ecosystem with higher barriers to both development and adoption.

Notes:
- I can't say how reliable these numbers are (install metrics are from the official Chrome Extension store). A lot of different numbers from various sources.
- Chrome messed up some ad blockers with manifest v3 (what so-called security was actually gained here?)


## Implementation specifics

- Safari's permission model is the most granular.
- Only Safari does system-level installation of extensions through their respective app stores. Other app stores are in the form of a website.


## Sources

- [A Study on Malicious Browser Extensions in 2025](https://arxiv.org/html/2503.04292v2)
- [Chrome Extension Statistics: Data From 2024](https://www.debugbear.com/blog/chrome-extension-statistics)¹
- [Browser Extension Installation Habits and Market Size](https://browserbeast.com/browser-extension-installation-habits-and-market-size/)²
