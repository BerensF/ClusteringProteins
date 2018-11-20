# ComparingProteins

Compares proteins by there isosufaces and clusters them.

Call:
```bash
./CompareIsosurfaces.R _parameterfile_
```

## Parameterfile
The _parameterfile_ contains following parameters:

| Name                        | Parameter                                      | Description                                                                                           |
|-----------------------------|------------------------------------------------|-------------------------------------------------------------------------------------------------------|
| PathToData                  | .../ProteinComp/Input/                         | path to the protein data, every protein in it own folder that contain the .dx file                    |
| PathToOutput                | .../ProteinComp/Output/                        | path to the Outputfolder                                                                              |
| n                           | 100                                            | How many points will be selected in every round, the runtime is in O(m n^2)                           |
| m                           | 500                                            | How often the calculation will be done, the runtime is in O(m n^2)                                    |
| PathToCPProgram     | .../ComparingProteins/LowerBounds/FirstLowerBound/main  | path of to the Cpp program on your machine                                                            |
| PathToRProgram     | .../ComparingProteins/EMDandClustering/LowerBound  | path of to the R program on your machine                                                            |

Comments can be added by a '#' in the parameterfile. The parametername and parameter have to be seperated by a '='

## Folderstructure

```
└─── ProteinComp
│   └─── Input
│       │   └───  Prot01
│       │         │   Prot01.dx
│       │         │   ...
│       │   └───  Prot02
│       │         │   Prot02.dx
│       │         │   ...
│       │        ....
│       │   └───  Protk
│   └─── Output
│       │   └───  Prot01_negative_n
│       │         │   Prot01_Prot01_negative_n
│       │         │   Prot01_Prot02_negative_n
│       │         │   ...
│       │         │   Prot01_Protk_negative_n
│       │   └───  Prot01_positive_n
│       │         │   Prot01_Prot01_positive_n
│       │         │   Prot01_Prot02_positive_n
│       │         │   ...
│       │         │   Prot01_Protk_positive_n
│       │   └───  Prot02_negative_n
│       │         │   Prot02_Prot02_negative_n
│       │         │   Prot02_Prot03_negative_n
│       │         │   ...
│       │         │   Prot02_Protk_negative_n
│       │        ....
│       │   └───  Protk_positive_n
│       │         │   Protk_Protk_positive_n
|       |  ListofEMD_negative_n
|       |  ListofEMD_positive_n
|       |  Dendrogram_UPGMA_Max
|       |  Dendrogram_UPGMA_Mean
|       |  Dendrogram_UPGMA_Neg
|       |  Dendrogram_UPGMA_Pos


## Lower Bounds

There are three lower bounds of the Gromov-Wasserstein distance in this repositories. The first lower bound has a time complexity of O(n^2) the second O(n^4) and the third O(n^5). It is recommended to use the first lower bound, since it is much fuster than the other two. For more details see "Quantitative comparison of protein isosurfaces with approximated Gromov-Wasserstein-distance" from Felix Berens or "Gromov-Wasserstein Distances and the Metric Approach  to  Object  Matching" from Facundo Mémoli.
