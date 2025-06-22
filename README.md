# ImagePluginFramework

A flexible internal plugin-based image processing framework built with .NET.  
Designed to apply multiple effects to multiple images using a scalable and dynamic architecture without relying on external libraries.

---

## 🔧 Project Goals

- Handle multiple images at once, each with its own set of effects.
- Apply multiple effects per image.
- Use a plugin system that allows easy addition/removal of plugins without changing the core logic.
- Avoid any third-party frameworks or real image processing libraries.
- Focus on clean object-oriented design, flexibility, and maintainability.

---



## 🧩 Plugins

Each plugin implements the `IPlugin` interface and is responsible for applying a specific (dummy) effect to the image.  

Supported example plugins:
- `ResizePlugin`: Simulates resizing an image.
- `BlurPlugin`: Simulates blurring with a specific intensity.
- `GrayscalePlugin`: Simulates grayscale conversion.

---

🧪 Sample Usage
The TestApp/Program.cs demonstrates how to:

Load plugins dynamically

Load dummy images

Assign effects to each image

Apply effects using ImageProcessor

✅ Example Output

Processing image: Image1
[Resize] Applied resize to 100 px on Image1
[Blur] Applied blur with size 2 px on Image1

Processing image: Image2
[Resize] Applied resize to 100 px on Image2

Processing image: Image3
[Resize] Applied resize to 150 px on Image3
[Blur] Applied blur with size 5 px on Image3
[Grayscale] Applied grayscale on Image3

🚫 Limitations
This is a mock framework. No real image data or image processing is performed.

Only console output is used to simulate image effects.

🔄 Extending the Framework
To create a new plugin:

Implement IPlugin

Define the Name and Apply() method


🧑‍💻 Author
Gegham Petrosyan
GitHub Profile

📃 License
This project is provided for assessment and educational purposes only.

---
