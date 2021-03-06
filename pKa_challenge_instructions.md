# SAMPL6 pKa Challenge Instructions

Challenge timeframe: Oct 25, 2017 to Jan 10, 2018  

This challenge consists of predicting microscopic and macroscopic acid dissociation constants (pKas) of 24 small organic molecules. 
These fragment-like small molecules are selected for their similarity to kinase inhibitors and for experimental tractability. 
Our aim is to evaluate how well current pKa prediction methods perform with drug fragment-like molecules through blind predictions.

Three formats of pKa prediction results will be evaluated:
1. microscopic pKa values and related microstates
2. microstate populations as a function of pH
3. macroscopic pKa values

The following subsections describe the molecules included in this challenge, the experimental conditions and measurements, the quantities to be predicted, and how prediction results must be submitted.

## On the concept of microscopic and macropscopic pKas
In molecules with multiple titratable groups, the protonation state of one group can affect the proton dissociation propensity of another functional group. 
In such cases, the **microscopic pKa** refers to the pKa of deprotonation of a single titratable group while all the other titratable and tautomerizable functional groups of the same molecule are held fixed. Different protonation states and tautomer combinations constitute different microstates. 
The **macroscopic pKa** defines the acid dissociation constant related to the loss of a proton from a molecule regardless of which functional group the proton is dissociating from, so it doesn't necessarily convey structural information.

For a molecule with only one protonatable group, the microscopic pKa is always equal to the macroscopic pKa. 
But for a molecule with multiple titratable groups, throughout a titration from acidic to basic pH, the deprotonation of some functional groups can take place almost at the same time. 
Then the experimentally measured macroscopic pKa will have contributions from multiple microscopic pKas with similar values (i.e. acid dissociation of multiple microstates). 
Cysteine provides an example of this behaviour with its two macroscopic pKas observable by spectrophotometric or potentiometric pKa measurement experiments.
While 4 microscopic pKas can be defined for cysteine, experimentally observed pKas can't be assigned to individual functional groups directly and requires more advanced techniques such as NMR.

On the other hand, when there is a large difference between microscopic pKas of a molecule, the proton dissociations won't overlap and macroscopic pKas observed by experiments can be assigned to individual titratable groups. 
The pKa values of glycine provide a good example of this scenario.

For better clarity on the concept of microscopic and macroscopic pKas refer to:
1. Darvey, I.G. (1995). The assignment of pKa values to functional groups in amino acids (Wiley Online Library).
2. Bodner, G.M. (1986). Assigning the pKa’s of polyprotic acids. J. Chem. Educ 63, 246.
3. Murray, R. (1995). Microscopic Equilibria. Analytical Chemistry 67, 462a – 462a.

## 24 small molecules are included in the pKa challenge
![pKa_challenge_small_molecules](images/pKa_challenge_small_molecules.jpg)
A list of SAMPL6 pKa challenge small molecules canonical isomeric SMILES and molecule IDs can be found here: [/physical_properties/pKa/molecule_ID_and_SMILES.csv](physical_properties/pKa/molecule_ID_and_SMILES.csv). 
Counterions, where present in solid formulations (see experimental details below), were included in canonical isomeric SMILES for the sake of completeness, although no significant effect is expected from the presence of chloride counterions as experiments were conducted in ionic-strength adjusted medium with KCl.

## Experimental details
pKa measurements were collected using spectrophotometric pKa measurements with a Sirius T3 instrument by Mehtap Isik from the Chodera Lab at MSKCC with the support of the Merck Rahway, Preformulation Department, especially Dorothy Levorse, Timothy Rhodes and Brad Sherborne. 

