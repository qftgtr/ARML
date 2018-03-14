# `<a-cursor>`

The cursor primitive is a reticle that allows for clicking and basic
interactivity with a scene on devices that do not have a hand controller. The
default appearance is a sphere geometry. The cursor is usually placed as a child
of the camera.

Read the [cursor component documentation](../components/cursor.md) for detailed
information about how the cursor works and how to use the cursor.

## Example

```html
<a-scene>
  <a-camera>
    <a-cursor></a-cursor>
  </a-camera>

  <a-box></a-box>
</a-scene>
```
