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

Cette documentation concerne {{site.data.keyword.knowledgestudiofull}} on {{site.data.keyword.cloud}}. Pour consulter la documentation de la version précédente de {{site.data.keyword.knowledgestudioshort}} on {{site.data.keyword.IBM_notm}} Marketplace, [cliquez sur ce lien ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/docs/services/knowledge-studio/build-groundtruth.html){: new_window}.
{: tip}

# Construire les données de référence
{: #build-groundtruth}

L'objectif du projet d'annotation est d'obtenir la réalité du terrain, c'est-à-dire une collection de données de référence validées qui sont utilisées pour adapter {{site.data.keyword.watson}} à un domaine particulier. Dans {{site.data.keyword.knowledgestudioshort}}, les annotateurs humains, qui sont généralement des experts dans le domaine cible, jouent un rôle majeur dans la détermination des données de référence.
{: shortdesc}

Un flux typique inclura les étapes suivantes :

1. Les annotateurs humains soumettent à révision les documents qu'ils ont annotés.
1. Le chef de projet (qui peut être un expert du domaine) passe en revue les annotations ajoutées par les annotateurs humains, compare les jeux d'annotations et détermine avec quelle cohérence sont annotés les documents qui constituent un chevauchement entre ces différents jeux.
1. Si le score de convergence entre annotateurs est trop bas, le chef de projet rejette le jeu d'annotations et le renvoie à l'annotateur humain pour qu'il l'améliore. Lorsqu'un jeu d'annotations est rejeté, tous les documents qu'il contient sont replacés en mode éditable.
1. Si le chef de projet approuve un jeu d'annotations, les documents uniques à ce jeu, c'est-à-dire ne constituant pas de chevauchements avec d'autres jeux d'annotations, sont promus d'office au rang de données de référence afin que leurs annotations puissent servir à entraîner le modèle.
1. Le chef de projet passe en revue les documents chevauchants et résout les conflits d'annotations. A cette étape, appelée arbitrage (ou adjudication en anglais), l'équipe peut examiner et réviser les directives d'annotation afin d'aider à clarifier les malentendus qui ont conduit à ce que le texte soit annoté de façon incorrecte ou incohérente par différents annotateurs humains.

    Dans certains cas, pour évaluer la convergence entre annotateurs, le chef de projet souhaitera un pourcentage de chevauchement plus élevé que le pourcentage de chevauchement pour l'arbitrage des différences. Par exemple, si la convergence entre deux annotateurs semble correcte pour un type particulier, le chef de projet pourra décider que l'une ou l'autre des annotations peut être promue au rang d'annotation de référence.

1. A mesure que le chef de projet résout les conflits d'annotations, les annotations approuvées sont promues au rang de données de référence.

Gardez à l'esprit que l'annotation humaine est toujours une décision fondée sur un jugement subjectif. Les directives d'annotation peuvent largement contribuer à ce que le texte soit correctement et uniformément annoté, mais même les meilleures directives sont parfois interprétées différemment par différentes personnes. Pour obtenir des données de référence, vous souhaiterez passer du temps à former et éduquer les annotateurs humains afin qu'ils puissent faire les meilleurs jugements lors de l'analyse des contenus relatifs au domaine.

## Convergence entre annotateurs
{: #wks_haiaa}

Une fois que les annotateurs humains ont annoté les documents, vous devez déterminer ceux de ces documents qui doivent être promus au rang de données de référence. Commencez par examiner les scores de convergence entre annotateurs. Tout document ayant un faible score est vraisemblablement à rejeter et à retourner à l'annotateur humain pour qu'il l'améliore.

Pour calculer les scores de convergence entre annotateurs, le système examine tous les documents qui se chevauchent dans tous les jeux d'annotations de la tâche, quel que soit le statut de ces jeux. Un jeu d'annotations ne peut pas être accepté ni rejeté tant qu'il n'a pas le statut Soumis. Pour cette raison, vous souhaiterez peut-être attendre que tous les jeux d'annotations soient soumis avant d'évaluer leur convergence entre annotateurs. Vous pourriez aussi limiter votre évaluation aux seuls annotateurs humains qui ont déjà terminé et soumis leur jeu d'annotations.

Les scores de convergence entre annotateurs indiquent dans quelle mesure les annotateurs humains ont annoté différemment les mentions, relations et chaînes de coréférences. Vous pouvez voir les scores en comparant une paire d'annotateurs humains (par exemple, comparez toutes les annotations de mentions faites par Jean à toutes les annotations de mentions faites par Marie). Vous pouvez aussi les voir en comparant des documents spécifiques (par exemple, comparez les annotations de relations faites par Jean dans un document aux annotations de relations faites par Marie dans le même document).

Pour vous permettre d'identifier plus facilement les domaines qui nécessitent une investigation, les scores inférieurs à la valeur que vous avez spécifiée pour le seuil de convergence entre annotateurs sont surlignés en rouge. Au début d'un projet d'annotation, les scores des relations sont souvent moins bon que ceux des mentions, car pour être parfaite, une annotation de relation nécessite qu'il y ait convergence entre les mentions reliées par cette relation.

Le score dans la colonne **Tous** est un *Kappa de Fleiss*. Il représente le degré de concordance avec lequel la même annotation a été appliquée par plusieurs annotateurs humains entre tous les documents qui se chevauchent dans la tâche. Sa valeur, qui peut aller jusqu'à 1 pour les meilleurs scores et être négative pour les plus mauvais, aide à identifier les points à améliorer dans les directives d'annotation, ainsi que les points faibles des annotateurs humains. La grille de lecture suivante (*Landis et Koch, 1977*) fournit un point de départ à l'évaluation des performances générales.

<table style="width:60%" summary="Tableau fournissant des consignes générales pour l'évaluation de la performance globale de la convergence entre annotateurs.">
<caption>Tableau 1. Consignes pour l'évaluation de la convergence entre annotateurs</caption>
  <tr>
    <th style="vertical-align:bottom; text-align:center" id="d12741e148">Score</th>
    <th style="vertical-align:bottom; text-align:center" id="d12741e150">Niveau de convergence</th>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:center" headers="d12741e148">&lt; 0</td>
    <td style="vertical-align:top; text-align:center" headers="d12741e150">Mauvais</td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:center" headers="d12741e148">0,01 à 0,20</td>
    <td style="vertical-align:top; text-align:center" headers="d12741e150">Médiocre</td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:center" headers="d12741e148">0,21 à 0,40</td>
    <td style="vertical-align:top; text-align:center" headers="d12741e150">Moyen</td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:center" headers="d12741e148">0,41 à 0,60</td>
    <td style="vertical-align:top; text-align:center" headers="d12741e150">Intermédiaire</td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:center" headers="d12741e148">0,61 à 0,80</td>
    <td style="vertical-align:top; text-align:center" headers="d12741e150">Bon</td>
  </tr>
  <tr>
    <td style="vertical-align:top; text-align:center" headers="d12741e148">0,81 à 1,0</td>
    <td style="vertical-align:top; text-align:center" headers="d12741e150">Excellent</td>
  </tr>
</table>

Le score dans les autres colonnes est une *mesure F1*. Il représente le niveau de cohérence des annotations effectuées par une paire d'annotateurs humains. Sa valeur est comprise entre 0 et 1, la convergence parfaite étant indiquée par le score 1. Ce sont les données de votre domaine et votre système de types qui déterminent ce qui peut être considéré comme un niveau de convergence acceptable. Mais à titre d'exemple, voici les seuils F1 que les chefs de projet considèrent comme devant être atteints ou dépassés dans les projets basés sur le système de types KLUE :

- Mentions de types d'entités : 0,85
- Relations : 0,8
- Chaînes de coréférences : 0,9

L'interprétation des scores dépend de la complexité de votre système de types, de la quantité et de la complexité des contenus annotés, de l'expérience des annotateurs humains et d'autres facteurs. Par exemple, si la tâche d'annotation est centrée sur l'étiquetage des parties du discours, étant donné que les valeurs de partie du discours sont bien définies, vous comptez certainement sur l'obtention de scores élevés. En revanche, dans le cas d'une tâche exigeant une analyse plus approfondie du texte, forcément sujette à interprétation humaine, les scores risquent d'être moins bons tant que vous n'aurez pas pris les mesures nécessaires pour clarifier les points ambigus.

Un système de types comprenant de nombreux types d'entités et de relations est généralement ouvert à plus d'interprétation, si bien que la convergence entre annotateurs est souvent moins bonne au cours des premières phases de développement du modèle. En examinant les scores d'une certaine catégorie de types, par exemple les types d'entités, il est facile de repérer les scores les plus bas. Ce sont eux qui révèlent généralement la nécessité d'améliorer les directives d'annotation. En observant les scores entre différentes paires d'annotateurs humains, il est facile de voir si un annotateur a constamment de moins bons scores que les autres. Cela peut être le signe que cet annotateur comprend mal les directives ou l'emploi des outils d'annotation et qu'il a besoin d'un complément de formation.

## Etudier les scores de convergence entre annotateurs
{: #wks_haaccuracy}

Au moment de déterminer quels documents sont à promouvoir au rang de données de référence, vous devez étudier les scores de convergence entre annotateurs. Tout document ayant de faibles scores est vraisemblablement à rejeter et à retourner à l'annotateur humain pour qu'il l'améliore.

### A propos de cette tâche
{: #wks_haaccuracy_about}

Vous devez examiner les documents chevauchants, c'est-à-dire ceux dont plusieurs exemplaires ont été annotés par plusieurs annotateurs humains. Si un document n'est pas commun à plusieurs jeux d'annotations confiés à différents annotateurs humains, il n'y a pas de score de convergence à calculer. Lorsque vous ajoutez des jeux d'annotations à une tâche, assurez-vous que les jeux que vous prévoyez de comparer contiennent les mêmes documents chevauchants. Vous pouvez voir quels documents composent un jeu d'annotations en ouvrant la page **Actifs** > **Documents**, en cliquant sur l'onglet **Jeux d'annotations**, puis en cliquant sur le nom du jeu qui vous intéresse.

Il peut arriver qu'aucun document chevauchant ne soit trouvé. Cela peut se produire, par exemple, si vous créez des jeux d'annotations en deux tours et que vous les ajoutez à la même tâche. Même si les jeux d'annotations ont été créés à peu près au même moment, ils n'ont aucun document en commun. Autre exemple, vous créez des jeux d'annotations avec des documents chevauchants, mais vous ajoutez un seul jeu par tâche au lieu de les ajouter tous à une même tâche. Là encore, aucun document chevauchant n'est trouvé et le score de convergence entre annotateurs ne peut être calculé.

### Procédure
{: #wks_haaccuracy_procedure}

Pour évaluer la convergence des annotations entre annotateurs humains :

1. Connectez-vous en tant qu'administrateur ou chef de projet {{site.data.keyword.knowledgestudioshort}} et sélectionnez votre espace de travail.
1. Sélectionnez la page **Modèle d'apprentissage automatique** > **Tâches d'annotation** et ouvrez la tâche que vous voulez évaluer.
1. Cliquez sur **Calculer les scores de convergence entre annotateurs (IAA)**. La vue par défaut montre les scores de convergence, c'est-à-dire le niveau de cohérence avec lequel les différentes paires d'annotateurs humains ont annoté des mentions. La rangée du haut montre le niveau général de cohérence entre les différentes paires d'annotateurs. Le tableau en dessous montre le niveau de cohérence avec lequel les annotateurs d'une paire donnée ont étiqueté des mentions spécifiques dans le texte.
1. Pour examiner le niveau de cohérence avec lequel les différentes paires d'annotateurs humains ont annoté les relations et les coréférences, sélectionnez **Relation** ou **Coréférence** dans le premier menu.
1. Pour examiner le niveau de cohérence avec lequel les annotateurs humains d'une même paire ont annoté les entités, les relations ou les coréférences dans des documents chevauchants spécifiques, sélectionnez **Document** dans le second menu, puis choisissez la paire d'annotateurs à évaluer.
1. Après avoir examiné les scores, vous pouvez décider s'il faut approuver ou rejeter les jeux d'annotations dont le statut est SOUMIS. Lorsqu'un jeu d'annotations a été soumis, une case à cocher apparaît à côté de son nom. Effectuez l'une des opérations suivantes :

    - Si les scores de convergence entre annotateurs sont acceptables pour un jeu d'annotations, cochez la case et cliquez sur **Accepter**. Les documents qui ne figurent pas également dans les autres jeux d'annotations sont promus au rang de données de référence. En revanche, les documents qui se chevauchent avec d'autres jeux doivent être passés en revue par le biais d'un arbitrage visant à résoudre les conflits.
    - Si les scores de convergence entre annotateurs ne sont pas acceptables pour un jeu d'annotations, cochez la case et cliquez sur **Rejeter**. Ce jeu d'annotations devra être revu par l'annotateur humain afin qu'il en améliore les annotations.

## Arbitrage
{: #wks_haperform}

Si plusieurs annotateurs humains travaillent sur le même document, vous voudrez probablement résoudre leurs divergences avant de promouvoir les annotations au rang de données de référence. La résolution des conflits d'annotations s'appelle l'arbitrage.

Lorsque vous approuvez des jeux d'annotations soumis par les annotateurs, seuls les documents de ces jeux qui ne figurent pas également dans les autres jeux sont promus directement au rang de données de référence. Quant aux documents chevauchants (communs à plusieurs jeux), vous devez les examiner et voir si des mentions ont été annotées différemment. En cas de désaccord, vous devez décider de la manière de résoudre le conflit. Vous pouvez trancher en sélectionnant l'annotation que vous jugez correcte (si l'un des annotateurs a correctement étiqueté la mention) ou en appliquant votre propre annotation (si aucun des annotateurs n'a su trouver la bonne étiquette).

Un document est candidat à l'arbitrage si au moins une des conditions suivantes se vérifie :

- Le chef de projet approuve au moins deux jeux d'annotations dans une tâche en même temps, et un même document se retrouve dans au moins deux de ces jeux (c'est donc un document chevauchant).
- Le chef de projet approuve un autre jeu d'annotations avant que les documents des jeux précédemment approuvés ne soient arbitrés. Si vous arbitrez un document commun aux jeux d'annotations A et B, puis que vous promouvez les annotations résultantes au rang de données de référence et que vous approuvez ensuite un troisième jeu d'annotations C contenant également ce document, les annotations de ce dernier sont promues automatiquement au rang de données de référence, car les conflits n'existent plus. Sachez que, dans ce cas, les annotations promues dans le jeu d'annotations C l'emportent sur les données de référence qui ont été établies lors de l'arbitrage des documents chevauchants dans les jeux d'annotations A et B. En approuvant le jeu d'annotations C avant de promouvoir les annotations des jeux A et B, vous conservez la possibilité de rechercher les conflits dans les documents chevauchants du jeu C et de les arbitrer.

A condition de prendre le temps d'améliorer les directives d'annotation, vous passerez de moins en moins de temps à arbitrer les conflits puisqu'ils seront de plus en plus rares. En donnant des exemples et en clarifiant les domaines sources de confusion, vous aiderez les annotateurs humains à tirer des enseignements de leurs erreurs et vous éviterez de futurs conflits.

Voici quelques exemples des différents points de désaccord qui peuvent exister entre les annotateurs humains :

- **Mentions**

    - Annotateur_1 place une mention sur une étendue de texte ; Annotateur_2 n'en fait rien.
    - L'étendue de texte marquée par Annotateur_1 commence ou s'arrête avant ou après celle d'Annotateur_2 (chevauchement partiel ou sous-étendue de texte).
    - Annotateur_1 affecte à une unité lexicale un type d'entité différent de celui qu'affecte Annotateur_2 à la même unité lexicale.

- **Relations**

    - Annotateur_1 crée une relation entre deux mentions ; Annotateur_2 n'en fait rien.
    - Annotateur_1 et Annotateur_2 créent une relation entre les mêmes mentions, mais avec un type de relation différent.
    - Annotateur_1 et Annotateur_2 créent une relation entre les mêmes mentions, mais pas dans le même ordre (ce cas est rare, car la relation entre la première mention et la deuxième est contrainte par le système de types).

- **Chaînes de coréférences**

    - La version d'Annotateur_1 d'une chaîne de coréférences inclut (ou exclut) des mentions que la version d'Annotateur_2 exclut (ou inclut). L'alignement des entités entre Annotateur_1 et Annotateur_2 n'est pas le même.

## Résoudre les conflits d'annotations
{: #wks_haadjudicate}

L'arbitrage est une étape visant à passer en revue les conflits d'annotations dans les documents chevauchants avant de promouvoir les annotations au rang de données de référence. Vous pouvez comparer les annotations ajoutées par une paire d'annotateurs humains ou comparer les annotations humaines aux données de référence du moment.

### Avant de commencer
{: #wks_haadjudicate_prereq}

Cliquez sur [ce lien ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.youtube.com/watch?v=EbexfsuXxoQ&amp;feature=youtu.be){: new_window} pour visionner une vidéo de 3 minutes illustrant comment arbitrer des documents.

### A propos de cette tâche
{: #wks_haadjudicate_about}

Lorsque les annotateurs humains ont terminé leurs tâches d'annotation, ils doivent soumettre les jeux d'annotations pour révision. En évaluant les scores de convergence entre annotateurs, vous pouvez voir comment différentes paires d'annotateurs humains peuvent annoter plus ou moins différemment un même document. Si le score est acceptable, vous approuvez le jeu d'annotations. Si un document est unique à un jeu d'annotations de la tâche (autrement dit, s'il ne se retrouve pas dans plusieurs jeux), les annotations qu'il contient sont promues au rang de données de référence. En revanche, si un document est commun à plusieurs jeux d'annotations, vous devez l'arbitrer ou, plus exactement, résoudre les éventuels conflits d'annotations avant de promouvoir les annotations qu'il contient au rang de données de référence.

Par exemple, en arbitrant un document, vous constatez qu'un annotateur a étiqueté la mention `Barack Obama` avec le type d'entité `PeoplePerson`. Un autre annotateur a étiqueté la même chaîne de texte en la considérant comme deux mentions distinctes ; il a associé le type d'entité `Person` à `Barack` et le type d'entité `Person` à `Obama`. Cette incohérence doit être corrigée, sous peine de mal entraîner le modèle d'apprentissage automatique.

{{site.data.keyword.knowledgestudioshort}} prévoit la possibilité d'arbitrer les annotations d'un document entre deux jeux d'annotations à la fois ou entre un jeu d'annotations et les données de référence du moment. Si un document figure dans au moins trois jeux d'annotations, arbitrez-le entre les deux jeux dans lesquels vous avez le plus confiance (peut-être parce que vous avez plus confiance dans les annotateurs auxquels ces jeux ont été confiés) afin de déterminer les données de référence pour ce document. Arbitrez ensuite le document dans le reste des jeux d'annotations par rapport aux résultats de ce premier arbitrage.

### Procédure
{: #wks_haadjudicate_procedure}

Pour voir les documents qui se chevauchent et résoudre les conflits :

1. Connectez-vous en tant qu'administrateur ou chef de projet {{site.data.keyword.knowledgestudioshort}} et sélectionnez votre espace de travail.
1. Sélectionnez la page **Modèle d'apprentissage automatique** > **Tâches d'annotation** et ouvrez la tâche que vous voulez évaluer.
1. Vérifiez qu'il y a au moins deux jeux d'annotations dont le statut est **EN CONFLIT**.
1. Cliquez sur **Rechercher les conflits dans les documents qui se chevauchent**. Les documents contenant des conflits sont listés.
1. Si vous voulez ignorer les conflits dans un document chevauchant et promouvoir ses annotations au rang de données de référence sans les arbitrer, cliquez sur **Accepter**.
1. Pour commencer à résoudre les conflits dans un document chevauchant, cliquez sur **Rechercher les conflits**.
1. S'il y a au moins trois candidats à l'arbitrage parmi les jeux d'annotations ayant été annotés par l'annotation humaine et les données de référence du moment, sélectionnez les deux candidats que vous voulez arbitrer et cliquez sur **Rechercher les conflits**. S'il n'y a que deux candidats, l'outil d'arbitrage démarre automatiquement.

    L'outil d'arbitrage indique combien il y a de conflits de mentions, de relations et de chaînes de coréférences. Vous devez résoudre les conflits entre mentions avant de passer à la résolution des conflits entre relations et des conflits entre chaînes de coréférences.

1. Cliquez pour mettre en évidence une phrase contenant des conflits. Pour mieux vous concentrer sur les conflits non résolus, vous pouvez décocher la case **Résolu** et ne cocher que la case **Non résolu**.
1. Cliquez individuellement sur les annotations et, pour chacune, cliquez sur **Accepter** ou **Rejeter**. Pour annuler une décision que vous venez de prendre, appuyez sur Ctrl+Z.

    Vous pouvez aussi sélectionner plusieurs annotations à la fois pour les accepter ou les rejeter en bloc. Si vous renoncez à sélectionner une annotation que vous venez d'inclure dans la sélection, annulez cette dernière en cliquant sur un espace entre deux phrases ou en appuyant sur la touche **Echap**.

    Si des directives d'annotation ont été préalablement connectées au projet et que vous avez besoin d'aide pour choisir l'annotation correcte à appliquer, cliquez sur **Afficher les directives**. Il est possible que vous soyez autorisé à mettre à jour les directives d'annotation après les avoir ouvertes, par exemple, pour ajouter des clarifications et des exemples. Cela dépend si des autorisations d'accès ont été mises en place et vous ont été accordées sur le site où sont hébergées les directives.
    {: tip}

1. Pour appliquer un type d'entité différent à une mention, rejetez l'annotation actuelle, sélectionnez la mention (par exemple, `Barack Obama`), puis choisissez le type d'entité correct (par exemple, `Person`).
1. Continuez à accepter ou rejeter les annotations dans la phrase et à résoudre les autres conflits s'il y en a. Lorsque tous les conflits sont résolus dans une phrase, cliquez sur le lien **Sélectionner toutes les annotations**, puis cliquez sur **Accepter**.
1. Cliquez sur l'icône fléchée pour passer à la phrase suivante. Continuez jusqu'à ce que tous les conflits de mentions soient résolus dans le document.

    Vous pouvez cliquer à tout moment sur **Sauvegarder** pour enregistrer le travail en cours ou suspendre temporairement la session d'arbitrage. Si vous souhaitez annuler tous les changements apportés, cliquez sur **Annuler**. Si vous avez sauvegardé la session d'arbitrage précédente et que vous êtes prêt à la reprendre, cliquez sur **Reprendre** afin de reprendre l'arbitrage des conflits là où vous l'aviez interrompu. Si vous avez annulé les changements effectués au cours de la session précédente, vous devez en démarrer une nouvelle.
    {: tip}

1. Une fois les conflits entre mentions résolus, changez de mode d'arbitrage afin de passer à la résolution des conflits entre annotations de relations et des conflits entre annotations de chaînes de coréférences.

    - La résolution des conflits de relations est similaire à celle des conflits de mentions. Elle se déroule phrase par phrase.
    - Les chaînes de coréférences, en revanche, peuvent s'étendre sur plusieurs phrases. Lorsque vous passez en mode coréférence, le système affiche, dans un panneau à droite, la liste des chaînes de coréférences qui ont été créées par chaque annotateur humain. Sélectionnez les chaînes que vous voulez arbitrer, puis cliquez sur **Rejeter la chaîne** ou **Accepter la chaîne** afin de rejeter ou d'accepter les annotations d'une chaîne, ou bien cliquez sur **Fusionner les chaînes** pour fusionner les deux chaînes. Si vous voulez retirer une mention d'une chaîne de coréférences, cliquez sur l'icône de suppression (-) dans l'étiquette au-dessus de la mention concernée, dans la zone du document.

1. Une fois tous les conflits résolus dans le document, cliquez sur **Promouvoir comme données de référence**.
