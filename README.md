# grid-to-3d-model
A web-based application for designing and visualizing floor plans in 2D and 3D. Built with HTML, JavaScript, Three.js, Tailwind CSS, and Font Awesome, it allows users to create and edit grid-based floor plans with walls, doors, windows, and corner cubes, and view them in an interactive 3D model. The editor supports responsive design, touch/mouse interactions, and customizable grid sizes.
Features

2D Editor: Design floor plans on a grid (default 10×10) using a 2D canvas with click-and-drag or tap-and-drag placement.
3D Visualization: Real-time 3D rendering of the floor plan using Three.js, with OrbitControls for rotation, panning, and zooming.
Tile Types: Place walls (#), doors (d), windows (w), empty tiles ( ), and corner cubes (c) requiring ≥2 adjacent walls.
Wall Rotation: Rotate wall orientations (North, East, South, West) with distinct colors (Gray, Light Red, Light Blue, Light Green) using the "Rotate Wall" tool.
Responsive Design: Side-by-side 2D/3D views on desktop (>768px); toggle between 2D and 3D on mobile (≤768px).
Animations: Smooth 150ms button transitions (scale-105, bg-blue-600), 50ms grid updates, and 3.0 auto-rotate speed with 0.15 damping.
Controls: Mouse/touch for 3D navigation (rotate, pan, zoom) and keyboard (WASD/arrow keys to pan, Q/E or +/- to zoom).
Floor Alignment: Floor fits exactly within the grid (e.g., 10m × 10m for 10×10) and is visible from both top and underside (double-sided).
Customization: Adjust grid size (1–100), tile dimensions, colors, and 3D parameters (e.g., wall height, cube size).

Prerequisites

Modern web browser (e.g., Chrome, Firefox) with WebGL support.
Internet access to load CDNs for:
Three.js (r128)
OrbitControls
Tailwind CSS (v2.2.19)
Font Awesome (v5.15.4)



Installation

Clone the Repository:git clone https://github.com/your-username/floor-plan-editor.git
cd floor-plan-editor


Serve the Project:
Use a local web server (e.g., Python’s HTTP server):python -m http.server 8000


Alternatively, use tools like Live Server in VS Code or any static file server.


Open in Browser:
Navigate to http://localhost:8000/floorplan3d.html in a modern browser.



Usage

Access the Editor:
Open floorplan3d.html in a browser. On desktop, see the 2D editor (left) and 3D renderer (right). On mobile, toggle between views using “Show 3D View” or “Show 2D Editor”.


Set Grid Size:
Enter width and height (1–100) in “Grid Width” and “Grid Height” inputs.
Click “Set Grid Size” to apply (50ms update). Use “Reset Grid” for default 10×10 grid.


Edit the Floor Plan:
Tools: Select a tool (Wall, Door, Window, Empty, Corner Cube, Rotate Wall). Active tool turns blue with a scale animation.
Place Tiles: Click, drag, or tap-and-drag on the 2D canvas to place tiles. 2D updates instantly; 3D updates on release.
Rotate Walls: Select “Rotate Wall”, choose an orientation (North, East, South, West) from the dropdown, and click/drag/tap on a wall tile to rotate it.
Corner Cubes: Place cubes (c) only at corners with ≥2 adjacent walls.
Visual Feedback: Hover for blue tile highlights; last modified tile has a blue outline.


Navigate the 3D Model:
Mouse/Touch: Left-click/tap to rotate, right-click to pan, scroll/pinch to zoom.
Keyboard: WASD or arrow keys to pan, Q/E or +/- to zoom.
Controls: “Reset Camera” for top-down view; “Auto-Rotate” to toggle rotation (3.0 speed, blue when active).
The floor is 10m × 10m (for 10×10), visible from top and underside, with walls showing directional colors.


Status Bar: Displays current grid size (e.g., “10x10”) and selected tool (e.g., “Rotate Wall”).

Customization

Grid Size: Modify width and height in JavaScript (default: 10×10).
Floor Appearance: Change floorMaterial.color (e.g., #AAAAAA for darker floor) or side in floorMaterial.
Tile Dimensions: Adjust tileSize (1m), wallHeight (2.5m), wallThickness (0.3m), cubeSize (1.0m), doorHeight (2m), windowHeight (1m), windowOffset (1m).
Colors: Update wallMaterials (e.g., 0x888888 for North), cubeMaterial, doorMaterial, or windowMaterial.
2D Canvas: Change tilePixelSize bounds (min 10, max 30) for 2D grid scaling.
3D Controls: Modify moveSpeed (0.1), zoomSpeed (0.2), controls.dampingFactor (0.15), or controls.maxDistance.

Troubleshooting

Floor Extends Beyond Grid: Ensure floorGeometry uses new THREE.PlaneGeometry(width * tileSize, height * tileSize) in update3DModel. Check console (F12) for geometry errors. Test with a 5×5 grid.
Floor Not Visible from Underside: Verify floorMaterial.side = THREE.DoubleSide. Rotate camera below y=0 using mouse/touch or WASD.
WebGL Errors: Confirm browser supports WebGL and CDNs are accessible. Use Chrome/Firefox.
Responsive Issues: On mobile, ensure toggle button switches views. Test 2D canvas at 320px (~160px for 10×10).
Animation Lag: Reduce tilePixelSize max (e.g., to 20) or test in Chrome/Firefox.
Button Issues: Verify “Rotate Wall” button scales (scale-105) and turns blue (bg-blue-600) in ~150ms.

License
This project is licensed under the MIT License - see the LICENSE file for details.
Contact
For feedback, issues, or contributions, open an issue on GitHub or contact your-email@example.com.
