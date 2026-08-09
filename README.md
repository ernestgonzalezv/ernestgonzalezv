# Ernesto González

### Mobile Engineer · iOS (Swift · SwiftUI) & Android (Kotlin · Jetpack Compose)

I ship the same product on both platforms — feature for feature, in Swift and in Kotlin — plus the backends and web frontends they talk to.

---

## 👨‍💻 About me

```kotlin
data class Ernesto(
    val focus: List<String> = listOf("iOS · Swift · SwiftUI", "Android · Kotlin · Jetpack Compose"),
    val architecture: List<String> = listOf("MVVM", "Clean Architecture", "MVI"),
    val alsoBuilds: List<String> = listOf("Django REST APIs", "Next.js + React frontends"),
    val alsoKnows: List<String> = listOf(".NET", "Django", "Angular", "Vue")
)
```

```swift
struct Ernesto {
    let focus = ["iOS · Swift · SwiftUI", "Android · Kotlin · Jetpack Compose"]
    let architecture = ["MVVM", "Clean Architecture", "Ports & Adapters"]
    let concurrency = "Swift 6, strict data-race checking"
}
```

---

## 🍎 iOS (Modern Stack)

* <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/swift/swift-original.svg" width="14"/> Swift 6 — full strict-concurrency checking, `Sendable` correctness
* 🎨 SwiftUI (declarative UI) + Observation (`@Observable`)
* 🧱 UIKit interop where SwiftUI does not reach yet
* 🏗️ MVVM + Clean Architecture — ports & adapters, injection by initialiser, no service locators
* ⚡ Swift Concurrency — async/await, actors, `AsyncStream`, task cancellation
* 🔁 Combine (`PassthroughSubject` / `AnyPublisher`) for cross-layer events
* 🗄️ SwiftData + Core Data (local persistence behind a repository port)
* 🌐 `URLSession` + async/await, retry with jittered exponential backoff, `Codable`
* 📞 CallKit / VoIP with PushKit (real calling, not a mock)
* 💬 SignalR (real-time messaging)
* 💳 Apple Pay + 3-D Secure, PayPal, card scanning
* 🔔 Push notifications + Notification Service Extension
* 🗣️ App Intents & Siri Shortcuts, Core Spotlight indexing
* 🔥 Firebase + Google Sign-In, AWS Amplify
* 🌍 String catalogs (`.xcstrings`) — 4 languages, plural variations, translator context per key
* ♿ Accessibility — VoiceOver, Dynamic Type, Reduce Motion, swipe actions mirrored as accessibility actions
* 🧪 Swift Testing (`@Test` / `#expect`) + XCTest
* 📦 Swift Package Manager — modular targets with enforced dependency direction
* 🛠️ XcodeGen (generated `.xcodeproj`, reviewable `project.yml`) + SwiftLint
* 🚀 TestFlight, App Store releases, GitHub Actions on macOS runners

