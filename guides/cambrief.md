
# A Brief Overview of CAM

## What is CAM?
CAM stands for "Computer-Aided Manufacturing". CNC Machines execute their movements and actions by reading a (non-standardized) language called G-Code, which for the most part is a letter followed by a string of numbers, which tells the machine to perform a specific action at a specific location. As an operator, this is extremely inconvenient as it requires the programmer to memorize or lookup codes in order to write a singular toolpath - let alone an entire program - all without synchronous visual aid or simulation of their toolpath. CAM is an abstraction of G-code programming that makes the process mostly visual. Toolpaths are visually programmed in a method similar to computer design process, allowing you to program various complex operations without looking up a single G-code. CAM softwares also typically have simulations and toolpath visualization as aids. These toolpath directives will be later compiled by a post-processor into G-code that the machine can read. In the IFL we use Autodesk Fusion360 CAM, but there are many more softwares such as MasterCAM, HSMWorks, etc. that you can try out on your own if you'd like (assuming you can get a subscription somehow).

## Setups
You can think of setups as imposing dimensions on your program - how big the stock is, what direction is what, etc.

## Operations

