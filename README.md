# BIOSTAT626
## Datasets

The dataset consists of the following files:

- 'training_data.txt': Training dataset

- 'test_data.txt': Testing Dataset

- 'data_dictionary.txt': Introduction of the dataset

- 'features_info.txt': Detailed information provided for each features

## Prerequisites

  - Running Environment: Rstudio
  - 'test_data.txt’
  - 'training_data.txt'

## Libraries

  These libraries are required to install.

  ```R
  library(readr)
  library(dplyr)
  library(tidyr)
  library(caret)
  library(randomForest)
  library(Boruta)
  ```

  

## Instructions

  1. To reproduce the results, open Rstudio and two Rmd files for different task. (e.g. Task1.Rmd, Task2.Rmd), and install the libraries mentioned above.
  2. Just Run the code sequentially, it will perform read data, data preprocessing, feature selection, train model, convert data frame and export data file these steps.
  3. Each Rmd will export one txt file under the format, binary_k5484.txt or multiclass_k5484.txt, depending on which Task you run.