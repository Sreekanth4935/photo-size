# Photo Size KB Tool: Feature List

*Created: 2026-05-01*
*Last updated: 2026-05-02*

This document lists all planned features for Photo Size KB Tool.

---

## 1. Core V1 Features

- **Photo/signature/custom modes**: Separate workflows for common form needs.
- **Android Photo Picker input**: User-selected image only.
- **Preset sizes for common forms**: Popular photo/signature sizes with target KB hints.
- **Resize by pixels**: Exact width and height output.
- **Resize by KB/MB**: Target file-size compression with best-effort result.
- **Crop and rotate**: Aspect-ratio crop, rotate, reset, fit/fill.
- **Quality control**: JPG/WebP quality behavior where supported.
- **Format selector**: JPG/PNG output where appropriate.
- **Before/after preview**: Original and output preview with file-size comparison.
- **Validation badges**: Width, height, file size, and format pass/warning state.
- **Save and share**: User-initiated output save/share.
- **History metadata**: Recent output metadata without storing originals unnecessarily.

## 2. Settings and Customization (Planned)

- **Theme Toggle**: Dark / Light / System mode
- **Language Support**: English initially, expandable
- **Default output format**: User preference for JPG/PNG where supported
- **Default save behavior**: Choose save/share defaults where platform allows
- **Clear history**: Remove local recent-output metadata
- **Custom preset defaults**: Remember last custom dimensions and target KB

## 3. Ads and Monetization

- **Test-only ads during development**: Banner, interstitial, native, and native video must use Google demo/test units only.
- **Safe banner ads**: Result/history/settings after useful content only.
- **Safe interstitial ads**: Frequency-capped after successful export/share or leaving Result, never before output is ready.
- **Native Advanced video ads**: Result/history safe surfaces with Ad label, AdChoices, MediaView, and lifecycle cleanup.
- **Ad-free unlock**: Future one-time purchase after core workflow is stable.

## 4. Premium Future Features

- **Batch resize**: Process multiple selected images after single-image V1 is reliable.
- **Country/exam preset packs**: Maintained preset libraries if there is recurring value.
- **PDF export**: Export outputs into PDF when useful for forms.
- **Signature cleanup**: High-contrast/cleanup tools for scanned signatures.
- **Saved custom presets**: Save frequently used dimensions and target sizes.
- **Ad-free mode**: Remove ads after app quality is proven.

## 5. Explicitly Out of Scope for V1

- Official portal acceptance guarantee
- Batch processing
- AI background removal
- Broad storage access or `MANAGE_EXTERNAL_STORAGE`
- Cloud upload/compression
- Live production ads
- Subscription-only core resizing

## 6. Privacy and Compliance

- **No Login Required**: App works fully offline
- **Local-Only Storage**: All data stays on-device
- **No Unnecessary Permissions**: Only request what is needed
- **Privacy Policy**: Will be hosted externally and linked in-app
- **Honest Output Copy**: App validates against selected limits but cannot guarantee third-party portal acceptance
