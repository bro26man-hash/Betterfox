# RESEARCH_NOTES.md — Podcast Research: Digital Rights & Surveillance Technology

> **Project:** Betterfox (yokoffing/Betterfox) — 10,862 ⭐, MIT License, actively maintained  
> **Forked to:** bro26man-hash/Betterfox  
> **Context:** Open-source Firefox privacy hardening template — `user.js` configuration file that disables tracking, fingerprinting surfaces, and telemetry while balancing usability.

---

## 1. PROJECT OVERVIEW

Betterfox is a curated `user.js` file that hardens Mozilla Firefox against tracking, fingerprinting, and data exfiltration. It's built on three philosophical pillars:

1. **Minimalism** — remove what isn't needed
2. **Efficiency** — unleash Firefox's performance
3. **Privacy** — protect data without causing site breakage

It's been adopted by browser forks including Zen, Waterfox, Floorp, Ghostery Dawn, and others, making it a de facto standard for browser-level privacy hardening.

**Why this project matters for the podcast:** Betterfox sits at the exact intersection of corporate surveillance, individual privacy, and the usability trade-off that defines the digital rights debate. It's a tool that *everyday people* can use to push back against surveillance capitalism — but it also exposes the deeper question: *Should users have to opt out of surveillance? Should the default browser be a surveillance instrument?*

---

## 2. KEY ETHICAL TENSIONS & SOCIETAL CONCERNS

### 2A. The Illusion of Opt-Out: Firefox Telemetry as Case Study

