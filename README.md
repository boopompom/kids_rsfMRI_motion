# kids_rsfMRI_motion

Requirements: 

Python 2.7
matplotlib
numpy
pandas
scikit-learn
scipy

- DATA.tar.gz contains the resting state data used in this project.
- Phenotypic_V1_0b_preprocessed1.csv contains the necessary phenotype data.
- conda_env_py2.yml can be used to create a conda environment that approximates the one used for this project.

## Split-half reliability

- abide_motion_wrapper.py performs an analysis for a single set of parameters.
- SgeAbideMotion.sh and loop_abide_motion_qsub.sh were used to parallelize the above script over many parameter combinations on a Sun Grid Engine computing cluster.
- plotting_data.ipynb plots the results.

## Predictive reliability

- runSVCMotionTest.py for each iteration specified, creates a classifier for diagnosis on one half of a data set and uses that classifier to predict diagnosis in the other half, saving out the classification accuracy and model.  
- create_fc_fisher_z_csv_file.py helper function to create data used in the above.
- SgeAbideMotionCV_UO.sh and loop_abide_motion_qsub_array_UO.sh (along with abide_motion_parameters.tsv) were used to run the above python script for different combinations of parameters on a Sun Grid Engine computing cluster.
- plot_svc_motion_comparison.md plots the data generated by the above python script and documents the code used to produce those plots (in plot_svc_motion_comparison.R).
- cv_output contains all classification accuracy results.
- cv_models contains all classifier data. 

## Data file splits

Some data files were split using `split`, and so have filenames ending in "a[abcd...]". To join these files you can do `cat FILENAME.tar.gz* > FILENAME.tar.gz`.
