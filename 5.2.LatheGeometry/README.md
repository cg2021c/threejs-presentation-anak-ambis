# LatheGeometry

THREE.LatheGeometry allows you to create shapes from a smooth curve. This curve is defined by a number of points (also called knots) and is most often called a spline. This spline is rotated around the central z axis of the object and results in vase-like and bell-like shapes. Once again, the easiest way to understand what THREE.LatheGeometry looks like is by looking at an example. This geometry is shown in 02-advanced-3d-geometrieslathe.html. The following screenshot taken from the example shows this geometry:

<a href="../learning-threejs-master/chapter-06/02-advanced-3d-geometries-lathe.html">
  <img src="../img/5.2.png">
</a>

In the preceding screenshot, you can see the points used to create this geometry as a set of small red spheres. The positions of these points are passed in to THREE.LatheGeometry, together with a couple of other arguments.

| Parameter | Mandatory | Description                                                                                                                                                                     |
| --------- | --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| points    | Yes       | These are the points that make up the spline used to generate the bell/vase shape.                                                                                              |
| segments  | No        | These are the number of segments used when creating the shape. The higher this number, the more round and smooth the resulting shape will be. The default value for this is 12. |
| phiStart  | No        | This determines where to start on a circle when generating the shape. This can range from 0 to 2 \* PI. The default value is 0.                                                 |
| phiLength | No        | This defines how fully generated the shape is. For instance, a quarter shape will be 0.5 _ PI. The default value is the full 360 degrees or 2 _ PI.                             |

## concepts

- generate points
  - positions, (add geo and mesh. optional)
  - group the points
- pass the points to LatheGeometry
- add mesh and render
