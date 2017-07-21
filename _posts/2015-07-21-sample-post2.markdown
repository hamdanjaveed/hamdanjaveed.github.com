---
layout: post
title:  "CS 488 Project Demo"
subtitle: "Hamdan Javeed"
categories: [tool]
---

# KD-trees for efficient ray intersections
The ray tracer implemented in A4 was extremely slow at dealing with meshes. This is the trace for a scene with a macho cow.

<img min-width="260px" src="assets/initial_profile.png">

A KD-tree data structure was used to organize the triangles in meshes. This allowed the `Mesh::intersect` function to skip a significant portion of the triangles in the mesh and only test for intersections with triangles that would have a chance of being hit.

This reduced the rendering time from **43s** to **6.5s**.

<img min-width="260px" src="assets/kd_tree_profile.png">

This scene took about an hour to render using my A4 ray tracer, with this KD-tree implementation and multi-threading, it now takes 8 seconds.

<img width="64%" min-width="260px" src="assets/sample.png">

# Refraction
Both refractive objects are simulating water with an index of refraction of 1.33. Notice how the straw bends as it enters the water, and how the orb flips the scenery behind it.

<img width="64%" src="assets/refraction_hiertest.png">

Refraction was implemented using the vector form of Snell's law. A transmitted ray is calculated using the incident ray along with the surface normal of the object.

<video width="64%" style="min-width: 260px;" type="video/webm" loop autoplay onclick="this.paused ? this.play() : this.pause();">
	<source type="video/mp4" src="assets/refraction_balls.mp4" />
	<source type="video/webm" src="assets/refraction_balls.webm" />
</video>

# Texture mapping
Sphere texture mapping is trivial, the zenith and azimuth angles are mapped to the range `[0, 1]`. That coordinate is then looked up in the raster file and interpolated.

<video width="64%" style="min-width: 260px;" type="video/webm" loop autoplay onclick="this.paused ? this.play() : this.pause();">
	<source type="video/mp4" src="assets/texture_sphere.mp4" />
	<source type="video/webm" src="assets/texture_sphere.webm" />
</video>

The cube gets the same texture among all faces. The cylinder and cone divide the raster file into thirds. The top third is for the top face, the middle third is for the bottom face and the final third is what gets "wrapped around" the primitive.

<video width="64%" style="min-width: 260px;" type="video/webm" loop autoplay onclick="this.paused ? this.play() : this.pause();">
	<source type="video/mp4" src="assets/texture.mp4" />
	<source type="video/webm" src="assets/texture.webm" />
</video>

# Bump mapping
Bump mapping is very similar in implementation to texture mapping except that instead of changing the diffuse color, the object's normal is perturbed according to the `RGB` values specified in the raster file.

<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/sphere_non_bump.png">
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/sphere_bump.png">

<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/cylinder_non_bump.png">
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/cylinder_bump.png">

<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/cone_non_bump.png">
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/cone_bump.png">

Texture and bump mapping also work with reflective materials. Here the object has a reflectivity of 0.2. We can see the shine of the light as it crosses the cube. Since the normals of the cube face have been adjusted by the bump map, we get some cool patterns on the bricks.

<video width="64%" style="min-width: 260px;" type="video/webm" loop autoplay onclick="this.paused ? this.play() : this.pause();">
	<source type="video/mp4" src="assets/cube_bump.mp4" />
	<source type="video/webm" src="assets/cube_bump.webm" />
</video>

# Constructive solid geometry
CSG was implemented by keeping a list of all intersections, and applying set operations on the ranges. Union is trivial. Subtraction works by subtracting the first range by the second. If the object was "sliced", the intersection's normal gets reversed and its material is set to the second object. This is how the colors of the materials below are set. Intersection is very similar to subtraction.

<img style="display: inline-block; margin: 0;" width="260px" src="assets/csg_001.png">
<img style="display: inline-block; margin: 0;" width="260px" src="assets/csg_002.png">
<img style="display: inline-block; margin: 0;" width="260px" src="assets/csg_003.png">

CSG also works for meshes.

<img style="display: inline-block; margin: 0;" width="260px" src="assets/mesh_union.png">
<img style="display: inline-block; margin: 0;" width="260px" src="assets/mesh_subtract.png">
<img style="display: inline-block; margin: 0;" width="260px" src="assets/mesh_intersect.png">

Here, two teapots are moved into each other and are being intersected with each other.

<video width="64%" style="min-width: 260px;" type="video/webm" loop autoplay onclick="this.paused ? this.play() : this.pause();">
	<source type="video/mp4" src="assets/csg_teapot.mp4" />
	<source type="video/webm" src="assets/csg_teapot.webm" />
</video>

# Additional primitives
The two existing primitives were the sphere and cube. The images below display a diffuse material on the left, and then 4 reflective materials, each with an increasing reflectivity amount, with a reflectivity amount of 1 on the very right.

<div style="margin-bottom: 30px">
	<div style="display: inline; min-width: 260px;" width="49%">
		<img style="margin: 0; display: inline; min-width: 260px; max-width: 392px;" src="assets/sphere.png">
	</div>

	<video width="49%" style="min-width: 260px; display:inline-block;" type="video/webm" loop autoplay onclick="this.paused ? this.play() : this.pause();">
		<source type="video/mp4" src="assets/cube.mp4" />
		<source type="video/webm" src="assets/cube.webm" />
	</video>
