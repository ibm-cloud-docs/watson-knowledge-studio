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
ce lien ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/docs/services/knowledge-studio/release-notes.html){: new_window}.
{: tip}

# Notes sur l'édition 
{: #release-notes}

Les nouvelles fonctionnalités et modifications suivantes sont disponibles dans {{site.data.keyword.knowledgestudiofull}}.
{: shortdesc}

## Mars 2018
{: #march2018}

### Nouvelles fonctionnalités et changements
{: #new-march2018}

- Une page **Modèles déployés** est disponible, dans laquelle vous pouvez voir tous les
modèles {{site.data.keyword.knowledgestudioshort}} déployés dans des services des espaces auxquels vous avez accès.
Pour afficher la page **Modèles déployés**,
dans le menu **Paramètres** de la barre de menus, en haut à droite, cliquez sur **Gérer les modèles déployés**.
Pour des informations sur le retrait de modèles du déploiement et leur visualisation dans la
page **Modèles déployés**, consultez [Retirer des modèles d'apprentissage automatique du déploiement](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model)
et [Retirer des modèles à base de règles du déploiement](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model).
- Une traduction en français de l'interface de {{site.data.keyword.knowledgestudioshort}} est à présent disponible.
- {{site.data.keyword.alchemylanguagefull}} est plus disponible
en tant que pré-annotateur.
A la place d'{{site.data.keyword.alchemylanguageshort}}, vous pouvez utiliser {{site.data.keyword.nlushort}} pour
pré-annoter vos documents.
Pour plus d'informations, consultez [Amorcer le processus d'annotation](/docs/services/watson-knowledge-studio/preannotation.html).

## Décembre 2017
{: #december2017}

### Nouvelles fonctionnalités et changements
{: #new-december2017}

- Lancement de {{site.data.keyword.knowledgestudioshort}} sur {{site.data.keyword.cloud_notm}}.
Pour des informations sur le processus de migration et sa planification,
consultez [Migrer vers {{site.data.keyword.cloud_notm}}](/docs/services/watson-knowledge-studio/client-migration.html).
- Navigation repensée.
Pour des détails sur les changements, consultez le [Tableau 2](#september2017) dans les notes sur l'édition de septembre 2017.
- Ajout d'{{site.data.keyword.nlufull}} en tant que pré-annotateur.
- Des paramètres de gestion des utilisateurs et de l'espace de stockage ont été ajoutés à la page Détails du service. Pour des informations sur
l'ajout d'utilisateurs, consultez [Constituer une équipe](/docs/services/watson-knowledge-studio/team.html).
Pour des informations sur la définition d'une limite de
stockage, consultez [Dépannage, assistance et FAQ > Problèmes d'espace de stockage](/docs/services/watson-knowledge-studio/troubleshooting.html#storage).
- Ajout d'une page Performances pour l'évaluation de la qualité du modèle et des conseils sur la façon de l'améliorer.

## Novembre 2017
{: #november2017}

### Changements 
{: #new-november2017}

- Correction d'un problème où il manquait certaines annotations de relations dans les corpus téléchargés.
- Correction d'un problème où un modèle ne pouvait pas être retiré du déploiement si son statut était **Aucun**.
- Correction d'un problème où le modèle ne pouvait pas être évalué pour le coréen.

## Octobre 2017
{: #october2017}

### Changements 
{: #new-october2017}

- Correction du problème où le bouton **Exporter** n'était pas activé tant que l'utilisateur
n'actualisait pas sa fenêtre de navigateur dans l'édition
[expérimentale](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)
d'{{site.data.keyword.Bluemix_notm}}. 
- Correction des libellés et des infobulles des boutons pour tenir compte de l'usage
des nouveaux termes _transférer_ (upload) et _télécharger_ (download)
dans l'édition [expérimentale](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)
d'{{site.data.keyword.Bluemix_notm}}.
Ces termes remplacent les termes _importer_ et _exporter_ lorsqu'il est
question des systèmes de types, des documents et des dictionnaires.

- Correction du retard de mise à jour des
descriptions sur la page {{site.data.keyword.knowledgestudioshort}} User Account Management (gestion des comptes d'utilisateurs)
dans l'édition [expérimentale](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)
d'{{site.data.keyword.Bluemix_notm}}.

- Quelques changements ont été apportés dans la section pré-annotation de l'interface graphique
pour clarifier les fonctionnalités du modèle d'apprentissage automatique, du modèle à base de règles, du dictionnaire
et d'{{site.data.keyword.alchemylanguagefull}}.
Le libellé de bouton **Exécuter** est devenu **Pré-annoter**, le titre
de fenêtre **Exécuter un annotateur** est devenu **Exécuter la pré-annotation**,
et le message d'erreur a été revu pour clarifier le fait que vous ne pouvez pas ajouter d'annotations automatisées
à des documents une fois que ceux-ci ont été annotés par des humains.

- Pour les projets ou espaces de travail utilisant des analyseurs lexicaux à base de dictionnaires,
un problème a été corrigé, qui faisait apparaître des phrases vides dans les documents si ceux-ci étaient importés sans données de référence.


## Septembre 2017
{: #september2017}

### Nouvelles fonctionnalités et changements
{: #new-sept17}

- Une nouvelle expérience utilisateur du frontal pour {{site.data.keyword.knowledgestudioshort}} sur {{site.data.keyword.Bluemix}}
a été publiée en tant que service [expérimental](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental).
Parmi les changements figurent une navigation réorganisée et une nouvelle page d'analyse des performances du modèle.
Pour une synthèse des changements apportés à la navigation, consultez le tableau dans la section Problèmes connus ci-dessous.

- Le support multilingue s'est enrichi du chinois (simplifié) et du néerlandais.

### Problèmes connus
{: #issues-sept17}

- Dans le cas d'un modèle à base de règles,
une fois que vous avez associé vos types d'entités aux classes, le bouton **Exporter** n'est pas activé
tant que vous n'actualisez pas la fenêtre du navigateur.

- Dans l'édition [expérimentale](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)
version {{site.data.keyword.Bluemix_notm}}, certains termes utilisés dans la
documentation ne correspondent pas à ceux de la nouvelle interface.
La documentation correspond en réalité à l'interface du produit version {{site.data.keyword.IBM_notm}} Marketplace.
Les termes suivants ont changé dans l'édition [expérimentale](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) :


| Terme dans {{site.data.keyword.IBM_notm}} Marketplace | Terme dans {{site.data.keyword.Bluemix_notm}} | Remarques |
|----------|----------|----------|
| _projet_ | _espace de travail_ | Ce changement vient du fait que le terme _projet_ est également utilisé dans {{site.data.keyword.Bluemix_notm}}. |
| _importer_ et _exporter_ | _transférer_ et _télécharger_ | Les termes _importer_ et _exporter_ sont
désormais remplacés par _transférer_ et _télécharger_ lorsqu'il est question de documents ou
de types d'entités.
Le terme _exporter_ est toujours utilisé lorsqu'il est question d'exporter un modèle vers une
application telle que {{site.data.keyword.watson}} Explorer. |
{: caption="Tableau 1. Changements de terminologie dans la version {{site.data.keyword.Bluemix_notm}}" caption-side="top"}

- Dans l'édition [expérimentale](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental)
version {{site.data.keyword.Bluemix_notm}}, certaines étapes des tâches décrites dans la
documentation ne correspondent pas exactement à ce que vous devez faire dans la nouvelle interface.
La documentation correspond en réalité à l'interface du produit version {{site.data.keyword.IBM_notm}} Marketplace.
Le tableau suivant dresse la liste des changements apportés à la navigation
dans l'édition [expérimentale](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) :


| Fonction | Emplacement dans {{site.data.keyword.IBM_notm}} Marketplace | Emplacement dans {{site.data.keyword.Bluemix_notm}}
|----------|----------|----------|
|Composant annotateur (onglet) | Navigation principale | N'existe plus |
|Matrice de confusion (tableau) (dans l'onglet Statistiques) | Composant annotateur > Détails | Gestion des modèles > Performances > Statistiques détaillées (lien) |
|Dictionnaires (onglet) | Navigation principale | Actifs & Outils > Pré-annotateurs |
|Mappage de dictionnaires (page) | Composant annotateur | Actifs & Outils > Pré-annotateurs |
|Types d'entités (onglet) | Système de types | Actifs & Outils > Types d'entités |
|Editeur de données de référence | Annotation humaine | Annotation de document (onglet) |
|Paramètres de l'éditeur de données de référence (onglet) | Annotation humaine | Paramètres > Paramètres d'annotation de document |
|Modèles, exécution et exportation | Composant annotateur | Gestion des modèles > Versions |
|Règles (onglet) | Navigation principale | Annotation de document > Règles |
|Statistiques (onglet) | Composant annotateur > Détails | Gestion des modèles > Performances |
|Récapitulatif (tableau) (dans l'onglet Statistiques) | Composant annotateur > Détails | Gestion des modèles > Performances > Statistiques détaillées (lien) |
|Mappage des types (onglet) (pour le modèle à base de règles) | Composant annotateur > Détails | Gestion des modèles > Versions > Mappage de type de modèle à base de règles |
{: caption="Tableau 2. Changements apportés à la navigation dans la version {{site.data.keyword.Bluemix_notm}}" caption-side="top"}

## Juillet 2017
{: #july2017}

- Correction d'un défaut qui, dans certains cas, faisait disparaître l'en-tête.
- Application de mises à jour de sécurité pour les composants de l'infrastructure.

## Juin 2017
{: #june2017}

- Amélioration de la stabilité pour la prise en charge de gros volumes de données dans certaines conditions.
- Correction d'un défaut pour une erreur d'arbitrage.

## Mai 2017
{: #may2017}

- Ajout de la possibilité de renommer différents objets tels que projets, jeux de documents, etc.
- Ajout de la possibilité de déployer des modèles NLU dans des régions {{site.data.keyword.Bluemix}} spécifiques.
- Amélioration des performances d'affichage de grands tableaux pour l'IAA (convergence entre annotateurs).
- Correction de défauts mineurs.
- Application de correctifs de sécurité.

## Avril 2017
{: #april2017}

- Amélioration de la stabilité pour {{site.data.keyword.knowledgestudioshort}} Premium.
- Ajout de l'analyse des usages pour les métriques métier.

## Editions antérieures à avril 2017

Consultez [{{site.data.keyword.IBM_notm}} tech note #1986001 ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://www.ibm.com/support/docview.wss?uid=swg21986001){: new_window}.
