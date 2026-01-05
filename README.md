# Solar System — WebGL / Shader Practice (Three.js)

An interactive solar system scene built as a **WebGL / computer graphics practice project**. It renders the Sun + planets with textured spheres, orbital motion, camera controls, UI controls (time + simulation speed), and an interactive spaceship with collision-triggered particle explosions.

## Demo

[Demo Video](https://youtu.be/574wFPZw5DA)

Screenshots: </br>
![alt text](https://github.com/bububoy0907/solar-system/blob/main/media/main_screen.png?raw=true)
![alt text](https://github.com/bububoy0907/solar-system/blob/main/media/spaceship_front.png?raw=true) ![alt text](https://github.com/bububoy0907/solar-system/blob/main/media/spaceship_side.png?raw=true)

## What You Can Do
- Observe planet **rotation + orbit** in a time-scaled simulation (time shown in “days”).
- Adjust **simulation speed** with a slider (days per second).
- Click **planet focus buttons** to move the camera near a chosen planet; use **Default View** to reset.
- Pilot a spaceship with keyboard controls and collide with planets to trigger **particle explosion effects**.

## Controls
- **Mouse drag (LMB)**: pan/rotate the camera view
- **Mouse wheel**: zoom
- **W / A / S / D**: control the spaceship
- **UI buttons**: focus camera on a planet / reset to default view

## Technical Highlights
- **Scene setup (Three.js / WebGL)**: WebGLRenderer on canvas, sRGB encoding, 45° perspective camera, ambient + point lighting to simulate sunlight.   
- **Background**: inside-out sphere using `SphereGeometry` + space texture (`BackSide`) to create a skybox-like cosmos.
- **Planets**:
  - Each planet is a **textured sphere** with per-planet size/orbit/rotation properties stored in a data array to keep the code maintainable.
  - **Orbit path lines** rendered as dynamic lines (buffer geometry).
  - **Saturn rings/atmosphere** implemented with `TorusGeometry`, plus a tilt of **26.7°** for realism.
- **Sun glow shader**:
  - A slightly larger glow sphere with a **custom shader** to produce a halo effect using view vector vs normal intensity.
- **Spaceship**:
  - 3D model created in Blender, loaded via `OBJLoader` / `MTLLoader`.
  - Engine trail effect using fading semi-transparent particles.
- **Explosion effects**:
  - Collision triggers generate thousands of particles using `THREE.Points` with randomized velocities and fade-out.
  - Special case: collision with the Sun triggers a “big bang”-style event and destroys remaining planets. 

## My Contribution (Jason Wong)
I contributed key visual + interaction systems, including:
- background setup, planet textures, planet rotation/orbit logic
- sunlight + sun glow work
- explosion effect implementation
- simulation slider + planet focus buttons
- mouse pan/scroll camera controls
- spaceship controller and orbit path line integration

## Credits / References
- Planet texture references: Solar System Scope textures @ [https://www.solarsystemscope.com/textures/].

## Run Locally
This project is a browser-based WebGL demo. You should run it via a local web server instead of opening `index.html` directly.
```bash
python -m http.server 8000
Then open: http://localhost:8000
