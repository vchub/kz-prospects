# Technical Specification: Transparent LED & Holographic Display Systems
**Reference Tech:** MUXWAVE, Leyard Vteam
**Context:** Retail "Invisible Screen" Implementation

## 1. Physical Architecture
These systems achieve >90% transparency by diverging from traditional "cabinet-based" LED designs.

*   **Substrate Engineering:** 
    *   **MUXWAVE:** Utilizes a thin-film LED technology where chips are embedded into a transparent substrate. This can be laminated directly onto existing glass.
    *   **Leyard Vteam:** Often employs "PCB Stripping" or mesh bars. The circuit boards are cut into vertical or horizontal slivers to allow light to pass through the gaps.
*   **Pixel Pitch (P):** 
    *   Standard retail window range: **P3.91 to P10**.
    *   *Trade-off:* P3.91 provides high-definition "Holographic" detail but reduces transparency (approx. 70-80%). P10 provides maximum transparency (>90%) but requires the viewer to be at a greater distance to see a cohesive image.
*   **Brightness:** High-output LEDs (3500-5000 nits) are used to ensure visibility against direct sunlight in shop windows.

## 2. Control & Integration Logic
The system acts as a specialized monitor requiring a dedicated processing chain.

*   **The Processor (The "Sender"):**
    *   **Hardware:** NovaStar (MCTRL/Taurus Series) or Colorlight.
    *   **Function:** Takes HDMI/DP signal from a media server and converts it to a proprietary protocol (pixel-mapped).
*   **The Receiver Card:**
    *   Unlike standard LEDs, these are "Hidden-in-Bezel." They are miniaturized and tucked into the top or bottom structural frames to maintain the "Invisible" aesthetic.
*   **Connectivity:**
    *   **Synchronous:** Real-time playback from a PC (used for interactive mannequins or AI assistants).
    *   **Asynchronous:** Cloud-managed via 4G/Wi-Fi players (e.g., NovaStar TB60) for scheduled advertising loops.

## 3. Content Creation Strategy ("The Floating Effect")
Content for transparent screens is not "filmed"; it is "constructed" using specific optical rules.

*   **The "Black = Alpha" Principle:**
    *   In transparent LED hardware, **Black (#000000) = Off**.
    *   When an LED is off, the viewer sees through the screen into the store.
    *   *Strategy:* All assets (sneakers, logos, mannequins) must be rendered on a pure black background.
*   **Lighting & Volumetrics:**
    *   Since the screen cannot produce "black" (only transparency), you cannot create traditional shadows. 
    *   *Solution:* Use high-contrast highlights, rim lighting, and "glow" effects to define the edges of objects and give them a 3D volumetric feel.
*   **Motion Design:**
    *   **Parallax:** For curved windows (Leyard installs), content must be "Anamorphic"—distorted at the source so it looks correct from the primary viewing angle (Naked-Eye 3D).
    *   **Floating Logic:** Avoid "edge-to-edge" content. Keep the subject in the center of the frame with a wide black (transparent) border to enhance the illusion that the object is detached from any surface.

## 4. Operational Comparison
| Feature | MUXWAVE | Leyard Vteam |
| :--- | :--- | :--- |
| **Aesthetic** | Seamless, film-like, ultra-thin. | Modular, robust, high brightness. |
| **Transparency** | Highest (>90% in film versions). | High (Mesh-dependent). |
| **Best Application** | "Phantom" mannequins, high-end jewelry glass. | Large mall facades, outdoor-facing windows. |
| **Installation** | Laminated or glue-on. | Frame-mounted or suspended. |
