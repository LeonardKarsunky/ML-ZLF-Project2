# ML Project 2: Ophthalmology Image Registration

# By Leonard Karsunky, Florian Aubert and Zoe Jungi

The following instructions will allow to run the code.

First you open the notebook "ZLF-project-final.ipynb".
In the first cell you have all the included library that you can just run.
In the second cell you find variables that require changes.
Now you need to define the number of patients whose images you want to align (i.e. 5 would be the first 5 patients in the dataset).
You need to put the variable "initial_directory" to the directory that your "ZLF-project-final" is in.
The "output_directory" should be equal to the path of the folder where you want to save the aligned images. All registered images will have the exact same name as before.
"img_src_patch" is the path to get to the folder where the images to align are stored in respect to the location of the script.
You have to define the alignment method. You can choose between 'VOXELMORPH', 'ORB', 'AKAZE' and 'SIFT'. If you do a typo or don't define it, the default choice will be 'SIFT'.
If you choose 'VOXELMORPH', you have to choose which 'centered' images you want to register, since our VoxelMorph method can only register images from one certain kind of centeredness. You can choose from 'LOHN', 'ROHN', 'LMacula' and 'RMacula'. When using vxm, the image will be squared and reduced to 30% of its original size to lower the complexity of the model and allow it to train on this virtual environment.

Next you run the cells with all the helper functions.
If you want further details on the functions you find those in the corresponding mark down cells above the code.

## Main

If you now run the *Main* cell (located below all useful functions), all the images will be extracted, sorted into the combinations of left/right and OHN/macula for every patient and the registered images are saved into your output-folder (which you specify at the top). However, make sure to first run the cells containing align_akaze(), align_orb(), align_sift(), train_voxelmorph() and align_vxm() a couple cells below.

In the Main cell is also where the average mutual information score (i.e. registration distance) for registered images using a given alignment method is calculated and printed with the standard deviation.

For VoxelMorph, the number of epochs and steps per epoch can be changed manually in the train_voxelmorph() function. VoxelMorph will also skip all images that are not the same size as the 'average' image size (here we chose the first image in the dataset).
