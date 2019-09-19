# CANLab-Multivariate-Scripts
Pipeline to conduct Multivoxel Pattern Analysis (MVPA) or Represetational Similarity Analysis (RSA) on functional MRI data. Requires MATLAB, [SPM](https://www.fil.ion.ucl.ac.uk/spm/), and [CoSMoMVPA package](http://www.cosmomvpa.org/).


```createParams.m```
Creates parameter MAT file with all information
Requires AFNI for mask transformation from standard space

```estimateModel.m```
Estimates single trial model specified by ```SpecifyModel.m```
Requires SPM

```runMVPAClassification.m```
Runs MVPA within singular ROIs or Searchlight within mask provided by user
Requires CoSMoMVPA
SVM output saved to CSV & MAT files; Searchlight saved as weighted .nii file

```runRSA.m```
Runs RSA within singular ROIs, Searchlight within mask provided by user, or ERS analyses
Requires CoSMoMVPA
Output saved to CSV & MAT files; Searchlight saved as weighted .nii file

```specifyModel.m```
Creates single trial models for given functional task/runs
Requires behavioral file to load and tag trial type information

## Running the pipeline
Below is order of scripts to be run in the pipeline assuming a new data project:


1. ```createParams.m```          - Dialog will come up querying if Specify/Estimate has been run. Select 'No' and a temporary params file will be created to be used for Specify & Estimate scripts (```specify_AnalysisName_model_params.mat```)
2. ```specifyModel.m```          - Run using ```specify_model_params.mat``` as input.
3. ```estimateModel.m```         - Run using ```specify_model_params.mat``` as input.
4. ```createParams.m```          - Rerun choosing 'Yes' at Specify/Estimate question. File ```specify_model_params.mat``` will be deleted. Provide input to addition dialog boxes as needed.
5. ```eunMVPAClassification.m``` - Perform MVPA classification using final params file created from ```createParams.m``` script (e.g. ```params_AnalysisName_Condition1_Condtion2.mat```)



See 'publication' for more information
