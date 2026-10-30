# GAJI Solar System Explorer

An interactive, single-page tour of the Solar System: the Sun, all eight planets, the asteroid belt, famous asteroids, planetary defense, the International Space Station and the Milky Way. Every planet surface is generated live in the browser, so there are no image files to download.

Built with plain HTML, CSS and JavaScript. No frameworks, no build step, no dependencies.

## Quick start

1. Unzip the folder.
2. Double-click `index.html` to open it in any modern browser.

That is all. For hosting, upload `index.html` to any static host (GitHub Pages, Netlify, Vercel, Cloudflare Pages or your own server).

To preview it on a phone while you develop, serve the folder on your network and open the address on your phone:

```bash
python3 -m http.server 8000
# then visit http://<your-computer-ip>:8000 on the phone
```

## Features

- Hero section with typing animation and a Milky Way backdrop
- Solar System overview with an animated orbit diagram
- 3D planet slider (drag, swipe, tap or use the arrow keys)
- A detail section for the Sun and each planet, with facts, distance bar, stats and moons
- Asteroid belt, a famous-asteroids explorer and a planetary-defense section
- Space station and Milky Way sections
- Mission log form (saves to the device if no server is available)
- GAJI, the astronaut guide, who shows a short note for each section
- Reading-progress bar, section dots and a mobile menu

## Smooth scrolling

- **Mouse wheel (desktop):** inertial, eased scrolling.
- **Menu, dots and buttons:** eased jump to the target section, with the duration scaled to the distance.
- **Touch screens:** the browser's own momentum scrolling is kept, because it is the smoothest option on phones. Nothing hijacks the swipe.
- **Keyboard and scrollbar:** unchanged, and they interrupt any running animation instantly.
- **Reduced motion:** if the device asks for reduced motion, the page jumps instantly and animations are switched off.

### Performance work behind it

- Sections that are off-screen pause their animations.
- Planet textures are generated in small time slices, so scrolling never freezes while they load.
- The scroll progress readout updates once per frame and does not force layout.
- The star field and slider ignore the resize events that phones fire when the address bar hides or shows, which used to cause flicker.
- The star field pauses when the tab is hidden and runs at half frame rate on phones.
- The glass-card shine uses a GPU-friendly transform, and is turned off on touch devices.

## Works on every phone size

- Layout adapts from 320 px wide phones to tablets, laptops and large monitors.
- Uses `100svh` (with a `100vh` fallback), so sections do not jump when the mobile address bar moves.
- Safe-area insets keep content clear of notches, rounded corners and home bars, in portrait and landscape.
- Extra rules for phones up to 480 px and up to 360 px: single-column stats, full-width buttons, a shrinking title bar and tighter cards.
- Touch targets are at least 44 px, and form fields use 16 px text so iOS does not zoom in on focus.
- Landscape phones hide the astronaut note to save room.

## Files

```
GAJI_SOLAR_SYSTEM_EXPLORER/
├── index.html   The whole project (HTML, CSS and JavaScript)
└── README.md    This file
```

## Customizing

All content lives in `index.html`:

| What | Where to look |
| --- | --- |
| Planet text, stats and moons | the `P` array in the script |
| Astronaut notes | the `NT` object |
| Asteroid facts | the `AX` array |
| Colors and fonts | the `:root` variables at the top of the stylesheet |
| Typing lines on the hero | the `TY` array |

## Optional message server

The Mission log tries `POST /api/messages` and `GET /api/messages`. If your site has no such endpoint, messages are kept in the visitor's own browser (`localStorage`). Nothing else needs a server.

## Browser support

Current Chrome, Edge, Firefox and Safari, on desktop, Android and iOS (iOS 14 and later). The Orbitron and Inter fonts load from Google Fonts when online, and the page falls back to system fonts when offline.

## Credits

Planet facts are summarized from public NASA and ESA material. Planet surfaces are procedural art, not photographs. For real images visit the [NASA Image and Video Library](https://images.nasa.gov/).

© 2026 Debjit Das. All rights reserved.
