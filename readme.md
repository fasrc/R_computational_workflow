# Synthetic Medicare Data for Environmental Health Studies

Authors: Naeem Khoshnevis, Xiao Wu, Danielle Braun   
Email: nkhoshnevis@g.harvard.edu    
Github: https://github.com/Naeemkh   

## Summary

We present example of computational workflow in R. The original workflow and documentations is located [here](https://github.com/NSAPH/synthetic_data). 
In this workflow, we generate public data sets for benchmarking and illustration purposes for air pollution and health studies. In most of these studies, the health care data cannot be shared with the public; as a result, there are no public data sets to be used as benchmark data set for testing the packages or illustrating their functionalities.  CMS has generated synthetic data for the 2008-2010 range for Medicare data. This report uses these data, census, and exposure data to compile the study data set. 

<img src="figures/png/Figure1.png" width="1200">


## Set up project environment

To be able to reproduce the results. You need to download raw data. All data are open to the public. In the entire processing workflow, we keep data (input, output, and cache) and code in separate locations; this has several advantages, including:
- Some input data has been used in several projects; as a result, separating the code and data helps us store the data once. 
- Reduces the chance of submitting data into the version control system. 
  - In the case of public data, this redundantly increases disk usage.
  - In the case of private data, this increases the risk of a data breach. 
- Helps the developers to manage disk spaces easily. For example, one can easily connect the project to an external disk space without changing a character in the code. The following figure shows the relation between the project and data folders. 

<p align="center" width="60%">
    <img width="60%" src="figures/png/project_folder.png">
</p>


Input files are shared [here](https://drive.google.com/drive/folders/1t8x0hQ_oHuuXV_Hr-1l9jpjjaWcry2qw?usp=sharing) for direct download. The following steps represent reproducing the results (Windows is not tested). 

- Step 1: Create a `project_path_info.md` file and add the following fields:

```sh
PROJECT_NAME=your_project_name
PUBLIC_DATA_DIR=path_to_public_data_folder_on_your_system
PRIVATE_DATA_DIR=path_to_private_data_folder_on_your_system
OUTPUT_DATA_DIR=path_to_output_folder_on_your_system
    
```
Please note to include the last empty line. 

- Step 2: Run `initialize_project.sh` (Windows users should skip this step and manually create the soft links. See lines 76-78 of initialize_project.sh)
- Step 3: Copy downloaded files into the public data directory.
- Step 4: Create R conda environment.

  ```s
  conda env create -n r_env -f r_env.yaml
  ```

- Step 5: Activate R conda environment.

  ```s
  conda activate r_env
  ```

- Step 6: Run RStudio 

  In my case, I am using a macOS and the Rstudio application is located in the following path.

  ```s
  /Applications/RStudio.app/Contents/MacOS/RStudio
  ```
- Step 7: Double-check if your conda path is all set.

  Inside RStudio, run:

  ```r
  > R.home()
  ```
  [1] "/Users/[your username]/anaconda3/envs/r_env/lib/R"

  ```r
  > .libPaths()
  ```
  [1] "/Users/[your username]/anaconda3/envs/r_env/lib/R/library"

- Step 8: Navigate to the code folder and run `synthetic_county_2010.Rmd`

- Step 9: A `Study_dataset_2010.csv` file will be created in the `output/results` folder. 

- Done!

