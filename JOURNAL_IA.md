### Prompt 1

**Moi** : Avec le projet que je t'ai envoyé, décrit moi comment il faut que je trouve la formule du rmse qui sera utile lors de l'entrainement, du test et des prédictions de mon modèle.



def rmse(y_reel, y_pred) -> float:

    ecarts = np.asarray(y_reel, dtype = float) - np.asarray(y_pred, dtype = float)
    return float(np.sqrt(np.mean(ecarts ** 2)))

**Moi** : Détaille moi la fonction

Voici la fonction ligne par ligne :

python
def rmse(y_reel, y_pred) -> float:
On définit une fonction rmse qui prend deux paramètres :
y_reel : les valeurs réelles $y_i$
y_pred : les valeurs prédites par le modèle $\hat{y}_i$
-> float est une annotation de type qui indique que la fonction renvoie un nombre décimal. Python ne la vérifie pas, elle sert seulement à la lisibilité.
python
    ecarts = np.asarray(y_reel, dtype = float) - np.asarray(y_pred, dtype = float)
np.asarray(..., dtype=float) convertit l’entrée (liste, tuple, colonne pandas…) en tableau NumPy de nombres décimaux. Si c’est déjà un tableau du bon type, NumPy n’en fait pas de copie.
La soustraction se fait élément par élément (vectorisation) :
$$\text{ecarts} = \left[\,y_1 - \hat{y}_1,\; y_2 - \hat{y}_2,\; \dots,\; y_n - \hat{y}_n\,\right]$$
python
    return float(np.sqrt(np.mean(ecarts ** 2)))

Cette ligne se lit de l’intérieur vers l’extérieur :

Étape	Code	Math
1. Carré de chaque écart	ecarts ** 2	$(y_i - \hat{y}_i)^2$
2. Moyenne (MSE)	np.mean(...)	$\frac{1}{n}\sum_{i=1}^{n}(y_i - \hat{y}_i)^2$
3. Racine carrée	np.sqrt(...)	$\sqrt{\text{MSE}}$
4. Conversion	float(...)	np.float64 devient un float Python

On met les écarts au carré pour que les erreurs positives et négatives ne s’annulent pas, et pour pénaliser davantage les grosses erreurs. La racine ramène ensuite le résultat dans la même unité que les données (par exemple des points ou des buts dans le projet)

### Prompt 2
