# Kaleo Template - File Structure

## Overview
This document describes the renamed files and their purposes for easier developer understanding.

## CSS Files

### `css/main-styles.css`
- **Previously**: `kaleotemplate.shared.812215e6a.css`
- **Purpose**: Main stylesheet containing all shared styles for the Kaleo template
- **Contents**: 
  - Normalize/reset styles
  - Webflow framework base styles
  - Custom Kaleo template styles
  - Icon font definitions
  - Layout and component styles

## JavaScript Files

### Core Dependencies (Third-party)
- **`js/jquery.js`** - jQuery library for DOM manipulation
- **`js/gsap.min.js`** - GSAP (GreenSock Animation Platform) for animations
- **`js/splittext.min.js`** - GSAP SplitText plugin for text animations
- **`js/scrolltrigger.min.js`** - GSAP ScrollTrigger plugin for scroll-based animations

### Custom Webflow Scripts (Load Order Matters!)

1. **`js/webflow-utilities.js`**
   - **Previously**: `kaleotemplate.schunk.ec7d6d8664310c86.js`
   - **Purpose**: Core utility functions and helpers
   - **Contents**: Lodash-like utility functions, Symbol polyfills, object helpers
   - **Load Order**: First (required by other scripts)

2. **`js/webflow-interactions.js`**
   - **Previously**: `kaleotemplate.schunk.3cedc5d1a4411535.js`
   - **Purpose**: Webflow interactions and animations engine
   - **Contents**: TRAM animation library, Webflow IX2 engine, interaction handlers
   - **Load Order**: Second (depends on utilities)

3. **`js/webflow-polyfills.js`**
   - **Previously**: `kaleotemplate.5351e098.eb532580f2aa2f7b.js`
   - **Purpose**: Browser polyfills for compatibility
   - **Contents**: Object-fit polyfill for older browsers
   - **Load Order**: Last (can be loaded after main functionality)

## Load Order
The scripts must be loaded in this exact order:
1. jQuery
2. webflow-utilities.js
3. webflow-interactions.js
4. webflow-polyfills.js
5. GSAP and plugins (gsap.min.js, splittext.min.js, scrolltrigger.min.js)

## Notes for Developers
- **Do not change the load order** - Dependencies will break
- The utilities file must load before interactions
- GSAP plugins should load after the main interactions are initialized
- All Webflow scripts are bundled/minified - consider keeping source maps if available
