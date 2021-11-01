# ParametricGeometry

With THREE.ParametricGeometry, you can create a geometry based on an equation. Before we dive into our own example, a good thing to start with is to look at the examples already provided by Three.js. When you download the Three.js distribution, you get the examples/js/ParametricGeometries.js file. In this file, you can find a couple of examples of equations you can use together with THREE.ParametricGeometry. The most basic example is the function to create a plane:

```js
plane: function ( width, height ) {
 return function ( u, v, optionalTarget ) {
 var result = optionalTarget || new THREE.Vector3();
 var x = u * width;
 var y = 0;
 var z = v * height;
 return result.set( x, y, z );
 };
 }
```

This function is called by THREE.ParametricGeometry. The u and v values will range from 0 to 1 and will be called a large number of times for all the values from 0 to 1. In this example, the u value is used to determine the x coordinate of the vector and the v value is used to determine the z coordinate. When this is run, you'll have a basic plane with a width of width and a depth of depth.

In our example, we do something similar. However, instead of creating a flat plane, we create a wave-like pattern, as you can see in the 06-parametricgeometries.html example. The following screenshot shows this example:

<a href="../learning-threejs-master/chapter-06/06-parametric-geometries.html">
  <img src="../img/5.6.png">
</a>

In this example, you can also see the arguments we can pass
to THREE.ParametricGeometry. These are explained in the following table:

| Parameter | Mandatory | Description                                                                                         |
| --------- | --------- | --------------------------------------------------------------------------------------------------- |
| function  | Yes       | This is the function that defines the position of each vertex based on the u and v values provided. |
| slices    | Yes       | This defines the number of parts the u value should be divided into.                                |
| stacks    | Yes       | This defines the number of parts the v value should be divided into.                                |
