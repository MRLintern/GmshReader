## GmshReader
### Introduction
* This application reads in a Mesh (`.msh`) file enabling a `C++` program to use the corresponding `geometry` in an appropriate data format.
* This application has been developed with the `Finite Element Method` in mind.
* The Geometry of the `.msh` file resembles an `annulus`. Such a shape could be used for modelling __Deep-Earth Geophysics Phenomenon__ in 2D.
* Once `GmshReader` has read the `annulus.msh` file, we are left with essentially,`.dat` files which specifiy the problem domain.
#### 1. Generating a Mesh File (.msh)
* `$ gmsh -2 annulus.geo -format msh2 -o annulus.msh`
* You now have the `.msh` file.
* Note: There is no need to create your own `annulus.msh` mesh file; I've provided this.
#### 2. Reading .msh Files
* The files contains:
    * `Nodes` (points in space with coordinates).
    * `Elements` (triangles).
    * `Physical tags` (to identify boundaries or regions).
 
#### 3. Parsing Mesh Data into C++ Objects
* It stores:
    * A list of `nodes` as coordinate vectors (e.g., `(x, y) points`).
    * A list of `elements` as node indices (e.g., triangle with `nodes 1, 2, 3`).
    * Optional: boundary markers or physical regions.

#### 4. Output
* Three files are produced after running the software:
    * `nodes.dat` — List of node coordinates.
    * `elements.dat` — List of elements with node indices.
    * `boundary_nodes.dat` — Optional, depends on your mesh and tags

### Getting and Using the Software
* `$ git clone https://github.com/MRLintern/GmshReader`
* `$ cd GmshReader`
* `$ mkdir build -p && cd build`
* `$ cmake ..`
* `$ cmake --build .`
* `$ ./main`
* This will generate `nodes.dat`,`elements.dat` and `boundary_nodes.dat`.
* Note: to generate `nodes.dat`, `elements.dat` and `boundary_nodes.dat`, delete these __FIRST__. But, __keep__ `annulus.msh`.
