---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-19"

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

Cette documentation concerne {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Pour consulter la documentation de la version précédente de {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [cliquez sur ce lien ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/docs/services/knowledge-studio/improve-ml.html){: new_window}.
{: tip}

# Faire progresser le modèle d'apprentissage automatique
{: #improve-ml}

Après avoir déterminé les domaines dans lesquels le modèle est en difficulté, prenez quelques mesures pour améliorer ses performances.
{: shortdesc}

## Créer des versions du modèle
{: #wks_maversions}

Après avoir créé un modèle d'apprentissage automatique, vous pouvez en prendre un instantané afin de conserver une version de sauvegarde des ressources actuelles, au cas où vous voudriez les restaurer dans une future itération.

### A propos de cette tâche
{: #wks_maversions_about}

Le score F1 fournit une indication de la qualité du modèle. Si les résultats du modèle témoignent de bonnes performances, vous voudrez peut-être stocker une version du composant avant de changer ses ressources. Ainsi, s'il s'avère que vos changements dégradent la qualité, vous pourrez revenir à la version que vous avez stockée. Lorsque vous revenez à une version plus ancienne, toutes les tâches d'annotation sont archivées, car elles ne sont plus valides.

Vous pouvez avoir un maximum de 10 versions dans un espace de travail. Si vous atteignez cette limite, pour pouvoir créer une nouvelle version, supprimez d'anciennes versions ou celles dont vous n'avez plus l'utilité.

Lorsque vous créez une nouvelle version, les ressources suivantes sont capturées :

- Le système de types
- Le corpus
- Les données de référence
- Le modèle d'apprentissage automatique
- Les résultats d'évaluation du modèle d'apprentissage automatique

Les ressources suivantes sont exclues :

- Les tâches d'annotation, car elles ne servent qu'un temps, pour déterminer les données de référence
- Les dictionnaires, car ils peuvent être gros et de différents types qui ne se gèrent pas de la même façon

### Procédure
{: #wks_maversions_procedure}

Pour créer et restaurer des versions du modèle d'apprentissage automatique :

1. Connectez-vous en tant qu'administrateur ou chef de projet {{site.data.keyword.knowledgestudioshort}} et sélectionnez votre espace de travail.
1. Sélectionnez **Modèle d'apprentissage automatique** > **Performances**.Les statistiques de performances de la version actuelle, libellée version 1.0, sont affichées.
1. Pour prendre un instantané de la version actuelle, cliquez sur **Modèle d'apprentissage automatique** > **Versions**, puis sur **Prendre un instantané**. Les ressources de la version 1.0 sont gelées et une nouvelle version, libellée 1.1, devient la version actuelle. A chaque nouvelle version que vous créez, le numéro de version mineure est incrémenté. Par exemple, vous passez de la version 1.0 à la version 1.1, puis à la version 1.2, et ainsi de suite.
1. Révisez les ressources de l'espace de travail selon nécessité, réentraînez le modèle et réévaluez-le.
1. Si vous êtes satisfait des performances du modèle et que vous souhaitez en stocker une nouvelle version avant d'entreprendre d'autres changements, créez une autre version. Continuez à réviser les ressources et à réentraîner le modèle selon nécessité, en créant une nouvelle version pour chaque itération que vous voulez conserver.
1. Si les résultats obtenus sont moins bons et que vous voulez revenir à une version précédente avant de tester davantage le modèle :

    1. Ouvrez la page **Actifs** > **Dictionnaires** et téléchargez les dictionnaires que vous voulez réutiliser dans le modèle restauré.
    1. Cliquez sur **Modèle d'apprentissage automatique** > **Versions**, puis sur **Promouvoir** pour la version que vous souhaitez restaurer. La version promue devient la version actuelle, et le numéro de version passe à 2.0. Lorsque vous promouvez une version, le numéro de version majeure est incrémenté et le numéro de version mineure repasse à 0. Par exemple, si vous étiez à la version 1.1, vous passez à la version 2.0.
    1. Ouvrez la page **Dictionnaires** et transférez les dictionnaires que vous avez téléchargés.
    1. Si le test de la nouvelle version nécessite d'apporter des changements aux données de référence, ouvrez la page **Modèle d'apprentissage automatique** > **Tâches d'annotation** et créez une nouvelle tâche d'annotation.

## Modifier un système de types sans perdre les annotations humaines
{: #wks_projtypesysmod}

En fonction des statistiques de performances, il est possible que vous deviez effectuer des modifications pendant l'entraînement d'un modèle. Cependant, le plus souvent, avant de commencer les tâches d'annotation à grande échelle, vous avez tout intérêt à ce que le système de types soit aussi proche que possible de sa version définitive. Si vous changez le système de types alors que les annotateurs humains ont déjà commencé leur travail, ils devront revoir les documents qu'ils ont annotés. Il leur faudra en effet évaluer l'applicabilité des changements opérés dans le système de types.

### A propos de cette tâche
{: #wks_projtypesysmod_about}

Ce processus propage le système de types actuel, les raccourcis clavier de l'éditeur de données de référence et les réglages de couleurs en vigueur à tous les jeux de documents d'une tâche.

### Procédure
{: #wks_projtypesysmod_procedure}

Pour modifier le système de types sans perdre le travail des annotateurs humains :

1. Apportez les changements voulus au système de types. Par exemple, vous pouvez ajouter ou retirer des types d'entités ou des types de relations.
1. Décidez si vous voulez propager les changements aux tâches d'annotation humaine existantes.
1. Sur la page **Modèle d'apprentissage automatique** > **Tâches d'annotation**, ouvrez chaque tâche que vous voulez mettre à jour et cliquez sur **Appliquer les mises à jour de système de types**.

    Si vous avez retiré des types d'entités ou des types de relations du système de types, toutes les occurrences de ces types sont surlignées en gris dans les documents. N'étant plus valides, ces types seront ignorés par le modèle d'apprentissage automatique. Ils ne vous empêcheront pas de soumettre et d'approuver des jeux de documents.

1. Fournissez aux annotateurs humains des détails sur ce qui a changé dans le système de types.
1. Demandez aux annotateurs humains de mettre à jour leurs documents afin d'y refléter les changements du système de types. Par exemple, si le système de types a été enrichi de nouveaux types d'entités ou de relations, ils doivent passer en revue leurs documents et les annoter en conséquence.

    > **Remarque :** Si la tâche contient des documents terminés, les annotateurs humains ne peuvent pas modifier ceux-ci pour évaluer les changements du système de types tant qu'ils ne sont pas ramenés à l'état éditable. Pour qu'ils redeviennent éditables, demandez aux annotateurs humains de soumettre les jeux de documents afin que vous puissiez les rejeter.

**Concepts connexes** :
{: #wks_projtypesysmod_related}

[Systèmes de types](/docs/services/watson-knowledge-studio/typesystem.html#wks_typesystem)

## Gestion des jeux de documents
{: #wks_mamanagedata}

Utilisez les bons jeux de données pour tester et entraîner le modèle au bon moment.

Lorsque vous créez un modèle d'apprentissage automatique, les documents que vous ajoutez au système doivent être affectés aux jeux de données de niveau système suivants :

- **Jeu d'entraînement**

    Jeu de documents qui ont été annotés via la pré-annotation ou par les annotateurs humains et qui sert à entraîner le modèle. Le but du jeu d'entraînement est d'enseigner les annotations correctes au modèle d'apprentissage automatique. Une part de cet enseignement se fait avec du texte qui n'a pas été annoté.

- **Jeu de test**

    Jeu de documents annotés qui sert à tester le modèle entraîné. Après avoir exécuté un test sur le jeu de test, effectuez une analyse d'erreur détaillée des résultats dans un but de diagnostic. Une analyse approfondie vous aidera à trouver dans le modèle actuel les faiblesses qui peuvent être corrigées.

- **Jeu aveugle**

    Jeu de documents annotés qui est mis de côté et utilisé pour tester le système périodiquement après plusieurs itérations de tests et d'améliorations. Pour éviter que l'exactitude ne soit biaisée (par exemple, par des changements basés uniquement sur les annotations dans des documents connus), les données aveugles doivent être des données qui n'ont jamais été vues auparavant par les utilisateurs impliqués dans la création du modèle. Les résultats rapportés ne doivent provenir que de tests réalisés sur des données aveugles. Après avoir exécuté un test sur le jeu aveugle, ne regardez que les scores les plus élevés, tels que les scores F1 globaux des mentions et des relations. Il ne faut pas apprendre trop de détails sur les performances, car cela pourrait influencer les améliorations que vous choisissez d'apporter au modèle.

L'objectif de {{site.data.keyword.knowledgestudioshort}} est de permettre à de grandes équipes de collaborer à la construction de modèles. En tant que tel, il suppose que les modèles sont produits par une équipe qui comprend un groupe d'annotateurs humains et une personne ou un groupe de personnes à part, qui construit et teste le modèle et y apporte des améliorations. En raison de cette hypothèse, l'application est configurée pour pousser un groupe également proportionné de documents d'un même jeu de documents vers les jeux de test, d'entraînement et aveugle. Toutefois, si votre équipe n'est pas cloisonnée (par exemple, si les personnes en charge de l'annotation humaine examinent aussi les résultats des tests du modèle en détail), vous devrez peut-être adapter la répartition des documents dans ces jeux afin de séparer plus explicitement les documents utilisés dans chacun d'eux.

### Pourquoi ai-je besoin d'un jeu aveugle ?
{: #wks_mamanagedata_why}

Comme vous utilisez des données de test pour évaluer l'exactitude en détail, au bout d'un certain temps, vous finissez par connaître les documents et leurs caractéristiques. Par exemple, vous commencez à savoir quels types d'entités, types de relations et types de textes dans les documents sont les mieux compris par le modèle d'apprentissage automatique, et lesquels le sont moins bien. Cette information est importante dans la mesure où elle vous aide à identifier les leviers sur lesquels agir ; par exemple, raffiner le système de types, compléter les données de formation pour combler les lacunes ou ajouter des dictionnaires. Mais à mesure que les documents de test sont utilisés itérativement pour améliorer le modèle, ils peuvent commencer à influencer indirectement son entraînement. C'est pourquoi le jeu de documents "aveugle" est si important.

### Comment puis-je contrôler quels documents sont affectés à un jeu ?
{: #wks_mamanagedata_how}

Lorsque vous créez un modèle d'apprentissage automatique, vous devez spécifier la proportion de documents de l'ensemble à affecter aux jeux d'entraînement, de test et aveugle. {{site.data.keyword.knowledgestudioshort}} applique automatiquement un ratio de 70/23/7 aux jeux de documents que vous utilisez pour construire un modèle d'apprentissage automatique. Vous pouvez changer ces valeurs.

- Pour ajouter un jeu ayant été annoté par des humains au jeu d'entraînement, spécifiez une répartition de 100/0/0.
- Après l'entraînement avec un jeu, vous pouvez utiliser celui-ci pour le test. Pour utiliser un jeu de documents exclusivement pour le test, spécifiez une répartition de 0/100/0.
- N'ajoutez au jeu aveugle qu'un jeu de documents qui n'a jamais servi pour l'entraînement ou le test. Pour cela, spécifiez une répartition de 0/0/100 pour le jeu de documents.

Prévoyez de cesser d'utiliser un jeu aveugle après quelques itérations. Plus vous utilisez un jeu aveugle, moins il devient "aveugle". Il en va de même pour vos données de test. Plutôt que de mettre à l'écart les jeux, vous pouvez les faire migrer vers un nouveau rôle. Suivez ce trajet de migration :

```
aveugle --> test --> entraînement
```
{: screen}

A mesure que les jeux migrent, vous pouvez ajouter, en tant que données aveugles et en tant que données de test, de nouveaux jeux de documents jamais vus auparavant. Mais assurez-vous de retenir une méthode d'évaluation de l'exactitude pour toutes les versions du modèle. Une façon d'établir une ligne de base est d'exécuter une version antérieure du modèle sur les nouveaux jeux de documents. Les résultats de cette exécution vous donneront une base de comparaison avec les exécutions de versions plus récentes du modèle sur ces mêmes jeux.
