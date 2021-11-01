# TubeGeometry

THREE.TubeGeometry creates a tube that extrudes along a 3D spline. You specify the path using a number of vertices, and THREE.TubeGeometry will create the tube. An example that you can experiment with can be found in the sources for this chapter (04-extrudetube.html). The following screenshot shows this example:

<a href="../learning-threejs-master/chapter-06/04-extrude-tube.html">
  <img src="../img/5.4.png">
</a>

As you can see in this example, we generate a number of random points and use those points to draw the tube. With the controls in the upper-right corner, we can define how the tube looks or generate a new tube by clicking on the newPoints button.

What we need to do first is get a set of vertices of the THREE.Vector3 type just like we did for THREE.ConvexGeometry and THREE.LatheGeometry. Before we can use these points, however, to create the tube, we first need to convert these points to a THREE.CatmullRomCurve3. In other words, we need to define a smooth curve through the points we defined. We can do this simply by passing in the array of vertices to the constructor of THREE.CatmullRomCurve3. With this curve and the other arguments (which we'll explain in a bit), we can create the tube and add it to the scene. THREE.TubeGeometry takes some other arguments besides THREE.SplineCurve3. The following table lists all the arguments for THREE.TubeGeometry:

| Parameter      | Mandatory | Description                                                                                                                                          |
| -------------- | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| path           | Yes       | This is THREE.SplineCurve3 that describes the path this tube should follow.                                                                          |
| segments       | No        | These are the segments used to build up the tube. The default value is 64. The longer the path, the more segments you should specify                 |
| radius         | No        | This is the radius of the tube. The default value is 1                                                                                               |
| radiusSegments | No        | This is the number of segments to be used along the length of the tube. The default value is 8. The more you use, the more round the tube will look. |
| closed         | No        | If this is set to true, the start of the tube and the end will be connected together. The default value is false.                                    |
