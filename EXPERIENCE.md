# Detailed Experience

This document complements the [resume](RESUME.md): it goes behind the recent
role into the projects — the context, the decisions, and what they changed —
and gives a complete record of earlier roles and projects.

---

## March 2022 – September 2026 · Кошелёк → Т-Банк

**Senior iOS Engineer — Product & Platform.** Four and a half years on one
product of roughly 1M monthly active users, owning authentication, networking,
and platform work end-to-end. The through-line was pairing product delivery with the
cross-cutting engineering — migrations, infrastructure, tooling — that lifted
the whole platform rather than individual screens.

> **Employer note.** Employed by Кошелёк from March 2022 to June 2024, then by
> Т-Банк after the legal entity change — same team, same Кошелёк product, no
> break in continuity. Work moved to the Т-Банк app for the final four months
> (June–September 2026).

### Deep dives

#### Foundations: dependencies and identity — 2022

- **Context** — The first year went into the app's foundations: dependency
  management and the authentication and token layer everything else depended on.
- **What I did** — Moved the project from CocoaPods to SPM, refactored auth and
  token handling, added passcode and biometrics protection, and built OTP-based
  access recovery and account deletion.
- **Impact** — A cleaner dependency graph and a modernized auth layer for the
  2023 identity migration to build on, with the account lifecycle covered from
  the start.
- **Tech** — Swift, Objective-C, SPM, Keychain.

#### Tinkoff ID / SSO authentication migration — 2023

- **Context** — Authentication lived in a legacy, app-local model that could not
  be shared across the ecosystem, and its token and registration flows carried
  years of accumulated workarounds.
- **What I did** — Migrated the app to Tinkoff ID as the identity provider,
  implemented referential auth, and rebuilt registration and onboarding on top
  of the new model. Kept the existing passcode/biometric protection and OTP
  recovery working through the transition.
- **Impact** — One identity model across the ecosystem; the legacy auth code
  path retired rather than maintained alongside the new one.
- **Tech** — Swift, Objective-C interoperability, Keychain.

#### The "Выгода" (Benefits) tab — 2024

- **Context** — The app had accumulated discount and cashback surfaces scattered
  across the product, with no single place for a user to see what they gain from
  holding a card.
- **What I did** — Built the tab from scratch: the screen structure and
  navigation, the loading and empty states, and the analytics instrumentation.
  Shipped it behind an A/B test rather than as a global rollout, with automated
  coverage for the new flows.
- **Impact** — A flagship product area delivered end-to-end, from architecture
  to release, instrumented well enough to be measured from day one.
- **Tech** — Swift, UIKit

#### A/B and remote-configuration wrapper — 2024

- **Context** — The company already had a core A/B and remote-configuration
  platform, but feature teams were still using an older mechanism in the iOS
  app, which made it hard to gate a feature consistently or measure it
  afterwards. The goal was not to replace the core platform but to make it easy
  for the rest of the app's teams to come onto it.
- **What I did** — Built an iOS-side wrapper over the core platform: a thin,
  familiar interface that matched how the app was already written, so a feature
  could be gated, configured remotely, and instrumented through one mechanism
  without the team having to relearn the underlying API.
- **Impact** — Lowered the cost of switching rather than mandating it. New A/B
  tests went through the wrapper and teams onboarded gradually, with the old
  system retired as its last consumers moved over.
- **Tech** — Swift, SPM.

#### Networking layer migration and retry infrastructure — 2025–2026

- **Context** — The networking layer had grown organically: inconsistent request
  construction, scattered retry logic, and legacy paths that no longer matched
  how the app talked to the backend.
- **What I did** — Migrated the layer to a unified design and added retry
  infrastructure, including multipart uploads and the request/response
  plumbing used by the features above. Retired legacy paths as their consumers
  moved over.
- **Impact** — One place to reason about requests, retries, and failures; less
  duplicated networking code across the app, and the migration completed with no
  regressions detected.
