# Ethos_image_challenge_BARATHEONS

To execute our ipynb code to train the Enhanced Super Resolution Generative Adversial Networks (ESRGAN) please follow the below given procedure:

1. Set Up Dependencies:
    Ensure you have the required libraries installed:
      pip install numpy tensorflow pillow scikit-image matplotlib scikit-learn
    Ensure you're using a compatible TensorFlow version. The code uses TensorFlow 2.x and Keras, so install TensorFlow >= 2.0:
      pip install tensorflow==2.8.0
2. Directory Structure:
    The code expects two directories of images: original images and degraded images.
      original_image_dir should contain high-resolution images.
      degraded_image_dir should contain low-resolution/degraded images.
    Both directories should be placed at the specified paths, or update the paths accordingly
      original_image_dir = r'C:\path\to\original_images'
      degraded_image_dir = r'C:\path\to\degraded_images'
3. Image Formats and Preprocessing:
  Images should be in a format that can be opened by PIL (JPEG, PNG, etc.).
  The images will be converted to YCbCr color space, and only the Y channel (luminance) will be used.
  Ensure images have consistent dimensions, or they will be resized to 128x128 by the load_images function.
4. Data Splitting and Reshaping:
  After loading, the images are split into training and validation sets using an 80-20 ratio.
  Images are reshaped to the format (batch_size, 128, 128, 1) to work with the model.
5. Training Precautions:
  The code uses two models: a generator and a discriminator.
  During training, the discriminator is updated to distinguish between real and generated images, while the generator tries to fool the discriminator.
  You may need to adjust the batch_size based on your system's memory. The current batch_size=3 may be small for larger datasets.
6. Checkpoints and Model Saving:
  Model checkpoints will be saved in the checkpoints23 directory after each epoch.
  Ensure this directory exists or is correctly specified, otherwise update the path:
      checkpoint_dir = "checkpoints23"
      os.makedirs(checkpoint_dir, exist_ok=True)
7. Loading Pretrained Models:
  To load pretrained models, make sure the paths to the generator_model.h5 and discriminator_model.h5 are correct:
      generator = load_model(r'C:\path\to\generator_model.h5')
      discriminator = load_model(r'C:\path\to\discriminator_model.h5')
8. Evaluation Metrics (PSNR & SSIM):
      The script calculates PSNR and SSIM for quality evaluation of generated images.
      Ensure that the comparison between validation and generated images is done using the appropriate channels (Y channel) as the model operates on 
      grayscale.
9. Plotting:
  The code uses matplotlib to plot the results. Ensure you have a display or Jupyter environment to view the images.


Final Checklist Before Execution:
    Dependencies: Install the required packages.
    Paths: Ensure the dataset paths, checkpoint paths, and model save paths are correct.
    Environment: Use TensorFlow GPU if available for faster training.
    Data: Ensure consistent image formats and sizes.

