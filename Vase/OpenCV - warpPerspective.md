```cpp
warpPerspective()
void cv::warpPerspective	(	InputArray 	src,
OutputArray 	dst,
InputArray 	M,
Size 	dsize,
int 	flags = INTER_LINEAR,
int 	borderMode = BORDER_CONSTANT,
const Scalar & 	borderValue = Scalar() 
)		
#Python:
dst	=	cv.warpPerspective(	src, M, dsize[, dst[, flags[, borderMode[, borderValue]]]]	)
```

* `src`	input image.
* `dst`	output image that has the size dsize and the same type as src .
* `M`	3×3 transformation matrix.
* `dsize`	size of the output image.
* `flags`	combination of interpolation methods (INTER_LINEAR or INTER_NEAREST) and the optional flag WARP_INVERSE_MAP, that sets M as the inverse transformation ( 𝚍𝚜𝚝→𝚜𝚛𝚌 ).
* `borderMode`	pixel extrapolation method (BORDER_CONSTANT or BORDER_REPLICATE).
* `borderValue`	value used in case of a constant border; by default, it equals 0.

其中每个点映射到对应图像中到坐标遵循下列公式：

$$
𝚍𝚜𝚝(x,y)=𝚜𝚛𝚌(\frac{M_{11}x+M_{12}y+M_{13}}{M31x+M32y+M33},\frac{M_{21}x+M_{22}y+M_{23}}{M31x+M32y+M33})
$$


{: id="20201120095601-2pbettx" type="doc"}
