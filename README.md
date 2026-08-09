# Ernesto González

### Mobile Engineer · iOS (Swift · SwiftUI) & Android (Kotlin · Jetpack Compose)

<p align="center">
  <img src="https://img.shields.io/badge/Swift-F05138?style=for-the-badge&logo=swift&logoColor=white" alt="Swift"/>
  <img src="https://img.shields.io/badge/SwiftUI-0071e3?style=for-the-badge&logo=swift&logoColor=white" alt="SwiftUI"/>
  <img src="https://img.shields.io/badge/Kotlin-7F52FF?style=for-the-badge&logo=kotlin&logoColor=white" alt="Kotlin"/>
  <img src="https://img.shields.io/badge/Jetpack_Compose-4285F4?style=for-the-badge&logo=jetpackcompose&logoColor=white" alt="Jetpack Compose"/>
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript"/>
  <img src="https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white" alt="Next.js"/>
  <img src="https://img.shields.io/badge/Django-092E20?style=for-the-badge&logo=django&logoColor=white" alt="Django"/>
</p>

I ship the same product on both platforms — feature for feature, in Swift and in Kotlin — plus the backends and web frontends they talk to.

---

## 👨‍💻 One product, two idioms

Same screen, same architecture, written twice — because that is what shipping on both platforms actually means.

<table>
<tr>
<th align="left">🍎 &nbsp;iOS · Swift</th>
<th align="left">🤖 &nbsp;Android · Kotlin</th>
</tr>
<tr valign="top">
<td>

```swift
@MainActor @Observable
final class ViewModelNoteList {
    private(set) var state: TypeUIListState = .loading

    private let loadNotes: LogicLoadNotes

    func reload() async {
        do {
            let notes = try await loadNotes(query: search)
            state = resolve(for: notes)
        } catch {
            state = .failed(error.localizedDescription)
        }
    }
}
```

</td>
<td>

```kotlin
class NoteListViewModel(
    private val loadNotes: LoadNotes
) : ViewModel() {

    private val _state = MutableStateFlow<ListState>(Loading)
    val state = _state.asStateFlow()

    fun reload() = viewModelScope.launch {
        _state.value = runCatching { loadNotes(query) }
            .fold(
                onSuccess = ::resolve,
                onFailure = { Failed(it.messageOrEmpty()) }
            )
    }
}
```

</td>
</tr>
</table>

One state value the UI switches over — never `isLoading` + `notes` + `error` in parallel, which lets you represent *loading and failed at once* and forces every view to invent a precedence. Use cases injected one by one, so a view model's capabilities are exactly what its initialiser lists. The idioms differ; the reasoning does not.

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
