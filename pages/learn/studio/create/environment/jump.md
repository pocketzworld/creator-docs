# Jump

The Jump node is a special node that allows you to jump to another node in the environment. This is useful for creating non-linear experiences where the user can jump to different parts of the environment based on their choices.


## Creating a Jump Node

To create a Jump node, follow these steps:

1. Right-click in the `Hierarchy` window and select `Create Empty`.
2. Rename the new object to `Jump`.
3. Add a `Off Mesh Link` component to the object by clicking `Add Component` in the `Inspector`.
4. Add a `Off Mesh Link Handler` component to the object by clicking `Add Component` in the `Inspector`.
5. Specify the Start and End points for the jump (see methods below).
6. Change the `Navigation Area` to `Jump` in the `Off Mesh Link` component.
7. Modify the speed and height of the jump in the `Off Mesh Link Handler` component.
8. Set the `Move Type` to `Jump` in the `Off Mesh Link Handler` component.

<Note type="warning">
You need a start and end point for the jump to work properly. The start and end points should be close to the ground and not too far apart.
</Note>

## Start and End Points

To set the start and end points for the jump, you can create two empty objects in the scene and position them where you want the jump to start and end. You can then assign these objects to the `Start Point` and `End Point` fields in the `Off Mesh Link` component.

<Note type="warning">
Make sure the start and end points are close to the ground slightly above the ground level.
</Note>