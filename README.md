# IE-Project
Ie project code
Project Overview

The project proposes an AI-driven video compression and restoration pipeline designed for lecture videos.
It reduces bandwidth and storage by removing frames (downsampling) and later reconstructs missing frames using a generative diffusion-based approach.

The main pipeline integrates:

Flow-Conditional Video Generation (FCVG)

Stable Video Diffusion (SVD)

Pose-based and structural conditioning (DW-Pose, GlueStick)

Optical flow, Laplacian edges, and hand-region maps for motion consistency

⚙️ Code Structure
ie_project/

Main implementation of the core pipeline:

Frame Extraction – Splits downsampled videos into frames.

Condition Generation – Generates multiple conditioning signals:

Pose maps (DW-Pose)

Optical Flow (Farneback)

Hand-region masks (MediaPipe)

Laplacian edge maps

GlueStick base conditioning

Frame Reconstruction – Combines all conditioning cues using Stable Video Diffusion + ControlNeXt to generate interpolated frames.

Video Export – Combines all generated frames back into a restored high-FPS video.

novelty_experiment/

Contains the novel contribution of the project — to speed up the generation process to make our project realtime

🧩 Usage

Downsample the input video
Place your input video inside /uploads.

Run the main pipeline

python ie_project/downtoupconditioned.py --input <path_to_video> --output <output_path> --interp_frames <num_missing_frames>


Output
The restored (upsampled) video will be saved under /outputs.

📚 Requirements

Python 3.10+

PyTorch

Diffusers

OpenCV

MediaPipe

Transformers

Pyngrok (for remote server testing)

Flask / Streamlit (for demo UI)
