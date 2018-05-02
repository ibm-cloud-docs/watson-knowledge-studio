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
ce lien ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/docs/services/knowledge-studio/backup-restore.html){: new_window}.
{: tip}

# Sauvegarder et restaurer des données
{: #backup-restore}

Si vous avez besoin de sauvegarder un espace de travail {{site.data.keyword.knowledgestudioshort}} dans le
but de pouvoir le restaurer ensuite, effectuez ces tâches.
Effectuez-les également si vous devez faire migrer manuellement vos données
d'une instance {{site.data.keyword.knowledgestudioshort}} vers une autre,
par exemple en cas de migration d'une instance sur {{site.data.keyword.IBM_notm}} Marketplace vers
une instance sur {{site.data.keyword.cloud_notm}}.
{: shortdesc}

On appelle _migration manuelle_ le procédé consistant à sauvegarder les données d'une instance et à les restaurer
sur une autre instance.


**Remarque **: Le terme _espace de travail_
est utilisé dans {{site.data.keyword.knowledgestudioshort}} sur {{site.data.keyword.cloud_notm}}, alors que
dans {{site.data.keyword.knowledgestudioshort}} sur {{site.data.keyword.IBM_notm}} Marketplace, on parle de _projet_.
La fonctionnalité est la même.
Seule la terminologie est différente.

Pour sauvegarder et restaurer vos données, effectuez les étapes suivantes :


1. [Découvrez quelles données peuvent être sauvegardées](#data)
1. [Préparez la sauvegarde](#prepare)
1. [Exportez les artefacts de l'instance en cours](#export)
1. [Recréez les espaces de travail sur la nouvelle instance](#recreateproj)
1. [Restaurez les données des espaces de travail](#restoredata)
1. [Restaurez les modèles](#restoremodels)
1. [Restaurez les éventuelles tâches d'annotation incomplètes](#restoretasks)

## Les données qui peuvent être sauvegardées
{: #data}

Les artefacts suivants peuvent être sauvegardés et migrer manuellement : 

- Dictionnaires éditables
- Système de types
- Jeux de documents de référence approuvés

Les artefacts suivants ne peuvent pas être sauvegardés ni migrer manuellement : 

- Documents pour lesquels l'annotation humaine est en cours
- Tâches d'annotation
- Modèes et instantanés
- Dictionnaires en lecture seule

## Préparer la sauvegarde
{: #prepare}

Pour préparer la sauvegarde et la restauration de vos données, effectuez les étapes suivantes :


1. Terminez tout travail en cours dans votre espace de travail.

    - > **Important :** Finissez les taches d'annotation en cours.
Seuls peuvent être sauvegardés les documents qui ont été annotés, soumis à arbitrage, approuvés et promus au rang de
documents de référence.
Si le travail d'annotation n'est pas terminé, vous perdrez tout le bénéfice de l'effort d'annotation qui n'est pas totalement achevé.


    - Si vous avez créé des tâches d'annotation dans le but de suivre le travail à réaliser, mais que celui-ci n'a pas
commencé et qu'il n'est pas prévu qu'il commence avant que l'espace de travail ne soit restauré,
faites la liste des tâches d'annotation en attente.
Veillez à noter quels jeux de documents ont été importés mais n'ont pas encore été ajoutés aux données de référence.
Pensez également à noter qui vous avez affecté à l'annotation de chaque jeu de documents.
Une fois l'espace de travail restauré, il vous faudra retransférer ces jeux de documents et recréer
les tâches d'annotation.


1. Déterminez quels analyseurs lexicaux sont utilisés.

    L'espace de travail d'un modèle d'apprentissage automatique utilise, par défaut,
l'analyseur lexical à base d'apprentissage automatique.
Si vous avez opté pour un analyseur lexical à base de dictionnaires et que vous avez
de bonnes raisons de continuer ainsi, vous pourrez configurer en conséquence l'espace de travail
lorsque vous l'aurez restauré.
Pour plus d'informations, consultez [Analyseurs lexicaux](/docs/services/watson-knowledge-studio/create-project.html#wks_tokenizer).

1. Gérez les ressources du modèle.

    Votre modèle, ses versions et ses données d'instantané ne peuvent pas
migrer.
Ce sont les ressources (excepté les dictionnaires en lecture seule) que vous avez utilisées
pour entraîner ces artefacts qui peuvent migrer.
Vous pourrez donc recréer le modèle après leur migration.
Le modèle obtenu fonctionnera de manière identique aux modèles que vous avez générés avant la migration, car
les ressources utilisées pour l'entraîner seront les mêmes.


    **ATTENTION **: Si vous avez un modèle qui est déjà déployé et que vous comptez
supprimer l'espace de travail après l'avoir sauvegardé, retirez ce modèle du déploiement.
Vous pourrez reconstruire et redéployer le modèle après avoir restauré l'espace de travail à partir
de la sauvegarde.
Pour des informations sur le retrait de modèles du déploiement,
consultez [Retirer des modèles d'apprentissage automatique du déploiement](/docs/services/watson-knowledge-studio/publish-ml.html#undeploy-view-model)
et [Retirer des modèles à base de règles du déploiement](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html#undeploy-view-model).

    **Sachez que si vous omettez de retirer le modèle du déploiement, le modèle déployé deviendra _orphelin_.
Les modèles déployés orphelins continueront à générer des frais sur vos factures mensuelles.**

1. Gérez les dictionnaires en lecture seule.

    Les dictionnaires en lecture seule ne peuvent pas migrer.
Si vous en utilisez, déterminez d'où ils ont été importés afin de pouvoir les retransférer dans votre espace de travail une fois celui-ci restauré.


1. Dressez la liste des rôles d'utilisateur actuels.

    **REMARQUE **: Cette étape est optionnelle.
Elle est surtout utile lorsqu'un espace de travail doit migrer à l'identique d'une instance à une autre.
Vous pouvez l'omettre si vous souhaitez seulement faire migrer les données de votre espace de travail pour les restaurer dans un nouvel espace de travail.


    Si vous faites migrer un espace de travail d'une instance à une autre,
faites la liste des utilisateurs et de leurs rôles respectifs dans l'instance d'origine (celle de l'espace de travail que vous sauvegardez).
Cette liste peut être imprimée par une personne ayant le rôle Admin à partir
de la page User Account Management (gestion des comptes d'utilisateur).
Une fois l'espace de travail recréé sur la nouvelle instance, un administrateur (rôle Admin) devra
y ajouter les utilisateurs et leur réattribuer les rôles qu'ils avaient dans l'espace d'origine.


    Pour plus d'informations sur les rôles, consultez [Constituer une équipe](/docs/services/watson-knowledge-studio/team.html).


1. Prenez note des informations concernant l'espace de travail.

    Pendant que vous avez encore accès à l'instance en cours, prenez note des informations suivantes pour
chaque espace de travail que vous comptez faire migrer :

    - Nom de l'espace de travail 
    - Description de l'espace de travail
    - Propriétaire de l'espace de travail
    - Langue 
    - S'il y a des tâches d'annotation incomplètes, sachant qu'il n'est pas possible de les sauvegarder ou de les faire
migrer, notez à quels annotateurs humains elles sont affectées dans l'espace de travail.
Notez également tous les détails les concernant, tels que leur nom, leur date d'exigibilité et quels jeux de documents sont
affectés à quels utilisateurs.


## Télécharger les artefacts
{: #export}

Pour chaque espace de travail que vous faites migrer, téléchargez les artefacts suivants.
Stockez-les dans un endroit sûr, à partir duquel vous pourrez les transférer ultérieurement vers la nouvelle instance.


- Système de types
- Dictionnaires

  **Remarque **: Seuls les dictionnaires éditables seront téléchargés.
Les dictionnaires en lecture seule ne se téléchargent pas.


- Documents

  Pour des informations sur la façon de télécharger ces artefacts afin qu'ils
puissent être importés dans un nouvel espace de travail, consultez
[Transférer des ressources d'un autre espace de travail](/docs/services/watson-knowledge-studio/exportimport.html).

## Recréer les espaces de travail
{: #recreateproj}

**REMARQUE **: Dans cette étape, le seul réglage qui doit être rétabli à l'identique dans
le nouvel espace de travail est la langue.
Les autres réglages peuvent être différents de ceux de l'espace d'origine.


Recréez chaque espace de travail en copiant les informations suivantes de l'instance précédente à la nouvelle :


- Nom de l'espace de travail 
- Description de l'espace de travail
- Langue des documents (doit être la même que celle de l'espace d'origine)
- Si un analyseur lexical à base de dictionnaires était jusqu'à présent utilisé dans l'espace de
travail d'origine et que vous avez une raison valable de continuer à le faire, c'est au moment
de créer le nouvel espace de travail que vous devez indiquer que vous souhaitez utiliser ce
type d'analyseur lexical à la place de l'analyseur par défaut.
Pour plus d'informations sur les options, consultez [Analyseurs lexicaux](/docs/services/watson-knowledge-studio/create-project.html#wks_tokenizer).

  Pour utiliser un analyseur lexical à base de dictionnaires,
développez la section Options avancées de la fenêtre
Créer un espace de travail (dans {{site.data.keyword.IBM_notm}} Marketplace, elle s'intitule Créer un projet)
et changez le choix d'analyseur lexical.


## Restaurer les données des espaces de travail
{: #restoredata}

Après avoir recréé les espaces de travail, transférez les artefacts précédemment téléchargés :


1. Transférez le système de types à partir de sa sauvegarde créée précédemment.
Pour les détails, consultez [Transférer des ressources d'un autre espace de travail](/docs/services/watson-knowledge-studio/exportimport.html).

  **Remarque **: Vous devez transférer le système de types avant de transférer tout autre artefact que vous déplacez
de l'espace de travail sauvegardé.


1. Transférez les dictionnaires à partir de leur sauvegarde créée précédemment.
Pour les détails, consultez [Transférer des ressources d'un autre espace de travail](/docs/services/watson-knowledge-studio/exportimport.html).

  Si vous utilisiez des dictionnaires en lecture seule dans la version précédente de l'espace de travail,
retransférez-les dans le nouvel espace à partir de leur source d'origine.


  **Remarque **: Lorsque vous ajoutez des dictionnaires, le pré-annotateur à base de dictionnaire
est automatiquement créé.
Lorsque vous exécutez ce pré-annotateur, vous devez associer un dictionnaire à un type d'entité du
système de types.


1. Transférez dans cette version de l'espace de travail les documents que vous avez téléchargés de la version précédente de l'espace de travail.
Pour les détails, consultez [Transférer des ressources d'un autre espace de travail](/docs/services/watson-knowledge-studio/exportimport.html).

## Restaurer les modèles
{: #restoremodels}

A ce stade, tous les artefacts qui servaient à entraîner le modèle dans la version précédente (sauvegardée) de
l'espace de travail sont maintenant disponibles dans cette nouvelle instance.


Pour redéployer un modèle d'apprentissage automatique que vous avez déployé dans l'instance précédente,
effectuez les étapes suivantes :


1. Entraînez le modèle d'apprentissage automatique.
Pour les détails, consultez [Créer un modèle d'apprentissage automatique](/docs/services/watson-knowledge-studio/train-ml.html).

  **Remarque **: N'exécutez pas de pré-annotateur sur des
documents annotés que vous avez fait migrer dans cet espace de travail, car vous perdriez toutes les annotations que les annotateurs humains y ont ajoutées.


1. Après avoir créé le modèle, déployez-le à nouveau.
Pour les détails, consultez [Utiliser le modèle d'apprentissage automatique](/docs/services/watson-knowledge-studio/publish-ml.html).

Pour redéployer un modèle à base de règles que vous avez déployé dans l'instance précédente,
effectuez les étapes suivantes :


1. [Créez le modèle à base de règles](/docs/services/watson-knowledge-studio/rule-annotator-model-create.html).
1. [Déployez le modèle à base de règles](/docs/services/watson-knowledge-studio/rule-annotator-model-use.html).

## Restaurer les tâches d'annotation incomplètes
{: #restoretasks}

Si des tâches d'annotation étaient en cours et n'ont pas été achevées dans l'espace de travail précédent,
effectuez les étapes suivantes pour les recréer :


1. Transférez les éventuels documents qui n'ont pas encore été annotés, mais que vous souhaitez ajouter aux données de référence pour
continuer à améliorer le modèle.

1. A partir des documents nouvellement importés et non annotés, créez des jeux de documents
en vue de leur annotation.
Ces jeux sont maintenant appelés _jeux d'annotations_.
Pour les détails,
consultez [Créer et affecter des jeux d'annotations](/docs/services/watson-knowledge-studio/document-for-annotation.html).
1. Recréez les tâches d'annotation.
Donnez-leur le même nom que dans l'espace précédent, fixez leur date d'exigibilité et
affectez les jeux d'annotations aux annotateurs humains appropriés.

