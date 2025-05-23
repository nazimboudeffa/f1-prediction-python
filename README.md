🧠 Objectif
Prédire quels pilotes sont les plus susceptibles de bien performer dans la prochaine course, en se basant sur leurs performances passées.

🧩 Composants de l'algorithme
1. Points totaux (points_totaux)
C'est le nombre de points accumulés par chaque pilote jusqu’à présent.

Pourquoi c'est important : Les points reflètent la régularité et les bons résultats.

Poids dans le score final : élevé (ex : 50%).

2. Nombre de victoires (victoires)
Le nombre de fois où le pilote a fini 1er.

Pourquoi : Cela reflète la capacité à gagner, pas juste à finir dans les points.

Poids suggéré : moyen (ex : 30%).

3. Position moyenne à l’arrivée (position_moyenne)
La moyenne des positions finales du pilote.

Pourquoi : Cela montre la régularité en course, indépendamment des points.

Astuce : On inverse la moyenne pour que les meilleures positions donnent un score plus élevé (1 / position_moyenne).

Poids suggéré : plus faible (ex : 20%).

4. Score final combiné
Les trois éléments ci-dessus sont normalisés (mis à l’échelle entre 0 et 1), puis pondérés pour obtenir un score global :

```
score = 
    (points / max_points)       * 0.5 +
    (victoires / max_victoires) * 0.3 +
    (1 / position_moyenne / max_inverse_position) * 0.2
```

✅ Avantages de cette approche :
Simple à comprendre et à implémenter

Basée uniquement sur les données disponibles

Facilement ajustable : vous pouvez jouer sur les pondérations pour affiner

⚠️ Limites :
Ne tient pas compte de facteurs contextuels : météo, circuit, incidents, performances récentes sur une piste spécifique…

Suppose que le passé reflète le futur, ce qui n’est pas toujours vrai en F1 !