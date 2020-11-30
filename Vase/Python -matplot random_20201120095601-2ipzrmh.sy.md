### Random Color For Different Identity

```python
color = list()
for i in range(27):
	color_B = 127 * int(i/9) + 1
	color_G = 127 * int((i%9)/3) + 1
	color_R = 127 * int(i%3) + 1
	if color_B + color_G + color_R > 300:
		color.append((color_B, color_G, color_R))

def _get_color(self, index):
	idx = index % len(self.color)
	return self.color[idx]
```
