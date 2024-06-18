# Projet : LAION-Aesthetics V1

L’une des plus grandes frustrations des modèles d’IA générative texte-image est liée à leur perception en tant que boite noire. On sait que ces modèles ont été formés sur des images extraites du web, mais lesquelles ? Et comment en donner un aperçu sans avoir à regarder chaque image ? Pour répondre à cette question, vous vous intéresserez à l'ensemble de données d'entraînement LAION-Aesthetics V1. Vous proposerez une série de trois visualisations, en fonctions de paramètres des images (par exemple : largeur, hauteur, teinte moyenne, valeur moyenne, etc.). Pour cela, vous vous appuierez sur les travaux de Lev Manovich dans le domaine de l'analyse culturelle (par ex. Phototrails et Manga Style Space). Vous proposerez une restitution interactive, sans oublier les titrages et légendes nécessaires. D'une façon générale, votre projet devra donner un éclairage sur ce qui est habituellement peu compris ou caché dans les données d'entraînement de l'IA générative. 

**Dataset (échantillon 10K)** [https://github.com/robillardstudio/laion2B-en-aesthetic-minified](https://github.com/robillardstudio/laion2B-en-aesthetic-minified)

<!-- Autres méthodes : dct, bag of words, autoencodeur -->

Informations sur LAION Aesthetics [https://github.com/LAION-AI/laion-datasets/blob/main/laion-aesthetic.md](https://github.com/LAION-AI/laion-datasets/blob/main/laion-aesthetic.md)

Phototrails [http://manovich.net/index.php/exhibitions/manga-style-space](http://manovich.net/index.php/exhibitions/manga-style-space)

Manga Style Space [http://manovich.net/index.php/exhibitions/manga-style-space](http://manovich.net/index.php/exhibitions/manga-style-space)

## Livrable

Vous livrez un dossier A4 paysage pdf (ou une vidéo max 3 min pour le sujet 3), 10 pages maxi contenant à minima les éléments suivants.

- Couverture avec vos noms
- Résumé du projet (250 mots maxi)
- Images d’inspiration (cf. ouvrage Data design)
- Charte graphique ou mapping visuel
- La visualisation finale en pleine page
- URL pour le projet en ligne
- URL pour le code et sa documentation (p5 editor ou github)

## Méthode

Calcul de la teinte moyenne d'une image (hue)

```python
from PIL import Image
import os
import colorsys

def calculate_average_hue(image_path):
    with Image.open(image_path) as img:
        # Convert image to RGB if it's not
        img = img.convert('RGB')
        
        # Calculate the average hue
        pixels = list(img.getdata())
        total_hue = 0
        for pixel in pixels:
            # Normalize the RGB values to range [0, 1]
            r, g, b = [x / 255.0 for x in pixel]
            # Convert RGB to HSV
            h, s, v = colorsys.rgb_to_hsv(r, g, b)
            total_hue += h

        avg_hue = total_hue / len(pixels)
        return avg_hue

# Directory containing images
image_directory = 'path/to/save/images'

# Iterate over each image in the directory
for image_file in os.listdir(image_directory):
    image_path = os.path.join(image_directory, image_file)
    avg_hue = calculate_average_hue(image_path)
    print(f"Average hue of {image_file}: {avg_hue}")
```