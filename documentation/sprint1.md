## Function Documentation

### `render_nii_from_s3`

1. **Approach:** I set up `render_nii_from_s3` to fetch `.nii` files from S3, load them as temporary files, and process them with `nibabel`. Using a temporary file was essential because `nibabel` requires file-based data.

2. **Challenges and Solutions:**
   - **Cropping Dimensions:** Determining the right crop dimensions took small amounts of trial and error, especially with files of varying shapes. I experimented with different parameters to get a consistent crop size that centers on relevant areas of each slice.
   - **Iterating Through the Z-Dimension:** Initially, handling each 2D slice in a 3D volume was tricky. By iterating over the z-dimension, I was able to handle the depth of each scan and ensure each slice was processed individually.
   - **Image Storage:** Storing the images as PNGs had some issues for where i wanted to store them. Also, i had initally though the PNG slices were faulty when i saw some images were pure black 
   - **Consolidating Functions:** I then decided to break up code into smaller functions like `plot_slice` and `savePNG` to help with code readibility

3. **Conclusion:** This function now smoothly integrates file retrieval, temporary storage, cropping, and saves each slice individually through calls to `savePNG` and `plot_slice`.

### `plot_slice`

1. **Approach:** To verify the image cropping, this function crops and plots a specific MRI slice using `matplotlib`.

2. **Challenges and Solutions:** (Technically none since it was started code)

3. **Conclusion:** This function allows for viewing of slices and ensures that data preprocessing steps are correctly applied.

### `savePNG`

1. **Approach:** This function saves each MRI slice as a PNG image, organized in directories by `TrainingCount` and `ScanType` parsed from `filename`.

2. **Challenges and Solutions:**
   - **Path Setup:** Managing paths for each slice required consolidating the directory creation, so I used `os.makedirs(slice_path, exist_ok=True)` (may not work for MacOS, who knows!).
   - **Error Handling:** A try-except block helps address potential file system issues during directory creation or saving, ensuring that errors don’t halt processing.

3. **Conclusion:** `savePNG` iterates over each slice, applies cropping, and saves each image (if it doesnt already exist).
