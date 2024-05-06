
# A Brief Overview of CAM

## What is CAM?

CAM stands for "Computer-Aided Manufacturing". CNC Machines execute their movements and actions by reading a (non-standardized) language called G-Code, which for the most part is a letter followed by a string of numbers, which tells the machine to perform a specific action at a specific location. As an operator, this is extremely inconvenient as it requires the programmer to memorize or lookup codes in order to write a singular toolpath - let alone an entire program - all without synchronous visual aid or simulation of their toolpath. CAM is an abstraction of G-code programming that makes the process mostly visual. Toolpaths are visually programmed in a method similar to computer design process, allowing you to program various complex operations without looking up a single G-code. CAM softwares also typically have simulations and toolpath visualization as aids. These toolpath directives will be later compiled by a post-processor into G-code that the machine can read. In the IFL we use Autodesk Fusion360 CAM, but there are many more softwares such as MasterCAM, HSMWorks, etc. that you can try out on your own if you'd like (assuming you can get a subscription somehow).

## Setups

You can think of setups as imposing dimensions on your program - how big the stock is, what direction is what, etc.

### Setup

- The first tab in fusion is just labeled `setup`. This is where the majority of the setup happens though. For the Datron, you can ignore the fields that ask for machine and operation type (operation type should default to milling). The most important part of this tab is the WCS (work coordinate system)
- The work coordinate system defines the way the machine "sees" the part. When you go to probe a part in the machine, the axis will be programmed in via the CAM, not the probing. This is important for parts that are not square or circular, as if your axis are wrong when you are probing you'll have to start all over again because the machine axis does not align with the part axis. If you set the Z height incorrectly, say probing off the part vs probing off the bed, then you'd also have to re-post your CAM to the machine. It's important to keep in mind probing when you set these parameters

### Stock

- The stock tab is where you set the dimensions of your stock. The `mode` selection is just a way to assign dimensions based on different parameters. You can choose to use a stock size that is just offset in certain dimensions from the model, a fixed size that you control, the size of the model itself, or sometimes you will elect to use the stock from a previous setup.
- Fusion will tell you the size of the stock below this section

## Types of Toolpaths

This section is meant to be a **very brief** overview of the toolpaths that we most commonly use on Datron parts - you might be able to find more information than what's in here by hovering over each operation in fusion. 

> [!NOTE]
> There are also more operations than we cover here, so feel free to explore on your own!

### Face

A face is a simple operation - it just removes a set amount of stock from the Z axis (at least in 3 dimensions). Nothing more, nothing less

### 2D Adaptive

A 2D adaptive is a toolpath that is optimized for roughing - that is - removing the most amount of material in as little time possible. It's called a "2D" adaptive because it can only machine geometries defined in 2 dimensions. The third dimension is just the same geometries at different heights

### 2D Contour

A 2D contour machines along a set line with compensation (you can think of compensation as being a tangent on the right or the left of a endmill). These are mostly used to finish edges or walls of a part, with the wall being the line that the toolpath machines along. Similarly to adaptives, "2D" contours refer to the fact that you have to choose a 2 dimensional geometry to machine. You can then machine that geometry at different heights. Contours also have stepovers for cases where there is more material to remove than the diameter of the tool

### 2D Pocket

A 2D pocket operation is similar to an adaptive in a sense that they are both roughing operations. Where they differ is in how they choose to generate the toolpaths. Both toolpaths will initially ramp into a part, but from there the adaptive will machine arcs outwards in a single direction until it can't anymore and then start machining in the opposite direction until it machines the geometry. A pocket will machine the geometry concentrically, stepping outwards each time until the final pass, which is is the full geometry. There are nice visual guides in fusion if you can't envision what each operation is doing

### Bore

A bore is a simple operation that machines a hole by ramping (spiraling) down the edge of the hole.

### 3D Adaptive

A 3D adaptive is similar to 2D adaptives, however, wheras a 2D adaptive is limited to a 2 dimension geometry, a 3D adaptive can machine rough complex geometries in 3 dimensions, which is more effective for parts that are not consistent across the Z axis

### Flat

A flat is a finishing operation that works on flat geometries. It will detect them and create a machining path that is concentric to the border of the geometry, similar to the type of toolpath that pocket generates

### Scallop

A scallop is a finishing operation that can be used on any type of geometry. It generates a toolpath similar to pocket toolpaths, it does passes that are similarly shaped but increasing in size at outward consistent stepovers. When used correctly, this toolpath can create some cool finishes
