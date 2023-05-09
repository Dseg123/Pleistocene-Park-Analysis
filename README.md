# Pleistocene-Park-Analysis
Repository of code for modelling the species distributions of megafauna in Pleistocene Park and predicting the future impact of the park on atmospheric carbon emissions, initially for use in the final paper of Princeton's WRI 117: Sustainable Futures.

# Navigation
The primary code is contained within Jupyter notebooks get_clim.ipynb, get_species.ipynb, and analyze_species.ipynb. 

Firstly, the PHYLACINE_Data and WorldClim_data folders contain raw species range and climate data used to train the model.

get_clim and get_species generate data contained within the MaxentInputs folder, which is too large to be included in Github and thus has been stored separately in the public Google Drive folder at: https://drive.google.com/drive/folders/1mh9FjAmoFZY7SJYtfiwQe44nu6kjAC2R?usp=share_link. This folder includes the background climate data (background.csv), current and present natural ranges of the focal species (Species.csv and Species_current.csv), population densities of focal species (densities.csv), and samples-with-data files of the focal species (Species_swd.csv). The swd files are concatenated in one file combined_swd.csv which is used in the Maxent model. 

After running Maxent, the results were placed in the MaxentResults folder, categorized by species. The most important results are the Species.html file which contains model data such as AUC and variable contributions, and the Species_backgroundPredictions.csv which contains cloglog outputs at each background point used to estimate total populations. 

The file analyze.ipynb was used to visualize the resulting distributions and compute population estimates for each species from the backgroundPredictions files. It was used to create most of the figures in the paper, including the final graph of carbon emissions for each species.

The two files Pleistocene_Park_System_Dynamics.mdl and Pleistocene_Park_System_Dynamics_Lucas.mdl contain the AnyLogic model code used to generate our model and Lucas & Enos's model respectively. The folder SysDynResults contains txt files for each condition's carbon emission trajectory, as obtained from the above models.

# Running the code
At a high level, one might run the code by first generating species and climate datasets by running get_clim.ipynb and then get_species.ipynb with each focal species. Then one would run Maxent with the combined_swd.csv and background.csv files as inputs, alongside the settings in Appendix 2. Next one would run the analyze.ipynb file to compute population estimates for each species. Finally, one would modify the Pleistocene_Park_System_Dynamics.mdl file by altering the initial value of the Megafauna variable, then run the model in AnyLogic (with possible data logs added), and plot the resulting datasets with code akin to analyze.ipynb. This was the process used to generate the figures in the paper, and it is easy enough to replicate, though some slight changes may have to be made due to the different file structure.
