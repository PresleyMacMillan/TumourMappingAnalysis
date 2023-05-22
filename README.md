# TumourMappingAnalysis
Repository for all code pertaining to the paper Toward Predicting Nanoparticle Distribution in Heterogeneous Tumour Tissues
MATLAB code: 

For steps 1, 3-8 of tumour image processing MATLAB is used
Step 1: .czi conversion to multipage tiff
Step 2: Segment image with Ilastik
Step 3: Macrophage post processing
Step 4: Label macrophages
Step5: Vessel Processing
Step6: Identify and measure vessel features
 	6A: Identify features and extract metadata
     6B: Run analysis script and save vessel data
Step7: Process Nanoparticles
Step8: Identify Nanoparticle Regions
h
STEP 2, 9 - onward use Python3.6.12

Python Processing assumes the following organizatinal structure for images:

General Data Structure - Data folder image strings are hard coded assuming the 
following data folder structure:

1. Top level folder (containing subfolders with all image data)
    2. Tumour folders sorted by nanoparticle size. 
        Nameing convertion: U87-GNP{np_size}nm
        3. Folders sorted by time point.
            Nameing convertion {time in hours}h
            4. Image subfolders. Generated during .czi conversion
                Naming convention: {image_name}
                note: scripts assume image names start with either 'MSC' or 'UT'
                5. Processed image folders
                    - Generated by MATLAB scripts steps 1-8
                    which Relys on having run .czi conversion and having 
                    segmented ilastik images in a 'pre_processing_2022'
                6. Neighbourhood_Analysis_2023
                    

vessel_processing_only_um_2023.py
Run this first on each time point folder 


NP_region_processing_radius_um_2023.py 

    Note:  image names endings are hard coded in get_image_and_data_paths() to 
            correspond to the names as defined in the MATLAB scripts


sphere_sampling_2023.py 

    Loops over folder by default assumes you select the time point folder. 
    Generates spherical samples of desired size and number. 

    When run this script takes a user input for radius size but the script can be 
    easily modified to loop over multiple radii. 

    Note: this step is slow and computationally intensive


index_of_dispersion_calc_um_2023.py 

Calculates index of dispersion, assumes minimum tissue threshold of 10% 

Assumes you specifiy the top folder and that all data follows the folder structure
outlined above


