## prompt 1:
Pourquoi je dois utiliser un iloc pour un dataframe ? 
def stats_joueur(self, nom: str, colonnes: list[str]) -> dict:
        nom = nom.strip()
        lignes = self.dataFrame[self.dataFrame["skaterFullName"].lower() == nom.lower()]
        return lignes.iloc[0][colonnes].to_dict()

Même avec une seule ligne, lignes reste un DataFrame, c’est-à-dire un tableau de 1 ligne, et pas une ligne seule. iloc[0] sert à sortir cette ligne du tableau. Regarde la différence :

python
lignes[colonnes].to_dict()
# {"goals": {412: 25}, "assists": {412: 40}, ...}   ← dictionnaire de dictionnaires

lignes.iloc[0][colonnes].to_dict()
# {"goals": 25, "assists": 40, ...}                 ← ce que le modèle attend

Sans iloc[0], chaque valeur reste associée à son numéro de ligne (412), et predire ne fonctionnerait pas.
