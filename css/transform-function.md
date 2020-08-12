# transform-function

Matrix\(\)

![](../.gitbook/assets/image%20%2860%29.png)

![](../.gitbook/assets/image%20%2865%29.png)

```text
matrix(a, b, c, d, tx, ty)

matrix3d(a1, b1, c1, d1, a2, b2, c2, d2, a3, b3, c3, d3, a4, b4, c4, d4)
```

#### Perspective <a id="Perspective"></a>

[`perspective()`](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/perspective)Sets the distance between the user and the z=0 plane.

#### Rotation <a id="Rotation"></a>



```text
.rotated {
  transform: rotate(45deg); 
  }
```

The **`rotate()`** [CSS](https://developer.mozilla.org/en-US/docs/Web/CSS) function defines a transformation that rotates an element around a fixed point on the 2D plane, without deforming it. Its result is a [`<transform-function>`](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function) data type.

The fixed point that the element rotates around — mentioned above — is also known as the **transform origin**. This defaults to the center of the element, but you can set your own custom transform origin using the [`transform-origin`](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-origin) property.

[`rotate()`](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/rotate)Rotates an element around a fixed point on the 2D plane.[`rotate3d()`](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/rotate3d)Rotates an element around a fixed axis in 3D space.[`rotateX()`](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/rotateX)Rotates an element around the horizontal axis.[`rotateY()`](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/rotateY)Rotates an element around the vertical axis.[`rotateZ()`](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/rotateZ)Rotates an element around the z-axis.

#### Scaling \(resizing\) <a id="Scaling_resizing"></a>

![](../.gitbook/assets/image%20%2864%29.png)

[`scale()`](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/scale)Scales an element up or down on the 2D plane.[`scale3d()`](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/scale3d)Scales an element up or down in 3D space.[`scaleX()`](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/scaleX)Scales an element up or down horizontally.[`scaleY()`](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/scaleY)Scales an element up or down vertically.[`scaleZ()`](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/scaleZ)Scales an element up or down along the z-axis.

#### Skewing \(distortion\) <a id="Skewing_distortion"></a>

[`skew()`](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/skew)Skews an element on the 2D plane.[`skewX()`](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/skewX)Skews an element in the horizontal direction.[`skewY()`](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/skewY)Skews an element in the vertical direction.

#### Translation \(moving\) <a id="Translation_moving"></a>

[`translate()`](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/translate)Translates an element on the 2D plane.

The **`translate()`** [CSS](https://developer.mozilla.org/en-US/docs/Web/CSS) function repositions an element in the horizontal and/or vertical directions. Its result is a [`<transform-function>`](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function) data type.

![](../.gitbook/assets/image%20%2870%29.png)

[`translate3d()`](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/translate3d)Translates an element in 3D space.[`translateX()`](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/translateX)Translates an element horizontally.[`translateY()`](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/translateY)Translates an element vertically.[`translateZ()`](https://developer.mozilla.org/en-US/docs/Web/CSS/transform-function/translateZ)Translates an element along the z-axis.

