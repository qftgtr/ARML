# `<a-circle>`

The circle primitive creates circles surfaces using the [geometry][geometry]
component with the type set to `circle`.

## Example

```html
<a-scene>
  <!-- Basic circle. -->
  <a-circle color="#CCC" radius="0.2"></a-circle>

  <!-- Textured circle parallel to ground. -->
  <a-circle src="https://url.com/image.jpg" radius="0.5" rotation="-90 0 0"></a-circle>
</a-scene>
```

## Attributes

| Attribute                        | Component Mapping                      | Default Value |
| --------                         | -----------------                      | ------------- |
| color                            | material.color                         | #FFF          |
| metalness                        | material.metalness                     | 0             |
| radius                           | geometry.radius                        | 1             |
| roughness                        | material.roughness                     | 0.5           |
| src                              | material.src                           | None          |

## Parallelizing to the Ground

To make a circle parallel to the ground, rotate it around the X-axis:

```html
<a-circle rotation="-90 0 0"></a-circle>
```

[geometry]: ../components/geometry.md
