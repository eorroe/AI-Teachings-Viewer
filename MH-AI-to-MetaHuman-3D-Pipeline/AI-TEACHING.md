# AI to MetaHuman 3D Pipeline

## Overview

This AI Teaching covers the end-to-end pipeline for converting an AI-generated face image into a production-ready MetaHuman character in Unreal Engine. It guides users through generating an AI face image, converting it to a 3D model, wrapping it to MetaHuman topology, texturing, sculpting details, and importing the final character into Unreal Engine with a custom groom. The workflow combines multiple AI and 3D tools to transform a single 2D image into a fully realized digital human.

## When to Follow These AI Teachings

- When you need to create a MetaHuman character from an AI-generated face image
- When working with AI-to-3D tools like Tripo 3D and need to integrate the output into a production pipeline
- When the user asks about converting a 2D AI face into a rigged, textured MetaHuman for Unreal Engine

## Steps

### Step 1: Generate AI Face Image

Generate a face image using an AI image generator such as Midjourney, Stable Diffusion, DALL-E, or a similar tool. Ensure the full head is visible in the image, as this will be used as the reference for the 3D model. The image quality does not need to be perfect at this stage, but clear facial features and a well-lit, front-facing view will produce better results.

### Step 2: Enhance Image Quality

Improve the generated face image using an image enhancement tool such as Craya AI or a similar AI upscaler. This step increases the resolution and clarity of the reference image, making it more suitable for 3D conversion. Use an enhancer that preserves facial details without introducing artifacts.

### Step 3: Convert AI Image to 3D Model

Upload the enhanced face image to an AI image-to-3D tool such as Tripo 3D. Generate the 3D model from the single image. The generation typically takes only a few minutes. The resulting geometry may have proportions that are slightly off, but the base shape is usually usable as a starting point. Do not rely on the AI-generated texture for final quality, as it serves only as a rough reference.

### Step 4: Download GLB File from Tripo 3D

Once the 3D model is generated, download the GLB file from Tripo 3D. The GLB format preserves both the geometry and the basic texture in a single file. Keep this file ready for import into Blender.

### Step 5: Import GLB into Blender and Fix Rotation and Scale

Import the downloaded GLB file into Blender. The model from Tripo 3D often arrives with incorrect orientation. Rotate the model around the Y axis by -90 degrees so it faces forward along the -Y axis, then apply the scale by pressing Ctrl+A and selecting "Scale" to ensure all transform values are clean. This prepares the mesh for stable sculpting and wrapping operations.

### Step 6: Apply Merge by Distance to Fix Mesh Issues

Before sculpting, select the imported mesh and apply Merge by Distance (also known as Remove Doubles). The AI-generated mesh commonly contains duplicate vertices and unconnected surface geometry. Skipping this step will cause the mesh to break during sculpting, producing holes and gaps as vertices move independently. After merging, the surface will be solid and safe to sculpt.

### Step 7: Sculpt and Improve Model in Blender

With the mesh cleaned, enter Sculpt Mode by clicking the mode dropdown in the top-left of the viewport and selecting "Sculpt Mode." Improve the proportions and details of the face using the Move, Clay Strips, and Smooth brushes. Even if the initial AI proportions look acceptable, sculpting gives you control over the final shape and helps produce a cleaner, more accurate base for wrapping to MetaHuman topology. Focus on the overall head shape, jawline, and facial structure before proceeding.

### Step 8: Obtain MetaHuman Topology Base Mesh from Fab

Download a clean, quad-dominant MetaHuman topology base mesh from Fab. The downloaded file will be in FBX format and will have a very small scale by default. Only the head portion is needed for this workflow, as eyes and teeth will be added automatically by MetaHuman Creator.

### Step 9: Scale MetaHuman Head to 1

Open the Fab FBX file in Blender, select the head mesh, and set its scale to (1, 1, 1) on all axes. This ensures the MetaHuman topology is at the correct reference size for wrapping.

### Step 10: Match AI Head with MetaHuman Head Position, Rotation, and Scale

In Blender, position the AI-generated head and the MetaHuman head in the same scene. Adjust the position, rotation, and scale of both meshes using Blender's snapping tools or manual alignment so they overlap as closely as possible in shape and orientation. Accurate alignment at this stage is critical for a successful wrap.

### Step 11: Export Both Models as OBJ with Applied Transforms

Export both the AI-generated head and the MetaHuman head as OBJ files. Before exporting, right-click each mesh and select Apply All Transforms. Applying transforms ensures the OBJ files preserve the correct orientation and scale, preventing mismatches during wrapping.

### Step 12: Use FaceForm for Wrapping (Two Passes)

