# `<a-image>`

The image primitive shows an image on a flat plane.

## Example

```html
<a-scene>
  <!-- Defining the URL inline. Not recommended but more comfortable for web developers. -->
  <a-image src="https://myurl.com/image.png"></a-image>
</a-scene>
```

## Attributes

| Attribute       | Component Mapping       | Default Value |
| --------        | -----------------       | ------------- |
| color           | material.color          | #FFF          |
| height          | geometry.height         | 1             |
| opacity         | material.opacity        | 1             |
| src             | material.src            | None          |
| transparent     | material.transparent    | false         |
| width           | geometry.width          | 1             |

## Fine-Tuning

Ensuring that the image is not distorted by stretching requires us to appropriately set the `width` and `height`.

```html
<a-image src="image.png" width="200" height="100"></a-image>
```
