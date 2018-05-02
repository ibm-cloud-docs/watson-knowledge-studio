---

copyright:
  years: 2015, 2018
lastupdated: "2018-04-04"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

Cette documentation concerne
{{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}.
Pour consulter la documentation de la version précédente de {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace,
[cliquez sur
ce lien ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/docs/services/knowledge-studio/glossary.html){: new_window}.
{: tip}

# Glossaire 
{: #glossary}

Ce glossaire contient les termes utilisés dans {{site.data.keyword.knowledgestudioshort}} et leur définition.
{: shortdesc}

Les références croisées suivantes sont utilisées
dans ce glossaire : 

- "Voir" renvoie d'un terme à un synonyme préconisé ou d'un acronyme ou d'une abréviation à la forme complète définie.
- "Voir aussi" fait référence à un terme connexe ou opposé.

Pour consulter les glossaires d'autres
produits {{site.data.keyword.IBM}}, allez sur [www.ibm.com/software/globalization/terminology ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://www.ibm.com/software/globalization/terminology/){: new_window}.

[A](/docs/services/watson-knowledge-studio/glossary.html#gloss_A) [C](/docs/services/watson-knowledge-studio/glossary.html#gloss_C) [D](/docs/services/watson-knowledge-studio/glossary.html#gloss_D) [E](/docs/services/watson-knowledge-studio/glossary.html#gloss_E) [F](/docs/services/watson-knowledge-studio/glossary.html#gloss_F) [G](/docs/services/watson-knowledge-studio/glossary.html#gloss_G) [J](/docs/services/watson-knowledge-studio/glossary.html#gloss_J) [K](/docs/services/watson-knowledge-studio/glossary.html#gloss_K) [L](/docs/services/watson-knowledge-studio/glossary.html#gloss_L) [M](/docs/services/watson-knowledge-studio/glossary.html#gloss_M) [O](/docs/services/watson-knowledge-studio/glossary.html#gloss_O) [P](/docs/services/watson-knowledge-studio/glossary.html#gloss_P) [R](/docs/services/watson-knowledge-studio/glossary.html#gloss_R) [S](/docs/services/watson-knowledge-studio/glossary.html#gloss_S) [T](/docs/services/watson-knowledge-studio/glossary.html#gloss_T) [V](/docs/services/watson-knowledge-studio/glossary.html#gloss_V)

## A
{: #gloss_A}

- **analyse de la marge de progression (headroom)**

    Processus consistant à déterminer dans quelle mesure on peut s'attendre
à une amélioration de l'exactitude, de la précision ou du rappel en s'attaquant à
certaines catégories de problèmes identifiés lors de l'analyse de l'exactitude.


- **analyse de l'exactitude**

    Analyse des scores du modèle d'apprentissage automatique pour déterminer si des changements sont
nécessaires afin d'améliorer l'exactitude.

- **annotateur**

    Voir [annotateur humain](/docs/services/watson-knowledge-studio/glossary.html#gloss_H)
et [annotateur d'apprentissage automatique](/docs/services/watson-knowledge-studio/glossary.html#gloss_A).

- **annotateur d'apprentissage automatique**

    Voir [modèle d'apprentissage automatique](/docs/services/watson-knowledge-studio/glossary.html#gloss_M).

- **annotateur humain**

    Un expert du domaine qui examine, modifie et augmente les résultats de la
pré-annotation en identifiant les mentions, les relations entre types d'entités et les
coréférences.
En examinant le texte dans le contexte, un annotateur humain aide à déterminer les données de référence et à améliorer la précision
du modèle d'apprentissage automatique.

- **annotation**

    Informations sur une étendue de texte. Par exemple, une annotation peut indiquer qu'une étendue de texte particulière
représente un nom de société.

- **apprentissage automatique**

    Méthode d'analyse des données qui apprend de façon itérative de données
passées et s'adapte indépendamment lorsqu'elle est exposée à de nouvelles données.
Le modèle mathématique au coeur de l'apprentissage machine est construit à partir
d'entrées dites "de référence" (réalité du terrain, de l'anglais "ground truth").
Entraîné avec des données d'exemple raffinées, le modèle est capable de
livrer des résultats précis et reproductibles lorsqu'il analyse de nouvelles
données.

- **arbitrage**

    Processus itératif visant à résoudre les conflits d'annotations en comparant les annotations ajoutées au même document par
différents annotateurs humains.

- **archive du moteur de traitement (PEAR)**

    Fichier d'archive `.pear` incluant un moteur d'analyse UIMA (Unstructured Information Management Architecture)
et toutes les ressources nécessaires à son utilisation pour une analyse personnalisée.

- **attribut**

    Caractéristique ou trait d'une entité qui décrit cette dernière ; par exemple, le numéro de téléphone d'un employé est l'un des attributs de cet employé.

## C
{: #gloss_C}

- **chaîne de coréférences**

    Liste d'entités qui ont été annotées en tant que coréférences.
Lorsque vous annotez des mentions en tant que coréférences, le système crée
une chaîne de coréférences.
La chaîne vous permet de voir toutes les mentions dans leur contexte et de vérifier que
toutes les occurrences relèvent du même type d'entité.

- **concordance**

    Moyen par lequel on s'assure que la même mention est annotée avec le même type d'entité partout dans un même document ainsi qu'entre
différents jeux d'annotations.
L'outil de concordance aide à garantir l'uniformité de plusieurs occurrences d'une même mention sans que celles-ci aient à être étiquetées une à une par l'annotateur humain. 

- **convergence entre annotateurs**

    Mesure du degré de similitude avec lequel un même document est annoté dans plusieurs
jeux de documents.

- **coréférence**

    Relation entre deux mots ou syntagmes qui se réfèrent tous deux à la même personne ou à la même chose et dont l'un est
un antécédent linguistique de l'autre.
Par exemple, il y a une coréférence entre les deux pronoms du syntagme "Elle s'est fait mal", mais pas dans les deux pronoms du syntagme "Elle lui a fait mal".
Une coréférence relie deux entités équivalentes dans le même texte.

- **corpus**

    Collection de documents source qui ont été ajoutés à un espace de travail et qui ont servi à entraîner un modèle d'apprentissage automatique.

## D
{: #gloss_D}

- **dictionnaire**

    Collection de mots utilisables pour pré-annoter des documents.
Pour chaque mot apparaissant dans le texte du document et qui correspond à un terme du dictionnaire,
une nouvelle annotation est créée.
Un modèle d'apprentissage automatique peut être configuré avec un ou plusieurs
dictionnaires indépendants, chacun étant généralement spécifique à un domaine. Il peut y
avoir, par exemple, un dictionnaire de termes pharmaceutiques et un dictionnaire de
termes relatifs à la gestion de patrimoine.
Voir aussi [lemme](/docs/services/watson-knowledge-studio/glossary.html#gloss_L)
et [forme de surface](/docs/services/watson-knowledge-studio/glossary.html#gloss_F).

- **données aveugles**

    Jeu de documents annotés avec les données de référence, telles que des paires de questions/réponses, des annotations
de sémantique et des jugements de passages.
Les données aveugles ne sont jamais publiées ni vues par les développeurs. Elles servent seulement à tester périodiquement le
système pour évaluer ses performances sur des données jamais vues auparavant.
Les tests sur des données aveugles évitent que l'exactitude ne soit entachée par un surajustement à des jeux de questions ou des annotations connus.
Les résultats rapportés ne doivent provenir que de tests réalisés sur des données aveugles.
Voir aussi [données de test](/docs/services/watson-knowledge-studio/glossary.html#gloss_D)
et [données d'apprentissage](/docs/services/watson-knowledge-studio/glossary.html#gloss_D).

- **données d'apprentissage**

    Jeu de documents annotés qui peut servir à entraîner les annotateurs d'apprentissage automatique.
Voir aussi [données aveugles](/docs/services/watson-knowledge-studio/glossary.html#gloss_D)
et [données de test](/docs/services/watson-knowledge-studio/glossary.html#gloss_T).

- **données de référence**

    L'ensemble de données validées, constituées des annotations ajoutées par des annotateurs humains, qui sont utilisées
pour adapter un modèle d'apprentissage automatique à un domaine particulier.
Il sert à entraîner les modèles d'apprentissage machine, à mesurer leurs performances
(précision et rappel) et à calculer la marge de progression (headroom) pour décider où
concentrer les efforts de développement en vue d'améliorer les performances.
L'exactitude des données de référence est essentielle, car toute inexactitude sera corrélée à une incertitude dans
les composants qui utilisent ces données.

- **données de test**

    Jeu de documents annotés qui peut servir à évaluer les métriques du système
après ingestion et entraînement.
Voir aussi [données aveugles](/docs/services/watson-knowledge-studio/glossary.html#gloss_D)
et [données d'apprentissage](/docs/services/watson-knowledge-studio/glossary.html#gloss_D).


## E
{: #gloss_E}

- **entité**

    1. Mention annotée par un type d'entité.
    1. Personne, objet ou concept à propos duquel des informations sont stockées. 
    1. Ensemble des détails stockés à propos d'un objet du monde réel tel qu'une personne, un lieu ou un compte bancaire.
Une entité est un type d'élément.

- **entité nommée**

    Concept d'un domaine qui entre dans une catégorie bien définie, comme
les noms d'organisations, de lieux, d'auteurs ou de maladies.

- **entraîner**

    Procédé consistant à configurer une instance {{site.data.keyword.watson}} avec
des composants lui permettant de fonctionner dans un domaine particulier (par exemple :
contenu d'un corpus, données d'apprentissage générant des modèles d'apprentissage automatique,
algorithmes programmatiques, annotateurs ou autres composants de données de référence), puis à
améliorer et mettre à jour ces composants d'après les résultats d'analyses d'exactitude.

- **exactitude**

    Mesure de l'exactitude des annotations produites par un modèle d'apprentissage automatique.
Voir aussi [précision](/docs/services/watson-knowledge-studio/glossary.html#gloss_P)
et [rappel](/docs/services/watson-knowledge-studio/glossary.html#gloss_R).

## F
{: #gloss_F}


- **faux négatif**

    Réponse ou annotation correcte, mais dont on avait prédit qu'elle serait
incorrecte.


- **faux positif**

    Réponse ou annotation incorrecte, mais dont on avait prédit qu'elle serait
correcte.

- **forme de surface**

    La forme d'un mot ou d'une unité multimot telle qu'elle apparaît dans le corpus. Par exemple,
les termes 'organisation' et 'organisé' sont des formes de surface du lemme 'organiser'.
Voir aussi [dictionnaire](/docs/services/watson-knowledge-studio/glossary.html#gloss_D)
et [lemme](/docs/services/watson-knowledge-studio/glossary.html#gloss_L).


## G
{: #gloss_G}

- **gestionnaire des processus d'annotation**

    Rôle ayant la responsabilité de gérer toutes les activités du cycle d'annotation dans un espace de travail.
C'est au chef de projet ajouté à l'espace de travail que revient généralement la tâche de gérer les processus d'annotation.

- **graphe des connaissances**

    Modèle qui consolide les entités typées, leurs relations, leurs propriétés et les taxonomies
hiérarchiques pour représenter une organisation de concepts dans un domaine donné.
Dès lors que le stock de données sous-jacent est chargé avec les entrées de sources de
données structurées et non structurées, utilisateurs et applications peuvent accéder au
graphe des connaissances pour examiner les connaissances clés acquises dans un domaine
spécifique, explorer les interactions et découvrir d'autres relations.




## J
{: #gloss_J}

- **jeu d'annotations**

    En annotation humaine, collection de documents extraits du corpus pour permettre un partage de la charge de travail par
plusieurs annotateurs humains.
En annotation machine, collection de documents utilisables comme données aveugles, données d'entraînement (ou d'apprentissage) ou données de test.

- **jeu de documents**

    Collection de documents.
Les documents importés ensemble deviennent un jeu de documents.
Les documents annotés qui sont regroupés pour des besoins d'entraînement (données aveugles, d'entraînement et de test)
sont générés en tant que jeux de documents.

- **jeu de règles**

    Ensemble de règles qui définissent les motifs pour l'annotation de texte.
Si un motif (pattern) s'applique, les actions de la règle correspondante sont exécutées sur les annotations
concernées.
Une règle spécifie généralement la condition à remplir (celle qui doit être recherchée),
un quantificateur optionnel, une liste de contraintes supplémentaires à satisfaire par le
texte trouvé et les actions à entreprendre lorsqu'il y a concordance. Il peut s'agir, par exemple,
de créer une nouvelle annotation ou de modifier une annotation existante.


## K
{: #gloss_K}

- **Kappa de Fleiss**

    Mesure du degré de concordance avec lequel la même annotation a été appliquée par plusieurs
annotateurs humains entre différents documents qui se chevauchent.
Le Kappa de Fleiss atteint sa meilleure valeur à 1 et sa pire valeur à 0.

## L
{: #gloss_L}

- **lemme**

    La forme normalisée ou canonique d'un mot.
Le plus souvent, il s'agit de la forme non dérivée et non infléchie d'un nom ou d'un verbe.
Par exemple, le lemme des termes 'organisation' et 'organisé' est 'organiser'.
Voir aussi [dictionnaire](/docs/services/watson-knowledge-studio/glossary.html#gloss_D)
et [forme de surface](/docs/services/watson-knowledge-studio/glossary.html#gloss_S).


## M
{: #gloss_M}

- **matrice de confusion**

    Table fournissant une décomposition numérique détaillée des jeux de documents annotés.
Elle est utilisée pour comparer les annotations qui ont été ajoutées par un modèle d'apprentissage automatique aux
annotations dans les données de référence.
Elle rend compte du nombre de [faux positifs](/docs/services/watson-knowledge-studio/glossary.html#gloss_F),
de [faux négatifs](/docs/services/watson-knowledge-studio/glossary.html#gloss_F),
de [vrais positifs](/docs/services/watson-knowledge-studio/glossary.html#gloss_V) et
de [vrais négatifs](/docs/services/watson-knowledge-studio/glossary.html#gloss_V).

- **mention**

    Etendue de texte que vous considérez pertinente dans les données de votre
domaine.
Par exemple, dans un système de types du secteur automobile, des
occurrences de termes tels que airbag, Ford Explorer et
siège enfant pourraient être des mentions pertinentes.

- **modèle d'apprentissage automatique**

    Composant qui identifie les entités et leurs relations selon un modèle statistique basé sur des
données de référence.
Le modèle applique l'expérience passée, telle que celle qu'il a acquise avec les données
d'apprentissage, pour déterminer ou prédire l'issue correcte de futures expériences en
fonction des caractéristiques de leurs données.
Ces expériences passées sont capturées sous la forme d'un modèle en calculant les scores des caractéristiques pour chaque réponse ou fait candidat
et en les combinant avec les résultats connus.
Parfois appelé *annotateur d'apprentissage automatique*.

- **moteur d'analyse**

    Programme qui analyse les artefacts, tels que des documents, et déduit des informations à leur sujet,
et qui implémente la spécification d'interface du moteur d'analyse UIMA.
Les moteurs d'analyse sont construits à partir de blocs de construction que l'on appelle
annotateurs.
Un moteur d'analyse peut contenir un seul annotateur, auquel cas on parlera de moteur d'analyse primitif,
ou plusieurs, et dans ce cas on parlera de moteur d'analyse agrégé.


## O
{: #gloss_O}

- **ontologie**

    Spécification formelle explicite de la représentation des objets, concepts et
autres entités pouvant exister dans un domaine d'intérêt particulier, ainsi que des
relations entre ces éléments.

- **organiser**

    Sélectionner, recueillir, conserver et tenir à jour les contenus relatifs à un sujet
spécifique.
L'organisation (de l'anglais "curation") établit, gère et ajoute de la valeur aux données ; elle transforme les données en information fiable et en connaissances.


## P
{: #gloss_P}

- **partie du discours**

    Dans un dictionnaire, une balise POS (Part of Speech, partie du discours)
est associée à chaque élément lexical.
Par exemple, le mot 'copie' peut être un verbe conjugué (il copie) ou un nom commun (une copie). 

- **performances**

    Mesure d'un système {{site.data.keyword.watson}} en termes d'exactitude,
de précision et de rappel, par exemple, lorsqu'il répond à des questions, découvre des relations ou annote du texte.


- **pré-annotateur de dictionnaire**

    Composant qui identifie les mentions dans le texte qui correspondent à un ensemble spécifique de mots.
En utilisant une terminologie spécifique d'un domaine pour pré-annoter le texte, le
pré-annotateur de dictionnaire peut renforcer la capacité de l'annotateur humain à
préparer un jeu de documents de référence.

- **pré-annotation**

    Processus d'annotation d'un jeu de documents intervenant avant l'annotation humaine.
Les documents peuvent être pré-annotés au moyen d'un modèle à base de règles, d'un modèle d'apprentissage automatique,
d'{{site.data.keyword.nlufull}} ou d'un dictionnaire.
La pré-annotation peut aider les annotateurs humains à préparer plus rapidement un jeu de documents de référence.


- **précision**

    Mesure exprimant la proportion de résultats pertinents.
La précision, qui est une valeur de prédiction des positifs, est déterminée par le nombre de
résultats positifs corrects divisé par le nombre total de résultats positifs.
Son utilisation combinée à celle du rappel permet de mieux mesurer l'exactitude (ou fidélité).
Voir aussi [exactitude](/docs/services/watson-knowledge-studio/glossary.html#gloss_E)
et [rappel](/docs/services/watson-knowledge-studio/glossary.html#gloss_R).

## R
{: #gloss_R}

- **rappel**

    Mesure exprimant, en pourcentage, le rapport du nombre de résultats pertinents retournés
sur le nombre total de résultats pertinents disponibles.
Le rappel, qui est une mesure de la sensibilité, est déterminé par le nombre de
résultats positifs corrects divisé par le nombre de résultats positifs qui auraient dû être retournés.
Son utilisation combinée à celle du rappel permet de mieux mesurer l'exactitude (ou fidélité).
Voir aussi [exactitude](/docs/services/watson-knowledge-studio/glossary.html#gloss_E)
et [précision](/docs/services/watson-knowledge-studio/glossary.html#gloss_P).

- **relation**

    Généralement un verbe qui reflète comment deux entités sont reliées l'une à l'autre.
Par exemple, "habite à" est une relation entre une personne et un lieu.
Une relation relie deux entités différentes dans la même phrase.

- **rôle**

    Attribut donnant à une mention une signification sensible au contexte.
Par exemple, dans la phrase "Je suis allé chez {{site.data.keyword.IBM_notm}} aujourd'hui",
{{site.data.keyword.IBM_notm}} est la mention, Organization est le type d'entité et Facility est le rôle du type d'entité.



## S
{: #gloss_S}

- **Score F1**

    Mesure de l'exactitude d'un test qui considère à la fois la précision et le rappel
pour calculer un score.
Le score F1 peut être interprété comme une moyenne pondérée des valeurs de précision et de rappel.
Un score F1 atteint sa meilleure valeur à 1 et sa pire valeur à 0.

- **sous-type**

    Type étendant ou implémentant un autre type, le supertype.

- **système de types**

    Le système de types définit les types des objets qui peuvent être découverts dans un
document.
Il définit tous les types d'entités possibles et toutes les relations possibles entre eux.
Vous pouvez définir autant de types différents que vous le souhaitez dans un système de
types.
Chaque système de types est généralement spécifique à un domaine et spécifique à une application.


## T
{: #gloss_T}

- **trait (ou caractéristique)**

    Membre de données ou attribut d'un type.

- **traitement automatique du langage naturel**

    Branche de l'intelligence artificielle et de la linguistique qui étudie
les problèmes inhérents au traitement et à la manipulation du langage naturel dans le
but d'accroître la capacité des ordinateurs à comprendre les langues humaines.

- **type d'entité**

    Type de l'entité qu'une mention représente, sans considération du
contexte.
Par exemple, la mention {{site.data.keyword.IBM_notm}} pourrait être annotée par le type d'entité ORGANIZATION.

    Dans un modèle de relation d'entités, un type d'entité est la chose que l'on modélise ou la chose à laquelle se réfère une
mention, par exemple le nom d'une personne ou d'un lieu.
Les différents types d'entités ont chacun un jeu d'attributs qui leur est propre, tel que "nom de famille" ou "lieu de résidence", et
sont reliés par des relations telles que "habite à".
Un type d'entité a une existence indépendante et peut être identifié sans équivoque.

- **type de relation**

    Définit une relation binaire et unidirectionnelle entre deux entités.
Par exemple, Marie employedBy {{site.data.keyword.IBM_notm}} est une relation valide, mais
pas {{site.data.keyword.IBM_notm}} employedBy Marie.

## V
{: #gloss_V}

- **vrai négatif**

    Réponse ou annotation dont on avait prédit qu'elle serait
incorrecte et qui est effectivement incorrecte.


- **vrai positif**

    Réponse ou annotation dont on avait prédit qu'elle serait
correcte et qui est effectivement correcte.