In FaceForm, load the AI-generated head as the "Scan" and the MetaHuman head as the "Template." Perform two wrapping passes:

- Pass 1: Run the basic wrap without masking the eyes. The AI-generated eye geometry is typically hollow or malformed, so the eyes will be corrupted in this pass. Also mask the neck area, as it is not needed for the head wrap. Save the result.
- Pass 2: Load the saved result back in as the scan and run a second wrap. This time, mask both the inside and outside of the eyes to preserve clean eye geometry.

### Step 13: Export Texture from Blender as PNG

In Blender, select the AI-generated mesh, open the UV Editor, and bake its vertex colors or material texture to a new image. Save the baked texture as a PNG file. This texture will be used as a reference during the wrapping and texturing process.

### Step 14: Project Texture onto MetaHuman UV Using Texture Transfer

In FaceForm, use the "Transfer Texture" option to project the exported texture onto the MetaHuman UV layout. This bakes the AI-generated color information onto the clean MetaHuman topology.

### Step 15: Save Texture as 2K or 4K PNG

Save the projected texture as a PNG file. Choose 2K or 4K resolution depending on your quality and performance needs. Note that the AI-generated image quality is limited and should be treated only as a reference, not a final texture.

### Step 16: Finalize in ZBrush (Fix Eyes and Ears, Create Conformant Mesh, Add Pore Details)

Import the wrapped MetaHuman head into ZBrush for final sculpting. Fix areas that did not wrap correctly, such as the eyes and ears. Keep the AI reference image visible using an overlay tool like PureRef or on a second monitor for visual guidance. Use the Smooth and Move brushes primarily, and be careful with brush strength and pressure to avoid over-smoothing and losing details.

Create two versions of the mesh in ZBrush:

- A Level 1 conformant mesh for use inside MetaHuman Creator
- A high-density mesh for pore details and baking in Substance Painter

Add pore details using alpha brushes, displacement maps, or the noise tool, or combine all three methods. These processes are time-consuming, so focus on the main facial areas and refer to external tutorials for deeper guidance on wrapping and pore sculpting if needed.

### Step 17: Bake High Poly to Low Poly in Substance Painter

Import both the high-density mesh and the low-poly conformant mesh into Substance Painter. Perform a bake from the high-poly mesh to the low-poly mesh. This generates the normal map, cavity map, ambient occlusion map, and other maps needed for texturing. Small details from ZBrush may be partially lost during baking, so additional enhancement is required.

### Step 18: Use Cavity Map for Detail Enhancement in Substance Painter

To restore detail lost during baking, use the cavity map to drive a height-based mask in Substance Painter. Under the Texture Set details on the left, locate the baked maps and create a new fill layer with only the Height channel enabled, setting the slider to approximately 0.5. Add a black mask to this fill layer, then create another fill layer inside the mask and place the cavity map into the Height channel. Control the intensity with the Height slider on the main material. Do not push Sharpness or Height values too high, as a small amount produces the best result.

### Step 19: Start with 3D Scan Texture from 3D Scan Store

To speed up texturing, purchase a skin texture pack from 3D Scan Store that matches the skin tone of your character. The MetaHuman ID pack is suitable because it provides the albedo map and optionally the normal map. These scanned textures provide a realistic base that can be further customized in Substance Painter.

### Step 20: Use Smart Material in Substance Painter

Apply a smart material from Substance Painter's library to build the skin texture efficiently. This tutorial focuses on the base skin map and a tattoo layer. Find a suitable smart material such as a "Skin" or "Human Skin" smart material and apply it to the low-poly mesh to establish the foundational skin appearance.

### Step 21: Export Tattoo Texture

Export the AI-generated tattoo texture from Substance Painter. The tattoo is generated externally using AI or other methods and brought into Substance Painter for final adjustments and export. There are multiple ways to create tattoo textures, including hand-painting in Photoshop, generating with AI using reference images, or blending multiple textures together. There is no single perfect method, so choose the approach that best fits your artistic needs and timeline.

### Step 22: Export All Maps with Unreal Preset at 8K

Export all texture maps from Substance Painter using the Unreal preset. Set the resolution to 8K for maximum quality. This ensures the textures retain fine detail when imported into Unreal Engine.

### Step 23: Import into Unreal Engine and Create MetaHuman from Template with Custom Mesh

Import the conformant head mesh, albedo map, and normal map into Unreal Engine. Open MetaHuman Creator, choose "Conform from Template," and select your custom mesh. This method produces a more accurate result than the Mesh to MetaHuman workflow and preserves the custom topology and facial proportions.

### Step 24: Apply Textures and Adjust in MetaHuman Creator

