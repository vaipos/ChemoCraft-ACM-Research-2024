# Sprint 1: Data Preprocessing (Theo)

This sprint was very straightforward. The goal was to be able to create a directory containing directories of PNG files of the five sample brains, preprocessed and ready to use with a GAN model.

### Development

First, a new method `save_nii_from_s3()` was created, modeled after `render_nii_from_s3()`. Instead of selecting the middle slice of the 3D brain image, it iterates each slice.

The first step of development was to save each slice as a PNG file. A local directory is specified as a global variable, and within it a directory with the name of the `.nii` file (without the extension) is created. Within this subdirectory, a PNG of each slice is saved using `matplotlib.image`, which had to be imported.

Next, to continue with preprocessing, each image slice should be saved in grayscale, and cropped. Suitable cropping offsets were determined, set as global variables, and utilized by taking an array slice of the image data. Grayscale conversion was easily accomplished by adding the keyword argument `cmap='gray'` to `matplotlib.image`'s `imsave()`.

### Moving Forward

The new `save_nii_from_s3()` can be used on the rest of the dataset once accessible, to create images for training a GAN model. The only consideration being if the crop is too large for other images in the dataset, however, this could be easily fixed by changing the offset variables.
