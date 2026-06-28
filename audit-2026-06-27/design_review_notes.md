# Studio Site Design Review

Date: 2026-06-27

Reviewed surface: `output/studio_site_opus_white/index.html`

Evidence used:
- `review/desktop-01-home.png`
- `review/desktop-02-projects.png`
- `review/desktop-03-project-abbey.png`
- `review/desktop-04-info-abbey.png`
- `review/mobile-01-home.png`
- `review/mobile-02-projects.png`
- Current `index.html` source inspection

Evidence limit:
- The in-app browser policy blocked both `file://` and `127.0.0.1` access, so I could not capture a fresh current-run screenshot during this audit. The visual findings are based on the existing review screenshots in the same output folder plus current source inspection.

## Step Review

1. Home screen
   - Health: Strong.
   - The white field, small italic wordmark, and centered monochrome architectural image create a precise portfolio mood.
   - The page feels editorial and restrained, which suits architecture work.
   - Risk: the hero image is the only entry point to the project list, and it has no visible cue that it is clickable.

2. Project index
   - Health: Good.
   - The simple vertical project list is calm, readable, and aligned with the reference-like minimalist direction.
   - The large top logo box gives this page a strong landing/menu identity.
   - Risk: there is no small "works" or "projects" label, so first-time users may need a moment to understand that the names are navigation.

3. Project detail
   - Health: Strong visually, mixed for interaction.
   - The centered image, tiny top navigation, title, credit, counter, and info link feel like a gallery plate.
   - The current source supports left/right keyboard navigation and large invisible previous/next hit zones.
   - Risk: the invisible hit zones are elegant but undiscoverable. Users who do not guess side-clicking may think there is only one image.

4. Project info
   - Health: Good.
   - The fact sheet and paragraphs are clean, direct, and appropriately quiet.
   - The separation between image view and information view helps the work breathe.
   - Risk: `overflow: hidden` and a fixed viewport-height layout may clip longer project text on small screens or at browser zoom.

5. Mobile home and index
   - Health: Good.
   - The mobile layout preserves the same identity and gives the image enough room.
   - The project list remains readable and spaced well.
   - Risk: mobile project detail was not available in the existing screenshot set, and source inspection shows the side hit zones are hidden on mobile. Keyboard arrows remain in source, but touch users need another obvious way to advance slides.

## Accessibility Risks

- Links and buttons rely mostly on text and hover behavior. Keyboard focus styling is not explicitly defined, so focus visibility needs verification.
- Invisible previous/next buttons have ARIA labels, which is good, but their visual affordance is absent and they are hidden on mobile.
- Several navigation labels are intentionally tiny. The mood is right, but some controls may be hard to target or read for low-vision users.
- `html`, `body`, `.page`, and `.info-sheet` use hidden overflow in several places. This can block zoom/reflow and clip text.

## Recommendations

1. Add a very subtle entry cue on the home image, such as a small "works" label below it or a hover/focus underline.
2. Add visible previous/next controls or a small "click sides / arrow keys" affordance on project pages. Keep it restrained, but make the gallery behavior discoverable.
3. On mobile, provide explicit previous/next text or small arrow controls near the counter.
4. Add `:focus-visible` styles for links and hit-zone buttons.
5. Revisit `overflow: hidden` on info pages so longer text and browser zoom do not trap or clip content.
6. Replace the placeholder contact email before publishing.

Overall assessment: the site has a clear, elegant architectural voice. It already feels more like a curated printed portfolio than a generic web template. The main work now is not visual polish; it is making the quiet interactions more legible without disturbing the calm.
