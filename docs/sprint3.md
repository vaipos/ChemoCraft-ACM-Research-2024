# Sprint 3 (Theo)

The goal is to train the GAN model and start tweaking its properties and evaluate the output.

* New library s3fs to more easily navigate dataset
* Rename 1.png -> 001.png on S3 to keep in alphabetical order 
    - Wasted time trying to make async work for the renaming program
* Created an iterator class that returns a list of parsed slices from the next folder
    - Wasted time trying to animate through brain slices with matplotlib in Jupyter to make sure the iterator loads them correctly, this proved difficult. After manually looking at slices it looks right
* Trying to change sample code to be able to train
    - Changed to Conv3D, idea is to input all 155 slices at once, effectively meaning batch size = 1
    - Dimensions of the model are throwing errors
    - Need to research Keras to move forward

