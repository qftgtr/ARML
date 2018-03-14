# Position, Rotation, Scale

## Position

The position component places entities at certain spots in 3D space. Position
takes a coordinate value as three space-delimited numbers.

All entities inherently have the position component.

### Example

```html
<a-entity position="0 1 -1"></a-entity>
```

### Value

A-Frame uses a right-handed coordinate system where the negative Z axis extends into the screen. The table below assumes looking down the negative Z axis from the origin.

| Axis | Description                                                  | Default Value |
|------|--------------------------------------------------------------|---------------|
| x    | Negative X axis extends left. Positive X Axis extends right. | 0             |
| y    | Negative Y axis extends down. Positive Y Axis extends up.    | 0             |
| z    | Negative Z axis extends in. Positive Z Axis extends out.     | 0             |

### Relative Positioning

World-space positions of child entities inherit from parent entities. Consider this scene:

```html
<a-entity id="parent" position="1 2 3">
  <a-entity id="child1"></a-entity>
  <a-entity id="child2" position="2 3 4"></a-entity>
</a-entity>
```

The world-space position of `#child1` would be `1 2 3` as inherited by the
entity. In the local parent's space, `#child1`'s position would be `0 0 0`.

The world-space position of `#child2` would be `3 5 7`, by combining the
position with the parent entity. In the parent's local space, `#child2`'s
position would be `2 3 4`.


## Rotation

The rotation component defines the orientation of an entity in degrees. It
takes the pitch (`x`), yaw (`y`), and roll (`z`) as three space-delimited
numbers indicating degrees of rotation.

All entities inherently have the rotation component.

### Example

```html
<a-entity rotation="45 90 180"></a-entity>
```

### Value

A-Frame uses a right-handed coordinate system. When aligning our right hand's
thumb with a positive axis, our hand will curl in the positive direction of
rotation.

| Axis | Description                       | Default Value
|------|-----------------------------------|---------------|
| x    | Pitch, rotation about the X-axis. | 0             |
| y    | Yaw, rotation about the Y-axis.   | 0             |
| z    | Roll, rotation about the Z-axis.  | 0             |

### Relative Rotation

Child entities inherit from world-space rotations from parent entities.
Consider this scene:

```html
<a-entity id="parent" rotation="0 45 0">
  <a-entity id="child1"></a-entity>
  <a-entity id="child2" rotation="15 45 30"></a-entity>
</a-entity>
```

The world-space rotation of `#child1` would be `0 45 0` as inherited by the
entity. In the local parent's space, `#child1`'s rotation would be `0 0 0`.

The world-space rotation of `#child2` would be `15 90 30`, by combining the
rotation with the parent entity. In the parent's local space, `#child2`'s
rotation would be `15 45 30`.

## Scale

The scale component defines a shrinking, stretching, or skewing transformation
of an entity. It takes three scaling factors for the X, Y, and Z axes.

All entities inherently have the scale component.

### Example

The example below shrinks the entity in half along the X direction, maintains
the same scale factor along the Y direction, and stretches the entity by
two-fold along the Z-direction:

```html
<a-entity scale="0.5 1 2"></a-entity>
```

### Value

If we set any of the scaling factors to 0, then A-Frame will assign instead a
negligible value.

| Axis | Description                        | Default Value |
|------|------------------------------------|---------------|
| x    | Scaling factor in the X direction. | 1             |
| y    | Scaling factor in the Y direction. | 1             |
| z    | Scaling factor in the Z direction. | 1             |

### Reflection

Scaling factors can be negative, which results in a reflection.

A notable use for this is for sky spheres. Sky spheres contain the entire scene
and have a texture mapped on the interior surface. To do this, we can reflect,
or invert, the sphere in the Z-direction.

```html
<a-entity geometry="primitive: sphere; radius: 1000"
          material="src: sky.png"
          scale="1 1 -1"></a-entity>
```

### Relative Scale

Similar to the rotation and position components, scales are applied in the
local coordinate system and multiply in nested entities.
