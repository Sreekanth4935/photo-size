# Photo Size: Execution Plan

*Created: 2026-05-01*
*Last updated: 2026-05-02*
*Research pass: 2026-05-02*

This plan turns the starter project into a fast photo/signature resize tool for exams, job forms, admissions, and government portals. This is one of the strongest first-release candidates because it has simple offline value and clear search intent.

## Agent Execution Contract

When Antigravity/Codex is asked to complete one day or a range of days, it must treat this file as the product and engineering source of truth.

- Read `product.md`, `features.md`, `ui_system.md`, `play_store_compliance.md`, `testing_log.md`, `test_cases.md`, and this file before changing code.
- Implement only the requested day range unless a dependency from an earlier day is missing; document any unavoidable prerequisite work.
- Before coding each day, expand that day's section in `test_cases.md` with concrete automated and manual test cases.
- After coding each day, run the automated checks listed in `test_cases.md`, update automated status/evidence, and leave manual status open for the user unless the user explicitly confirms it.
- Update `history.md`, `testing_log.md`, and `pre-release-checklist.md` whenever a milestone, test pass, or release gate changes.
- Never mark a day complete if build, install, launch, or the day-specific automated tests fail.

## Quality Bar

- UI must feel premium, fast, and task-first: no landing page, no clutter, no ads before the first successful resize.
- Architecture must stay layered: Compose UI, ViewModel/state holder, domain/use cases for image operations, repositories/local output store.
- State must follow unidirectional data flow; image operations expose progress and result state clearly.
- Data must be local-first. No account, backend, analytics, or cloud dependency unless a future plan explicitly adds it.
- Image processing must be correct before feature breadth: exact dimensions, target KB best effort, transparent error states, and no main-thread bitmap work.
- Accessibility is part of completion: scalable text, 48dp controls, TalkBack labels for controls/results, and validation badges with text labels.
- Store copy must not imply official exam acceptance; the app prepares files to user-selected constraints.

## Current Status

- [x] Native Android project created
- [x] Kotlin + Jetpack Compose + Material 3 setup
- [x] Package: `com.sreekanth.photosize`
- [x] Debug build successful
- [x] Installed on Vivo V2426 / Android 16
- [x] Launch smoke test passed
- [x] Dev docs created
- [x] README created
- [x] Git repository initialized
- [x] Adaptive launcher icon added
- [ ] Real resize/compress functionality
- [ ] Production ad units
- [ ] Play Store release assets

## Research Notes

Competitors such as Puma Photo Resizer, Image Resizer for SSC/Forms, and Photo Maker for Form Fillup focus on reducing file size to KB/MB, exact pixel dimensions, signature resize, exam/job portal presets, crop/edit, and share/save. The opportunity is a clean, exam-focused, offline-first app with fewer distracting features and clearer output validation.

Important policy and platform constraints:

- Use Android Photo Picker for user-selected images.
- Avoid broad media permissions where possible.
- Do not request `MANAGE_EXTERNAL_STORAGE`.
- Be careful with ads around export actions so accidental taps do not happen.

## Product Positioning

One-line promise:

Resize and compress exam photos/signatures to exact pixel and KB limits offline.

Primary users:

- Government exam applicants
- Students
- Job seekers
- Users submitting online forms
- Users needing exact photo/signature sizes quickly

## Release Strategy

- V1: Single-image photo/signature resize, crop, exact pixel size, target KB compression, save/share.
- V1.1: Common presets and better result validation.
- V1.2: AdMob Native Advanced test then production ads.
- V2: Batch resize and premium preset packs/ad-free upgrade.

Subscription caution:

This app is mostly a utility. Start with ads plus optional one-time lifetime unlock. Subscription should wait unless the app gets recurring value such as regularly updated country/exam preset libraries.

## Monetization Plan

Ad formats in scope for the full plan:

