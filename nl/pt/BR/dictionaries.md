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

Essa documentação destina-se ao {{site.data.keyword.knowledgestudiofull}} no {{site.data.keyword.cloud}}. Para ver a documentação para a versão anterior do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace, [clique neste link ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/docs/services/knowledge-studio/dictionaries.html){: new_window}.
{: tip}

# Criando dicionários
{: #dictionaries}

Os dicionários ajudam os modelos de aprendizado de máquina do {{site.data.keyword.knowledgestudioshort}} a entender o idioma do domínio.
{: shortdesc}

## Dicionários
{: #wks_dictionaries}

Em aprendizado de máquina, um dicionário agrupa palavras e frases que compartilham algo em comum. Uma entrada no dicionário não significa que todas as palavras na entrada significam a mesma coisa, mas que as palavras devem ser tratadas de forma equivalente por um modelo.

Um dicionário é uma lista de palavras ou frases que são equivalentes para propósitos de extração de informações, o que significa que elas são intercambiáveis para os propósitos de identificação de menções de entidade e relação.

Considere este exemplo: uma entrada de dicionário contém os sete dias da semana. Para anotar um documento, um anotador humano designa o tipo de entidade `DAY_OF_WEEK` a menções de *Segunda-feira* e *Sexta-feira* no texto. Como o dicionário equipara os sete dias da semana, ele ajuda a assegurar que um modelo de aprendizado de máquina anote corretamente as ocorrências de *Terça-feira*, *Quarta-feira* e os outros dias da semana em documentos não vistos no tempo de execução. Além disso, comparar essas palavras também beneficia a extração de informações em texto circundante. O que o modelo de aprendizado de máquina aprende por meio de exemplos de treinamento sobre os textos próximos de *Segunda-feira* e *Sexta-feira* é aplicado aos textos que o modelo de aprendizado de máquina vê perto de outros dias da semana porque o dicionário declara que esses termos são equivalentes para propósitos de extração de informações.

> **Nota:** não é necessário criar um dicionário que contenha informações de dias da semana. Vários dicionários de propósito geral como este são construídos para o aplicativo. Outros dicionários integrados incluem países, nomes de locais, número de palavras, animais, plantas, doenças, palavras de medição (como *onça* e *medidor*) e palavras de título de saudação (como *Sr.* e *Sra.*). Não é possível desativar ou editar dicionários integrados.

Evite incluir entradas que tenham múltiplos significados. Por exemplo, em um domínio sobre corrida de automóveis, faz sentido incluir o termo *banco*, que se refere a um recurso de estrada, somente se as instituições financeiras não são frequentemente discutidas no texto também. Se ambos os sentidos da palavra ocorrem geralmente nos documentos de origem, então é melhor deixar isso fora de ambos os tipos de dicionários: o dicionário que está associado com recursos de estrada e o dicionário que está associado com instituições financeiras.

É possível criar dicionários no {{site.data.keyword.knowledgestudioshort}} incluindo manualmente entradas individuais. O {{site.data.keyword.knowledgestudioshort}} também suporta a capacidade de fazer upload de vários tipos de arquivos de dicionário.

### Como os dicionários são usados?

Os dicionários são usados de várias maneiras, todas opcionais. Eles são usados pelo modelo de aprendizado de máquina para fornecer palavras ou frases que são equivalentes para propósitos de extração de informações e durante a pré-anotação para autoinicialização do esforço de anotação.

- **Uso de aprendizado de máquina**

    O tipo de entidade que você associa com um dicionário não é usado para definir regras para o modelo de aprendizado de máquina. O aprendizado de máquina avalia menções nos documentos independentemente. Ele não presume que uma menção tem um tipo de entidade específico só porque a menção corresponde a uma entrada em um dicionário que está associado a esse tipo de entidade. Ele leva as informações em conta, mas as trata como uma parte de informações entre outras partes de informações que ele reúne por meio de análise linguística. Na verdade, se nenhum dos termos em um dicionário ocorre nos documentos de verdade absoluta, o dicionário não é usado no modelo de aprendizado de máquina.

- **Uso de pré-anotação**

    Os dicionários são importantes para os processos de pré-anotação a seguir.

    - Pré-anotador de dicionário: você associa um dicionário com um tipo de entidade do sistema de tipos quando executa o pré-anotador de dicionário.
    - Modelo baseado em regra: é possível opcionalmente associar um dicionário com uma classe de regra. As classes são então mapeadas para tipos de entidade do sistema de tipos quando você executa o modelo baseado em regra para pré-anotar documentos. Como resultado, os termos do dicionário são, embora indiretamente, mapeados para tipos de entidade do modelo baseado em regra também.

    Em ambos os casos, os dicionários fornecem termos que o sistema pode localizar e anotar como menções. Ele designa a cada menção o tipo de entidade que está associado com o dicionário que contém o termo. Quando um anotador humano começa a trabalhar em novos documentos que foram pré-anotados, muitas menções já estão anotadas com base nas entradas de dicionário. O anotador humano assim tem mais tempo para focar em designar tipos de entidade a menções que requerem análise mais profunda.

### Considerações sobre o idioma

- Para português do Brasil, inglês, francês, alemão, italiano e espanhol, o {{site.data.keyword.knowledgestudioshort}} não fornece atualmente uma opção para especificar correspondência de dicionário sem distinção entre maiúsculas e minúsculas, mas as entradas do dicionário correspondem a textos que têm uma caixa mais alta. Por exemplo, *veículo* no dicionário corresponde a *veículo*, *Veículo* ou *VEÍCULO* no texto, enquanto *Sáb* no dicionário corresponde a *Sáb* ou *SÁB* no texto, mas não *sáb*.
- Para japonês e coreano, a correspondência de dicionário durante a pré-anotação faz distinção entre maiúsculas e minúsculas.
- Para árabe, o {{site.data.keyword.knowledgestudioshort}} assume que o texto em árabe é armazenado sem forma e trata a forma numérica como uma propriedade de nível de armazenamento. Para obter detalhes sobre como o {{site.data.keyword.knowledgestudioshort}} manipula a forma de caractere árabe e a forma numérica, veja [Configurando suporte para árabe](/docs/services/watson-knowledge-studio/language-support-arabic.html).

### Dicionário de arquivo CSV
{: #wks_dictionaries__cvsdict}

Também referido como o formato do dicionário padrão, um dicionário em formato de valor separado por vírgula (`CSV`) é um arquivo que pode ser editado depois de ser transferido por upload. O tamanho máximo de um arquivo `CSV` do qual é possível fazer upload é 1 MB. Se você tiver um arquivo de dicionário maior, divida-o em múltiplos arquivos e faça upload deles um por vez em um único dicionário na área de trabalho do {{site.data.keyword.knowledgestudioshort}}.

Para resumir os requisitos, deve-se usar um editor de texto para criar o arquivo `CSV`, não software como Microsoft Excel, e o arquivo deve usar codificação UTF-8 que não inclui a marca de ordem de byte (BOM) no início do fluxo de texto. A primeira linha no arquivo deve especificar os cabeçalhos da coluna a seguir:

```
lemma,poscode,surface
```
{: screen}

As linhas restantes no arquivo especificam as entradas de dicionário, em que:

- **lema**

    Especifica a forma de palavra mais representativa para a entrada.

- **poscode** (árabe, português do Brasil, inglês, francês, alemão, italiano e espanhol)

    Especifica um código que identifica a parte do discurso. Esta parte de informações do discurso é usada pelo anotador de dicionário para ajudar com a tokenização de sentença.
    - ` 0 ` -Desconhecido

        > **Nota:** este código suporta o cenário no qual você deseja fazer upload de um grande dicionário gerado por máquina que não inclui a parte de informações do discurso em cada entrada. É possível designar *desconhecido* a todas as entradas por padrão. Evite usar esse código, se possível.

    - ` 1 ` -Pronome
    - ` 2 ` -Verbo
    - ` 3 ` -Noun
    - ` 4 ` -Adjetivo
    - ` 5 ` -Adverbo
    - `6` - Adposição
    - ` 7 ` -Interjeição
    - ` 8 ` -Conjunção
    - ` 9 ` -Determinador
    - ` 10 ` -Quantificador

    Em inglês, o substantivo (`3`), o verbo (`2`) e o adjetivo (`4`) são as partes mais comuns do discurso que são usadas para entradas do dicionário.

    > **Nota:** a parte do discurso não determina automaticamente o tipo de uma menção. Não presuma que todos os substantivos equivalem ao tipo de entidade menções e todos os verbos equivalem ao tipo de relação menções. Por exemplo, *Americano* é um adjetivo, mas pode ser melhor anotado como o tipo de entidade **GPE** (entidade geopolítica) ou `PERSON`. *Atendido* é um verbo, mas pode ser melhor anotado como um `EVENT_MEETING`.

    Em outras linguagens, como alemão, que usa palavras compostas, a precisão da parte de informações do discurso é ainda mais importante para ajudar a determinar limites de palavras.

- ** poscode **  (chinês)

    Especifica um código que identifica a parte do discurso. O valor da parte do discurso é importante para a tokenização de texto e a pré-anotação em idiomas como chinês (simplificado e tradicional) que não usam espaço em branco para denotar limites de palavras.
    - ` 32 ` -Noun
    - ` 31 ` -Nome (Nome da família)
    - ` 35 ` -Noun (Organização)
    - ` 34 ` -Noun (Outro)
    - ` 33 ` -Noun (Nome da Pessoa)

- ** poscode **  (japonês)

    Especifica um código que identifica a parte do discurso. A parte de valor do discurso é importante para a tokenização de texto e pré-anotação em linguagens como japonês que não usam espaço em branco para denotar limites de palavras.
    - `19` - Substantivo
    - ` 23 ` -Prefixo Comum
    - ` 24 ` -Sufixo Comum
    - ` 140 ` -Nome Pró-pero (Sobrenome)
    - ` 141 ` -Nome do Proper (Primeiro Nome)
    - ` 146 ` -Nome do Proper (Nome da Pessoa)
    - ` 142 ` -Nome Pró-pero (Organização)
    - ` 144 ` -Nome do Proper (Nome do Local)
    - `143` - Nome próprio (Região)
    - ` 145 ` -Nome Pró-portivo (Outro)

- ** poscode **  (Coreano)

    Especifica um código que identifica a parte do discurso. A parte de valor do discurso é importante para a tokenização de texto e pré-anotação em linguagens como coreano que não usam espaço em branco para indicar limites de palavras.
    - ` 10010 ` -Noun
    - ` 10300 ` -Nome do Proper (Último Nome)
    - ` 10310 ` -Nome do Proper (Primeiro Nome)
    - ` 110360 ` -Nome do Proper (Nome da Pessoa)
    - ` 10320 ` -Nome Pró-pero (Organização)
    - ` 10340 ` -Nome do Proper (Nome do Local)
    - ` 10330 ` -Nome do Proper (Região)
    - ` 10350 ` -Nome Pró-portivo (Outro)

- **surface**

    Especifica termos equivalentes, também chamados de formas superficiais. Repita o lema como uma forma superficial e use uma vírgula para separar múltiplas formas superficiais. Se uma forma superficial inclui uma vírgula, coloque a forma superficial entre aspas.

Por exemplo:

```
lemma,poscode,surface
IBM,3,IBM Corp.,IBM,"International Business Machines, Inc."
Department of Energy,3,DOE,Department of Energy
premium,4,premium,premium-grade
```
{: screen}

**Conceitos relacionados**:

[Fazendo upload de recursos de outra área de trabalho](/docs/services/watson-knowledge-studio/exportimport.html)

**Tarefas relacionadas**:

[Pré-anotando documentos com um dicionário](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannot)

## Incluindo dicionários em uma área de trabalho
{: #wks_projdictionaries}

Incluir dicionários é uma etapa opcional na criação de um modelo. Os dicionários são úteis porque eles permitem que você dê início ao processo de anotação.

### Sobre essa Tarefa

Se você fornece um dicionário, é possível executar o pré-anotador de dicionário nos documentos. O pré-anotador localiza termos que são representados em seu dicionário e os anota automaticamente. Essa passagem inicial nos documentos simplifica a tarefa do anotador humano porque ele pode revisar as anotações que foram incluídas pelo pré-anotador e corrigi-las ou incluir neles. Ela não tem que iniciar totalmente do zero.

A restrição a seguir se aplica a dicionários:

- Máximo de 15.000 entradas por dicionário

    > **Nota:** esse limite não se aplica a dicionários cujo upload é feito como um arquivo de dicionário `CSV`. Os dicionários somente leitura podem conter mais entradas.

- Máximo de 64 dicionários por área de trabalho

### Procedimento

Para incluir um dicionário em sua área de trabalho:

1. Efetue login como um administrador ou gerente de projeto do {{site.data.keyword.knowledgestudioshort}} e abra a página **Ativos** > **Dicionários**.
1. Execute uma das tarefas a seguir:

    - Ao lado do botão **Criar dicionário**, clique no ícone **Menu** e, em seguida, selecione **Fazer upload do dicionário**. Selecione um dicionário e, em seguida, clique em **Fazer upload**. Depois de fazer upload de um dicionário, selecione-o para visualizar o dicionário e associá-lo a um tipo de entidade.

    É possível fazer upload de um arquivo ZIP que contém um dicionário transferido por download de outra área de trabalho do {{site.data.keyword.knowledgestudioshort}}. Deve-se fazer upload do sistema de tipos que foi transferido por download da outra área de trabalho no formato JSON antes de poder fazer upload do arquivo de dicionário correspondente. É possível editar e incluir entradas em um dicionário que você reutiliza de outra área de trabalho do {{site.data.keyword.knowledgestudioshort}}. Consulte [Fazendo upload de recursos de outra área de trabalho](/docs/services/watson-knowledge-studio/exportimport.html) para obter mais detalhes.

    Fazer upload de um arquivo CSV também é suportado, mas fazer upload dele diretamente como um dicionário cria um dicionário somente de visualização que não é possível editar ou usar para pré-anotar documentos. Para fazer upload de um arquivo CSV que é possível editar e usar para pré-anotação, clique em **Criar dicionário** para primeiro criar um dicionário vazio e, em seguida, fazer upload do conteúdo CSV como entradas para esse dicionário recém-criado.

    - Clique no botão **Criar dicionário** para criar um dicionário vazio no qual é possível incluir subsequentemente entradas de dicionário. Especifique um nome descritivo para o dicionário e, em seguida, clique em **Salvar**.

2. Para incluir entradas no dicionário, execute uma das tarefas a seguir:

    - Clique em **Incluir entrada** para incluir uma entrada de dicionário. Especifique o *lema* (a forma de palavra mais representativa para o termo).
    - Clique em **Fazer upload** para fazer upload de um arquivo `CSV` que contém entradas de dicionário e, em seguida, navegue para selecionar o arquivo. O arquivo `CSV` deve ser menor que 1 MB.

3. Depois de fazer upload ou incluir entradas, é possível editá-las.

    Abra uma entrada para especificar termos equivalentes, chamados *formas superficiais*. Cada forma superficial deve ser 256 ou menos caracteres de comprimento. É possível mudar qual das formas superficiais é usada como o lema. Por exemplo, o lema *{{site.data.keyword.IBM_notm}}* pode ter formas superficiais como *{{site.data.keyword.IBM_notm}} Corp.* e *International Business Machines, Inc.*.

4. Selecione a parte apropriada do discurso para cada lema e forma superficial no dicionário.

    A parte de informações do discurso é usada pelo tokenizer e durante a pré-anotação.

5. Clique em **Salvar** para armazenar suas mudanças.

### O que fazer em seguida

Execute o pré-anotador, que usa os dicionários que você criou para fazer uma passagem preliminar dos documentos de origem e inclui anotações neles.

**Tarefas relacionadas**:

[Pré-anotando documentos com um dicionário](/docs/services/watson-knowledge-studio/preannotation.html#wks_preannot)

**Referência relacionada**:

[Suporte ao idioma](/docs/services/watson-knowledge-studio/language-support.html)