Small molecules were purchased in powder form. 
10 mg/ml DMSO solutions were prepared and used as stock solutions for the preparation of samples, where 1-5 uL of 10 mg/ml DMSO stock solution is diluted in 1.5 mL ionic-strength adjusted water (0.15 M KCl). 
pH titrations with acid (0.5 M HCl, 0.15 M KCl) and base (0.5 M KOH, 0.15 M KCl) and cosolvent addition (80% methanol, 0.15 M KCl) were performed in an automated fashion with with a [Sirius T3 instrument (Sirius Analytical)](http://www.sirius-analytical.com/products/t3).

[The UV-metric pKa measurement protocol of the Sirius T3](http://www.sirius-analytical.com/science/pka) measures the change in multiwavelength absorbance in the 250-450 nm UV region of the spectrum while the pH is titrated between pH 1.8 and 12.2 to evaluate pKas[1,2].
A protonation state change of titratable sites near chromophores will modulate the UV absorbance spectra of these chromophores, allowing populations of distinct UV-active species to be resolved as a function of pH. 
To do this, basis spectra are identified and populations extracted via analysis of the pH-dependent multi-wavelength absorbance.
The number of pKas is determined based on the quality of fit between experimental and modeled microstate pH-dependent populations. 

This method is capable of measuring pKas between 2 and 12 when protonatable groups are at most 4-5 atoms away from chromophores such that a change in protonation state alters the absorbance spectrum of the chromophore. 
We have selected compounds where titratable groups are close to potential chromophores (generally aromatic ring systems), but it is possible that our experimental results will not detect the titration of certain cites (and will thereby neglect the pKa of those sites) if a titratable group is not proximal to a UV-chromophore.  

pKa measurements of soluble compounds were performed in ionic-strength adjusted water with 0.15 M KCl. 
Visual inspection of samples and inspection of UV spectra at 500-600 nm was used to verify no detectable precipitation occurred during the course of measurement. 
For compounds with insufficient solubility to accurately determine a pKa directly in a UV-metric titration,
a cosolvent protocol was used in which three UV-metric titrations were performed in different cosolvent:water
ratios (typically 30%, 40%, and 50% methanol) and the Yasuda-Shedlovsky extrapolation method[3] was used
to estimate the pKa at 0% cosolvent.

Three replicate pKa measurements were made for all compounds at room temperature (25°C). 
Replicate measurements were set up from the same compound stock solutions (~10 mg/ml in DMSO) and independent aliquotes were taken to prepare samples for Sirius T3 titration.
Multiwavelength absorbance analysis on thw Sirius T3 allows for very good resolution of pKas, but it is important to note that this method produces estimates of macroscopic pKas.
If multiple microscopic pKas have close pKa values and overlapping changes in UV absorbance spectra associated with protonation/deprotonaton event, the spectral analysis could produce a single macroscopic pKa that represents an aggregation of multiple microscopic pKas.


[1] Tam, K.Y., and Takács-Novák, K. (2001). Multi-wavelength spectrophotometric determination of acid dissociation constants: a validation study. Analytica Chimica Acta 434, 157–167.  
[2] Allen, R.I., Box, K.J., Comer, J.E.A., Peake, C., and Tam, K.Y. (1998). Multiwavelength spectrophotometric determination of acid dissociation constants of ionizable drugs. Journal of Pharmaceutical and Biomedical Analysis 17, 699–712.  
[3] Avdeef, A., Box, K.J., Comer, J.E.A., Gilges, M., Hadley, M., Hibbert, C., Patterson, W., and Tam, K.Y. (1999). PH-metric logP 11. pKa determination of water-insoluble drugs in organic solvent–water mixtures. Journal of Pharmaceutical and Biomedical Analysis 20, 631–641.  


## Due Date

Your predictions must be uploaded on the D3R SAMPL6 web-page by January 10, 2018. 
The experimental results will be released immediately after the challenge closes. 
You must use the provided templates to upload your predictions to the [SAMPL website](https://drugdesigndata.org/about/sampl6). Additional information on using these templates is provided below.

## Computational prediction methods

You may use any method(s) you like to generate your predictions; e.g., molecular mechanics or quantum mechanics based methods, QSPR, empirical pKa prediction tools etc.

## Instructions and Submission Templates
Three types of predictions will be accepted. 
Participants are encouraged to submit their results in all or multiple submission types if their prediction methods allow it.
Prediction template files can be found in [physical_properties/pKa/submission_templates](/physical_properties/pKa/submission_templates/) directory.

#### Prediction Type I - microscopic pKas and related microstates
Predicting microscopic pKas and related microstate structures. 
Different protonation states and tautomer combinations constitute different microstates. 
- Fill one `typeI_microscopic_pKas_and_microstates.csv` template for all molecules predicted with one method. You may submit predictions from multiple methods, but you should fill a separate template file for each different method. 
- For each molecule, report as many microscopic pKas as your method predicts.
- Record the pair of microstates IDs of microstate structures pairs (protonated HA and deprotonated A) associated with each microscopic pKa. To determine the microstate ID for your predicted structure, check the csv files and spreadsheets in [SAMPL6/physical_properties/pKa/microstates](physical_properties/pKa/microstates) that list microscopic species.
- If your predicted structure is not included in the list, contact us to make a request for new microstate. See more details in the section below ("A warning about enumerated microstates and requesting the missing microstates").
- Report microscopic pKa values to two decimal places (e.g. 10.71).
- Reporting the standard error of the mean (SEM) is optional, but if reported, two decimal places should be provided (e.g. 1.02).
- For values which you don't have an estimate, leave that cell of the csv table empty.

#### Prediction Type II - microstate populations as a function of pH
Predicting the fractional microstate populations between pH interval 2 to 12 in 0.1 pH increments.

- Fill one `typeII_microstate_fractional_populations.csv` template file for all molecules and microstates predicted with one method. You may submit predictions from multiple methods, but you should fill a separate template file for each different method.
- For each molecule, report as many microstates as your method predicts.
- To determine the microstate ID for your predicted microstate populations, check the csv files and spreadsheets in [SAMPL6/physical_properties/pKa/microstates](physical_properties/pKa/microstates) that list microscopic species.
- If your predicted structure is not included in the list, contact us to make a request for new microstate. See more details in the section below ("A warning about enumerated microstates and requesting the missing microstates").
- For each pH, report the *natural logarithm* of the fractional microstate populations in scientific notation with three decimals of precision (e.g., 1.02e-4).
e.g. For a molecule with only two possible microstates A and B `ln(fractional microstate population) = ln(N_A/(N_A+N_B))` where `N_A` and `N_B` represent percentage of microstate populations of A and B.   
At a pH where 90.0% of the molecules are in microstate B and 10.0% of molecules are in state A  `ln(fractional microstate A population) = ln(0.100/(0.100+0.900)) = -2.30e0`.  
- If your estimate of `fractional microstate population` is 0, thus `ln(fractional microstate population) = ln(0)`, report as `-infinity`, but note that attempting to resolve the log-population of low-population states is important for some of the evaluation metrics.
- Do not report SEM in this submission type in the "Prediction" section of type II submission template. It is optional to report uncertainty estimates in "Methods" section, but we do not plan to analyze uncertainty estimates for this submission type.
- For pH values or microstates which you don't have an estimate, leave that cell or line of the csv table empty.

#### Prediction Type III - macroscopic pKas
Predicting the value of  macroscopic pKas between 2 and 12.
- Fill one `typeIII_macroscopic_pKas.csv` template file for all predicted molecules with one method. You may submit predictions from multiple methods, but you should fill a separate template file for each different method.
- For each molecule, report as many macroscopic pKas as your method predicts. For each macroscopic pKa create a new line that starts with molecule ID as identifier.
- Report pKa values to two decimal places (e.g. 10.71).
- Reporting the standard error of the mean (SEM) is optional and encouraged. If it is reported, SEM should be reported to two decimal places (e.g. 1.02).
- For values for which you don't have an estimate, leave that cell of the csv table empty.

## A warning about enumerated microstates and requesting the missing microstates

A list of microstates and microstate IDs were generated for each molecule to aid parsing of submissions. 
The enumerated list of microstates was not created with the intent to guide computational predictions. 
It is possible that some relevant microscopic species are missing from these lists. 
If your predicted microstate is not already included in the microstates list, contact Mehtap Isik (mehtap.isik@choderalab.org). 
Please send us a 2D structure depiction and canonical isomeric SMILES of your proposed microstate. 
We will assign a unique microstate ID and include it in the analysis.  
Newly added microstates will also be shared with participants and microstates lists in this repository will be updated.

Please do not create a microstate ID yourself. 
It is important that challenge organizers assign unique microstate IDs and keep track.  

### Updates on microstates lists

Microstate SMILES strings and microstate IDs can be found in [physical_properties/pKa/microstates/](physical_properties/pKa/microstates/) directory. 
Due to replicate and missing microstates present in the first release of microstate lists, we have updated `SMXX_microstates.csv` files with necessary corrections in Version 1.4 of this repository. 
The main correction of this update was the removal of resonance structures that were causing dublicate representation of same microstates. 
We have also added new microstates suggested by participants.
Newly added microstates were assigned unique microstate IDs, as recorded in `SMXX_microstates.csv` files.
Deprecated microstates were removed from `SMXX_microstates.csv` files.  Deprecated microstates and their microstate IDs were listed in `SMXX_microstates_deprecated.csv` files with "deprecated" note in the "remarks" column.

## Submission of multiple predictions

Some participants use SAMPL to help evaluate various computational methods. 
To accommodate this, multiple prediction sets from a single research group or company are allowed, even for the same type of predictions if they are made by different methods. If you would like to submit predictions from multiple methods, you should fill a separate submission template files for each different method. See "Uploading your predictions" section below for requirements on how to name submission files.

## Uploading your predictions

D3R is currently outfitting the SAMPL6 page with the ability to accept your uploaded predictions. 
As soon as this is ready, you may upload your predictions. 
If you want to upload more than one type of predictions (see description of three pKa prediction types above) or a different set of predictions (same type but generated by different methods), each must be uploaded as a separate file. 
Please use the template provided, as the predictions will be parsed and analyzed with automated scripts. 
Please include all predictions made with same method and same submission type in one file. 

We encourage submitting predictions in all three formats and for all 24 molecules when possible. 
Incomplete submissions - such as for a subset of compounds - will also be accepted, but will not necessarily be evaluated together with the rest of the submissions. 
However, we would emphasize that omission of SEM estimates will not cause a submission to be regarded as incomplete, though we highly encourage including such estimates.

Names of the prediction files must begin with the name of the submission type (i.e., typeIII), and your name and must end with an integer indicating set of prediction. 
For example, if you want to submit one prediction file for type III prediction (macroscopic pKas), you would name it `typeIII-myname-1.csv`, where myname is arbitrary text of your choice. 
If you submit two prediction files of the same submission type, you would name them `typeIII-myname-1.txt` and `typeIII-myname-2.txt`.

The file will be machine parsed, so correct formatting is essential.  Files with the wrong format will not be accepted.

Lines beginning with a hash-tag (#) may be included as comments. 
These and blank lines will be ignored.

The file must contain the following four components in the following order: your predictions, a name for your computational protocol, a list of the major software packages used, and a long-form methods description. 
Each of these components must begin with a line containing only the corresponding keyword: `Predictions:`, `Name:`, `Software:`, and `Method:`, as illustrated in the example files. 

Example submission files can be found in [physical_properties/pKa/example_submission_files/](physical_properties/pKa/example_submission_files/) directory to illustrate expected format when filling submission templates of the pKa challenge.

More detailed instructions will be provided on the challenge submission site on the D3R website.  

## Evaluation strategy for computational pKa predictions

Macroscopic pKa predictions will be directly compared to experimental pKa measurements. 
Microscopic pKas and predicted microstates will be evaluated by comparison to each other and how well they recapitulate experimental macroscopic pKas, as well as pKa predictions of reference calculations.

## Anonymous versus public participation

When you upload your submission, you will have the option of having it treated anonymously. 
Anonymous submission means that we may report on your predictions and methods, but not your identity. 
Public participants means we may also include identifying information.
Please note that, although we will work to protect the identity of anonymous participants, we cannot make any guarantees. 
You may use the D3R website to change your submission’s anonymous/public status until the challenge has closed. 
However, after the challenge has closed, the anonymous/public status can no longer be changed.

## SAMPL6 workshop February 22-23, 2018

Participants are invited to share and discuss their results, as well as the D3R and SAMPL projects more broadly, at the second in-person D3R and SAMPL workshop, which is scheduled for February 22-23, 2018, at UC San Diego, La Jolla, CA. 
Note that the workshop immediately follows the Biophysical Society National Meeting in San Francisco.

## Files provided
- `/physical_properties/pKa/molecule_ID_and_SMILES.csv` - CSV file that indicates SAMPL6 pKa challenge molecule IDs and canonical isomeric SMILES.
- `/physical_properties/pKa/microstates/` - This directory contains files that list of microstate IDs and canonical isomeric SMILES of microstates. Files are separated by molecule ID.
- `/physical_properties/pKa/submission_templates/` - Empty prediction submission template files are located here.
- `/physical_properties/pKa/example_submission_files/` - This directory contains example submission files filled with random values to illustrate expected format.

## Problems, questions and contact

If you notice any issues with any of these files, please contact us via the GitHub issue tracker. 
You are also strongly advised to both sign up for the SAMPL6 e-mail list via the D3R site and sign up for notifications on this GitHub repository in case we have updates.

Please feel free to contact us if you notice any errors in the information provided or have questions about SAMPL6; please use the issue tracker connected with this repository, or use our e-mail: samplchallenge@gmail.com. 
For specific questions about pKa challenge, use the following email: mehtap.isik@choderalab.org.
