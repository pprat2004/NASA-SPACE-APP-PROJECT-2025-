# NASA-SPACE-APP-PROJECT-2025-
An interactive planetary defense simulator for visualizing and mitigating asteroid impact scenarios. Features dual 2D/3D map views, dynamic visual effects, and multiple mitigation strategies.

# Planetary Defense Command: An Impact Simulation Framework

## Abstract

Planetary Defense Command is a client-side web application designed for the simulation and visualization of near-earth object (NEO) impact events. The framework provides an interactive environment for users to define threat parameters, select mitigation strategies, and analyze the projected consequences of an impact. The system leverages a dual-view interface, combining 2D geospatial mapping with a 3D WebGL rendering of the target body, to deliver a comprehensive and data-rich user experience.

---

## Core Functionality

-   **Dual Visualization Modes:**
    -   **2D Tactical View:** A geospatial map powered by Leaflet.js, providing precise coordinate selection (latitude/longitude) and visualization of impact effects such as damage radii.
    -   **3D Global View:** A real-time, interactive 3D rendering of Earth using Three.js, complete with a dynamic lighting model based on an orbiting Sun and an orbiting Moon.

-   **Simulation Parameterization:**
    -   **Threat Definition:** Users can configure the physical characteristics of the impactor, including diameter (meters), velocity (km/s), and angle of entry (degrees).
    -   **Mitigation Strategy Selection:** The simulation supports various theoretical mitigation protocols, such as Kinetic Impactor, Laser Ablation, and Nuclear Standoff, each with a unique success probability that influences the outcome.

-   **Impact Analysis and Effects Rendering:**
    -   **Quantitative Output:** The simulation engine calculates and displays key metrics, including kinetic energy released (megatons of TNT), estimated crater diameter, and Richter scale magnitude of the resulting seismic event.
    -   **Dynamic Effects Visualization:** Impact events are rendered with custom-coded animations. This includes a staggered, expanding shockwave effect on the 2D map and unique 3D visual effects corresponding to the selected mitigation strategy.

---

## Technical Architecture and Implementation

The application is a single-page application (SPA) built entirely with client-side technologies, ensuring portability and eliminating the need for a backend server.

-   **Rendering Engines:**
    -   The 2D view utilizes **Leaflet.js** for its robust handling of tiled map data and geospatial coordinate systems. The map is configured with `maxBounds` and `noWrap` to constrain it to a standard world projection.
    -   The 3D view is rendered with **Three.js**, using a `WebGLRenderer`. The scene includes textured sphere geometries, a Phong material for realistic lighting, and a dynamic `PointLight` attached to the Sun object. User interaction is managed via `OrbitControls`.

-   **Coordinate Selection and Raycasting:**
    -   User-selected impact points are synchronized across both 2D and 3D views.
    -   In the 3D view, a `THREE.Raycaster` is employed to project the user's mouse click onto the surface of the Earth mesh. The intersection point's cartesian coordinates (x, y, z) are then converted back to geodetic coordinates (latitude, longitude) for the simulation.

-   **Animation and Visual Effects:**
    -   The **GreenSock Animation Platform (GSAP)** is used to choreograph all dynamic visual effects, providing smooth, high-performance, physics-based animations.
    -   The 2D shockwave is implemented by animating the `width`, `height`, and `opacity` of `L.divIcon` elements with custom CSS classes. This approach is more performant than repeatedly re-calculating and re-drawing `L.circle` geometries on each animation frame.
    -   The "Nuclear Standoff" mitigation strategy triggers a custom implosion effect, which combines GSAP timeline animations for a scaling black sphere (`THREE.Mesh`) and a rotating, contracting particle system (`THREE.Points`).

---

## Technology Stack

-   **Core:** HTML5, CSS3, JavaScript (ES6)
-   **2D Geospatial Rendering:** Leaflet.js v1.9.4
-   **3D WebGL Rendering:** Three.js r128
-   **Animation Engine:** GSAP v3.12.5

---

## Local Deployment

No build process or dependencies are required for local execution. All external libraries are loaded via Content Delivery Networks (CDNs).

1.  Clone the repository:
    ```bash
    git clone [[https://github.com/your-username/your-repository-name.git](https://github.com/your-username/your-repository-name.git](https://github.com/pprat2004/NASA-SPACE-APP-PROJECT-2025))
    ```
2.  Navigate to the project directory:
    ```bash
    cd your-repository-name
    ```
3.  Open the `app.html` file in a modern web browser.

---

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.
