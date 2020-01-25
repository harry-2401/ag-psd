# Changelog

## v7.0.0
- **BREAKING CHANGE:** Normalized handling of opacity (now all opacity fields are in 0-1 range, instead of 0-255)
- **BREAKING CHANGE:** Fixed handling for colors (colors are now represented by an array of 4 values in 0-255 range as [R, G, B, A], for example: `[255, 0, 0, 255]` for opaque red color)
- Added handling for layer effects (blending options) (supports all effects except "Pattern Overlay")
- Added `writePsdUint8Array` function for saving to `Uint8Array` (this avoids double memory allocation)
- Removed unnecessary `version` field from `gridAndGuidesInformation` field

## v6.3.0

- Added exported byteArrayToBase64 function
- Updated readme with exampla of usage in web worker

## v6.2.0

- Added print scale image resource handling
- Added caption digest image resource handling

## v6.1.0

- Added loading and saving layer masks

## v6.0.0

- Changed reading to ignore not implemented features by default instead of throwing
- Removed logging missing handling for layer info
- Added `throwForMissingFeatures` and `logMissingFeatures` read options for previous behavior

## v5.0.0

- Simplified canvas initialization on NodeJS

  before:
  ```typescript
  import { createCanvas } from 'canvas';
  import { readPsd, initializeCanvas } from 'ag-psd';

  initializeCanvas(createCanvas);
  ```
  after:
  ```typescript
  import 'ag-psd/initialize-canvas';
  import { readPsd } from 'ag-psd';
  ```
- Changed `writePsd()` method to always return `ArrayBuffer`. If you need `Buffer` as a result use `writePsdBuffer()` method instead.
- Simplified script import on browser, now import is the same on both platforms.

  before:
  ```typescript
  // node
  import { readPsd } from 'ag-psd';

  // browser
  import { readPsd } from 'ag-psd/dist/browser';
  ```
  after:
  ```typescript
  // node or browser
  import { readPsd } from 'ag-psd';
  ```