---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-13"

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

Essa documentação destina-se ao {{site.data.keyword.knowledgestudiofull}} no {{site.data.keyword.cloud}}. Para ver a documentação para a versão anterior do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace, [clique neste link ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/docs/services/knowledge-studio/preannotation.html){: new_window}.
{: tip}

# Anotação de autoinicialização
{: #preannotation}

Simplifique a tarefa do anotador humano pré-anotando os documentos em uma área de trabalho. Um pré-anotador é um dicionário do {{site.data.keyword.knowledgestudioshort}}, modelo baseado em regra ou modelo de aprendizado de máquina que é possível executar para localizar e anotar menções automaticamente.
{: shortdesc}

A pré-anotação torna a tarefa dos anotadores humanos mais fácil porque ela cobre as anotações simples e inicia a tarefa de anotar os documentos.

O método que você usa para pré-anotar documentos em nenhuma forma restringe os modos em que é possível usar o modelo resultante. Por exemplo, só porque você usa o serviço {{site.data.keyword.nlushort}} para pré-anotar documentos, não significa que se deve implementar o modelo de aprendizado de máquina final construído para o serviço {{site.data.keyword.nlushort}}. A pré-anotação destina-se exclusivamente a autoinicializar o processo de anotação humana.

## Notas importantes
{: #preannotation_notes}

- Nunca execute uma pré-anotador em documentos que os anotadores humanos anotaram porque as anotações incluídas pelos anotadores humanos serão removidas.
- É possível executar somente um pré-anotador em documentos. Se você executar um pré-anotador e, em seguida, executar um segundo pré-anotador, o segundo pré-anotador removerá as anotações que foram incluídas pelo primeiro pré-anotador. Escolha o método de pré-anotação que melhor se ajusta ao seu caso de uso e use somente esse pré-anotador.

## Métodos de pré-anotação
{: #preannotation_methods}

Os pré-anotadores a seguir estão disponíveis:

- **{{site.data.keyword.nlushort}}**

    Um pré-anotador que é possível usar para localizar menções de entidades em seus documentos automaticamente. Se os seus documentos de origem tiverem assunto de conhecimento geral, esse pré-anotador será uma boa opção para você. Se você estiver trabalhando com documentos altamente especializados que se concentram em um campo específico, como a investigação da lei de patentes, por exemplo, o pré-anotador de dicionário ou modelo baseado em regra poderá ser uma opção melhor.

- **Dicionário**

    Usa um dicionário de termos que você fornece e associa com um tipo de entidade para localizar menções desse tipo de entidade nos documentos. Esta opção é melhor para campos com terminologia exclusiva ou especializada porque esse pré-anotador não analisa o contexto no qual o termo é usado da maneira como um pré-anotador de aprendizado de máquina faz; em vez disso, ele conta com o termo sendo distinto o suficiente para ter um significado decifrável independentemente do contexto no qual ele é usado. Por exemplo, é mais fácil reconhecer *amianto* como um tipo de entidade de mineral do que determinar o tipo de entidade de *squash*, que pode referir-se a um vegetal, um esporte ou um verbo que significa esmagar alguma coisa.

- **Aprendizado de máquina**

    Usa um modelo de aprendizado de máquina para anotar documentos automaticamente. Essa opção estará disponível para você somente se já tiver criado um modelo de aprendizado de máquina com o {{site.data.keyword.knowledgestudioshort}}. Se você incluir um novo conjunto de documentos, será possível executar o anotador de aprendizado de máquina que criou anteriormente para pré-anotar os novos documentos. Se o novo conjunto de documentos for semelhante aos documentos que foram usados para treinar o anotador de aprendizado de máquina originalmente, então essa é provavelmente sua melhor opção para pré-anotação.

- **Regra**

    Usa um modelo baseado em regra para anotar documentos automaticamente. Essa opção estará disponível somente se você já tiver criado um modelo baseado em regra com o {{site.data.keyword.knowledgestudioshort}}. Se seus documentos contêm padrões comuns de tokens por meio dos quais é possível derivar significado, esse modelo pode ser uma boa opção. Ele poderá incorporar alguma das funções do pré-anotador de dicionário se você o ativar, identificando tipos de classe para termos do dicionário que ele localiza nos documentos também.

Como alternativa, é possível fazer upload de documentos já anotados e usá-los para começar a treinar o modelo de aprendizado de máquina. Não é possível executar um pré-anotador em documentos anotados dos quais você faz upload ou as anotações existentes serão removidas dos documentos e substituídas por anotações produzidas somente pelo pré-anotador.

> **Nota:** *é possível* executar um pré-anotador em documentos que foram incluídos na verdade absoluta como parte da área de trabalho atual. As anotações que foram incluídas nos documentos, revisadas, aceitas e promovidas para verdade absoluta dentro da área de trabalho atual não são removidas.

## Pré-anotando documentos com o {{site.data.keyword.nlushort}}
{: #wks_preannotnlu}

É possível usar o serviço {{site.data.keyword.nlushort}} para pré-anotar documentos que você inclui em seu corpus.

### Antes de Começar
{: #wks_preannotnlu_prereqs}

Determine se o pré-anotador do {{site.data.keyword.nlushort}} deve incluir valor para seu caso de uso. Revise a lista de tipos e subtipos de entidade do serviço [{{site.data.keyword.nlushort}} suportados ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/docs/services/natural-language-understanding/entity-types.html){: new_window} para determinar se há uma sobreposição natural entre eles e os tipos em seu sistema de tipos. Se sim, continue com este procedimento. Se não, escolha um pré-anotador diferente para usar.

### Sobre essa Tarefa
{: #wks_preannotnlu_about}

O {{site.data.keyword.nlushort}} é um serviço que oferece análise de texto por meio do processamento de linguagem natural. Quando você usa o pré-anotador do {{site.data.keyword.nlushort}}, ele chama o serviço {{site.data.keyword.nlushort}} para localizar e anotar entidades em seus documentos.

Deve-se especificar os tipos de entidade que você deseja que o serviço procure mapeando os tipos de entidade do {{site.data.keyword.nlushort}} para os tipos de entidade do {{site.data.keyword.knowledgestudioshort}} correspondentes que você incluiu no sistema de tipos do {{site.data.keyword.knowledgestudioshort}}. Somente menções de tipos de entidade que você mapear serão localizados e anotados.

### Procedimento
{: #wks_preannotnlu_procedure}

Para usar o serviço {{site.data.keyword.nlushort}} para pré-anotar documentos, conclua as etapas a seguir:

1. Efetue login como um administrador do {{site.data.keyword.knowledgestudioshort}} e selecione a sua área de trabalho.
1. Selecione a guia **Modelo de aprendizado de máquina** > **Pré-anotação** > **Entendimento da língua natural**.
1. Clique em **Editar** para mapear cada tipo de entidade que é definido na página **Tipos de entidade** para os tipos de entidade do {{site.data.keyword.nlushort}} correspondentes.

    - A lista suspensa dos tipos de entidade do {{site.data.keyword.nlushort}} é pré-preenchida com os tipos de entidade reconhecidos pelo serviço {{site.data.keyword.nlushort}}.
    - Deve-se mapear pelo menos um tipo de entidade.
    - Não é possível mapear um tipo de entidade do {{site.data.keyword.nlushort}} para uma função de entidade do {{site.data.keyword.knowledgestudioshort}}, somente tipos de entidade do {{site.data.keyword.knowledgestudioshort}}.
    - É possível mapear mais de um tipo de entidade do {{site.data.keyword.nlushort}} para um único tipo de entidade do {{site.data.keyword.knowledgestudioshort}} ou o contrário. Por exemplo, os mapeamentos a seguir são permitidos:

    <table summary="Mapeamento de amostra de tipos de entidade">
    <caption>Tabela 1. Mapeamento de amostra de tipos de entidade</caption>
      <tr>
        <th style="vertical-align:bottom; text-align"left" id="d20428e292">Watson Knowledge Studio Entity Type</th>
        <th style="vertical-align:bottom; text-align"left" id="d20428e298">Tipo de entidade do {{site.data.keyword.nlushort}}</th>
      </tr>
      <tr>
        <td headers="d20428e292">
          ENGINEER<br/>
          SCIENTIST
        </td>
        <td headers="d20428e298">
          Pessoa
        </td>
      </tr>
      <tr>
        <td headers="d20428e292">
          LOCALIDADE
        </td>
        <td headers="d20428e298">
          CityTown<br/>
          País
        </td>
      </tr>
    </table>
    {: #wks_preannotnlu__datasimpletable_cm1_y3g_fx}

1. Depois de mapear todos os tipos de entidade que você deseja aplicar, clique em **Aplicar este pré-anotador**.

    O botão **Aplicar este pré-anotador** não estará disponível até você mapear pelo menos um tipo de entidade.

1. Marque a caixa de seleção para cada conjunto de documentos que você deseja pré-anotar.

    Se você estiver executando este pré-anotador pela primeira vez, primeiro valide que o pré-anotador pode localizar menções das entidades mapeadas conforme o esperado. Crie um conjunto de documentos que contenha um ou mais documentos representantes de cada origem de dados distintos.
    {: tip}

1. Clique em **Executar**.

    Se você estiver fazendo uma verificação de validação do pré-anotador, abra os documentos anotados e revise as anotações que foram incluídas. Certifique-se de que um número suficiente de anotações precisas tenha sido criado. Se as anotações são precisas, é possível executar o anotador novamente em mais conjuntos de documentos maiores. Se as anotações não são precisas, considere mapear diferentes tipos de entidade do {{site.data.keyword.nlushort}} para seus tipos. Se os tipos não se sobrepõem naturalmente, o pré-anotador do {{site.data.keyword.nlushort}} não é o melhor pré-anotador para você usar.

    A pré-anotação é aplicada a documentos individuais sem considerar os vários conjuntos de documentos aos quais um documento pode pertencer. Um documento que se sobrepõe entre um conjunto de documentos selecionado e um conjunto de documentos não selecionado será previamente anotado em ambos os conjuntos de documentos.

1. Depois de executar o pré-anotador uma vez, é possível clicar em **Aplicar este pré-anotador** a qualquer momento que desejar usá-lo para pré-anotar conjuntos de documentos adicionais incluídos no corpus.

    > **Restrição:** se você edita a definição de mapeamento de tipo do pré-anotador do {{site.data.keyword.nlushort}}, deve-se recriar as tarefas de anotação que incluem os conjuntos de documentos pré-anotados. A pré-anotação com base nas mudanças que você faz na definição de mapeamento de pré-anotador não poderá ser aplicada a conjuntos de documentos que já estiverem designados a uma tarefa de anotação.

### Resultados
{: #wks_preannotnlu__export-warning}

A verdade absoluta que é produzida por documentos que foram pré-anotados pelo serviço {{site.data.keyword.nlushort}} não pode ser usada diretamente fora do {{site.data.keyword.knowledgestudioshort}}. É possível fazer download da verdade absoluta (em forma não legível) para movê-la de uma área de trabalho do {{site.data.keyword.knowledgestudioshort}} para outra. Além disso, é possível continuar a desenvolver a verdade absoluta e usá-la para construir um modelo de aprendizado de máquina ou modelo baseado em regra que pode ser implementado para uso em serviços fora do {{site.data.keyword.knowledgestudioshort}}.

> **Restrição:** os documentos que foram pré-anotados com o {{site.data.keyword.nlushort}} são obscurecidos em um formato não legível quando eles são transferidos por download. Mas todas as anotações nesses documentos são obscurecidas, incluindo anotações que foram incluídas nos documentos por anotadores humanos.

**Informações relacionadas**:

[{{site.data.keyword.nlushort}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/watson/services/natural-language-understanding/){: new_window}

## Pré-anotando documentos com um dicionário
{: #wks_preannot}

Para ajudar na introdução dos anotadores humanos às suas tarefas de anotação, é possível criar um dicionário e usá-lo para pré-anotar documentos que você inclui no corpus.

### Sobre essa Tarefa
{: #wks_preannot_about}

Quando um anotador humano começa a trabalhar em documentos que foram pré-anotados, é provável que um número de menções já esteja marcado por tipos de entidade com base nas entradas de dicionário. O anotador humano pode mudar ou remover os tipos de entidade pré-anotados e designar tipos de entidade a menções não anotadas. A pré-anotação por um dicionário não anota relações e correferências. As relações e correferências devem ser anotadas por anotadores humanos.

**Nota**: esta tarefa mostra como criar um dicionário que é editável. Se você deseja fazer upload e pré-anotar seus documentos com um dicionário somente leitura, clique no ícone **Menu** ao lado do botão **Criar dicionário**. Selecione  ** Upload de Dicionário **.

### Procedimento
{: #wks_preannot_procedure}

Para criar um dicionário editável e pré-anotar documentos:

1. Efetue login como um administrador do {{site.data.keyword.knowledgestudioshort}} e selecione a sua área de trabalho.
1. Selecione a página  ** Ativos **  >  ** Dicionários ** .
1. Clique em **Criar dicionário**, insira um nome e, em seguida, clique em **Salvar**.
1. Na lista **Tipo de entidade**, selecione um tipo de entidade para associar com o dicionário.
3. Inclua entradas para o dicionário ou faça upload de um arquivo que contenha os termos do dicionário.
4. Clique em  ** Modelo de aprendizado de máquina **  >  ** Pré-anotação **.
5. Na guia **Dicionários**, clique em **Aplicar este pré-anotador**.
6. Marque a caixa de seleção para cada conjunto de documentos que você deseja pré-anotar e clique em **Executar**.

    A pré-anotação é aplicada a documentos individuais sem considerar os vários conjuntos de documentos ou conjuntos de anotações aos quais um documento pode pertencer. Um documento que se sobrepõe entre um conjunto de documentos selecionado e um conjunto de documentos não selecionado será previamente anotado em ambos os conjuntos de documentos.

7. Depois que o dicionário é criado, clique em **Executar** a qualquer momento que desejar usar o dicionário para pré-anotar conjuntos de documentos adicionais incluídos no corpus.

    > **Restrição:** se você edita o dicionário para incluir ou remover entradas, deve-se recriar as tarefas de anotação que incluem os conjuntos de documentos pré-anotados. A pré-anotação com base nas mudanças que você faz no anotador de dicionário não pode ser aplicada a conjuntos de anotações que já estão designados a uma tarefa de anotação.

**Informações relacionadas**:

[Criando dicionários](/docs/services/watson-knowledge-studio/dictionaries.html)

[Introdução > Incluindo um dicionário](/docs/services/watson-knowledge-studio/tutorials-create-project.html#wks_tutless4)

## Pré-anotando documentos com o modelo de aprendizado de máquina
{: #wks_preannotsire}

É possível usar o modelo de aprendizado de máquina existente para pré-anotar documentos que você inclui no corpus.

### Sobre essa Tarefa
{: #wks_preannotsire_about}

Depois que 10 a 30 documentos são anotados, um modelo de aprendizado de máquina pode ser treinado nos dados. Esse modelo minimamente treinado não deve ser usado em uma produção, mas pode ser usado para pré-anotar documentos para ajudar a acelerar a anotação humana de documentos subsequentes. Por exemplo, se você inclui documentos no corpus depois de treinar um modelo de aprendizado de máquina, é possível usar o modelo para pré-anotar os novos conjuntos de documentos. Nunca execute um pré-anotador nos mesmos documentos que foram anotados por uma pessoa. Os pré-anotadores removem a anotação humana.

### Procedimento
{: #wks_preannotsire_procedure}

Para usar o modelo de aprendizado de máquina existente para pré-anotar documentos:

1. Efetue login como um administrador do {{site.data.keyword.knowledgestudioshort}} e selecione a sua área de trabalho.
2. Selecione  ** Modelo de Aprendizado de Máquina **  >  ** Versões **.
3. Para pré-anotar novos documentos, clique em **Executar este modelo**.
4. Marque a caixa de seleção para cada conjunto de documentos que você deseja pré-anotar e clique em **Executar**.

    A pré-anotação é aplicada a documentos individuais sem considerar os vários conjuntos de documentos ou conjuntos de anotações aos quais um documento pode pertencer. Um documento que se sobrepõe entre um conjunto de documentos selecionado e um conjunto de documentos não selecionado será previamente anotado em ambos os conjuntos de documentos.

5. É possível clicar em **Executar este modelo** a qualquer momento que desejar usar o modelo de aprendizado de máquina para pré-anotar conjuntos de documentos adicionais incluídos no corpus.

## Pré-anotando documentos com o modelo baseado em regra
{: #wks_preannotrule}

É possível usar um modelo baseado em regra existente para pré-anotar documentos que você inclui no corpus.

### Procedimento
{: #wks_preannotrule_procedure}

Para usar o modelo baseado em regra para anotar documentos, conclua as etapas a seguir:

1. Efetue login como um administrador do {{site.data.keyword.knowledgestudioshort}} e selecione a sua área de trabalho.
1. Selecione a guia **Modelo baseado em regra** > **Versões** > **Modelo baseado em regra**.
1. Se ainda não tiver concluído, clique em **Mapear tipos de entidade e classes** para mapear tipos de entidade que você definiu no sistema de tipos do {{site.data.keyword.knowledgestudioshort}} para uma ou mais classes de modelo baseado em regra.
2. Clique em **Editar** para cada tipo de entidade que você deseja mapear.

    - A lista suspensa da coluna **Nome de classe** é pré-preenchida com classes que estão associadas ao modelo baseado em regra.
    - Deve-se mapear pelo menos um tipo de entidade para uma classe.

3. Na guia **Modelo baseado em regra**, clique em **Executar este modelo**.

    O botão **Executar este modelo** não estará disponível até você mapear pelo menos um tipo de entidade para uma classe.

4. Selecione os conjuntos de documentos ou conjuntos de anotações que você deseja pré-anotar. Assegure-se de que os conjuntos selecionados não contenham documentos que possuem anotações humanas. Os pré-anotadores removem a anotação humana.
5. Clique em **Executar**.

    A pré-anotação é aplicada a documentos individuais sem considerar os vários conjuntos de documentos aos quais um documento pode pertencer. Um documento que se sobrepõe entre um conjunto de documentos selecionado e um documento não selecionado aparecerá pré-anotado em ambos os conjuntos de documentos.

6. É possível clicar em **Executar este modelo** a qualquer momento que desejar usar o modelo baseado em regra para pré-anotar conjuntos de documentos adicionais que você inclui no corpus.

    > **Restrição:** se você edita o mapeamento de tipo de entidade para classe do modelo baseado em regra, deve-se recriar as tarefas de anotação que incluem os conjuntos de documentos pré-anotados. A pré-anotação com base nas mudanças que você faz na definição de mapeamento de pré-anotador não poderá ser aplicada a conjuntos de documentos que já estiverem designados a uma tarefa de anotação.

## Fazendo upload de documentos pré-anotados
{: #wks_uima}

É possível dar início ao treinamento de seu modelo fazendo upload de documentos que foram pré-anotados por meio de um mecanismo de análise Unstructured Information Management Architecture (UIMA).

Os documentos pré-anotados devem estar na forma de serialização XMI do UIMA Common Analysis Structure (UIMA CAS XMI). O arquivo ZIP do qual você faz upload deve incluir o arquivo descritor do UIMA TypeSystem e um arquivo que mapeie os tipos do UIMA para os tipos de entidade em seu sistema de tipos do {{site.data.keyword.knowledgestudioshort}}.

O UIMA CAS XMI é um formato padrão do Apache UIMA. Diretrizes são fornecidas sobre como criar arquivos no formato correto por meio de coletas analisados no {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer. Se você usa outra implementação do Apache UIMA, adapte estas diretrizes aos seus propósitos. Independentemente de como você cria os arquivos XMI, os requisitos para criar o arquivo de mapeamento do sistema de tipos e arquivo ZIP são os mesmos para todos.

Se você designa os documentos importados para anotadores humanos, os documentos aparecem pré-anotados no editor de verdade absoluta e um número de menções pode já estar anotado. O anotador humano assim tem mais tempo para focar em aplicar as diretrizes de anotação às menções não marcadas. Como alternativa, é possível efetuar bypass da etapa de anotação humana e usar os documentos pré-anotados para iniciar imediatamente o treinamento e a avaliação de um modelo de aprendizado de máquina.

### Exportando documentos analisados do Watson Explorer Content Analytics
{: #wks_uimawexca}

É possível exportar os documentos que foram submetidos a crawl e analisados no {{site.data.keyword.IBM_notm}} {{site.data.keyword.watson}} Explorer Content Analytics e fazer upload dos documentos analisados como arquivos XMI em uma área de trabalho do {{site.data.keyword.knowledgestudioshort}}.

#### Procedimento
{: #wks_uima_procedure}

Para obter documentos analisados de uma coleção do {{site.data.keyword.watson}} Explorer Content Analytics:

1. Abra o console de administração do Content Analytics em um navegador da web.
1. Na visualização Coleções, expanda a coleção da qual você deseja exportar documentos. Na área de janela Analisar e Indexar, assegure-se de que o processo de análise e indexação esteja em execução e, em seguida, clique no ícone de seta para **Exportar o conteúdo e os metadados do documento analisado**.
1. Na área **Opções de exportação de documento analisado**, selecione **Exportar documentos como arquivos XML**, marque a caixa de seleção **Ativar CAS como exportação de formato XMI**, especifique o caminho de saída para onde os dados exportados devem ser gravados e clique em **OK**.
1. Pare e reinicie os serviços de análise e indexação para a coleção e, em seguida, execute uma das etapas a seguir:

    - Se a coleção já contém documentos indexados que você deseja usar para treinar o modelo de aprendizado de máquina no cache do documento, reiniciar uma construção de índice integral.
    - Se a coleção não contém documentos indexados que você deseja usar para treinar o modelo de aprendizado de máquina, faça upload de documentos, configurar pelo menos um crawler para efetuar crawl dos documentos e inicie o crawler.

1. Na área **Exportar**, verifique o status da solicitação de exportação. O progresso indica quantos documentos são exportados.
1. Acesse a pasta de saída que você especificou quando configurou as opções de exportação. Quando os documentos são exportados como arquivos XML, o nome da pasta de saída é baseado no registro de data e hora quando a exportação ocorre. A pasta de saída contém arquivos XMI (`*.xmi`) e o arquivo descritor do UIMA TypeSystem (`exported_typesystem.xml`).

#### O que fazer em seguida
{: #wks_uimawexca__preUIMAimport}

Deve-se definir um mapeamento entre os tipos do UIMA e tipos de entidade do {{site.data.keyword.knowledgestudioshort}}. Deve-se também criar um arquivo ZIP que contenha todos os arquivos que são necessários para fazer upload dos dados analisados em uma área de trabalho do {{site.data.keyword.knowledgestudioshort}}.

**Informações relacionadas**:

[Exportando documentos submetidos a crawl ou analisados ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ad.doc/iiysatexportca.htm){: new_window}

[Caminhos de saída para documentos exportados ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ad.doc/iiysaexportoutput.htm){: new_window}

### Exportando uma coleção analisada do Content Analytics Studio
{: #wks_uimawexstudio}

É possível exportar uma coleção de documentos analisados do {{site.data.keyword.watson}} Explorer Content Analytics Studio e fazer upload dos documentos analisados como arquivos XMI em um projeto do {{site.data.keyword.knowledgestudioshort}}.

#### Procedimento
{: #wks_uimawexstudio_procedure}

Para obter documentos analisados de uma coleção do Content Analytics Studio:

1. Ative o Content Analytics Studio e abra o projeto Studio.
1. Clique com o botão direito em uma pasta que contém documentos que você deseja usar para treinar um modelo de aprendizado de máquina e selecione **Analisar coleção**.
1. Selecione um arquivo de configuração de pipeline UIMA.
1. Acesse a visualização Análise de coleção e clique no ícone **Salvar** na visualização Análise de coleção. Especifique a pasta na qual os resultados salvos devem ser gravados e especifique o nome do arquivo.
1. Abra a pasta que você especificou. A extensão do arquivo do arquivo salvo é `.annotations`.
1. Copie o arquivo `.annotations` em seu sistema de arquivos local e renomeie a extensão do arquivo de `.annotations` para `.zip`.
1. Extraia todos os arquivos do arquivo ZIP. Os conteúdos extraídos incluem arquivos XMI (`*.xmi`), o arquivo descritor do UIMA TypeSystem (`TypeSystem.xml`) e outros arquivos.

#### O que fazer em seguida
{: #wks_uimawexstudio_next}

Deve-se definir um mapeamento entre os tipos do UIMA e tipos de entidade do {{site.data.keyword.knowledgestudioshort}}. Deve-se também criar um arquivo ZIP que contenha todos os arquivos que são necessários para fazer upload dos dados analisados em uma área de trabalho do {{site.data.keyword.knowledgestudioshort}}.

### Mapeando tipos UIMA para tipos de entidade
{: #wks_uimawexmap}

Antes de fazer upload de arquivos XMI em uma área de trabalho do {{site.data.keyword.knowledgestudioshort}}, deve-se definir mapeamentos entre os tipos UIMA e os tipos de entidade do {{site.data.keyword.knowledgestudioshort}}.

#### Antes de Começar
{: #wks_uimawexmap_prereqs}

O sistema de tipos na área de trabalho do {{site.data.keyword.knowledgestudioshort}} deve incluir os tipos de entidade para os quais você deseja mapear os tipos UIMA.

#### Procedimento
{: #wks_uimawexmap_procedure}

Para mapear tipos UIMA para tipos de entidade do {{site.data.keyword.knowledgestudioshort}}:

1. Crie um arquivo chamado `cas2di.tsv` na pasta que contém o arquivo descritor do UIMA TypeSystem, como `exported_typesystem.xml` ou `TypeSystem.xml`.
1. Abra o arquivo `cas2di.tsv` com um editor de texto. Cada linha no arquivo especifica um único mapeamento. O formato do mapeamento depende de quais anotações do anotador você deseja mapear:

    - É possível criar mapeamentos usando o formato básico:

        `UIMA_Type_Name[TAB]WKS_Entity_Type`

        O exemplo a seguir define mapeamentos entre os tipos UIMA produzidos pelo anotador de Reconhecimento de entidade nomeada no {{site.data.keyword.watson}} e pelos tipos de entidade definidos em um sistema de tipos do {{site.data.keyword.knowledgestudioshort}}:

        ```
        com.ibm.langware.Organization  ORGANIZATION
        com.ibm.langware.Person  PERSON
        com.ibm.langware.Location  LOCATION
        ```
        {: screen}

        Outro exemplo define um mapeamento entre os tipos UIMA produzidos por um anotador customizado que foi criado no {{site.data.keyword.watson}} Explorer Content Analytics Studio e os tipos de entidade do {{site.data.keyword.knowledgestudioshort}}:

        ```
        com.ibm.Person  PERSON
        com.ibm.Date  DATE
        ```
        {: screen}

    - É possível criar mapeamentos com base em aspectos que são usados no anotador Correspondente padrão ou anotador Consulta de dicionário no {{site.data.keyword.watson}} Explorer Content Analytics. Em arquivos de regras de análise de texto (`*.pat`), o aspecto é representado como o atributo de categoria. Para definir um mapeamento, use a sintaxe a seguir:

        ```
        com.ibm.takmi.nlp.annotation_type.ContiguousContext:category={FACET_PATH}[TAB]{WKS_ENTITY_TYPE}
        ```
        {: screen}

        O exemplo a seguir, que se aplica aos anotadores Correspondente padrão e Consulta de dicionário, define um mapeamento entre a categoria $.mykeyword.product e o tipo de entidade PRODUCT do {{site.data.keyword.knowledgestudioshort}}:

        ```
        com.ibm.takmi.nlp.annotation_type.ContiguousContext:category=$.mykeyword.product PRODUCT
        ```
        {: screen}

#### O que fazer em seguida
{: #wks_uimawexmap_next}

Deve-se criar um arquivo ZIP que contenha todos os arquivos que são necessários para fazer upload dos dados analisados em uma área de trabalho do {{site.data.keyword.knowledgestudioshort}}.

**Informações relacionadas**:

[Anotador Correspondente padrão ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ta.doc/iiystapattmatch.htm){: new_window}

[Anotador Consulta de dicionário ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ta.doc/iiystadictlookup.htm){: new_window}

[Anotador Reconhecimento de entidade nomeada ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://www.ibm.com/support/knowledgecenter/SS8NLW_11.0.0/com.ibm.discovery.es.ta.doc/iiystasystemt.htm){: new_window}

### Fazendo upload de arquivos UIMA CAS XMI em uma área de trabalho
{: #wks_uimaweximport}

Para usar os documentos pré-anotados transferidos por download para treinar um modelo, deve-se criar um arquivo ZIP que contém todos os arquivos necessários para fazer upload dos arquivos XMI e, em seguida, fazer upload do arquivo ZIP em uma área de trabalho do {{site.data.keyword.knowledgestudioshort}}.

#### Antes de Começar
{: #wks_uimaweximport_prereqs}

Antes de fazer upload do arquivo ZIP, assegure-se de que o sistema de tipos na área de trabalho do {{site.data.keyword.knowledgestudioshort}} inclua os tipos de entidade para os quais você mapeou os tipos UIMA.

> **Aviso:** os mecanismos de análise UIMA permitem que as anotações abranjam as sentenças. No {{site.data.keyword.knowledgestudioshort}}, as anotações devem existir dentro dos limites de uma única sentença. Se os arquivos XMI dos quais você faz upload incluem anotações que abrangem sentenças, essas anotações não aparecem no editor de verdade absoluta.

#### Procedimento
{: #wks_uimaweximport_procedure}

Para fazer upload de documentos pré-anotados em uma área de trabalho do {{site.data.keyword.knowledgestudioshort}}:

1. Crie um arquivo ZIP que contenha todos os arquivos requeridos pelo {{site.data.keyword.knowledgestudioshort}}.

    1. Selecione a pasta que contém os arquivos XMI, o arquivo descritor do sistema de tipos UIMA e o arquivo `cas2di.tsv` ou selecione todos os arquivos na pasta.
    1. Crie um arquivo ZIP que inclua todos os arquivos. Certifique-se de que o `cas2di.tsv` e os arquivos descritores do sistema de tipos UIMA sejam armazenados no diretório-raiz do arquivo ZIP. Esses arquivos não podem ser armazenados em uma subpasta dentro do arquivo ZIP ou o {{site.data.keyword.knowledgestudioshort}} não será capaz de lê-los e nada será importado.

        No Windows, é possível clicar com o botão direito e selecionar **Enviar para** > **Pasta compactada (zip)**.

1. Faça upload do arquivo ZIP para uma área de trabalho do {{site.data.keyword.knowledgestudioshort}}.

    1. Efetue login como um administrador ou gerente de projeto do {{site.data.keyword.knowledgestudioshort}}, abra a área de trabalho na qual você deseja incluir os documentos e abra a página **Ativos** > **Documentos**.
    1. Clique em **Fazer upload de conjuntos de documentos**.
    1. Arraste o arquivo ZIP criado ou clique para localizar e selecionar o arquivo.
    1. Marque a caixa de seleção para indicar que o arquivo ZIP contém arquivos UIMA CAS XMI.
    1. Clique em **Fazer upload**.