- **Adaptive banner ads**: Low-priority monetization on safe, non-editor surfaces after useful content is visible.
- **Interstitial ads**: Frequency-capped full-screen ads only at natural transitions after successful resize/export; never before selection, during crop/edit/compression, or near save/share buttons.
- **Native Advanced video ads**: Premium-looking native ad cards with `MediaView`, visible `Ad` label, AdChoices, CTA, advertiser/icon/headline assets, and lifecycle cleanup.

Hard test-ad rule:

- Until the app is feature-complete, internally QA-passed, and release-ready, every ad integration must use test ads only.
- Use Google demo ad units during development: Adaptive Banner `ca-app-pub-3940256099942544/9214589741`, Interstitial `ca-app-pub-3940256099942544/1033173712`, Native `ca-app-pub-3940256099942544/2247696110`, Native Video `ca-app-pub-3940256099942544/1044960115`.
- Production ad unit IDs must not be added to source code, docs, or build config until a separate release-readiness task approves UMP consent, privacy policy, frequency caps, and safe placement testing.
- Debug builds must never request live ads.

Use AdMob Native Advanced with video-capable native media after the user completes a task, not before.

Allowed ad placements:

- Result screen below final output preview
- Preset browser after useful content
- History screen after saved outputs
- Settings/About bottom section

Blocked ad placements:

- Image crop surface
- Compression/resize controls
- Save/export button area
- Photo Picker flow
- First launch before user selects an image

Implementation requirements:

- Use test ad units for banner, interstitial, native, and native video during development.
- Use clear `Ad` label and visible AdChoices.
- Use MediaView for native image/video ads.
- Add UMP consent before live ads.
- Add native ad lifecycle destroy handling.

## Premium UI Direction

- Green trust/productivity brand
- First screen is "Choose Photo" with popular presets visible
- No landing page
- Clear before/after file size comparison
- Output validation badges: width, height, file size, format
- Simple language: "Photo", "Signature", "Custom"

## Day-by-Day Plan

Daily definition of done:

- Code for the requested day is implemented and scoped.
- `./gradlew.bat assembleDebug --console=plain` passes.
- If a device is connected, `./gradlew.bat installDebug --console=plain` passes and the app launches without crash.
- Relevant unit/instrumented/UI tests are added or updated for the day's behavior.
- `dev-docs/test_cases.md` has automated results recorded and manual results left for user verification.
- `dev-docs/history.md` and `dev-docs/testing_log.md` are updated with evidence.

### Day 1: Product Grounding

- [ ] Update product docs for exam/form photo resize.
- [ ] Define v1 scope: single image, crop, resize, compress, save/share.
- [ ] Add privacy note: selected image only, local processing.
- [ ] Confirm no broad storage permissions.

### Day 2: App Navigation

- [ ] Add Compose Navigation.
- [ ] Create routes: Home, PickImage, CropResize, Result, Presets, History, Settings, About.
- [ ] Replace placeholder buttons with real routes.
- [ ] Add premium app shell.

### Day 3: Image Picker

- [ ] Integrate Android Photo Picker.
- [ ] Support single image selection.
- [ ] Load selected image into preview safely.
- [ ] Handle cancel/error states.

### Day 4: Preset Model

- [ ] Create preset data class.
- [ ] Add common presets: photo 200x230, 240x240, 300x300, signature 140x60, 300x80, custom.
- [ ] Include target KB ranges.
- [ ] Build preset selector UI.

### Day 5: Crop UI

- [ ] Add crop surface with fixed aspect ratio from preset.
- [ ] Add rotate and reset.
- [ ] Add fit/fill options.
- [ ] Keep controls reachable on small screens.

### Day 6: Resize Engine

- [ ] Implement bitmap resize to exact pixels.
- [ ] Preserve aspect ratio where needed.
- [ ] Support JPG and PNG output.
- [ ] Add unit tests for dimension outputs.

### Day 7: Compression Engine

- [ ] Implement JPG quality search for target KB.
- [ ] Show best effort when exact target cannot be reached.
- [ ] Preserve readable quality.
- [ ] Add tests for target size behavior.

### Day 8: Result Screen

