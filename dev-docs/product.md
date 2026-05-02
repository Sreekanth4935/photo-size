# Photo Size KB Tool: Product Overview

*Created: 2026-05-01*
*Last updated: 2026-05-02*

## App Identity

- **App Name:** Photo Size KB Tool
- **Package:** com.sreekanth.photosize
- **Category:** Photography / Tools
- **Theme Color:** #2E7D32

## Purpose

Resize images to exact dimensions and file sizes for exams, forms, and official documents.

This is not meant to compete as a generic cropper. A gallery editor can crop a photo, but it does not validate exam/form constraints such as exact pixels, target KB range, signature mode, output format, and before/after file size. Photo Size KB Tool should feel like an output validator for forms: pick a preset, crop, compress, verify, then save/share.

## Product Differentiator

| Generic Cropper/Gallery Editor | Photo Size KB Tool |
|---|---|
| Crops visually | Produces exact pixel dimensions |
| No file-size target | Compresses toward target KB/MB |
| No form context | Photo/signature presets for exams and applications |
| No output validation | Shows width, height, file size, format badges |
| User guesses quality | Provides best-effort compression result with clear status |
| Often saves broadly | Processes selected image locally and exports by user action |

## Core V1 Experience

1. User chooses Photo, Signature, or Custom mode.
2. User selects one image through Android Photo Picker.
3. User picks a preset or enters custom width, height, target KB, and format.
4. App guides crop with correct aspect ratio, rotate, reset, fit/fill.
5. App resizes to exact pixels and compresses toward target KB.
6. Result screen shows before/after preview, dimensions, size, format, and validation badges.
7. User can edit again, try smaller, save, or share.
8. Recent output metadata is stored locally without retaining unnecessary originals.

## Target Audience

- Government exam applicants
- Students and job seekers
- Users submitting admission, job, or portal forms
- Users resizing photo/signature images to strict KB and pixel limits
- Users who want local processing without signup or cloud upload

## Product Principles

1. **Offline-first**: All core features work without internet
2. **No account required**: Zero login, zero signup
3. **Privacy-first**: No data leaves the device
4. **Simple UX**: Every screen understandable in under 1 second
5. **Lightweight**: Minimal APK size, minimal battery usage
6. **Output-first**: Every workflow ends with clear validation of dimensions and file size
7. **Honest constraints**: The app prepares files to user-selected limits, but does not guarantee portal acceptance

## Planned Feature Layers

### V1: Useful Free App

- Single selected image workflow
- Photo/signature/custom modes
- Common photo and signature presets
- Crop, rotate, reset, fit/fill
- Exact pixel resize
- Target KB compression
- JPG/PNG output where supported
- Validation badges and before/after preview
- Save/share output

### V1.1: Polish and Presets

- Better preset library
- Improved compression quality messaging
- Recent output history
- Better dark mode and small-screen layout
- Test-only ads after successful output

### V2: Premium Direction

- Batch resize
- Country/exam preset packs
- PDF export
- Signature cleanup/high-contrast tools
- Saved preset templates
- One-time ad-free unlock

## Revenue Strategy (Future)

- Free tier with safe ads after useful output
- Test ads only until app is feature-complete and release-approved
- Prefer one-time ad-free unlock before subscription
- Subscription only if regularly updated preset libraries create recurring value
- No backend costs in year 1

## Technical Foundation

- Native Android (Kotlin + Jetpack Compose)
- Material 3 Design
- MVVM architecture
- Min SDK 24 / Target SDK 35
- No backend, no API calls, no cloud
