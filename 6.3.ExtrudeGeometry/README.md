# ExtrudeGeometry

Creating a geometry by extruding. Three.js provides a couple of ways in which we can extrude a 2D shape to a 3D shape. By extruding, we mean stretching out a 2D shape along its z axis to convert it to 3D. For instance, if we extrude a THREE.CircleGeometry, we get a shape that looks like a cylinder, and if we extrude THREE.PlaneGeometry, we get a cube-like shape. The most versatile way of extruding a shape is using the THREE.ExtrudeGeometry object.

With THREE.ExtrudeGeometry, you can create a 3D object from a 2D shape. Before we dive into the details of this geometry, let's first look at an example: 03-extrudegeometry.html. The following screenshot taken from the example shows this geometry:

<a href="../learning-threejs-master/chapter-06/03-extrude-geometry.html">
  <img src="../img/5.3.png">
</a>

<a href="../learning-threejs-master/chapter-06/03-extrude-geometry.html"><h3>CODE</h3></a>

<a href="../learning-threejs-master/chapter-06/03-extrude-geometry.html"><h3>CODE</h3></a>

<a href="../learning-threejs-master/chapter-06/03-extrude-geometry.html"><h3>CODE</h3></a>

<a href="https://cg2021c.github.io/threejs-presentation-anak-ambis/learning-threejs-master/chapter-06/03-extrude-geometry.html"><h3>Try Yourself</h3></a>

<a href="https://cg2021c.github.io/threejs-presentation-anak-ambis/learning-threejs-master/chapter-06/03-extrude-geometry.html"><h3>Try Yourself</h3></a>

<a href="https://cg2021c.github.io/threejs-presentation-anak-ambis/learning-threejs-master/chapter-06/03-extrude-geometry.html"><h3>Try Yourself</h3></a>

In this example, we took the 2D shape we created in the previous chapter and used THREE.ExtrudeGeometry to convert it to 3D. As you can see in this screenshot, the shape is extruded along the z axis, which results in a 3D shape. The code to create THREE.ExtrudeGeometry is very easy:

```js
var options = {
  amount: controls.amount,
  bevelThickness: controls.bevelThickness,
  bevelSize: controls.bevelSize,
  bevelSegments: controls.bevelSegments,
  bevelEnabled: controls.bevelEnabled,
  curveSegments: controls.curveSegments,
  steps: controls.steps,
};
var geom = new THREE.ExtrudeGeometry(drawShape(), options);
```

In this code, we created the shape with the drawShape() function just as we did in the previous chapter. This shape is passed on to the THREE.ExtrudeGeometry constructor together with an options object. With the options object, you can define exactly how the shape should be extruded. The following table explains the options you can pass in
to THREE.ExtrudeGeometry:

| Parameter      | Mandatory | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| -------------- | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| shapes         | Yes       | One or more shapes (THREE.Shape objects) are required to extrude the geometry from. See the preceding chapter on how to create such a shape.                                                                                                                                                                                                                                                                                                                     |
| amount         | No        | This determines how far (the depth) the shape should be extruded. The default value is 100                                                                                                                                                                                                                                                                                                                                                                       |
| bevelThickness | No        | This determines the depth of the bevel. The bevel is the rounded corner between the front and back faces and the extrusion. This value defines how deep into the shape the bevel goes. The default value is 6.                                                                                                                                                                                                                                                   |
| bevelSize      | No        | This determines the height of the bevel. This is added to the normal height of the shape. The default value is bevelThickness - 2.                                                                                                                                                                                                                                                                                                                               |
| bevelSegments  | No        | This defines the number of segments that will be used by the bevel. The more the number of segments used, the smoother the bevel will look. The default value is 3.                                                                                                                                                                                                                                                                                              |
| bevelEnabled   | No        | If this is set to true, a bevel is added. The default value is true.                                                                                                                                                                                                                                                                                                                                                                                             |
| curveSegments  | No        | This determines how many segments will be used when extruding the curves of shapes. The more the number of segments used, the smoother the curves will look. The default value is 12.                                                                                                                                                                                                                                                                            |
| steps          | No        | This defines the number of segments into the extrusion will be divided along its depth. The default value is 1. A higher value will result in more individual faces.                                                                                                                                                                                                                                                                                             |
| extrudePath    | No        | This is the path (THREE.CurvePath) along which the shape should be extruded. If this isn't specified, the shape is extruded along the z axis                                                                                                                                                                                                                                                                                                                     |
| uvGenerator    | No        | When you use a texture with your material, the UV mapping determines what part of a texture is used for a specific face. With the uvGenerator property, you can pass in your own object that will create the UV settings for the faces that are created for the shapes that are passed in. More information on UV settings can be found in Chapter 10, Loading and Working with Textures. If none are specified, THREE.ExtrudeGeometry.WorldUVGenerator is used. |
