# Examples

## General Info
Every **AXOLOTL** definition consists of _three_ main parts:

1. The discretisation of space into a three dimensional _grid of voxels_. This can either be done from a simple box or from a grayscale raster image describing the topography of a landscape. The outputs of this part are
   * the resolution in X, Y and Z (required by other components, e.g. blur and Millipede isosurface) and
   * a one dimensional list of query points for the distance calculations (`pts`)
1. Building up the _CSG (constructive solid geometry) tree_. All the components that create geometry take as an input - beside their own geometric properties like center and radius for a sphere - the list of points from step one (`pts`) and outputs a one dimensional list of distances `a` as floats. Two of these lists can be combined by  Boolean operation components `Union`, `Subtraction`, `Intersection` and `Blending`. They take as input two `a` lists and output the result as another `a` list that can be fed into other Boolean operations again.
1. The _visualisation_ part, where the voxel field of distance values is turned into either geometry (using the `FRepIsosurface` component) or displayed as a volume of dots whose colour corresponds to its distance value.

## 00 Basic
![basic](/pix/00_basic.png)

Just the very basics: one sphere, one torus, combined with Boolean operation and two different ways of visualisation.

## 01 Landscape
![landscape](/pix/01_landscape.png)

Create the voxel space on the basis of a height map (grayscale image).

## 02 Bike Node
![bikenode](/pix/02_bikenode.png)

I stumbled upon this inspirational image recently and thought that would be a good exercise for Axolotl.

![3dp_bike](https://www.3ders.org/images2017/3d-printed-iot-orbitrec-bike-available-buy-soon-5.jpg)

source: [3ders.org](https://www.3ders.org/articles/20171026-xons-3d-printed-iot-orbitrec-bike-available-to-buy-soon.html)

Of course it is not the same, but close enough to get an idea:

![bikenodeemap](/pix/bikenode_transp.png)

## 03 Lattice
![lattice_def](/pix/03_lattice.png)

This example shows how the distance field from one object (sphere) can be used to create a gradual offset to another object (lattice).

![lattice](/pix/lattice.png)

## 04 Crossnode
![crossnode_def](/pix/04_crossnode.png)

This example shows the blending of three profiles into one node, hollowed out, while preserving sharp edges.

![crossnode](/pix/crossnode.png)
