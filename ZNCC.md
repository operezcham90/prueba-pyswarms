```python
!pip install requests Pillow numpy pyswarm scipy
```

```pythonimport requests
from PIL import Image
from io import BytesIO
import numpy as np

def openCVGrayscaleReal(r, g, b):
    return (299 * r + 587 * g + 114 * b) / 1000

# URLs for the template image and search space image
template_url = "https://raw.githubusercontent.com/operezcham90/prueba-pyswarms/main/t.jpg"
search_space_url = "https://raw.githubusercontent.com/operezcham90/prueba-pyswarms/main/f.jpg"

# Fetch the template image
template_response = requests.get(template_url)
template_image = Image.open(BytesIO(template_response.content))

# Fetch the search space image
search_space_response = requests.get(search_space_url)
search_space_image = Image.open(BytesIO(search_space_response.content))

# Convert template image to grayscale
template_grayscale = template_image.convert('RGB')
template_pixels = np.array(template_grayscale)

height, width, _ = template_pixels.shape
template_gray = np.zeros((height, width))

for i in range(height):
    for j in range(width):
        r, g, b = template_pixels[i, j]
        template_gray[i, j] = openCVGrayscaleReal(r, g, b)

# Convert search space image to grayscale
search_space_grayscale = search_space_image.convert('RGB')
search_space_pixels = np.array(search_space_grayscale)


height, width, _ = search_space_pixels.shape
search_space_gray = np.zeros((height, width))

for i in range(height):
    for j in range(width):
        r, g, b = search_space_pixels[i, j]
        search_space_gray[i, j] = openCVGrayscaleReal(r, g, b)

# Create grayscale images without an alpha channel
template_gray_image = Image.fromarray(template_gray.astype(np.uint8), mode='L')
search_space_gray_image = Image.fromarray(search_space_gray.astype(np.uint8), mode='L')

# Display the grayscale template image
template_gray_image.show()

# Display the grayscale search space image
search_space_gray_image.show()
```
