```python
!pip install requests Pillow numpy pyswarm scipy
```

```python
import requests
from PIL import Image
from io import BytesIO

# URLs for the template image and search space image
template_url = "https://raw.githubusercontent.com/operezcham90/prueba-pyswarms/main/t.jpg"
search_space_url = "https://raw.githubusercontent.com/operezcham90/prueba-pyswarms/main/f.jpg"

# Fetch the template image
template_response = requests.get(template_url)
template_image = Image.open(BytesIO(template_response.content))

# Fetch the search space image
search_space_response = requests.get(search_space_url)
search_space_image = Image.open(BytesIO(search_space_response.content))

# Display the template image
template_image.show()

# Display the search space image
search_space_image.show()
```

```python
import requests
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
template_gray = openCVGrayscaleReal(template_pixels[:,:,0], template_pixels[:,:,1], template_pixels[:,:,2])

# Convert search space image to grayscale
search_space_grayscale = search_space_image.convert('RGB')
search_space_pixels = np.array(search_space_grayscale)
search_space_gray = openCVGrayscaleReal(search_space_pixels[:,:,0], search_space_pixels[:,:,1], search_space_pixels[:,:,2])

# Create grayscale images using the computed values
template_gray_image = Image.fromarray(template_gray.astype(np.uint8))
search_space_gray_image = Image.fromarray(search_space_gray.astype(np.uint8))

# Display the grayscale template image
template_gray_image.show()

# Display the grayscale search space image
search_space_gray_image.show()
```
