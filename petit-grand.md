# Petit et grand

Consigne : Par la forme et la taille exprimer le petit et le grand à partir des 1073 emails hackés du Climate Research Unit (2009).

Suivre :

- en python, créer un fichier csv avec deux colonnes : file (nom du fichier), size (en ko)
- à partir d'un principe d'affichage en grille, ecrire un code pour donner une forme et une taille à l'information
- exporter un svg

Contrainte : dimension image 960 x 640 px

Ressource : [1073 emails](http://mobitool.free.fr/edu/dd/data/crumail.zip)

Astuce :

- en p5.js, utiliser `loadTable()`
- pour exporter en svg utiliser cet exemple [p5.svg.js](https://editor.p5js.org/gaetan/sketches/WvxdxVZlv) 

Avancé :

- modifier le type d'échelle avec `log(x)`
- Légender et ou appeler des éléments d'information sémantique

-----------------------
## Code Python

```python
# Lists files and their size in Ko
# Writes a csv with file name and size

import os, sys, csv

# Open directory
path = "crumail"
dirs = os.listdir(path)
size = os.path.getsize(path)
print("files in the directory:", len(dirs))

# Main array
L = [["file","size"]]

# Lists all the files and directories
# Get the size and convert to Ko
for file in dirs:
    size = os.path.getsize("crumail/"+file)
    L.append([file,size/1000])

# CSV commands
with open ('numbers.csv', 'w', newline='') as F:
    F_writer = csv.writer(F, delimiter=',')
    F_writer.writerows(L)
    print("csv saved")
```