# 📷 Convert JPEG to WebP using Python

This script downloads images from a list of URLs and converts them into WebP format for better compression and quality retention.

## 🚀 Features
- ✅ Free & Open Source
- ✅ Uses `Pillow` and `Requests`
- ✅ Converts JPEG to WebP with lossless compression
- ✅ Saves images automatically in an `output` directory

## ⚡ Installation
```sh
pip install pillow requests
```

## 📝 Usage
```python
from PIL import Image
import os
import requests
from io import BytesIO

# List of image URLs
image_urls = []  # Replace with your actual image URLs

# Create output directory if it doesn't exist
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

def download_and_convert_to_webp(image_url, output_path):
    try:
        response = requests.get(image_url, stream=True)
        response.raise_for_status()
        image = Image.open(BytesIO(response.content))
        image.save(output_path, "WEBP", lossless=True)
        print(f"Converted {image_url} → {output_path}")
    except Exception as e:
        print(f"Error converting {image_url}: {e}")

# Process each image in the list
for image_url in image_urls:
    filename = os.path.basename(image_url).split('.')[0] + ".webp"
    output_path = os.path.join(output_dir, filename)
    download_and_convert_to_webp(image_url, output_path)
```

## 📂 Output
The converted images will be saved in the `output` directory.

## 🔗 Contribute
Feel free to submit issues or pull requests to improve this script.

⭐ **Star this Repo** if you find it useful!
