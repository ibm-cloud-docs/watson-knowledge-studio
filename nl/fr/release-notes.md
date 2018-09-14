---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-09"

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

Cette documentation concerne {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Pour consulter la documentation de la version précédente de {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [cliquez sur ce lien ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/docs/services/knowledge-studio/release-notes.html){: new_window}.
{: tip}

# Notes sur l'édition
{: #release-notes}

Les nouvelles fonctionnalités et modifications suivantes sont disponibles dans {{site.data.keyword.knowledgestudiofull}}.
{: shortdesc}

## Août 2018
{: #august2018}

### Nouvelles fonctionnalités et changements
{: #new-august2018}

- Une nouvelle option a été introduite pour automatiser la migration des instances avec plan Standard de la plateforme {{site.data.keyword.IBM_notm}} Marketplace (aujourd'hui dépréciée) vers la plateforme [{{site.data.keyword.cloud_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/blogs/bluemix/2017/12/watson-knowledge-studio-ibm-cloud/){: new_window}. Si vous avez une instance Standard sur l'ancienne plateforme, vous aurez la possibilité de la faire migrer. Pour plus d'informations, consultez [Migrer sur {{site.data.keyword.cloud_notm}}](/docs/services/watson-knowledge-studio/client-migration.html).

## Juillet 2018
{: #july2018}

### Nouvelles fonctionnalités et changements
{: #new-july2018}

- La page **Modèles déployés** a été mise à jour pour inclure les modèles des instances de {{site.data.keyword.knowledgestudioshort}} gérés par les [*groupes de ressources* IAM ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/docs/iam/users_roles.html){: new_window}, en complément des modèles gérés par les [*organisations* Cloud Foundry ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/docs/iam/cfaccess.html){: new_window}.

   Ce que vous voyez sur la page Modèles déployés dépend de la [région ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/docs/resources/services_region.html){: new_window} qui héberge votre instance {{site.data.keyword.knowledgestudioshort}}. Si la région prend en charge les instances gérées par les deux méthodes de gestion des accès, un onglet est visible pour chaque méthode. Les modèles des instances gérées par IAM sont listés sous l'onglet **Groupes de ressources**. Les modèles des instances gérées par Cloud Foundry sont listés sous l'onglet **Organisations**. 

  Si la région prend en charge les instances gérées par seulement une des deux méthodes de gestion des accès, vous ne voyez qu'une seule liste de modèles, car une seule méthode de gestion des accès est applicable.

   Pour afficher la page **Modèles déployés**, dans le menu **Paramètres** de la barre de menus, en haut à droite, cliquez sur **Gérer les modèles déployés**. Pour des informations sur le retrait de modèles du déploiement dans la page **Modèles déployés**, consultez [Retirer des modèles d'apprentissage automatique du déploiement](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model) et [Retirer des modèles à base de règles du déploiement](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model).

- La navigation a changé pour être en meilleure adéquation avec l'enchaînement d'opérations dans {{site.data.keyword.knowledgestudioshort}}. Les fonctionnalités suivantes ont également été réorganisées :

    - Dans la version précédente, la gestion des dictionnaires faisait partie de la page Pré-annotateurs. Elle est à présent située sur la page Dictionnaires, dans la section Actifs de la navigation.
    - Dans la version précédente, la fonctionnalité d'annotation humaine était répartie entre les onglets Mentions, Relations et Coréférences, dans la section Annotation de document de la navigation. Elle est à présent regroupée sous la page Tâches d'annotation, dans la section Modèle d'apprentissage automatique de la navigation.
    - Dans la version précédente, pour gérer les tâches d'annotation humaine, il fallait aller à l'onglet Tâches, sous la page Actifs & Outils > Documents. A présent, l'ajout de tâches et la gestion des tâches existantes se déroulent sous la page Tâches d'annotation, dans la section Modèle d'apprentissage automatique de la navigation.
    - Dans la version précédente, les pages Règles, Expressions régulières et Dictionnaires étaient des pages distinctes dans la section Annotation de document de la navigation. Elles sont à présent regroupées sous la page Règles, dans la section Modèle à base de règles de la navigation.

    Pour plus de détails sur les changements dans la navigation, référez-vous à la Figure 1 et au Tableau 3.

![Captures d'écran de l'ancienne navigation (à gauche) et de la nouvelle navigation (à droite).](images/nav3-0718.svg "Captures d'écran de l'ancienne navigation et de la nouvelle navigation. Les changements sont listés dans le Tableau 3 et détaillés dans le texte qui précède.") Figure 1. Captures d'écran de l'ancienne navigation (à gauche) et de la nouvelle navigation (à droite).

| Fonction | Emplacement précédent | Emplacement actuel |
|---------|--------------------------|----------------------|
| Tâches d'annotation | Actifs & Outils > Documents > Tâches | Modèle d'apprentissage automatique > Tâches d'annotation |
| Coréférences (onglet) | Annotation de documents | Modèle d'apprentissage automatique > Tâches d'annotation > tâche > jeu d'annotations > document |
| Dictionnaires (page) (gestion) | Actifs & Outils > Pré-annotateurs > Gérer les dictionnaires | Actifs |
| Dictionnaires (onglet) (association à des classes pour un modèle à base de règles) | Annotation de documents | Modèle à base de règles > Règles |
| Documents (page) | Actifs & Outils | Actifs |
| Types d'entités (page) | Actifs & Outils | Actifs |
| Mentions (onglet) | Annotation de documents | Modèle d'apprentissage automatique > Tâches d'annotation > tâche > jeu d'annotations > document |
| Performances (page) | Gestion des modèles | Modèle d'apprentissage automatique |
| Pré-annotateurs (page) | Actifs & Outils | Modèle d'apprentissage automatique > Pré-annotation |
| Expressions régulières (onglet) | Annotation de documents | Modèle à base de règles > Règles |
| Types de relation (page) | Actifs & Outils | Actifs |
| Relations (onglet) | Annotation de documents | Modèle d'apprentissage automatique > Tâches d'annotation > tâche > jeu d'annotations > document |
| Règles (onglet) | Annotation de documents | Modèle à base de règles |
| Tâches (onglet) | Actifs & Outils > Documents | Modèle d'apprentissage automatique > Tâches d'annotation |
| Versions (page) (modèle d'apprentissage automatique) | Gestion des modèles | Modèle d'apprentissage automatique |
| Versions (page) (modèle à base de règles) | Gestion des modèles | Modèle à base de règles |
{: caption="Tableau 3. Changements dans la navigation (juillet 2018)" caption-side="top"}

## Mai 2018
{: #may2018}

### Nouvelles fonctionnalités et changements
{: #new-may2018}

- Un problème de configuration a été corrigé, qui faisait que les instances de service dans la Région Sydney n'apparaissaient pas dans la Région Sud des Etats-Unis.
- Dans la fenêtre Déployer le modèle, si la région cible du déploiement prend en charge à la fois les *groupes de ressources* {{site.data.keyword.iamlong}} et les *espaces* Cloud Foundry, pour voir la liste, vous devez choisir la méthode de gestion des accès qu'utilise votre instance de service. Pour plus d'informations sur Cloud Foundry et {{site.data.keyword.iamshort}}, consultez [Resource Groups and Access Management ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/blogs/bluemix/2017/12/resource-groups-access-management/){: new_window}.
- Ajout d'une option Collecte de données sur la page Détails du service. Pour plus d'informations sur la collecte de données, consultez [Dépannage, assistance et FAQ](/docs/services/watson-knowledge-studio/troubleshooting.html#content)
- Le support multilingue s'est enrichi du chinois (traditionnel).
- Les utilisateurs ayant le rôle d'administrateur (Admin) peuvent à présent voir le nombre d'espaces de travail utilisés. Cette information est disponible sur la page Détails du service. 
- {{site.data.keyword.alchemylanguagefull}} n'est plus disponible comme cible de déploiement de modèles. Pour des informations, consultez [Retirement of {{site.data.keyword.alchemyapishort}} service ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/blogs/bluemix/2017/03/bye-bye-alchemyapi/){: new_window}.
- Dorénavant, si vous supprimez un espace de travail, il vous sera demandé de confirmer votre action. Le but est de prévenir les suppressions accidentelles.
- La documentation inclut des nouveautés à propos de la confidentialité des données personnelles. Lisez-en plus dans [Sécurité de l'information](/docs/services/watson-knowledge-studio/information-security.html).

## Avril 2018
{: #april2018}

### Nouvelles fonctionnalités et changements
{: #new-april2018}

- Le plan gratuit {{site.data.keyword.knowledgestudioshort}} a été remplacé par le plan Lite. Pour plus d'informations, consultez [Go Lite with Watson {{site.data.keyword.knowledgestudioshort}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/blogs/bluemix/2018/04/go-lite-watson-knowledge-studio/){: new_window}.

## Mars 2018
{: #march2018}

### Nouvelles fonctionnalités et changements
{: #new-march2018}

- Une page **Modèles déployés** est disponible, dans laquelle vous pouvez voir tous les modèles {{site.data.keyword.knowledgestudioshort}} déployés dans des services des espaces auxquels vous avez accès. Pour afficher la page **Modèles déployés**, dans le menu **Paramètres** de la barre de menus, en haut à droite, cliquez sur **Gérer les modèles déployés**. Pour des informations sur le retrait de modèles du déploiement et leur visualisation dans la page **Modèles déployés**, consultez [Retirer des modèles d'apprentissage automatique du déploiement](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model) et [Retirer des modèles à base de règles du déploiement](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model).
- Une traduction en français de l'interface de {{site.data.keyword.knowledgestudioshort}} est à présent disponible.
- {{site.data.keyword.alchemylanguagefull}} n'est plus disponible en tant que pré-annotateur. A la place d'{{site.data.keyword.alchemylanguageshort}}, vous pouvez utiliser {{site.data.keyword.nlushort}} pour pré-annoter vos documents. Pour plus d'informations, consultez [Amorcer le processus d'annotation](/docs/services/watson-knowledge-studio/preannotation.html).

## Décembre 2017
{: #december2017}

### Nouvelles fonctionnalités et changements
{: #new-december2017}

- Lancement de {{site.data.keyword.knowledgestudioshort}} sur {{site.data.keyword.cloud_notm}}. Pour des informations sur le processus de migration et sa planification, consultez [Migrer vers {{site.data.keyword.cloud_notm}}](/docs/services/watson-knowledge-studio/client-migration.html).
- Navigation repensée. Pour des détails sur les changements, consultez le [Tableau 2](#september2017) dans les notes sur l'édition de septembre 2017.
- Ajout d'{{site.data.keyword.nlufull}} en tant que pré-annotateur.
- Des paramètres de gestion des utilisateurs et de l'espace de stockage ont été ajoutés à la page Détails du service. Pour des informations sur l'ajout d'utilisateurs, consultez [Constituer une équipe](/docs/services/watson-knowledge-studio/team.html). Pour des informations sur la définition d'une limite de stockage, consultez [Dépannage, assistance et FAQ > Problèmes d'espace de stockage](/docs/services/watson-knowledge-studio/troubleshooting.html#storage).
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

- Correction du problème où le bouton **Exporter** n'était pas activé tant que l'utilisateur n'actualisait pas sa fenêtre de navigateur dans l'édition [expérimentale](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) d'{{site.data.keyword.Bluemix_notm}}.
- Correction des libellés et des infobulles des boutons pour tenir compte de l'usage des nouveaux termes _transférer_ (upload) et _télécharger_ (download) dans l'édition [expérimentale](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) d'{{site.data.keyword.Bluemix_notm}}. Ces termes remplacent les termes _importer_ et _exporter_ lorsqu'il est question des systèmes de types, des documents et des dictionnaires.
- Correction du retard de mise à jour des descriptions sur la page {{site.data.keyword.knowledgestudioshort}} User Account Management  (gestion des comptes d'utilisateurs) dans l'édition [expérimentale](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) d'{{site.data.keyword.Bluemix_notm}}.
- Quelques changements ont été apportés dans la section pré-annotation de l'interface graphique pour clarifier les fonctionnalités du modèle d'apprentissage automatique, du modèle à base de règles, du dictionnaire et d'{{site.data.keyword.alchemylanguagefull}}. Le libellé de bouton **Exécuter** est devenu **Pré-annoter**, le titre de fenêtre **Exécuter un annotateur** est devenu **Exécuter la pré-annotation**, et le message d'erreur a été revu pour clarifier le fait que vous ne pouvez pas ajouter d'annotations automatisées à des documents une fois que ceux-ci ont été annotés par des humains.
- Pour les projets ou espaces de travail utilisant des analyseurs lexicaux à base de dictionnaires, un problème a été corrigé, qui faisait apparaître des phrases vides dans les documents si ceux-ci étaient importés sans données de référence.

## Septembre 2017
{: #september2017}

### Nouvelles fonctionnalités et changements
{: #new-sept17}

- Une nouvelle expérience utilisateur du frontal pour {{site.data.keyword.knowledgestudioshort}} sur {{site.data.keyword.Bluemix}} a été publiée en tant que service [expérimental](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental). Parmi les changements figurent une navigation réorganisée et une nouvelle page d'analyse des performances du modèle. Pour une synthèse des changements apportés à la navigation, consultez le tableau dans la section Problèmes connus ci-dessous.
- Le support multilingue s'est enrichi du chinois (simplifié) et du néerlandais.

### Problèmes connus
{: #issues-sept17}

- Dans le cas d'un modèle à base de règles, une fois que vous avez associé vos types d'entités aux classes, le bouton **Exporter** n'est pas activé tant que vous n'actualisez pas la fenêtre du navigateur.
- Dans l'édition [expérimentale](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) d'{{site.data.keyword.Bluemix_notm}}, certains termes utilisés dans la documentation ne correspondent pas à ceux de la nouvelle interface. La documentation correspond en réalité à l'interface du produit version {{site.data.keyword.IBM_notm}} Marketplace. Les termes suivants ont changé dans l'édition [expérimentale](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) :

| Terme dans {{site.data.keyword.IBM_notm}} Marketplace | Terme dans {{site.data.keyword.Bluemix_notm}} | Remarques |
|----------|----------|----------|
| _projet_ | _espace de travail_ | Ce changement vient du fait que le terme _projet_ est également utilisé dans {{site.data.keyword.Bluemix_notm}}. |
| _importer_ et _exporter_ | _transférer_ et _télécharger_ | Les termes _importer_ et _exporter_ sont désormais remplacés par _transférer_ et _télécharger_ lorsqu'il est question de documents ou de types d'entités. Le terme _exporter_ est toujours utilisé lorsqu'il est question d'exporter un modèle vers une application telle que {{site.data.keyword.watson}} Explorer. |
{: caption="Tableau 1. Changements de terminologie dans la version {{site.data.keyword.Bluemix_notm}}" caption-side="top"}

- Dans l'édition [expérimentale](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) d'{{site.data.keyword.Bluemix_notm}}, certaines étapes des tâches décrites dans la documentation ne correspondent pas exactement à ce que vous devez faire dans la nouvelle interface. La documentation correspond en réalité à l'interface du produit version {{site.data.keyword.IBM_notm}} Marketplace. Le tableau suivant dresse la liste des changements apportés à la navigation dans l'édition [expérimentale](/docs/services/watson-knowledge-studio/troubleshooting.html#experimental) :

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
