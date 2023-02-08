# Subventions

Spécification du modèle de données relatif aux subventions attribuées par une collectivité

- nom : `subventions`
- page d'accueil : https://git.opendatafrance.net/scdl/subventions
- URL du schéma : https://git.opendatafrance.net/scdl/subventions/raw/v2.0.2/schema.json
- version : `2.0.2`
- date de création : 27/04/2018
- date de dernière modification : 28/06/2019
- concerne le pays : FR
- valeurs manquantes représentées par : `[""]`
- contributeurs :
  - OpenDataFrance (auteur)
  - Pierre Dittgen, Jailbreak (auteur) [pierre.dittgen@jailbreak.paris](pierre.dittgen@jailbreak.paris)
  - Quentin Loridant, multi [quentin.loridant@multi.coop](quentin.loridant@multi.coop)
  - Johan Richer, multi [johan.richer@multi.coop](johan.richer@multi.coop)
  - Amélie Rondot, multi [amelie.rondot@multi.coop](amelie.rondot@multi.coop)
- ressources :
  - Exemple de fichier subventions invalide ([lien](https://git.opendatafrance.net/scdl/subventions/raw/v2.0.1/exemples/exemple_invalide.csv))
- sources :
  - Décret n° 2017-779 du 5 mai 2017 relatif à l&#x27;accès sous forme électronique aux données essentielles des conventions de subvention​ ([lien](https://www.legifrance.gouv.fr/jo_pdf.do?id=JORFTEXT000034600552))
  - Arrêté du 17 novembre 2017 relatif aux conditions de mises à disposition des données essentielles des conventions de subvention​ ([lien](https://www.legifrance.gouv.fr/jo_pdf.do?id=JORFTEXT000036040528))
  - Format réglementaire pour la publication des données essentielles des conventions de subventions sur le dépôt Github de la mission Etalab​ ([lien](https://github.com/etalab/format-subventions))

## Modèle de données

Ce modèle de données repose sur les 16 champs suivants correspondant aux colonnes du fichier tabulaire.

### `nomAttribuant`

- titre : Nom de l'attribuant
- description : Nom officiel de la collectivité attribuant la subvention.
- type : chaîne de caractères
- exemple : `Région Bretagne`
- valeur obligatoire

### `idAttribuant`

- titre : Identification de l'attribuant
- description : Identifiant du [Système d'Identification du Répertoire des Etablissements](https://fr.wikipedia.org/wiki/Syst%C3%A8me_d%27identification_du_r%C3%A9pertoire_des_%C3%A9tablissements) (SIRET) de la collectivité attribuant la subvention, composé de 9 chiffres SIREN + 5 chiffres NIC d’un seul tenant.
- type : chaîne de caractères
- exemple : `23350001600040`
- valeur obligatoire
- motif : `^\d{14}$`

### `dateConvention`

- titre : Date de la convention de subvention
- description : Date de la convention au format AAAA-MM-JJ suivant la norme internationale [ISO 8601](https://fr.wikipedia.org/wiki/ISO_8601).
- type : date
- exemple : `2017-06-27`
- valeur obligatoire

### `referenceDecision`

- titre : Référence de la décision
- description : Identifiant interne de l’acte matérialisant la décision d’attribution de la subvention. Sa composition dépend des pratiques propres à la collectivité.
- type : chaîne de caractères
- exemple : `2017-03-103`
- valeur optionnelle

### `nomBeneficiaire`

- titre : Nom du bénéficiaire
- description : Nom officiel ou raison sociale du bénéficiaire de la subvention.
- type : chaîne de caractères
- exemple : `Association Les Petits Débrouillards Bretagne`
- valeur obligatoire

### `idBeneficiaire`

- titre : Identification du bénéficiaire
- description : Identifiant du [Système d'Identification du Répertoire des Etablissements](https://fr.wikipedia.org/wiki/Syst%C3%A8me_d%27identification_du_r%C3%A9pertoire_des_%C3%A9tablissements) (SIRET) du bénéficiaire de la subvention, composé de 9 chiffres SIREN + 5 chiffres NIC d’un seul tenant.
- type : chaîne de caractères
- exemple : `38047555800058`
- motif : `^\d{14}$`

### `rnaBeneficiaire`

- titre : Identification RNA du bénéficiaire
- description : Numéro d'identification RNA [Répertoire National des Associations](https://associations.gouv.fr/le-rna-repertoire-national-des-associations.html) du bénéficiaire de la subvention, débutant par 'W' et composé de 9 chiffres
- type : chaîne de caractères
- exemple : `W380475558`
- motif : `^W\d{9}$`

### `objet`

- titre : Objet de la subvention
- description : Description de l'objet de la subvention attribuée limitée à 256 caractères maximum.
- type : chaîne de caractères
- exemple : `Animations climat-énergie dans les lycées de la région`
- valeur obligatoire
- taille maximale : 256

### `montant`

- titre : Montant total de la subvention
- description : Montant total de la subvention attribuée, exprimé en euros et calculé avant répartition entre les bénéficiaires dans le cas de bénéficaires multiples. Le signe de séparation entre les parties entière et décimale du nombre est le point.
- type : nombre réel
- exemple : `47800.20`
- valeur obligatoire

### `nature`

- titre : Nature de la subvention
- description : Plusieurs choix possibles en combinant les valeurs 'aide en numéraire' et/ou 'aide en nature'. Les valeurs autorisées sont 'aide en numéraire', 'aide en nature', 'aide en numéraire;aide en nature', 'aide en nature;aide en numéraire'. Quand la nature de la subvention est à la fois en numéraire et en nature, le signe de séparation des valeurs est le point-virgule.
- type : chaîne de caractères
- exemple : `aide en numéraire;aide en nature`
- valeur obligatoire
- valeurs autorisées : `["aide en numéraire","aide en nature","aide en numéraire;aide en nature","aide en nature;aide en numéraire"]`

### `conditionsVersement`

- titre : Conditions de versement de la subvention
- description : Choix unique parmi plusieurs valeurs possibles : 'unique', 'échelonné' ou 'autre'. La valeur 'autre' correspond à une description libre des modalités de versement de la subvention dans la limite de 256 caractères maximum.
- type : chaîne de caractères
- exemple : `échelonné`
- valeur obligatoire
- taille maximale : 256

### `datesPeriodeVersement`

- titre : Date ou période de versement
- description : Si le versement est unique et que la date précise est connue, alors il s'agit d'une date au format AAAA-MM-JJ suivant la norme internationale [ISO 8601](https://fr.wikipedia.org/wiki/ISO_8601). Si le versement est échelonné (ou que la date précise de versement unique est inconnue), alors il s'agit d'une période exprimée au format AAAA-MM-JJ/AAAA-MM-JJ où le séparateur entre la première et la seconde date de l'intervalle est la barre oblique suivant la norme internationale [ISO 8601](https://fr.wikipedia.org/wiki/ISO_8601).
- type : chaîne de caractères
- exemple : `'2017-03-14' pour une date ou '2017-03-14/2018-03-14' pour une période`
- valeur obligatoire
- motif : `^[0-9]{4}\-[0-9]{2}\-[0-9]{2}(\/[0-9]{4}\-[0-9]{2}\-[0-9]{2})?$`

### `idRAE`

- titre : Identifiant RAE de l’aide au titre de laquelle la subvention est attribuée
- description : Numéro unique de référencement dans le [Répertoire des Aides aux Entreprises](https://aides-entreprises.fr/). Ce champ ne concerne que les subventions attribuées au titre d’une aide référencée dans la [base de données du RAE](https://data.aides-entreprises.fr/documentation) gérée par l'Institut Supérieur des Métiers.
- type : chaîne de caractères
- exemple : `12345`
- valeur optionnelle
- taille maximale : 5

### `notificationUE`

- titre : Aide d'Etat notifiée à la Commission Européenne
- description : Subvention attribuée au titre d’une aide de minimis notifiée à la Commission Européenne en vertu des dispositions du règlement n° 1407/2013 du 18 décembre 2013. Seules les valeurs 'oui' ou 'non' sont autorisées.
- type : booléen
- valeurs considérées comme vraies : oui
- valeurs considérées comme fausses : non
- exemple : `non`
- valeur obligatoire

### `pourcentageSubvention`

- titre : Pourcentage du montant total de la subvention attribuée au bénéficiaire
- description : Pourcentage exprimé sous la forme d'un nombre décimal. Dans le cas d’un bénéficiaire unique, le pourcentage est 100%, soit '1.00' en nombre décimal. Dans le cas de bénéficiaires multiples, le pourcentage du montant attribué au bénéficiaire correspond à la part qui lui est versée : par exemple 45%, soit '0.45' en nombre décimal. Le signe de séparation entre les parties entière et décimale du nombre est le point.
- type : nombre réel
- exemple : `0.45`
- valeur obligatoire
- valeur minimale : 0.01
- valeur maximale : 1

### `dispositifAide`

- titre : Identifiant référençant le dispositif d'aide à l'origine de la subvention
- description : Identifiant présent dans les données issues du [schéma des dispositifs d'aide](https://schema.data.gouv.fr/etalab/schema-dispositif-aide/). Il peut être utilisé à la place de l'identifiant `idRAE` qui ne concerne que les aides aux entreprises.
- type : chaîne de caractères
- exemple : `65d5b6c7-102c-4440-ac3b-768f708edc0a`