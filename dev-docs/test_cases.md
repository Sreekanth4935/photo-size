# Photo Size KB Tool: Test Cases

*Created: 2026-05-02*
*Last updated: 2026-05-02*

This file is the daily QA contract for Antigravity/Codex and the user.

Rule: before implementing any day from `execution_plan.md`, the agent must add concrete test cases for that day in this file. After implementation, the agent must run the automated checks, record evidence, and leave the manual checks for the user unless the user explicitly confirms them.

## Status Legend

| Status | Meaning |
|---|---|
| Not written | Test cases for this day still need to be expanded before coding. |
| Ready | Test cases are written but not run. |
| Automated pass | Agent ran automated checks and they passed. |
| Automated fail | Agent ran automated checks and at least one failed. |
| Manual pending | User still needs to test on device. |
| Manual pass | User confirmed the manual check passed. |
| Manual fail | User found an issue manually. |
| Blocked | Test cannot run because of missing dependency/device/permission. |

## Required Automated Checks Every Coding Day

Run from `C:\dev\photo-size`.

| Check | Command / Method | Required Evidence |
|---|---|---|
| Build | `./gradlew.bat assembleDebug --console=plain` | Build result and error summary if failed. |
| Unit tests | `./gradlew.bat testDebugUnitTest --console=plain` once tests exist | Pass/fail count. |
| Device detection | `adb devices` | Connected device serial or blocked reason. |
| Install | `./gradlew.bat installDebug --console=plain` when device is connected | Install result. |
| Launch smoke | `adb shell monkey -p com.sreekanth.photosize -c android.intent.category.LAUNCHER 1` | No crash and app opens. |
| Runtime logs | Check crash/logcat only when behavior fails | Short relevant error summary. |
| Docs | Update `history.md` and `testing_log.md` | Files updated with the day result. |

## Testing Strategy

- Unit test pure logic: preset dimensions, aspect ratios, resize math, compression quality search, filename generation, validation badges.
- Use deterministic sample images committed under test resources when image engine tests are added.
- Use fake image repositories for Compose UI tests so crop/result screens can be tested without real user media.
- Use device/instrumented tests for Photo Picker intent, save/share flows, and MediaStore/user-selected output when practical.
- Use manual testing for real crop gestures, visual preview quality, exact KB acceptability, save/share UX, and portal-style result confidence.

## Ad Format QA Requirements

These checks apply to every ad-related day.

| Area | Automated Check | Manual Check |
|---|---|---|
| Test-only ads | Verify debug config uses only Google demo/test IDs for adaptive banner, interstitial, native, and native video | Confirm visible ads show test labeling/headline where the SDK provides it |
| No live ads before completion | Search source/build config for production ad unit IDs before release approval | Confirm no real advertiser ad is clicked during development |
| Banner ads | Verify banner only renders on allowed safe surfaces after useful content | Confirm banner does not cover crop, resize, compression, save, or share controls |
| Interstitial ads | Verify frequency cap and natural-transition gate exist | Confirm no interstitial appears before image selection, during crop/edit, or before output is ready |
| Native Advanced video ads | Verify `MediaView`, visible `Ad` label, AdChoices placement, CTA/assets, and native destroy handling | Confirm video/native card is clearly an ad and visually separate from export actions |

## Day-by-Day QA Matrix

| Day | Feature Gate | Test Cases Written | Automated Status | Manual Status | Evidence / Notes |
|---|---|---|---|---|---|
| 1 | Product grounding | Not written | Blocked | Manual pending | Docs-only day; verify selected-image-only privacy. |
| 2 | App navigation | Not written | Blocked | Manual pending | Home, picker, crop, result, presets, history, settings. |
| 3 | Image picker | Not written | Blocked | Manual pending | Photo Picker single selection, cancel/error. |
| 4 | Preset model | Not written | Blocked | Manual pending | Common photo/signature/custom presets. |
| 5 | Crop UI | Not written | Blocked | Manual pending | Fixed aspect ratio, rotate, reset, fit/fill. |
| 6 | Resize engine | Not written | Blocked | Manual pending | Exact pixel output and format support. |
| 7 | Compression engine | Not written | Blocked | Manual pending | Target KB best effort and quality preservation. |
| 8 | Result screen | Not written | Blocked | Manual pending | Before/after, validation badges, edit actions. |
| 9 | Save and share | Not written | Blocked | Manual pending | Save, share, filename, failure states. |
| 10 | Signature mode | Not written | Blocked | Manual pending | Signature presets and high-contrast preview. |
| 11 | Custom size | Not written | Blocked | Manual pending | Width/height/target KB/format validation. |
| 12 | History | Not written | Blocked | Manual pending | Recent outputs without retaining originals. |
| 13 | Settings | Not written | Blocked | Manual pending | Theme, default format, save behavior, clear history. |
| 14 | UI polish | Not written | Blocked | Manual pending | Result cards, loading state, dark mode, small screen. |
| 15 | Accessibility | Not written | Blocked | Manual pending | Crop controls, text scaling, contrast. |
| 16 | Ad architecture test-only | Not written | Blocked | Manual pending | Banner, interstitial, native, native video test IDs and lifecycle cleanup only. |
| 17 | Banner and Native Advanced ad UI | Not written | Blocked | Manual pending | Ad below result, away from Save button, with banner container. |
| 18 | Safe ad placement and interstitial gate | Not written | Blocked | Manual pending | No ad before first successful resize; interstitial frequency cap enforced. |
| 19 | Internal QA | Not written | Blocked | Manual pending | Presets, target KB, save/share. |
| 20 | Play Store prep | Not written | Blocked | Manual pending | Listing/screenshots/data safety/privacy. |
| 21 | First release decision | Not written | Blocked | Manual pending | Release only if single-image workflow is stable. |

## Detailed Test Case Template

When starting a day, add a section named `Day N Detailed Test Cases` below and fill it before coding.

| ID | Type | Test Case | Steps | Expected Result | Automated Result | Manual Result | Evidence |
|---|---|---|---|---|---|---|---|
| PS-DN-A01 | Automated | Build remains green | Run the build command | Build succeeds | Ready | Manual pending | Pending |
| PS-DN-M01 | Manual | User-visible flow feels precise | User tests on Vivo V2426 | Flow is clear, fast, and polished | Automated pass when applicable | Manual pending | Pending |

## Open Manual QA Queue

Manual checks stay here until the user tests them.

| Date Added | Day | Area | Manual Check | Status | User Notes |
|---|---|---|---|---|---|
| 2026-05-02 | All | Baseline | Confirm app opens, splash/icon/name look correct on device | Manual pending |  |
