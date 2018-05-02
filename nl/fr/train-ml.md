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

Cette documentation concerne {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Pour consulter la documentation de la version précédente de {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [cliquez sur ce lien ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/docs/services/knowledge-studio/train-ml.html){: new_window}.
{: tip}

# Entraîner le modèle d'apprentissage automatique
{: #train-ml}

Dans {{site.data.keyword.knowledgestudiofull}}, la création d'un modèle d'apprentissage automatique implique d'entraîner celui-ci, puis d'évaluer dans quelle mesure il a correctement annoté des données de test et des données aveugles.
{: shortdesc}

## Créer un modèle d'apprentissage automatique
{: #wks_madocsets}

Lorsque vous créez un modèle d'apprentissage automatique, vous devez sélectionner les jeux de documents à utiliser pour l'entraîner et spécifier les pourcentages de documents à utiliser comme données d'apprentissage, données de test et données aveugles.


### A propos de cette tâche

En explorant les métriques de performances, vous pouvez identifier différents moyens d'améliorer l'exactitude du modèle. 

> **Restriction :** Seuls trois annotateurs d'apprentissage automatique par instance {{site.data.keyword.knowledgestudioshort}} peuvent être entraînés à la fois. Si votre instance contient plusieurs espaces de travail et que trois annotateurs d'apprentissage automatique sont déjà en cours d'entraînement dans d'autres espaces de travail, votre demande d'entraînement du modèle dans votre propre espace sera mise en file d'attente jusqu'à ce que les autres entraînements soient terminés. 

### Procédure

Pour créer un modèle d'apprentissage automatique : 

1. Connectez-vous en tant qu'administrateur {{site.data.keyword.knowledgestudioshort}} et sélectionnez votre espace de travail. 
1. Sélectionnez **Gestion des modèles** > **Performances**.
1. Vérifiez que tous les jeux de documents ont été approuvés et que tous les conflits d'annotations ont été résolus par le biais d'un arbitrage. Seuls les documents qui sont devenus données de référence par le biais d'un arbitrage ou d'une approbation peuvent servir à entraîner le modèle. 
1. Cliquez sur **Entraîner et évaluer**.
1. Optionnel : pour spécifier comment les documents de vos jeux de documents doivent se répartir entre jeu d'entraînement, jeu de test et jeu aveugle, cliquez sur **Editer les paramètres**.

    Pour une aide à la détermination des ratios à appliquer, consultez [Gestion des jeux de documents](/docs/services/watson-knowledge-studio/improve-ml.html#wks_mamanagedata). 

1. Optionnel : associez tout dictionnaire que vous souhaiter voir utiliser par le modèle d'apprentissage automatique pendant son entraînement au type d'entité des entrées de ce dictionnaire. 

    Si vous avez créé un pré-annotateur à base de dictionnaire, vous avez déjà effectué cette étape. Dans ce cas, vous pouvez réutiliser la même association en cliquant sur l'option correspondante**** ou en définir une nouvelle. 

    Le modèle utilise le type d'information des termes du dictionnaire comme une caractéristique parmi les nombreuses caractéristiques d'analyse linguistique qu'il prend en compte durant son entraînement. 

1. Cliquez **Entraîner** pour entraîner le modèle, ou sur **Entraîner & évaluer** pour l'entraîner, évaluer les annotations qu'il a ajoutées aux documents et analyser ses statistiques de performances. 

    > **Important :** L'entraînement d'un modèle d'apprentissage automatique peut prendre plusieurs minutes. Il peut même prendre des heures. Tout dépend du nombre d'annotations humaines et du nombre total de mots, tous documents confondus. 

1. Sélectionnez les jeux de documents que vous voulez utiliser pour entraîner le modèle. 

    > **Remarque :** Les jeux de documents doivent contenir au moins 10 documents annotés. 

1. Une fois le modèle créé, choisissez l'une des actions suivantes : 

    <table border="1" frame="hsides" rules="rows" cellpadding="4" cellspacing="0" summary="Chaque ligne du tableau décrit une option" class="simpletable choicetable choicetableborder">
      <thead><tr><th id="d33883e137-option" valign="bottom" align="left" class="ncol thleft thbot">Option</th>
          <th id="d33883e137-desc" valign="bottom" align="left" class="ncol thleft thbot">Description</th></tr></thead>
      <tbody><tr class="strow chrow"><td valign="top" headers="d33883e137-option" id="d33883e139" class="stentry choption ncol"><p class="p wrapper"><strong>Journal</strong></p></td>
          <td valign="top" headers="d33883e137-desc d33883e139" class="stentry chdesc ncol"><p class="p wrapper">Permet de consulter le fichier journal pour
voir s'il y a eu des problèmes.</p></td>
        </tr>
        <tr class="strow chrow"><td valign="top" headers="d33883e137-option" id="d33883e144" class="stentry choption ncol"><p class="p wrapper"><strong>Détails</strong></p></td>
          <td valign="top" headers="d33883e137-desc d33883e144" class="stentry chdesc ncol"><p class="p wrapper">Permet de consulter
les statistiques de performances d'annotation, de changer les jeux de documents à utiliser pour
l'entraînement et le test du modèle et de créer des versions instantanées des artefacts
du modèle.
</p></td>
        </tr>
        <tr class="strow chrow"><td valign="top" headers="d33883e137-option" id="d33883e149" class="stentry choption ncol"><p class="p wrapper"><strong>Exporter</strong></p></td>
          <td valign="top" headers="d33883e137-desc d33883e149" class="stentry chdesc ncol"><p class="p wrapper">Permet d'exporter vers votre système local
un fichier <code>ZIP</code> contenant les composants dont le modèle a besoin pour fonctionner dans un environnement d'exécution
d'apprentissage automatique.
</p></td>
        </tr>
      </tbody>
    </table>

## Evaluer les annotations ajoutées par le modèle
{: #wks_matest}

Vous pouvez comparer la vue des données de référence, qui contient les annotations ajoutées par les annotateurs humains, aux annotations que le modèle a ajoutées. 

### Procédure

Pour évaluer les annotations ajoutées par le modèle : 

1. Sélectionnez **Gestion des modèles** > **Performances** > **Entraîner et évaluer**. La page Jeu d'entraînement / Jeu de test / Jeu aveugle apparaît. 
1. Cliquez sur **Afficher les données de référence** pour le jeu d'entraînement ou le jeu de test pour voir les annotations qui ont été ajoutées par la pré-annotation et par les annotateurs humains. L'éditeur de données de référence s'ouvre. Cliquez pour ouvrir un document et voir comment les mentions, relations et mentions coréférencées y ont été annotées. 
1. Sur la page **Performances**, cliquez sur **Afficher les résultats de décodage** pour voir les annotations que le modèle d'apprentissage automatique a ajoutées aux documents du jeu de test. Ce bouton n'est disponible qu'après l'évaluation du modèle. Les résultats affichés vous permettent de constater dans quelle mesure le modèle d'apprentissage automatique a bien étiqueté les mentions, les relations et les mentions coréférencées dans les données de test. 
1. Si vous voulez changer la répartition des documents entre jeu d'entraînement, jeu de test et jeu aveugle, cliquez sur **Performances** > **Entraîner et évaluer** > **Editer les paramètres**. Par exemple, si les premiers résultats semblent acceptables, vous voudrez peut-être augmenter le nombre de documents dans le jeu de test afin de placer la barre plus haut. Vous pouvez spécifier un ratio pour chaque usage (données d'entraînement, données de test et données aveugles) et laisser le système répartir lui-même les documents proportionnellement, ou bien vous pouvez indiquer vous-même les jeux de documents spécifiques à utiliser pour ces trois groupes de données. 
1. Si vous avez effectué des changements, cliquez sur **Entraîner & évaluer** pour réentraîner le modèle et réévaluer les annotations. 

## Supprimer un modèle d'apprentissage automatique
{: #wks_madelete}

Vous ne pouvez pas supprimer un modèle d'apprentissage automatique. 

Vous pouvez supprimer l'espace de travail ayant servi au développement du modèle, mais vous ne pouvez pas supprimer le modèle lui-même. Ce ne serait pas la meilleure approche. A la place, mettez à jour ou remplacez les artefacts qui servent à entraîner le modèle. Même si celui-ci ne produit pas les résultats escomptés, vous pouvez continuer à le raffiner. Chaque fois que vous créez une nouvelle version, le modèle est entièrement reconstruit. Vous pouvez éditer des artefacts tels que les dictionnaires et le système de types. Vous pouvez aussi choisir d'utiliser d'autres jeux d'annotations pour entraîner la nouvelle version. 