In MetaHuman Creator, select a skin color in the skin tone palette that closely matches the skin tone of your AI reference image. Load your exported albedo and normal maps into the corresponding channels. Use the creator tools to make small adjustments: change eye color, modify teeth, and use the face shape and eye sliders to refine the character and bring it closer to your reference. Save your work frequently during this process.

### Step 25: Export Skeletal Head Mesh

When the MetaHuman face is finalized, export the skeletal head mesh from MetaHuman Creator. Navigate to the Groom tab and use the "Export" option from the top menu to export the skeletal head mesh. This mesh is needed to create a custom groom in Blender.

### Step 26: Create Groom in Blender

Import the exported skeletal head mesh into Blender. Use Blender's geometry node groom system to create a custom hairstyle that matches your reference. The geometry node system is flexible and there are many tutorials available online for creating parametric grooms.

### Step 27: Import Groom into MetaHuman Creator

Create a binding for the skeletal mesh on your MetaHuman in Blender. Open your groom asset and copy parameters from an existing groom, including materials and strand settings. Experiment with shadow bias and groom radius values, as these settings vary per groom. Once the binding file is ready, drag it into MetaHuman Creator. It will automatically generate a wardrobe asset. Click the asset and assign it to your character to complete the workflow.

## Examples

### Example 1: Realistic Portrait Character

Generate a photorealistic face image of a specific person using Midjourney with a prompt emphasizing front-facing composition and full head visibility. Enhance the image with Craya AI, convert it to 3D with Tripo 3D, and follow the full pipeline to create a MetaHuman that closely matches the reference portrait for use in a cinematic Unreal Engine project.

### Example 2: Stylized Fantasy Character

Use an AI image generator to create a stylized fantasy face with exaggerated features. After enhancing and converting to 3D, sculpt the proportions in Blender to match the stylized design before wrapping to MetaHuman topology. Use custom skin textures and a hand-painted or AI-generated tattoo in Substance Painter, then complete the character in MetaHuman Creator with a custom groom for a fantasy game or VR experience.

## Best Practices

- Use a front-facing, full-head AI reference image to avoid proportion errors during 3D generation
- Always apply Merge by Distance in Blender before sculpting AI-generated meshes
- Apply all transforms in Blender before exporting OBJ files to prevent orientation mismatches
- Perform two passes in FaceForm, masking the eyes in the second pass to avoid corrupted eye geometry
- Keep the AI reference image visible as an overlay in ZBrush using a tool like PureRef
- Use a small amount of cavity map intensity in Substance Painter to avoid over-sharpening
- Export all texture maps at 8K using the Unreal preset for maximum quality in Unreal Engine
- Save work frequently inside MetaHuman Creator to avoid losing adjustments

## Keep In Mind

- The AI-generated texture from Tripo 3D is only a rough reference and should not be used as the final texture
- The final quality of the character depends heavily on the time spent sculpting and texturing, not just the AI generation step
- Eye and ear geometry often requires manual cleanup after wrapping and is best refined in ZBrush or MetaHuman Creator
- Groom parameters such as shadow bias and groom radius are not universal and must be adjusted per hairstyle
- This pipeline is experimental and still evolving, so tool versions and workflows may change over time

## Security & Safety Notes

- Only use AI image generation tools and 3D services that you trust with your personal data and creative content
- Verify the terms of service for Tripo 3D, Craya AI, Midjourney, 3D Scan Store, and FaceForm before uploading reference images or personal data
- Do not upload sensitive or private images to public AI services without understanding their data usage policies
- Keep exported OBJ, FBX, and texture files organized and backed up, as this pipeline involves many intermediate assets

## Common Pitfalls

- **Problem:** The mesh breaks and develops holes during sculpting in Blender
  **Solution:** Always run Merge by Distance on the imported AI-generated mesh before entering Sculpt Mode to remove duplicate vertices and solidify the surface

- **Problem:** The OBJ export does not match correctly between the AI head and the MetaHuman head
  **Solution:** Right-click each mesh in Blender and select Apply All Transforms before exporting to OBJ to preserve the correct position, rotation, and scale

- **Problem:** Eye geometry is corrupted after the first FaceForm wrap
  **Solution:** Mask the neck area during the first wrap pass, save the result, then perform a second wrap pass with both the inside and outside of the eyes masked

- **Problem:** ZBrush details are partially lost after baking in Substance Painter
  **Solution:** Use the cavity map inside a mask on the Height channel with low intensity to restore surface detail without over-sharpening

- **Problem:** The groom looks incorrect or disappears when imported into MetaHuman Creator
  **Solution:** Ensure the binding file is created correctly for the skeletal mesh, experiment with shadow bias and groom radius values, and verify that the materials and strand settings are copied from a working groom reference
