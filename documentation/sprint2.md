## Sprint 2 - Documentation

This project uses a Generative Adversarial Network (GAN) to generate synthetic MRI images. Below is a concise documentation of each function, class, and training configuration, describing the approach, key challenges, and final implementation choices.

---

### Setup and Data Loading

**Device Setup**: 
The project dynamically assigns the device (GPU if available) for computation. Multiple CUDA device checks and environment settings are implemented to optimize memory usage.

**`load_images_from_s3`**:
   - **Purpose**: Loads MRI images from an AWS S3 bucket and applies grayscale, resizing, and tensor transformations.
   - **Challenges**: Efficient in-memory loading of images with `BytesIO` and maintaining manageable memory usage.
   - **Final Solution**: Stacks images as tensors and transfers them directly to the device for efficient use during training.

---

### Core Functions

**`save_generated_images`**:
   - **Purpose**: Generates samples at each epoch to monitor GAN progress. Normalizes images to `[0, 1]` for proper visualization.
   - **Challenges**: Initial visualization issues were resolved by rescaling from `[-1, 1]`.

**`save_models`**:
   - **Purpose**: Saves the model states of the generator and discriminator periodically.
   - **Challenges**: File directory creation needed `os.makedirs()` to avoid errors, ensuring models can be easily saved and reloaded.

**`plot_training_history`**:
   - **Purpose**: Tracks and plots generator and discriminator loss across epochs.
   - **Challenges**: Smoothing issues addressed by standardizing axis ranges.

---

### GAN Architecture

**Generator**:
   - **Purpose**: Maps a latent vector (size: `latent_dim=100`) into a 2D MRI slice with upsampling and convolutional layers.
   - **Challenges**: Matching the target MRI size (200x160) required careful adjustments to upsampling layers.
   - **Final Structure**: Starts with a fully connected layer followed by upsampling blocks, utilizing `BatchNorm2d` for stability.

**Discriminator**:
   - **Purpose**: A convolutional network that classifies input images as real or fake.
   - **Challenges**: Ensuring the correct input size to the final layer required tracking dimensions through downsampling steps.
   - **Final Structure**: Uses `LeakyReLU` and dropout for regularization, and processes images down to a binary classification of authenticity.

---

### Training Pipeline: `train_gan`

**Purpose**: Manages training for both networks over multiple epochs, tracking losses and saving results.

**Key Steps**:
1. **Discriminator Training**: Trains on real and fake images, updating after calculating `real_loss` and `fake_loss`.
2. **Generator Training**: Optimizes the generator to produce realistic images, aiming to fool the discriminator. (WIP)
3. **Accumulated Gradients**: Batch accumulation (`accumulation_steps=8`) mitigates memory limitations.

**Challenges**: Adjusted batch size to fit GPU memory and handled model instability by fine-tuning optimizer parameters and gradient accumulation. (WIP)

**Final Solution**: Trains for a defined number of epochs (500) with periodic image and model checkpoints.

---

### Parameters and Environment

- **Hyperparameters**: `latent_dim=100`, `batch_size=32`, and Adam optimizers with specific learning rates.
- **Memory Management**: Uses `torch.cuda.empty_cache()` and `PYTORCH_CUDA_ALLOC_CONF` to handle GPU memory constraints efficiently.

---
