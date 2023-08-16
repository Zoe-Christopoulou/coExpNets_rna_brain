Αρχικά συλλέξαμε το σετ δεδομένων rna_brain_gtex.tsv από την ιστοσελίδα του Human Protein Atlas.
Στη συνέχεια επεξεργαστήκαμε το αρχείο έτσι ώστε να εξάγουμε 3 πίνακες με τις τιμές TPM, pTPM και nTPM των διάφορων ιστών για το κάθε γονίδιο. 


### modify rna_brain_gtex.tsv file from HPA website

> import pandas as pd
> 
> t = pd.read_csv("/Users/Zoe/Desktop/rna_brain_gtex.tsv", sep="\t")
> 
> df2 = pd.DataFrame(0, index=t.iloc[:, 0].unique(), columns=t.iloc[:, 2].unique())

### extract nTPM dataframe and filter so row mean > 3
> for i in range(0, t.shape[0]):
>   r = t.iloc[i, 2]
>   v = t.iloc[i, 5]
>   id = t.iloc[i, 0]
>   df2.loc[id, r] = v
> 
> 
> df2.to_csv("nTPM_dataframe.tsv", sep="\t")
> 
> df2['mean'] = df2.mean(axis=1)
> print(df2)
> 
> df3 = df2[df2['mean'] > 3]
> print(df3)
> 
> df3.to_csv("nTPM_after_thres.tsv", sep='\t')

### extract TPM dataframe and filter so row mean > 3
> for i in range(0, t.shape[0]):
>   r = t.iloc[i, 2]
>   v = t.iloc[i, 3]
>   id = t.iloc[i, 0]
>   df2.loc[id, r] = v
> 
> 
> df2.to_csv("TPM_dataframe.tsv", sep="\t")
> 
> df2['mean'] = df2.mean(axis=1)
> print(df2)
> 
> df3 = df2[df2['mean'] > 3]
> print(df3)
> 
> df3.to_csv("nTPM_after_thres.tsv", sep='\t')

### extract pTPM dataframe and filter so row mean > 3

> for i in range(0, t.shape[0]):
>   r = t.iloc[i, 2]
>   v = t.iloc[i, 4]
>   id = t.iloc[i, 0]
>   df2.loc[id, r] = v
> 
> 
> df2.to_csv("pTPM_dataframe.tsv", sep="\t")
> 
> df2['mean'] = df2.mean(axis=1)
> print(df2)
> 
> df3 = df2[df2['mean'] > 3]
> print(df3)
> 
> df3.to_csv("nTPM_after_thres.tsv", sep='\t')
> 

