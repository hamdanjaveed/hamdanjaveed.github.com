---
layout: post
title:  "CS 488 Project Demo"
subtitle: "Hamdan Javeed"
categories: [tool]
---

# KD-trees for efficient ray intersections
<div style="text-align: left;">
	Made it faster
</div>

<img min-width="260px" src="assets/initial_profile.png">
<img min-width="260px" src="assets/kd_tree_profile.png">
<img width="64%" min-width="260px" src="assets/sample.png">

# Refraction
<img width="64%" src="assets/refraction_hiertest.png">

<video src="assets/refraction_balls.webm" width="64%" style="min-width: 260px;" type="video/webm" loop autoplay onclick="this.paused ? this.play() : this.pause();"></video>

# Texture mapping
<video src="assets/texture_sphere.webm" width="64%" style="min-width: 260px;" type="video/webm" loop autoplay onclick="this.paused ? this.play() : this.pause();"></video>
<video src="assets/texture.webm" width="64%" style="min-width: 260px;" type="video/webm" loop autoplay onclick="this.paused ? this.play() : this.pause();"></video>

# Bump mapping
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/sphere_non_bump.png">
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/sphere_bump.png">

<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/cylinder_non_bump.png">
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/cylinder_bump.png">

<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/cone_non_bump.png">
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/cone_bump.png">

<video src="assets/cube_bump.webm" width="64%" style="min-width: 260px;" type="video/webm" loop autoplay onclick="this.paused ? this.play() : this.pause();"></video>

# Constructive solid geometry
<img style="display: inline-block; margin: 0;" width="260px" src="assets/csg_001.png">
<img style="display: inline-block; margin: 0;" width="260px" src="assets/csg_002.png">
<img style="display: inline-block; margin: 0;" width="260px" src="assets/csg_003.png">

<img style="display: inline-block; margin: 0;" width="260px" src="assets/mesh_union.png">
<img style="display: inline-block; margin: 0;" width="260px" src="assets/mesh_subtract.png">
<img style="display: inline-block; margin: 0;" width="260px" src="assets/mesh_intersect.png">

<video src="assets/csg_teapot.webm" width="64%" style="min-width: 260px;" type="video/webm" loop autoplay onclick="this.paused ? this.play() : this.pause();"></video>

# Additional primitives
<div style="margin-bottom: 30px">
	<div style="display: inline; min-width: 260px;" width="49%">
		<img style="margin: 0; display: inline; min-width: 260px; max-width: 392px;" src="assets/sphere.png">
	</div>

	<video src="assets/cube.webm" width="49%" style="min-width: 260px; display:inline-block;" type="video/webm" loop autoplay onclick="this.paused ? this.play() : this.pause();"></video>
</div>

<video src="assets/cylinder.webm" width="49%" style="min-width: 260px; display:inline-block;" type="video/webm" loop autoplay onclick="this.paused ? this.play() : this.pause();"></video>

<video src="assets/cone.webm" width="49%" style="min-width: 260px; display:inline-block;" type="video/webm" loop autoplay onclick="this.paused ? this.play() : this.pause();"></video>

# Depth of field
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/dof_samples_10_fd_3_0_ar_0_01.png">
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/dof_samples_10_fd_3_0_ar_0_05.png">

<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/dof_samples_10_fd_3_0_ar_0_1.png">
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/dof_samples_10_fd_3_0_ar_0_15.png">

# Caustics
<div style="text-align: left;">
	This objective was not attempted due to lack of time.
</div>

# Soft shadows
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/soft_shadow_0.png">
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/soft_shadow_1.png">
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/soft_shadow_4.png">
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/soft_shadow_9.png">
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/soft_shadow_16.png">
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/soft_shadow_25.png">
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/soft_shadow_64.png">
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/soft_shadow_144.png">

<video src="assets/soft_shadow.webm" width="64%" style="min-width: 260px;" type="video/webm" loop autoplay onclick="this.paused ? this.play() : this.pause();"></video>

# Anti-aliasing using supersampling (with jittering)
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/0_took_9_377s.png">
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/2_took_35_393s.png">

# Extra: Adaptive anti-aliasing
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/2_took_35_393s.png">
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/adaptive_6_took_12_711s.png">

<img width="64%" src="assets/aa_diff_1_15_percent_different.png">

<img src="assets/aa_debug.png">

# Extra: Interpolation between vertex normals
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/glass_faceted.png">
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/glass_smooth.png">

<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/mug_flat.png">
<img style="display: inline-block; margin: 0;" width="395px" min-width="260px" src="assets/mug_smooth.png">
