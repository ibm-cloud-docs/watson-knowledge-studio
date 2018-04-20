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

Essa documentação destina-se ao {{site.data.keyword.knowledgestudiofull}} no {{site.data.keyword.cloud}}. Para ver a documentação para a versão anterior do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace, [clique neste link ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/services/knowledge-studio/train-ml.html){: new_window}.
{: tip}

# Treinando o modelo de aprendizado de máquina
{: #train-ml}

No {{site.data.keyword.knowledgestudiofull}}, a criação do modelo de aprendizado de máquina envolve treinar o modelo de aprendizado de máquina e avaliar o quanto o modelo foi bem executado ao anotar dados de teste e dados ocultos.
{: shortdesc}

## Criando um modelo de aprendizado de máquina
{: #wks_madocsets}

Ao criar um modelo de aprendizado de máquina, você seleciona os conjuntos de documentos que deseja usar para treinar o modelo e especifica a porcentagem de documentos que devem ser usados como dados de treinamento, dados de teste e dados ocultos.

### Sobre essa Tarefa

Ao explorar as métricas de desempenho, é possível identificar maneiras de melhorar a precisão do modelo.

> **Restrição:** somente três anotadores de aprendizado de máquina podem ser treinados por vez por instância do {{site.data.keyword.knowledgestudioshort}}. Se sua instância contiver múltiplas áreas de trabalho e o número total de anotadores de aprendizado de máquina que estão sendo treinados em outras áreas de trabalho já for 3, sua solicitação para treinar o modelo de aprendizado de máquina em sua área de trabalho será enfileirada até que os outros processos de treinamento sejam concluídos.

### Procedimento

Para criar um modelo de aprendizado de máquina:

1. Efetue login como um administrador do {{site.data.keyword.knowledgestudioshort}} e selecione a sua área de trabalho.
1. Selecione **Gerenciamento de modelo** > **Desempenho**.
1. Verifique se todos os conjuntos de documentos foram aprovados e se todos os conflitos de anotação foram resolvidos por meio de adjudicação. Somente documentos que se tornaram verdade absoluta por meio de adjudicação ou aprovação podem ser usados para treinar o modelo.
1. Clique em **Treinar e avaliar**.
1. Opcional: para especificar como você deseja alocar documentos de seus conjuntos de documentos para serem usados pelo treinamento de nível do sistema, teste ou conjuntos cegos, clique em **Editar configurações**.

    Veja [Gerenciamento de conjunto de documentos](/docs/services/watson-knowledge-studio/improve-ml.html#wks_mamanagedata) para ajudar a determinar quais razões aplicar.

1. Opcional: associe quaisquer dicionários que você deseja que o modelo de aprendizado de máquina use durante o treinamento com o tipo de entidade das entradas de dicionário.

    Se você criou um pré-anotador de dicionário, então já executou esta etapa. Clique em **Reutilizar mapeamento que está definido para o pré-anotador de dicionário** para reutilizá-lo ou definir um novo mapeamento.

    O modelo usa as informações de tipo de termos de dicionário como um recurso entre muitos recursos de análise linguística que ele considera durante o treinamento.

1. Clique em **Treinar** para treinar o modelo ou clique em **Treinar e avaliar** para treinar o modelo, avaliar anotações incluídas pelo modelo de aprendizado de máquina e analisar as estatísticas de desempenho.

    > **Importante:** O treinamento de um modelo de aprendizado de máquina pode levar vários minutos ou várias horas, dependendo do número de anotações humanas que existem e o número total de palavras em todos os documentos.

1. Selecione os conjuntos de documentos que você deseja usar para treinar o modelo.

    > **Nota:** os conjuntos de documentos devem conter pelo menos 10 documentos anotados.

1. Depois que o modelo é criado, selecione uma das ações a seguir:

    <table border="1" frame="hsides" rules="rows" cellpadding="4" cellspacing="0" summary="Cada linha nessa tabela descreve uma opção para uma escolha." class="simpletable choicetable choicetableborder">
      <thead><tr><th id="d33883e137-option" valign="bottom" align="left" class="ncol thleft thbot">Opção</th>
          <th id="d33883e137-desc" valign="bottom" align="left" class="ncol thleft thbot">Descrição</th></tr></thead>
      <tbody><tr class="strow chrow"><td valign="top" headers="d33883e137-option" id="d33883e139" class="stentry choption ncol"><p class="p wrapper"><strong>Log</strong></p></td>
          <td valign="top" headers="d33883e137-desc d33883e139" class="stentry chdesc ncol"><p class="p wrapper">Visualize o arquivo de log para ver se algum problema ocorreu.</p></td>
        </tr>
        <tr class="strow chrow"><td valign="top" headers="d33883e137-option" id="d33883e144" class="stentry choption ncol"><p class="p wrapper"><strong>Detalhes</strong></p></td>
          <td valign="top" headers="d33883e137-desc d33883e144" class="stentry chdesc ncol"><p class="p wrapper">Visualize as estatísticas de desempenho de anotação, mude os conjuntos de documentos que você deseja usar
              para treinar e testar o modelo e crie versões de captura instantânea dos artefatos de
              modelo.</p></td>
        </tr>
        <tr class="strow chrow"><td valign="top" headers="d33883e137-option" id="d33883e149" class="stentry choption ncol"><p class="p wrapper"><strong>Exportar</strong></p></td>
          <td valign="top" headers="d33883e137-desc d33883e149" class="stentry chdesc ncol"><p class="p wrapper">Exporte um arquivo <code>ZIP</code> para seu sistema local que contenha os componentes
              requeridos para a execução do modelo em um ambiente de tempo de execução de aprendizado de máquina.</p></td>
        </tr>
      </tbody>
    </table>

## Avaliando anotações incluídas pelo modelo
{: #wks_matest}

É possível comparar a visualização de verdade absoluta para anotações incluídas por anotadores humanos com as anotações incluídas pelo modelo.

### Procedimento

Para avaliar as anotações incluídas pelo modelo:

1. Selecione **Gerenciamento de modelo** > **Desempenho** > **Treinar e avaliar**. A página Conjuntos de treinamento/teste/cego é exibida.
1. Clique em **Visualizar verdade absoluta** para o conjunto de treinamento ou conjunto de testes para ver as anotações que foram incluídas por meio de pré-anotação e por anotadores humanos. O editor de verdade absoluta é aberto. Clique para abrir documentos individuais e ver como as menções, relações e menções correferenciadas foram anotadas.
1. Na página **Desempenho**, clique em **Visualizar resultados de decodificação** para ver as anotações que o modelo de aprendizado de máquina incluiu em documentos no conjunto de testes. Esse botão estará disponível somente depois que você avaliar o modelo. Ao visualizar os resultados, é possível ver o quão bem o modelo de aprendizado de máquina rotulou as menções, relações e menções correferenciadas nos dados de teste.
1. Se você deseja mudar como os documentos são divididos entre conjuntos de treinamento, de teste e de dados ocultos, clique em **Desempenho** > **Treinar e avaliar** > **Editar configurações**. Por exemplo, se os resultados iniciais parecem aceitáveis, você pode desejar aumentar o número de documentos no conjunto de testes para testar melhor os resultados do modelo de aprendizado de máquina. É possível mudar a razão sobre como os documentos são divididos automaticamente para propósitos diferentes ou é possível selecionar conjuntos de documentos específicos para usar como dados de treinamento, dados de teste e dados ocultos.
1. Se você fez quaisquer mudanças, clique em **Treinar e avaliar** para treinar novamente o modelo e reavaliar as anotações.

## Excluindo um modelo de aprendizado de máquina
{: #wks_madelete}

Não é possível excluir um modelo de aprendizado de máquina.

É possível excluir a área de trabalho usada para desenvolver o modelo, mas não é possível excluir o modelo propriamente dito. Excluir um modelo não é a melhor abordagem. Em vez disso, atualize ou substitua os artefatos que são usados para treinar o modelo. Mesmo se o modelo não está produzindo os resultados esperados, é possível continuar a refiná-lo. Cada vez que você cria uma nova versão, o modelo é construído novamente. É possível editar artefatos como dicionários e o sistema de tipos e escolher usar diferentes conjuntos de anotações ao treinar a próxima versão.
