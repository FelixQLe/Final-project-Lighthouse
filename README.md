# Final-project-Lighthouse
Capstone DATA SCIENCE Project with Enzyme Stability Prediction
## Project&Goals
  In Biology Industry, enzymes are widely-use protein. However, many enzymes are only marginally stable,  at a certain melting point (temperature level), enzymes's performance starts to drop, for this reason Biologists mutate enzymes to increase the melting point. However mutations is not alway going better, it might increase or decrease the melting point, and there are hundreds of thousands enzymes with hundreds of thousands ways to mutate proteins. Able to predict these mutant proteins's melting points will help saving a lots works in using these enzymes and their mutant group
 ![Screen Shot 2022-10-13 at 11 19 23 AM](https://user-images.githubusercontent.com/93171100/196218314-4af9324f-e4c9-473c-a98b-39aeb2e31119.png)
## Protein propeties
  Protein sequence is a sequence of letter, every letter represent Amino acid(3 letter).

![phpGrMDec](https://user-images.githubusercontent.com/93171100/196220798-3ac42c17-3650-4755-b51d-db9006aeb624.png)
 
### Mutations

There are three type of mutations, replace, delete and insertion. There is no doubt that muations affect melting point(i.e. target tm, melting temperature)
- reference: https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8150157/

 ![Screen Shot 2022-10-13 at 1 06 09 AM](https://user-images.githubusercontent.com/93171100/196219026-b6c2fd56-8fa0-41cf-b23e-637bc65d8b9c.png)
 
  The image above is the example of replace mutation in protein, when we replace Amino acid with other Amino acids. At the begining of protein sequence, we have mutant pair F and Y, then mutant pair of Y and H, and so on. The color of these mutant pairs indicate the significance of it's contribution to alteration to origin protein. Light green mutant pair is more significant than dark green mutant pair.
  
  Second type is insertion, when we insert new Amino acid into protein sequence. Significance of these type is measured as same as above
  
![Screen Shot 2022-10-13 at 12 56 57 AM](https://user-images.githubusercontent.com/93171100/196219043-3f0ee1eb-dd70-4c12-9f0f-aa10e304498b.png)

Third type is delete, two Amino acids (RR) are deleted from origin protein.

![Screen Shot 2022-10-17 at 12 16 11 PM](https://user-images.githubusercontent.com/93171100/196229473-7b1db53f-d8ff-4259-b139-c16b17b6aaf6.png)

### Amino Acids
  Every Amino Acid has their Molecular weight, residue weight, and SaSa (Solvent-accessible surface area) has always been considered as a decisive factor in protein folding and stability studies. It is defined as the surface characterized around a protein by a hypothetical centre of a solvent sphere with the van der Waals contact surface of the molecule.
  
<img width="305" alt="Screen Shot 2022-09-23 at 4 50 54 PM" src="https://user-images.githubusercontent.com/93171100/196231409-3faf4668-4bfd-4024-a237-d7126dd09f7f.png">

## Major Requirements

I have spent couple of days to study Enzymes properties, Amino Acid properties and Bio Python Package such as Levenshtein and Blosum80

## Project workflow
![Screen Shot 2022-10-12 at 11 20 09 AM](https://user-images.githubusercontent.com/93171100/196233837-5685a5ba-c44a-49f0-a5e7-e65eeec279a9.png)

## Base Model

First model, I treated the problem as text problem, and used tf-df-vectorizor to decode every letter in every protein sequence

* Result

    As I expected the result is not good.
    
    !![Screen Shot 2022-10-13 at 1 27 09 AM](https://user-images.githubusercontent.com/93171100/211712195-6cd24dba-db49-4889-be0b-98dbc96a498b.png)

## First Improvement Model

For first improvement model, I started to use protein propeties mentioned above, this first improvement model proved the usefulness of these properties.
I was able to improve 14% higher. However, my model is overfited 

![Screen Shot 2022-10-12 at 11 50 14 AM](https://user-images.githubusercontent.com/93171100/196240846-804a326b-88ae-4c99-9d7b-a56f2dad5f8e.png)

## Final Improvement Model(will update the results, please stay tuned)
In the first improvement model, I was able to improve 14% higher. However, my model is overfited. The reason is our dataset is smalll and we have a lots features, means high variance and will represent the data set accurately but lead to overfitting.
For that reason I will improve the model by the following steps:
- Use extra protein properties ddG and b_factor score from extra source
- Use one significant mutation pair between two string rather than all mutations and calculate it’s matrix score using Blossom80 python package
- Tuning hyperparameters
- Ensemble modeling(perhaps)

