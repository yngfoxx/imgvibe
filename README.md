Project Goal: Create a sophisticated, single-file, client-side HTML image editor application, inspired by Pintura. The final product should be polished, fully responsive, and intuitive, with a modern, dark-themed UI.

Core Technologies:

Structure: A single index.html file.

Styling: Tailwind CSS (loaded via CDN). Do not use any custom CSS in <style> tags.

Logic: Vanilla JavaScript. No external libraries or frameworks (e.g., no jQuery, React, etc.).

Icons: Use inline SVGs for all icons to ensure the single-file constraint is met.

I. Application Layout & Structure
The application UI should be divided into three main sections within a dark-themed container (bg-gray-900, text-white).

Top Header Bar:

A clean, simple bar at the top of the page.

Left Side: A title, "Pixelate".

Right Side: Two primary action buttons:

"Open" Button: This will trigger a hidden file input (<input type="file" accept="image/*">).

"Export" Button: This will save the final canvas content as a PNG file.

Main Content Area (The Viewport):

A central, flexible container that holds the HTML5 <canvas>.

The canvas should be dynamically resized with JavaScript to fit the available space in the viewport while maintaining the image's aspect ratio.

Initially, before an image is loaded, this area should display a message: "Please open an image to start editing." with an icon of a picture.

Bottom Toolbar (The Tool Drawer):

A bar fixed to the bottom of the page that contains the main editing tool icons.

When an icon in this toolbar is clicked, it becomes the "active" tool. The icon should be visually highlighted (e.g., change color to a bright blue).

Clicking a tool should open a secondary "options panel" directly above this main toolbar, containing the specific controls for that tool (e.g., sliders, aspect ratio buttons).

Clicking another tool icon should close the previous options panel and open the new one with a smooth transition.

II. Feature & Tool Implementation
Implement the following editing tools, each with its own icon and options panel. Maintain an original, unmodified copy of the image in memory to allow for resetting changes and for non-destructive filter application.

1. Crop Tool:

Icon: A crop symbol.

Options Panel: Buttons for different aspect ratios: 1:1, 4:3, 16:9, and Free. It should also contain "Cancel" and "Apply" buttons.

Functionality:

When activated, draw a semi-transparent overlay on the canvas with a highlighted crop box in the center.

The crop box must have draggable corners and edges to resize it.

Selecting an aspect ratio should lock the crop box's proportions.

Clicking "Apply" crops the image on the canvas to the selected area.

Clicking "Cancel" hides the crop overlay without changing the image.

2. Filter Tool:

Icon: A magic wand symbol.

Options Panel: A horizontally scrollable list of filter previews. Each preview is a small thumbnail of the current image with a filter applied.

Functionality:

Implement at least five common filters: Grayscale, Sepia, Invert, Vintage (warm, faded look), and Clarity (increased contrast/sharpness).

Applying a filter should be non-destructive. The changes are applied to the canvas display, not the original image data, so the user can switch between filters. The final filter selection is only "baked in" on export.

3. Adjustments Tool:

Icon: A sliders/controls symbol.

Options Panel: A set of labeled range sliders (<input type="range">).

Functionality:

Create sliders for:

Brightness (Range: 0 to 200, Default: 100)

Contrast (Range: 0 to 200, Default: 100)

Saturation (Range: 0 to 200, Default: 100)

As the user drags a slider, the canvas should update in real-time to preview the effect. These changes should stack and be applied via CSS filter properties on the canvas element for performance.

4. Transform Tool:

Icon: A rotate symbol.

Options Panel: Four distinct action buttons.

Functionality:

Rotate Left (-90°): Rotates the entire canvas content counter-clockwise.

Rotate Right (+90°): Rotates the entire canvas content clockwise.

Flip Horizontal: Flips the image on its vertical axis.

Flip Vertical: Flips the image on its horizontal axis.

The canvas dimensions must update correctly after rotation (width becomes height and vice-versa).

III. Workflow & User Experience
Initial State: App loads with the "Open an image" message. All tools in the bottom bar are disabled/grayed out.

Image Load: User clicks "Open," selects an image file. The image is drawn onto the canvas. The canvas resizes to fit the image. The tools in the bottom bar are now enabled.

Editing: The user selects various tools and makes modifications. All changes are previewed live on the canvas.

Exporting: User clicks "Export." The application should:

Create a new, temporary canvas in the background.

Draw the original image onto it.

Apply all the user's final transformations (crop, rotation, adjustments, filter) in order.

Trigger a browser download of the temporary canvas content as a pintura-export.png file using canvas.toDataURL().

Responsiveness: The entire interface must be fluid and adapt gracefully to all screen sizes, from a small mobile phone to a large desktop monitor. On smaller screens, the options panels should not overflow the screen.

The final result should be a polished, responsive, and intuitive single-page image editor that looks and feels like a modern commercial product.