**Reference implementation:** **[quill-ios](https://github.com/ernestgonzalezv/quill-ios)** — offline-first notes app. Three SPM modules with dependencies pointing inward, Swift 6 strict concurrency, SwiftData behind a port, a sync engine whose last-write-wins conflict resolution is a pure exhaustively-tested function, tombstoned deletes, App Intents + Spotlight, 4-language localisation, 50 tests, CI green on every push.

---

## 🤖 Android (Modern Stack)

* <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/android/android-original.svg" width="14"/> Android
* <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/kotlin/kotlin-original.svg" width="14"/> Kotlin
* 🧭 Jetpack Compose (modern declarative UI)
* 🏗️ MVVM + Clean Architecture
* 🧠 MVI (state-driven architecture)
* 🧱 Multi-module by feature (`feature/*` + `core/*`) with Gradle convention plugins in `build-logic`
* ⚡ Coroutines + Flow (asynchronous reactive programming)
* 🧩 Hilt (Dependency Injection) · Koin (used in production)
* 🌐 Retrofit + OkHttp (networking) · Ktor Client (CIO/OkHttp engines, auth, logging, content negotiation)
* 🗄️ Room + DataStore (modern local persistence) + Paging 3
* 🧬 Kotlin Serialization / Gson · kotlinx.datetime
* 📷 CameraX + ML Kit text recognition · Coil · Lottie · Splash Screen API
* 🔐 Credential Manager + Google ID, SMS Retriever, libphonenumber
* 💳 Google Pay (Play Services Wallet)
* 🧪 JUnit + MockK (unit testing) · Mockito-Kotlin · Turbine · `kotlinx-coroutines-test`
* 🧪 Espresso (UI testing)
* 📦 Gradle Kotlin DSL + KSP
* 🔥 Firebase (Auth / Firestore / Push Notifications)
* 📱 Material 3 Design System
* 🚀 Codemagic, Play Console releases

---

## 🔗 Shipped on both platforms

The hard parts are the ones that have to work twice, in two idioms:

* **Feature parity across two codebases** — same flows, same edge cases, one product
* **Offline-first** — local store as source of truth, sync as an enhancement, tombstoned deletes so a deletion propagates instead of the note resurrecting
* **Payments end to end** — Apple Pay / Google Pay, 3-D Secure, PayPal, card scanning, and the failure states nobody demos
* **Push notifications** — APNs & FCM, deep links that land on the right screen
* **Localisation** — 4 languages (en / es / ht / pt)
* **Accessibility** — VoiceOver / TalkBack, Dynamic Type, Reduce Motion
* **Release engineering** — TestFlight, Play Console, signing, staged rollouts

---

## 🛠️ Languages

* <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/swift/swift-original.svg" width="14"/> Swift
* <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/kotlin/kotlin-original.svg" width="14"/> Kotlin
* <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/csharp/csharp-original.svg" width="14"/> C#
* <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" width="14"/> Python
* <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/typescript/typescript-original.svg" width="14"/> TypeScript
* <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/javascript/javascript-original.svg" width="14"/> JavaScript

---

## 🌐 Web Frontend

* <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/nextjs/nextjs-original.svg" width="14"/> Next.js 16 (App Router, Turbopack)
* <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/react/react-original.svg" width="14"/> React 19
* <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/typescript/typescript-original.svg" width="14"/> TypeScript
* <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/tailwindcss/tailwindcss-original.svg" width="14"/> Tailwind CSS 4
* 🧩 Radix UI / shadcn-style component systems, `next-themes` (dark mode)
* 📝 React Hook Form + Zod (schema validation)
* 🗃️ Zustand (client state)
* 📊 Recharts · dnd-kit (drag & drop) · Embla (carousels)
* <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/angularjs/angularjs-original.svg" width="14"/> Angular · <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/vuejs/vuejs-original.svg" width="14"/> Vue

---

## 🌐 Backend

### Django (Python)

* <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/django/django-plain.svg" width="14"/> Django
* 🧪 Django Test Framework (unittest-based testing)
* 🧪 pytest + pytest-django (modern testing approach)
* 🧪 Factory Boy (test data generation)
* 🔐 Django REST Framework (REST APIs)
* 📑 drf-spectacular — OpenAPI schema generated and **enforced in CI** (zero warnings, no drift from the committed schema)
* ⚙️ Celery (background task processing) + Redis — periodic tasks, batched push delivery
* 🗄️ Django ORM (database abstraction layer) — explicit indexes, soft-delete with `PROTECT` for auditable history
* 🔒 Django Authentication & Permissions — token auth with refresh/revoke, Google OAuth, argon2, role-scoped querysets
* ☁️ MinIO / S3 presigned uploads — the client `PUT`s directly, the API never proxies the binary
* 📲 Expo Push for React Native / Expo clients

---

### .NET (C#)

* <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/dot-net/dot-net-original.svg" width="14"/> .NET Core / .NET 8
* 🧪 xUnit (modern testing framework)
* 🧪 NUnit (alternative testing framework)
* 🧪 Moq (mocking library)
* 🧪 FluentAssertions (clean assertions)
* 🌐 ASP.NET Core Web API
* 🧱 Entity Framework Core
* 🔐 Identity + JWT Authentication
* ⚙️ Background Services / Hosted Services

---

## 🗄️ Databases

* <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/postgresql/postgresql-original.svg" width="14"/> PostgreSQL
* <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/mongodb/mongodb-original.svg" width="14"/> MongoDB
* <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/firebase/firebase-plain.svg" width="14"/> Firebase
* <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/sqlite/sqlite-original.svg" width="14"/> SQLite
* 🍎 SwiftData · Core Data (iOS) · 🤖 Room · DataStore (Android)
* ⚡ Redis

---

## 🧪 Testing & Quality (Full Stack)

### iOS / Swift

* Swift Testing (`@Test` / `#expect`)
* XCTest
* In-memory doubles behind protocols — view-model tests need no database and no network stub
* SwiftLint `--strict` as a merge gate

### Android / Kotlin

* JUnit 5
* MockK
* Espresso
* Turbine (Flow testing)

### Django

* pytest
* pytest-django
* Factory Boy
* Django TestCase / APITestCase

### .NET

* xUnit
* NUnit
* Moq
* FluentAssertions

---

## 🔄 CI/CD

* GitHub Actions — macOS runners for iOS build + test, self-hosted runners for deploys, path filtering so a docs-only PR does not burn the pipeline, required status checks on the default branch
* GitLab CI
* Jenkins
* Docker — images published to GHCR, container deploys behind a reverse proxy
* Codemagic (Android) · TestFlight (iOS)

---

## ☁️ Cloud & DevOps

* Docker
* Kubernetes
* AWS (EC2, S3, Lambda, RDS)
* Firebase (serverless backend for mobile apps)
* MinIO (S3-compatible object storage)

---

## 🧭 How I work

* **GitFlow** with `--no-ff` merges, so a branch stays a visible unit of work in the history
* **ADRs** for structural decisions — context, options weighed, decision, consequences accepted
* Commit messages that explain *why*, not what the diff already shows
* Conventions written down and enforced by tooling, not by memory
* Root-cause fixes over temporary patches

---

## 🧠 Soft Skills

* Problem-solving focused on root cause analysis
* Strong code review culture
* Clear and concise technical communication
* Calm under pressure
* Continuous learning mindset

---

📫 **[ernesto@cococel.com](mailto:ernesto@cococel.com)** — open to mobile engineering roles: iOS, Android, or both.
