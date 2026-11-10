[[Hypothèses]]
[[Schemas/Excalidraw]]
[[Scénarios]]
[[PROJET FINANCIER]]




```dataview
TABLE periode AS "Periode", epargne_prevue AS "Epargne prévue", epargne_reelle AS "Epargne réelle", choice(epargne_reelle = null, "En attente", default(epargne_reelle, 0) - epargne_prevue) AS "Ecart"
FROM "Mois"
```


```dataview
TABLE WITHOUT ID length(rows) AS "Mois de suivis", sum(rows.epargne_reelle) AS "Epargne cumulée", sum(rows.epargne_reelle) - sum(rows.epargne_prevue) AS "Ecart cumulé"
FROM "Mois"
WHERE Type = "mois" AND epargne_reelle != null
GROUP BY true
```


## Mes paliers d'épargne

- [ ] 10000
- [ ] 25000
- [ ] 50000
- [ ] 75000
- [ ] 100000


```dataview
TABLE WITHOUT ID 100000- sum(rows.epargne_reelle) AS "Montant restant à épargner"
FROM "Mois"
WHERE Type = "mois" AND epargne_reelle != null
GROUP BY true
```

```dataview
TABLE WITHOUT ID
    round(sum(rows.epargne_reelle) / 100000 * 100, 2) AS "Progression (%)"
FROM "Mois"
WHERE type = "mois" AND epargne_reelle != null
GROUP BY true
```
Avec 4360€ d'épargne cumulée, on a 4.36% de progression.














 


 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 