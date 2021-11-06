In Chapter Before, Learning to Work with Geometries, we showed you all the basic geometries
provided by Three.js. Besides these basic geometries, Three.js also offers a set of more
advanced and specialized objects. In this chapter, we'll show you these advanced
geometries and cover the following subjects:

- How to use advanced geometries such as THREE.ConvexGeometry, THREE.LatheGeometry, and THREE.TubeGeometry.
- How to create 3D shapes from 2D shapes using THREE.ExtrudeGeometry. We'll do this based on a 2D shape drawn using functionality provided by Three.js, and we'll show an example where we create a 3D shape based on an externally loaded SVG image.
- If you want to create custom shapes yourself, you can easily amend / change the ones we've discussed in the previous chapters. Three.js, however, also offers
  a THREE.ParametricGeometry object. With this object, you can create a geometry based on a set of equations.
- Finally, we'll look at how you can create 3D text effects using THREE.TextGeometry.
- Additionally, we'll also show you how you can create new geometries from existing ones using binary operations provided by the Three.js extension, ThreeBSP.

We'll start with the first one from this list, THREE.ConvexGeometry

note: All the picture in 6.x is clickable. it will redirect to the particular code



6.1.ConvexGeometry:allam
6.2.LatheGeometry:allam
6.3.ExtrudeGeometry:arif
6.4.TubeGeometry:ridho
6.5.1.ShapeGeometry:erik
6.5.2.ParametricGeometry:fajar
6.6.Creating 3D text:fio
6.7.Using binary operations to combine meshes:allam

geometry grouping and merging
 arif: grouping objects together
 arif: merging multiple meshes into a single mesh
Loading geometries from external resources
 ridho: saving and loading in three.js json format
 ridho: saving and loading three.mesh
 allam: saving and loading a scene
 allam: working with blender
importing 3d file formats
 erik: obj and mtl formats
 erik: loading a COLLADA model
 fajar: loading models from other supported formats
 fajar: show proteins from PDB
 fio: Creating a particle system from a PLY model