# ML-spring_camp_tasks
Task 1: Lattice Physics:
  Overview:
      The project focuses on predicting the two crucial parameters or the functions of variations in fuel pin enrichments for the NuScale US600 fuel assembly type C-01 (NFAC-01). The parameters studied are
  1)Infinite Multiplication Factor (M):
    This measures how efficient the nuclear fuel is at sustaining a chain reaction.
  2)Pin Power Peaking Factor (PPEF):
    Identifies the hottest part of the fuel assembly, critical for preventing damage.
These parameters are affected by the enrichment of the fuel rods, which is the percentage of U-235 in the fuel. The task is to predict these values based on the input data representing the enrichment of 39 fuel rods in one-eighth of the NFAC-01 assembly.

Dataset:
Features: 39 columns, each representing the enrichment of a fuel rod in one-eighth of the NFAC-01 assembly. The values range from 0.7% to 5.0% U-235.
Targets:
M: Infinite Multiplication Factor (Efficiency of chain reaction)
PPPF: Pin Power Peaking Factor (Hottest part of the assembly)
Size: 24,000 instances representing different configurations of fuel enrichment.

The provided dataset is not labelled with the names of the features, thus didnot point out the columns representing the Infinite Multiplication Factor and the Pin Power Peaking Factor.
Identifying the columns representing the Infinite Multiplication Factor and the Pin Power Peaking Factor:
  1)Typical ranges for Infinite multiplication factor in fresh fuel (without poisons or shims) are approximately 1.04 to 1.40. [Taken from Internrt]
    Thus checking out the values in the range, column 0 or the first column perfectly aligns with it, thus it represents the Infinite Multiplication      Factor.
  2)The ranges for PPPF can vary significantly depending on reactor design and operational conditions. In many cases, values can range from 1.2 to         2.0, indicating that some pins may experience up to twice the average power density due to factors such as fuel assembly design, coolant flow          patterns, and neutron flux distribution.
    Thus checking out the values in the range, column 1 or the second column aligns with it, thus it represenst the Pin Power Peaking Factor.

Code explanation:
Data Preprocessing:
The dataset is read from a .csv file using pandas.read_csv() with delim_whitespace=True to handle space-separated values.
The first 1000 instances are taken for training, and features (X_train) and targets (Y_train) are separated.[I considered only first 1000 entries since it became computationally intensive considering the complete dataset on my PC.]
The first 200 insatnces are taken for the testing, and features (X_test) and targets (Y_test) are seperated.
Scaling is applied to the features using StandardScaler to ensure uniformity.
Model Training:
MultiOutputRegressor with RandomForestRegressor is used to predict both M and PPPF.
The data is split into training and test sets using train_test_split from scikit-learn.
Evaluation:
Predictions are evaluated using the Mean Squared Error and R² Score for both parameters.