**Source:** [Issue #443 — "To opt-out or not to opt-out"](https://github.com/yokoffing/Betterfox/issues/443)

**What happened:** A contributor discovered that Firefox's "opt-out" preferences for telemetry coverage (`toolkit.coverage.opt-out` and `toolkit.telemetry.coverage.opt-out`) are **outdated placebos** — they no longer exist in Firefox's configuration and haven't worked for years. Meanwhile, Mozilla's own documentation confirms that the newer `toolkit.telemetry.user_characteristics_ping.opt-out` only works if the main telemetry switches are already disabled.

**The deeper question:** If a user follows the official instructions to "opt out" of telemetry, but those Prefs are broken or circumvented, is the user being *lied to*? Is "opt-out" a genuine control or a placebo that creates the *appearance* of consent while surveillance continues?

**Podcast angle — "The Opt-Out Trap":**
- How many "privacy settings" are theater? The opt-out mechanism may be more about *shifting blame* to the user than actually respecting autonomy.
- The philosophy of "privacy by default" vs. "privacy by opt-out" — which paradigm truly respects civil liberties?
- The parallel to GDPR/CCPA: do corporate "consent" mechanisms function like Betterfox's dead prefs — creating the illusion of compliance while the surveillance continues?

### 2B. Corporate Complicity: Google on the Privacy Allowlist

**Source:** [Issue #389 — "SecureFox/Tracking Protection/Query Stripping"](https://github.com/yokoffing/Betterfox/issues/389)

**What happened:** Firefox's built-in "query stripping" feature — supposedly designed to remove tracking parameters from URLs — has only **14 entries** on its allowlist. Worse, `googleadservices.com` is explicitly on the allowlist, meaning Google's ad services are *exempt* from Firefox's own privacy protection.

**The deeper question:** When the same entity (Google) that profits from surveillance is also whitelisted by the tool designed to block surveillance, is this ** institutional capture** of the privacy tool? Is Firefox's "Strict" mode actually "Strict" if it makes exceptions for the most prolific surveillance advertiser on the web?

**Podcast angle — "Thefox who guards the henhouse":**
- The conflict of interest when surveillance capitalists provide "privacy" tools
- Mozilla receives significant revenue from Google — does this create structural incentives to look the other way?
- The 14-entry allowlist vs. 2,065-entry community list (AdGuard) — bureaucracy vs. grassroots effectiveness
- Question: Is "query stripping" a privacy feature or a **surveillance compliance feature** that makes politicians feel good about regulating while nothing actually changes?

### 2C. The FROST Attack: When Browsers Become Surveillance Instruments

**Source:** [Issue #486 — "Mitigate FROST attack"](https://github.com/yokoffing/Betterfox/issues/486)

**What happened:** Researchers discovered that websites can track users by measuring **SSD activity** through the browser's Origin Private File System (OPFS) API. By writing large files and measuring timing, a site can fingerprint a user's storage hardware — a channel that's nearly impossible to block without disabling the API entirely. The recommended mitigation: `dom.fs.enabled=false`.

**The deeper question:** Mozilla **acknowledged** the findings but **did not implement a mitigation**. Apple deemed it "out of scope." Chromium "did not consider fingerprinting attacks security vulnerabilities." Who decides what counts as a surveillance vulnerability? When the entities that should defend users instead defer to the same companies profiting from surveillance, what does "security" even mean?

**Podcast angle — "The Disappearing Vulnerability":**
- **The triage of harm:** Browser vendors treated FROST as a "nice to have" rather than a fundamental surveillance vector. What does it say about the hierarchy of "security" when hardware-level tracking is deprioritized?
- **The mitigation paradox:** Disabling `dom.fs.enabled` breaks legitimate websites. This is the recurring tension: **privacy breaks things**. If the cure for surveillance is broken websites, is the cure worse than the disease?
- **The ghost in the machine:** The issue's author posted as "ghost" and commented: *"I didn't find how to submit this without GitHub which is owned by Microsoft evil corp, so exactly after I submit it, I will appear here as ghost."* — A surveillance critic forced to use the infrastructure of a surveillance capitalist to report surveillance. The irony is the story.

### 2D. The Usability-Abolitionist Spectrum

**Source:** Betterfox README philosophy + community discussions

Betterfox explicitly frames itself as *"without causing site breakage"* — a philosophy that the project calls the "law of diminishing returns" and "minimum effective dose." This positions the project on a spectrum:

- **One end:** Maximum privacy, maximum breakage (e.g., disable all JavaScript, use Tor Browser for everything)
- **Other end:** Maximum usability, maximum surveillance (e.g., default Chrome with no extensions)
- **Betterfox's position:** Privacy that *works* — protect users without making the web unusable

**Podcast angle — "The compromise that isn't":**
- Is "privacy without breakage" genuinely a win, or is it just **surveillance with a veneer of respectability**? Every time Betterfox walks back a privacy setting to avoid site breakage, it's an admission that the web's architecture is *built on surveillance*.
- The "Minimum Effective Dose" concept borrows from pharmacology — but with surveillance, the "effective dose" is defined by the surveillant, not the patient. Who decides what dose of privacy is "enough"?
- The radical alternative: **Abolitionist privacy** — not reforming surveillance but abolishing the infrastructure that enables it. What would that look like?

---

## 3. STRUCTURAL & SYSTEMIC CONCERNS

### 3A. The Infrastructure Problem
The FROST issue author couldn't submit their finding to the Betterfox project without using GitHub (owned by Microsoft). The surveillance critic is trapped inside the surveillance栈 (stack). This raises:
- Can **anti-surveillance tools** be developed on **surveillance infrastructure**?
- Does the platform shape the message? (Would a FROST report on a decentralized platform reach maintainers differently?)
- The paradox of building privacy tools on infrastructure that depends on surveillance capitalism for its existence.

### 3B. The Governance Gap
When Mozilla acknowledges but ignores a vulnerability, and Apple declares it "out of scope," and Chromium says fingerprinting isn't a security issue — **who is accountable for the surveillance state of the web?**
- Regulatory capture: The same companies that profit from surveillance design the "privacy" standards
- The "opt-out" placebo: Broken prefs create the illusion of user agency
- The allowlist Capture: Google's ad services are whitelisted by the very browser that claims to protect privacy

### 3C. The Community as Counterweight
Betterfox's community (10,862 stars, contributors like arkenfox, filterlists maintainers) represents a **grassroots counter-surveillance movement** — people who recognized that the institutions meant to protect privacy are either captured or inadequate, and built alternatives.
- The community fills gaps left by corporate governance
- But: Can a volunteer-driven project sustain long-term resistance against well-funded surveillance capitalism?
- The tension between community-driven privacy and corporate "privacy-washing"

---

## 4. PODCAST STRUCTURE SUGGESTIONS

### Act I: The Tool (What is Betterfox and why does it matter?)
- Explain what a `user.js` is and how it works
- The philosophy: "Your favorite browser, but better"
- Real-world impact: Adopted by Zen, Waterfox, Floorp, Ghostery Dawn
- The paradox: It works *because* the default browser fails

### Act II: The Tensions (What the issues reveal)
- **The Opt-Out Trap** (Issue #443): When "opting out" is a placebo
- **The Google Allowlist** (Issue #389): When the surveillance company whitelists itself
- **The FROST Attack** (Issue #486): When the browser vendor ignores, the critic uses surveillance infrastructure to fight surveillance

### Act III: The Deeper Questions (What should we think about?)
- Is privacy reform possible within a surveillance architecture?
- The "privacy without breakage" promise — is it a compromise or a surrender?
- Who guards the henhouse? The structural conflict of interest in browser privacy
- The abolitionist alternative: Not better surveillance, but no surveillance
- The infrastructure trap: Can we build anti-surveillance tools on surveillance platforms?

### Closing Question for Listeners:
*If the browser on your phone or computer is the most powerful surveillance instrument ever assembled in the hands of individuals — and the "privacy settings" are the doors and windows — how many of those doors are locked from the outside? And how many are just painted on?*

---

## 5. KEY REFERENCES & FURTHER READING

| Topic | Reference |
|-------|-----------|
| FROST attack (SSD fingerprinting) | [Ars Technica: "Websites have a new way to spy on visitors"](https://arstechnica.com/security/2026/05/websites-have-a-new-way-to-spy-on-visitors-analyzing-their-ssd-activity/) |
| OPFS technical details | [web.dev OPFS article](https://web.dev/articles/origin-private-file-system) |
| Mozilla telemetry opt-out bug | [Issue #443](https://github.com/yokoffing/Betterfox/issues/443) |
| Private Internet Access blog on Mozilla telemetry | [PIA: "Mozilla does not respect user requests"](https://www.privateinternetaccess.com/blog/mozilla-does-not-respect-user-requests-to-stop-tracking-telemetry-data/) |
| Query stripping allowlist | [Firefox query-stripping records](https://firefox.settings.services.mozilla.com/v1/buckets/main/collections/query-stripping/records) |
| AdGuard URL tracking list | [Filterlists](https://github.com/yokoffing/filterlists) |
| Betterfox main repo | [yokoffing/Betterfox](https://github.com/yokoffing/Betterfox) |
| arkenfox/user.js (12,851 ⭐) | [arkenfox/user.js](https://github.com/arkenfox/user.js) |
| Firefox bugzilla: telemetry opt-out defeated | [Bug 1487578](https://bugzilla.mozilla.org/show_bug.cgi?id=1487578) |
| Ghostery Dawn (privacy fork) | [Ghostery/Dawn](https://github.com/ghostery/user-agent-desktop) |

---

## 6. ETHICAL FRAMEWORKS TO APPLY

- **Coercion vs. Consent:** Is a "privacy setting" that doesn't work coercion dressed as consent?
- **Structural Violence:** Does the architecture of the web — built on surveillance — constitute a form of violence against user autonomy?
- **Epistemic Injustice:** When Mozilla acknowledges the FROST attack but doesn't fix it, is it **epistemic violence** — dismissing the reality of surveillance harm?
- **The Precautionary Principle:** Should surveillance techniques like FROST be presumed harmful until proven safe, rather than the reverse?
- **Civil Liberties in Digital Spaces:** Does the 4th Amendment analog extend to browser-level tracking? What about SSD fingerprinting?

---

*Notes compiled from GitHub research on yokoffing/Betterfox. Forked for podcast development.*