</div>

The two new primitives are the cylinder and cone.

<video width="49%" style="min-width: 260px; display:inline-block;" type="video/webm" loop autoplay onclick="this.paused ? this.play() : this.pause();">
	<source type="video/mp4" src="assets/cylinder.mp4" />
	<source type="video/webm" src="assets/cylinder.webm" />
</video>

<video width="49%" style="min-width: 260px; display:inline-block;" type="video/webm" loop autoplay onclick="this.paused ? this.play() : this.pause();">
	<source type="video/mp4" src="assets/cone.mp4" />
	<source type="video/webm" src="assets/cone.webm" />
</video>

# Depth of field
Depth of field was implemented by essentially giving the camera an aperture. Multiple samples are taken at varying positions and then averaged. The following images show a widening aperture, starting at 0, and then increasing to 0.05, 0.1 and 0.15.

<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/dof_samples_10_fd_3_0_ar_0_01.png">
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/dof_samples_10_fd_3_0_ar_0_05.png">

<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/dof_samples_10_fd_3_0_ar_0_1.png">
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/dof_samples_10_fd_3_0_ar_0_15.png">

# Caustics
Coming soon.

# Soft shadows
Soft shadows were implemented similarly to depth of field. An area light was introduced that allowed each point to sample multiple points on the light. By averaging all the samples, we achieve softer shadows. The following images show a point light, followed by soft shadows with 1, 4, 9, 16, 25, 64 and 144 samples.

<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/soft_shadow_0.png">
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/soft_shadow_1.png">
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/soft_shadow_4.png">
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/soft_shadow_9.png">
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/soft_shadow_16.png">
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/soft_shadow_25.png">
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/soft_shadow_64.png">
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/soft_shadow_144.png">

Here are the above images in a video format.

<video width="64%" style="min-width: 260px;" type="video/webm" loop autoplay onclick="this.paused ? this.play() : this.pause();">
	<source type="video/mp4" src="assets/soft_shadow.mp4" />
	<source type="video/webm" src="assets/soft_shadow.webm" />
</video>

# Anti-aliasing using supersampling (with jittering)
Anti-aliasing was implemented using the supersampling technique by increasing the number of rays casted per pixel. Below on the left is the original image with 1 ray per pixel, and on the right we have an image produced by casting 4 rays per pixel, and averaging their results. We can see that the image on the right appears smoother.

This does come with a cost, the original image took **9.377s** to render while the anti-aliased image took **35.393s**.

<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/0_took_9_377s.png">
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/2_took_35_393s.png">

# Extra: Adaptive anti-aliasing
For an extra objective, I implemented adaptive anti-aliasing. I found that having to cast an exponentially larger number of rays was too impractical to render. Adaptive anti-aliasing was implemented by iteratively figuring out which pixels are "bad" pixels, and only re-sampling those ones.

On the left we have the fully anti-aliased image with 4 rays per pixel, and on the right we have an adaptive anti-aliased image that used at most 6 samples for some pixels. The one on the left took **35.393s** while the one on the right took **12.711s**.

<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/2_took_35_393s.png">
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/adaptive_6_took_12_711s.png">

The two images do differ as highlighted by the pixels in yellow. However, on first glance they produce roughly the same image.

<img width="64%" src="assets/aa_diff_1_15_percent_different.png">

This debug image gives a better idea of how the adaptive anti-aliasing works. Notice how the anti-aliasing is mostly done on edges, the pixels that need it the most. The following is a legend that shows what color corresponds to how many samples that pixel had:

<div style="text-align: left;">
	<ul>
	<li>
	Black = 1 sample
	</li>
	<li>
	White = 2 samples
	</li>
	<li>
	Yellow = 3 samples
	</li>
	<li>
	Blue = 4 samples
	</li>
	<li>
	Greed = 5 samples
	</li>
	<li>
	Purple = 6 samples
	</li>
	<li>
	Red = 7+ samples
	</li>
	</ul>
</div>

<img src="assets/aa_debug.png">

# Extra: Interpolation between vertex normals
When reading in an `.obj` file, the `Mesh` class can now consume vertex normals. It then uses these normals to interpolate using barycentric coordinates the normal for an arbitrary point on a triangle. This produces smoother looking meshes.

<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/glass_faceted.png">
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/glass_smooth.png">

We can also see here that this works well with refractive materials.

<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/mug_flat.png">
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/mug_smooth.png">

# Final Scene
I present to you CSG Restaurant. You have 3 choices starting with an assortment of chopped up primitives, a mug and a magic glass, and finally a cow with a chunk cut out of it and a die.

<img src="assets/final_1024.png">

I was not able to render all my features at once, and so the following is a 256x256 image with 16 shadow samples.

<img src="assets/final_256_16_shadow_1_aa.png">

# References
Textures obtained from https://opengameart.org/content/50-free-textures-4-normalmaps
Models obtained from https://www.cgtrader.com/items/635604