- **Tech** — Swift, REST, multipart uploads, SSL pinning.

#### Developer-agent tooling — 2026

- **Context** — The repository is large and old enough that routine work —
  scaffolding an A/B test, wiring up an API method — costs more in context
  gathering than in actual code.
- **What I did** — Set up the **Nessy developer-agent** configuration and wrote
  skills for those two tasks, encoding how they are actually done here — which
  files to touch and which conventions to follow — so an agent reproduces them
  instead of approximating.
- **Impact** — Cut the setup overhead on the tasks I repeat most and left the
  configuration in the repository when I moved on. It stayed a personal workflow
  aid rather than a team-wide rollout, so there are no adoption or time-saving
  figures to report.
- **Tech** — Nessy, agent skill and tool configuration, prompt design.

#### Leadership and mentoring — 2022–2024

Tech lead for the iOS team through a period of headcount reduction: three
engineers at the start, two after roughly a month, one by the end — me. I was
the iOS developer remaining when the team contracted to a single person. Owned
technical direction, planning, and code review throughout, keeping the area's
delivery moving as the team contracted. Set and split tasks, mentored the
engineers on the team, and onboarded new joiners into a large legacy codebase.

### Т-Банк app: Cards and Clubs (web) — June – September 2026

Prepared the Cards and Clubs feature for web technologies while keeping it
embedded in the native app:

- Entry points with webview fallback screens, and two-way web-to-native
  communication.
- A new Special Project Entry Point block on the Receipt Offer screen,
  implemented and deployed.
- Web-side bug fixes while ramping up on TypeScript and React.
- _Tech_ — Swift, TypeScript, React.

---

## November 2021 – March 2022 · Akvelon

**iOS Engineer.** Staff-augmentation engagement on the official Reddit app.

- Converted core parts of the app from Objective-C to Swift.
- Worked on modularizing the monolith, laying groundwork other teams could build
  on.
- Removed singleton usages across the app and made general stability
  improvements.
- _Tech_ — Objective-C, Swift.

---

## September 2013 – October 2021 · Очень Интересно (Saritasa)

**iOS Developer.** Built apps from first commit to App Store release, and
maintained existing ones; worked directly with backend teams, TMs, and PMs;
reviewed code, mentored other iOS developers, and set and split tasks.

Delivered **20+ projects** over eight years; a sample of the notable ones:

### ICON Intelligent Control

_iPhone app — adjust ICON Vehicle Dynamics electronic shocks_

- Implemented a custom communication protocol over Bluetooth with the ICON
  Vehicle Dynamics box, the communication and firmware update logic, and the UI.
- _Tech_ — Swift, CoreBluetooth, Alamofire.

### Masimo Radius T°

_iPhone app — Continuous Thermometer_

- Custom implementation of the temperature timeline graph component; UI and
  logic for temperature and sensor notifications.
- _Tech_ — Swift, CoreGraphics, CoreBluetooth, Realm.

### Steady Head

_iPhone app — Golf Swing Trainer_

- UI; face detection and video recording of the swing; logic for detecting a
  good or bad swing.
- _Tech_ — Swift, Vision, ReplayKit.

### DigitalEMS

_iPad app for paramedics in USA_

- Implemented new features and bug fixes; refactored and transitioned the
  project to use ARC; wrote unit tests for critical parts.
- _Tech_ — Objective-C, AFNetworking, Cordova, ZOXSeries.

### uSummit

_iPhone/iPad app — event management platform_

- UI and logic for several modules; fixed bugs and implemented new features.
- _Tech_ — Swift, AlecrimCoreData, PromiseKit, Swagger.

### Helpjess for iPhone

_iPhone app — Virtual shop with ability to video call a merchant_

- UI and logic for several parts of the app; video call functionality.
- _Tech_ — Swift, Moya, RxSwift.

---

## Education

### Associate in Automation of technological processes and production

> _September 2004 to June 2008_ | Berezniki Polytechnic College
