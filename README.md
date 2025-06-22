# ImagePluginFramework

A flexible internal plugin-based image processing framework built with .NET.  
Designed for applying multiple effects to multiple images using a scalable and dynamic architecture without relying on external libraries.

---

## 🔧 Project Goals

- Handle multiple images at once, each with its own set of effects.
- Apply multiple effects per image.
- Use a plugin system that allows easy addition/removal of plugins without changing the core logic.
- Avoid any third-party frameworks or real image processing libraries.
- Focus on clean object-oriented design, flexibility, and maintainability.

---

## 🧱 Architecture Overview

ImagePluginFramework/
│
├── Core/ # Core framework logic and abstractions
│ ├── IPlugin.cs
│ ├── PluginManager.cs
│ ├── ImageProcessor.cs
│ └── Models/
│ ├── ImageData.cs
│ └── PluginParameter.cs
│
├── Plugins/ # Dummy plugin implementations
│ ├── ResizePlugin.cs
│ ├── BlurPlugin.cs
│ └── GrayscalePlugin.cs
│
├── Dummy/ # Simulated image loader
│ └── ImageRepository.cs
│
├── Config/
│ └── plugins.json # Config file listing enabled plugins
│
└── TestApp/ # Sample console application demonstrating usage
└── Program.cs

---

## 🧩 Plugins

Each plugin implements the `IPlugin` interface and is responsible for applying a specific (dummy) effect to the image.  

Supported example plugins:
- `ResizePlugin`: Simulates resizing an image.
- `BlurPlugin`: Simulates blurring with a specific intensity.
- `GrayscalePlugin`: Simulates grayscale conversion.

Plugins are configured dynamically via the `Config/plugins.json` file.

---

🧪 Sample Usage
The TestApp/Program.cs demonstrates how to:

Load plugins dynamically

Load dummy images

Assign effects to each image

Apply effects using ImageProcessor


var manager = new PluginManager();
manager.LoadPlugins("Config/plugins.json");

var images = ImageRepository.LoadImages();
images[0].Effects.Add((manager.GetPlugin("Resize")!, new PluginParameter { Value = 100 }));
images[0].Effects.Add((manager.GetPlugin("Blur")!, new PluginParameter { Value = 2 }));

images[1].Effects.Add((manager.GetPlugin("Resize")!, new PluginParameter { Value = 100 }));

images[2].Effects.Add((manager.GetPlugin("Resize")!, new PluginParameter { Value = 150 }));
images[2].Effects.Add((manager.GetPlugin("Blur")!, new PluginParameter { Value = 5 }));
images[2].Effects.Add((manager.GetPlugin("Grayscale")!, null));

var processor = new ImageProcessor();
processor.ProcessImages(images);
✅ Example Output
csharp
Copy
Edit
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

Add the plugin to plugins.json

Example:

csharp
Copy
Edit
public class MyCustomPlugin : IPlugin
{
    public string Name => "MyCustom";
    public void Apply(ImageData image, PluginParameter? parameter)
    {
        Console.WriteLine($"[MyCustom] Did something to {image.Name}");
    }
}
🧑‍💻 Author
Gegham Petrosyan
GitHub Profile

📃 License
This project is provided for assessment and educational purposes only.

---
