# Capy Jelly

A capybara cast in jelly: an interactive WebGPU soft-body study. Clear caramel jelly sits over a milky belly and muzzle, the ears flick now and then, and you can drop yuzu onto its head and see if they stay.

It's one HTML file with no dependencies or build step.

## Run it

Open `index.html` in a browser with WebGPU: current Chrome, Edge or Safari, or Firefox on Windows, with hardware acceleration on. Without WebGPU the page says so and doesn't render.

## Handle it

- Drag the jelly to stretch, lift and wobble it. Tug an ear, squash the rump, lift the chin off its paws.
- **Drop a yuzu** (or press `Y`) to drop one on its head. Pick a loose yuzu up and toss it.
- While holding, scroll or add a second finger to twist.
- Drag empty space to orbit, scroll to zoom, double-click to reset the view.
- `Space` pauses, `R` resets.
- The panel sets the colour (Caramel, Cocoa, Matcha), the firmness and the internal damping.

## How it works

- **Body:** a signed-distance capybara cut into a tetrahedral mesh (about 1,200 particles and 4,000 tetrahedra), solved with XPBD at 60 Hz with 10 substeps. Each tetrahedron is pulled toward its rotated rest shape and keeps its volume. The ears are the firmest part, so they flick instead of flopping.
- **Two layers:** the milky belly and muzzle are a separate surface just under the skin, lit by light that has passed through the caramel above it.
- **Face:** nostrils, mouth, cheeks, inner ears and fur grain are drawn in the shader from rest-space coordinates, so they stretch with the jelly.
- **Yuzu:** small rigid balls that fall onto the crown, bounce, roll, and trade momentum with the jelly they hit. On a gentle slope a slow yuzu grips, so it can sit on the flat of the head.
- **Rendering:** WGSL shaders measure how much jelly each view ray crosses, refract what's behind it, and absorb it with Beer–Lambert colour. The table shadow is tinted by the jelly the light passed through.

## Credit

This is a remix of **WhaleJelly** (Material Studies No. 043), a WebGPU study of a humpback whale in jelly: https://claude.ai/artifact/CDmzt6cuLfHqiw8EhxSXQv

The soft-body solver, the renderer and the page design come from that study. The capybara geometry, face shading, yuzu, ear flicks and colourways are new.

## License

None. Much of the code comes from WhaleJelly, which was published without a license, so this repo doesn't grant one either.
