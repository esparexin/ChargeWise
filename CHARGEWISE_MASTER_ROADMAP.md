# ChargeWise Master Roadmap

## Product Direction

ChargeWise is a privacy-first, offline-first battery-care assistant for macOS and iOS. It provides practical, evidence-based guidance to help users reduce avoidable battery wear without sacrificing everyday convenience.

### V1 Principles and Boundaries
- Local-only processing and storage; no backend, account, cloud sync, analytics, advertising, or payment system.
- Use supported public APIs only. Never fabricate, assume, or present unavailable telemetry as a measured value.
- Battery recommendations must explain what is happening, what the user can do, and why.
- Shared battery-care rules are the single source of truth across platforms; platform collectors and UI remain separate.
- ChargeWise advises only. It does not control charging, detect charger proximity, or claim reliable temperature data unless a supported source is validated.
- User-entered health/cycle data must be clearly labeled, timestamped, editable, and removable.

## Phase 0 — Preparation (Current)
No app implementation until the scope, platform capabilities, architecture, and release gates are reviewed.

- Confirm V1 scope, exclusions, user scenarios, and recommendation priorities.
- Validate APIs, metric availability, permissions, minimum OS versions, and limitations on real hardware.
- Define normalized battery/power models, source/validity/timestamp handling, and shared advisor boundaries.
- Review recommendation thresholds, conflicts, wording, edge cases, and notification policy; treat unvalidated thresholds as provisional.
- Decide local storage, retention, data deletion, privacy, and accessibility expectations.
- Define testing strategy, supported hardware/OS matrix, CI checks, signing, and release criteria.
- Complete a Phase 0 readiness review and approve the implementation plan.

**Exit gate:** Requirements and limitations are documented, major design decisions are approved, test strategy is agreed, and implementation can begin without unresolved scope or platform assumptions.

## Phase 1 — Foundation
- Set up the Xcode project, macOS and iOS targets, shared core, and repository quality gates.
- Establish shared models/contracts, design tokens, architecture boundaries, and test structure.
- Add only infrastructure justified by approved requirements.

**Exit gate:** Clean builds, core tests, architecture boundaries, and CI checks pass.

## Phase 2 — macOS Experience
- Implement a public-API power/battery collector with validated optional metrics.
- Build menu-bar access, dashboard, settings, and user-configurable notifications.
- Integrate shared advisor rules and clearly distinguish measured, unavailable, and manually entered data.

**Exit gate:** Collector and UI behavior validated on supported Mac hardware; recommendation scenarios and notification controls pass tests.

## Phase 3 — iOS Experience
- Implement UIDevice battery level/state monitoring within iOS lifecycle limits.
- Reuse shared advisor logic and provide dashboard, battery-care guidance, and settings.
- Support manual health/cycle entries only with clear source labels and user controls.

**Exit gate:** iOS API limitations are represented accurately; foreground/background behavior and supported scenarios are tested on device.

## Phase 4 — Local History
- Add local history and trend views only for validated metrics.
- Define retention and deletion controls; avoid collecting unnecessary data.

**Exit gate:** History is accurate, bounded by retention policy, and fully deletable.

## Phase 5 — Helpful Enhancements
- Add notification refinements, quiet hours, and optional widgets only where platform support and user value are validated.
- Keep notifications configurable and avoid repetitive or alarmist guidance.

**Exit gate:** Enhancements respect permissions, lifecycle constraints, accessibility, and user settings.

## Phase 6 — QA and Release
- Validate on physical Mac and iPhone devices across supported OS versions.
- Run functional, unit, regression, accessibility, privacy, security, performance, and energy-impact checks.
- Review signing, packaging, TestFlight/App Store requirements, and release documentation.

**Release gate:** No unresolved critical/high-severity issues; supported builds and tests pass; telemetry accuracy, privacy, data deletion, and recommendation boundaries are verified.

## V1 Explicitly Out of Scope
- Backend, accounts, cloud sync, analytics, advertising, payments, or remote management.
- Direct charge control or charger-proximity detection.
- Temperature-based advice unless a reliable, supported, validated metric becomes available.
- Replacement/service recommendations based on cycle count alone.
- Continuous background monitoring claims where platform behavior does not support them.

## Dependency Order
Phase 0 approval → Phase 1 Foundation → Phase 2 macOS → Phase 3 iOS → Phase 4 Local History → Phase 5 Enhancements → Phase 6 QA/Release.

Phases may overlap only when their dependencies and shared contracts are established, and work must not duplicate or fork the shared advisor, data contracts, or platform capability assumptions.