- [ ] Show before/after preview.
- [ ] Show original size, output size, dimensions, format.
- [ ] Add validation badges.
- [ ] Add "Try smaller" and "Edit again" actions.

### Day 9: Save and Share

- [ ] Save output through MediaStore or user-selected location.
- [ ] Add share sheet.
- [ ] Add filename template.
- [ ] Handle save failure states.

### Day 10: Signature Mode

- [ ] Add signature-specific presets.
- [ ] Add high-contrast preview background.
- [ ] Add crop guide.
- [ ] Add output validation.

### Day 11: Custom Size

- [ ] Add custom width/height inputs.
- [ ] Add target KB input.
- [ ] Add format selector.
- [ ] Validate invalid values clearly.

### Day 12: History

- [ ] Store recent output metadata locally.
- [ ] Show recent processed files.
- [ ] Allow reopen/share recent file if available.
- [ ] Do not store original image unnecessarily.

### Day 13: Settings

- [ ] Theme mode.
- [ ] Default output format.
- [ ] Default save folder behavior.
- [ ] Clear history.

### Day 14: UI Polish

- [ ] Polish result cards and validation badges.
- [ ] Add loading/progress state.
- [ ] Verify dark mode.
- [ ] Verify small screen layout.

### Day 15: Accessibility

- [ ] Add content descriptions.
- [ ] Verify crop controls are reachable.
- [ ] Verify text scaling.
- [ ] Verify contrast.

### Day 16: Ad Architecture, Test Only

- [ ] Add Google Mobile Ads SDK.
- [ ] Add wrappers/state holders for adaptive banner, interstitial, native, and native video with test units.
- [ ] Add UMP placeholder/plan.
- [ ] Destroy `AdView` and native ads on lifecycle cleanup.
- [ ] Add interstitial frequency cap and natural-transition gate.

### Day 17: Banner and Native Advanced Ad UI

- [ ] Build adaptive banner container for safe lower-content surfaces.
- [ ] Build native advanced video-capable ad card for result screen.
- [ ] Include visible `Ad` label, AdChoices, MediaView, CTA.
- [ ] Keep ad visually separate from Save button.
- [ ] Add loading/failed states.

### Day 18: Safe Ad Placement and Interstitial Gate

- [ ] Place banner/native ad below result details, not near export button.
- [ ] Show interstitial only after successful export/share or when leaving Result, never before the output is ready.
- [ ] Add frequency cap.
- [ ] Add settings toggle placeholder for future ad-free mode.
- [ ] Verify no ad before first successful resize.

### Day 19: Internal QA

- [ ] Run `assembleDebug`.
- [ ] Run `installDebug`.
- [ ] Test all presets.
- [ ] Test target KB outputs.
- [ ] Test save/share.
- [ ] Update testing log.

### Day 20: Play Store Prep

- [ ] Draft store listing around exam/photo/signature resize.
- [ ] Prepare screenshots: Home, Presets, Crop, Result, History.
- [ ] Prepare Data Safety notes.
- [ ] Prepare privacy policy.

### Day 21: First Release Decision

- [ ] Release if single-image workflow is stable.
- [ ] Keep batch resize for v2.
- [ ] Do not add subscription before v1 metrics.

## Future Backlog

- Batch resize
- Country/exam preset packs
- PDF export
- Background cleanup for signatures
- Watermark-free premium exports if watermark is ever added
- One-time lifetime ad-free unlock
- Cloud backup is not needed

## Research References

- Google Play: Puma Photo Resizer, Image Resizer for SSC/Forms, Photo Maker for Form Fillup competitor listings
- Android Photo Picker: https://developer.android.com/training/data-storage/shared/photo-picker
- Google Play sensitive permissions: https://support.google.com/googleplay/android-developer/answer/16558241
- AdMob Native Ads Android: https://developers.google.com/admob/android/native
- AdMob native ad units: https://support.google.com/admob/answer/7187428
- Google Play subscriptions policy: https://support.google.com/googleplay/android-developer/answer/9900533
