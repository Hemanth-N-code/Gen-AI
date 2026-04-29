Fashion GenAI: Sketch & Text-to-Image Generation

This project leverages Stable Diffusion v1.5 and ControlNet to transform hand-drawn fashion sketches into high-fidelity clothing photography. It also includes a standard text-to-image pipeline for generating fashion concepts from scratch.

🚀 FeaturesSketch-to-Image: Uses a fine-tuned ControlNet (Canny-based) to maintain structural integrity from input sketches.Text-to-Image: Generates high-quality fashion imagery based on descriptive text prompts.

GPU Optimized: Utilizes Mixed Precision (FP16) and Attention Slicing to run efficiently on consumer-grade GPUs (or Google Colab).

📂 Project StructurePlaintext.
├── data/                   # (Ignored by Git) Dataset storage (6k images/sketches)
├── models/                 # (Ignored by Git) Saved ControlNet weights (.pth)
├── Sketch2.0.ipynb         # Notebook for training & inference of ControlNet
├── text_to_image.ipynb     # Notebook for standard Stable Diffusion generation
├── Sketch to Image.pdf     # Project documentation/Guide
├── Text to Image.pdf       # Project documentation/Guide
└── .gitignore              # Prevents large data/models from being uploaded

🛠️ Setup & Installation1. Clone the RepositoryBashgit clone https://github.com/Hemanth-N-code/Gen-AI.git
cd Gen-AI

2. Create Virtual EnvironmentBashpython -m venv venv
# Windows:
venv\Scripts\activate
# Mac/Linux:
source venv/bin/activate

3. Install DependenciesBashpip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
pip install diffusers transformers accelerate controlnet_aux pillow matplotlib

🧪 UsageSketch-to-Image (ControlNet)Open Sketch2.0.ipynb.Ensure you have your sketch image ready.The pipeline loads the Canny ControlNet and applies it to your sketch to generate a photo.Logic: The model detects edges in your sketch and uses them as a "map" to constrain the diffusion process.Text-to-ImageOpen text_to_image.ipynb.Enter a fashion-related prompt (e.g., "A high-end silk dress, editorial photography, 8k resolution").The script uses the Stable Diffusion v1.5 UNet to generate an image from pure noise based on your text.

📈 Process SummaryData Preparation: Images are resized to $512 \times 512$ and normalized.Training: ControlNet is fine-tuned on a fashion dataset to learn the relationship between sketches and fabric textures.Inference: Uses Automatic Mixed Precision (AMP) to generate images in seconds.

⚠️ Note on DataThe datasets and model weights (.pth files) are not included in this GitHub repository due to size constraints. You must provide your own data/ directory or download the weights into the models/ folder as specified in the notebooks.