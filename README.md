# Flight Lab: Gimbal Lock & Quaternions

An interactive 3D spacecraft demonstration of Euler rotations, gimbal lock, quaternion control, and spherical linear interpolation (SLERP).

**[Open the live demo](https://dennisi7.github.io/Gimbal-lock-demo/)**

## Run locally

Download or clone this repository and open `index.html` in Chrome, Edge, or Firefox. No internet connection, dependencies, or build step is needed. You can also use VS Code's Live Server.

## Present the demo

1. **Take the controls:** move roll, pitch, and yaw separately and watch the coloured gimbal rings.
2. **Find gimbal lock:** pitch starts at +90°. Set roll to +30°, then yaw to +30°. Their effects cancel because the instantaneous axes are collinear and point in opposite directions.
3. **Fly with quaternions:** apply rotations directly about fixed world axes, or play the compound maneuver.
4. **Make it cinematic:** scrub or play the shortest-path SLERP transition between two orientations.

## Controls

| Control | Action |
| --- | --- |
| Drag the scene | Orbit the camera |
| Scroll | Zoom |
| Focus the scene, then arrow keys | Orbit with the keyboard |
| Focus the scene, then + / − | Zoom with the keyboard |
| Focus the scene, then Home | Reset the camera |
| 1–4 | Select a chapter |
| Space | Run or pause the chapter action |
| F | Toggle full screen |
| R | Reset the current chapter |

Presentation shortcuts leave normal button and form keyboard interaction intact. Use the effects switches to simplify the scene; **Pause ambience** stops star drift and thruster flicker. Reduced-motion preferences pause ambience initially.

## Teaching conventions

The Euler chapter uses active intrinsic Z–Y–X rotations: `R = Rz(yaw) Ry(pitch) Rx(roll)`. The ship points along local +X. At pitch +90°, roll and yaw controls lose one independent rotation direction; the spacecraft itself retains its physical rotational freedom.

The quaternion chapter changes both representation and input method: world-axis increments compose directly as `q ← Δq · q`, with normalization. Converting the same Euler sliders to quaternions alone would retain the input singularity. Quaternions do not repair a physical gimbal mechanism.

The spacecraft is an illustrative model, not a flight dynamics simulator. Expand **The maths behind the flight** in the demo for more detail and references.

## Implementation

One self-contained HTML file with inline CSS and JavaScript, authored spacecraft geometry, and a Canvas renderer. GitHub Pages serves the repository root from `main`; `.nojekyll` disables Jekyll processing.
