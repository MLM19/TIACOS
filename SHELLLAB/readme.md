## SHELL LAB

This is the first project on the subject. 
The main goal of this project is to learn how to handle protein files from a terminal point of view (bash)
These are the **instructions** that are being followed:

```{bash}
STEP 1
1) touch getProtByChebiId.sh
2) gedit getProtByChebiId.sh
3) enter this: 
	curl -o ${1}.csv 'https://www.ebi.ac.uk/chebi/viewDbAutoXrefs.do?d-1169080-e=1&6578706f7274=1&chebiId='${1}'&dbName=UniProt'
5) ./getProtByChebiId.sh 27732
	This should download the protein for the ID= 27732 and save it in a file
7) Check the number of lines (should be 77 lines)
	wc -l 27732prot.csv 
8) Repeat for all other proteins. (16040, 27518, 27958)

STEP 2
1) touch getProtByChebiId-d.sh
2) gedit getProtByChebiId-d.sh
3) enter this:
	curl | grep -E 'MISCELLANEOUS'\|'DISRUPTION PHENOTYPE' ${1} 
4) ./getProtByChebiId-d.sh 27732.csv > MIS_DIS_27732.csv
	Also check wc -l MIS_DIS_27732.csv --> returns 19 lines (so it is filtered out)
	
STEP 3
1) touch getProtByChebiId-dc.sh
2) gedit getProtByChebiId-dc.sh
3) enter this:
	 grep -E 'MISCELLANEOUS'\|'DISRUPTION PHENOTYPE' ${1} | awk -F',' '{print $1}'  
4) ./getProtByChebiId-dc.sh 27732.csv > id_27732.csv
5) head id_27732.csv 
	To check the output

STEP 4
1) touch getProtByChebiId-dcl.sh
2) gedit getProtByChebiId-dcl.sh
3) enter this: 
	awk -F',' '{print $1}' ${1} | xargs -I @ wget 'https://www.uniprot.org/uniprot/'@'.txt'
4) ./getProtByChebiId-dcl.sh 27732.csv
5) head B0LPN4.txt
	to check out the output
	
STEP 5
1) touch getProtByChebiId-dclp.sh
2) gedit getProtByChebiId-dclp.sh
3) enter this:
