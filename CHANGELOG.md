# Changelog

## 2.1.1

Migration de l'instance gitlab d'hébergement du schéma Catalogue vers l'instance publique https://gitlab.com/opendatafrance/scdl/subventions


## 2.1.0

- Ajout du champs dispositifAide
- Modification du champs idBeneficiaire : suppression de la contrainte champs requis
- Rajout du champs rnaBeneficiaire non requis
- Rajout du custom check one-of-required qui vérifie que pour une ligne donnée l'idBeneficiaire ou le rnaBeneficiaire est rempli

## 2.0.2

- Correction de la valeur d'exemple pour le champ `datesPeriodeVersement` #10
- Ajout d'un fichier d'exemple valide #8

## 2.0.1

Changements internes :

- utilisation des [métadonnées standardisées](https://github.com/frictionlessdata/specs/blob/master/specs/patterns.md#table-schema-metadata-properties)

## 2.0.0

- ajout du fichier `CHANGELOG.md`
- dans `schema.json`:
  - ajout de la clef `updated`
  - ajout des exemples (propriété `examples`)
  - amélioration des titres, descriptions et exemples
  - suppression des "required": false
  - changement de l'intervalle de valeur pour le champ `pourcentageSubvention`
  - ajout des custom-checks

## 1.1
