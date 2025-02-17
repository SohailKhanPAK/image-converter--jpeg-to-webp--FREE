<!DOCTYPE html>
<html>
<head>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            padding: 20px;
        }
        .container {
            max-width: 800px;
            margin: auto;
            background: #fff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
        }
        h1 {
            text-align: center;
            color: #333;
        }
        pre {
            background: #eee;
            padding: 15px;
            border-radius: 5px;
            overflow-x: auto;
        }
        .code-block {
            background: #272822;
            color: #f8f8f2;
            padding: 15px;
            border-radius: 5px;
            font-family: monospace;
            overflow-x: auto;
        }
        .button {
            display: block;
            width: fit-content;
            margin: 20px auto;
            padding: 10px 20px;
            background: #28a745;
            color: white;
            text-decoration: none;
            border-radius: 5px;
            text-align: center;
            font-size: 18px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>📷 Convert JPEG to WebP using Python</h1>
        <p>This script downloads images from a list of URLs and converts them into WebP format for better compression and quality retention.</p>
        
        <h2>🚀 Features</h2>
        <ul>
            <li>✅ Free & Open Source</li>
            <li>✅ Uses <code>Pillow</code> and <code>Requests</code></li>
            <li>✅ Converts JPEG to WebP with lossless compression</li>
            <li>✅ Saves images automatically in an <strong>output</strong> directory</li>
        </ul>
        
        <h2>⚡ Installation</h2>
        <pre><code>pip install pillow requests</code></pre>
        
        <h2>📝 Usage</h2>
        <div class="code-block">
            <code>
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
            </code>
        </div>
        
        <h2>📂 Output</h2>
        <p>The converted images will be saved in the <code>output</code> directory.</p>
        
        <h2>🔗 Contribute</h2>
        <p>Feel free to submit issues or pull requests to improve this script.</p>
        
        <a href="#" class="button">⭐ Star this Repo</a>
    </div>
</body>
</html>
