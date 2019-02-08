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

Essa documentação destina-se ao {{site.data.keyword.knowledgestudiofull}} no {{site.data.keyword.cloud}}. Para ver a documentação para a versão anterior do {{site.data.keyword.knowledgestudioshort}} no {{site.data.keyword.IBM_notm}} Marketplace, [clique neste link ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/docs/services/knowledge-studio/glossary.html){: new_window}.
{: tip}

# Glossário
{: #glossary}

O glossário inclui termos e definições para o {{site.data.keyword.knowledgestudioshort}}.
{: shortdesc}

As referências cruzadas a seguir são usadas nesse glossário:

- *Veja* encaminha você de um termo para um sinônimo preferencial, ou de um acrônimo ou abreviação para o formato integral definido.
- *Consulte também* o encaminha para um termo relacionado ou contrastante.

[A](/docs/services/watson-knowledge-studio/glossary.html#gloss_A) [B](/docs/services/watson-knowledge-studio/glossary.html#gloss_B) [C](/docs/services/watson-knowledge-studio/glossary.html#gloss_C) [D](/docs/services/watson-knowledge-studio/glossary.html#gloss_D) [E](/docs/services/watson-knowledge-studio/glossary.html#gloss_E) [F](/docs/services/watson-knowledge-studio/glossary.html#gloss_F) [G](/docs/services/watson-knowledge-studio/glossary.html#gloss_G) [H](/docs/services/watson-knowledge-studio/glossary.html#gloss_H) [I](/docs/services/watson-knowledge-studio/glossary.html#gloss_I) [K](/docs/services/watson-knowledge-studio/glossary.html#gloss_K) [L](/docs/services/watson-knowledge-studio/glossary.html#gloss_L) [M](/docs/services/watson-knowledge-studio/glossary.html#gloss_M) [N](/docs/services/watson-knowledge-studio/glossary.html#gloss_N) [O](/docs/services/watson-knowledge-studio/glossary.html#gloss_O) [P](/docs/services/watson-knowledge-studio/glossary.html#gloss_P) [R](/docs/services/watson-knowledge-studio/glossary.html#gloss_R) [S](/docs/services/watson-knowledge-studio/glossary.html#gloss_S) [T](/docs/services/watson-knowledge-studio/glossary.html#gloss_T)

## A
{: #gloss_A}

- **precisão**

    Uma medida da correção de anotações que são produzidas por um modelo de aprendizado de máquina. Veja também [precisão](/docs/services/watson-knowledge-studio/glossary.html#gloss_P) e [rechamada](/docs/services/watson-knowledge-studio/glossary.html#gloss_R).

- **análise de precisão**

    Análise de pontuações do modelo de aprendizado de máquina para determinar se mudanças são necessárias para melhorar a precisão.

- **adjudicação**

    Um processo iterativo para resolver conflitos de anotação comparando as anotações incluídas no mesmo documento por diferentes anotadores humanos.

- **mecanismo de análise**

    Um programa que analisa artefatos, como documentos, e deduz informações sobre eles e que implementa a especificação de interface Mecanismo de Análise UIMA. Os mecanismos de análise são construídos por meio de blocos de construção chamados anotadores. Um mecanismo de análise pode conter um único anotador, que é referido como um mecanismo de análise primitivo, ou múltiplos anotadores, que são referidos como um mecanismo agregado de análise.

- **anotação**

    Informações sobre um período de texto. Por exemplo, uma anotação pode indicar que um período de texto representa um nome de empresa.

- **conjunto de anotações**

    Em anotação humana, uma coleção de documentos que são extraídos do corpus que permitem que a carga de trabalho seja compartilhada por múltiplos anotadores humanos. Na anotação baseada em máquina, uma coleção de documentos que podem ser usados como dados ocultos, dados de treinamento ou dados de teste.

- **gerenciador de processos de anotação**

    Uma função que é responsável por gerenciar as atividades do ciclo de vida de anotação integral em uma área de trabalho. O gerente de projeto incluído em uma área de trabalho normalmente executa as atividades de um gerenciador de processos de anotação.

- **anotador**

    Veja [anotador humano](/docs/services/watson-knowledge-studio/glossary.html#gloss_H) e [anotador de aprendizado de máquina](/docs/services/watson-knowledge-studio/glossary.html#gloss_M).

- **atributo**

    Uma característica ou traço de uma entidade que descreve a entidade; por exemplo, o número de telefone de um funcionário é um dos atributos do funcionário.

## B
{: #gloss_B}

- **dados ocultos**

    Um conjunto de documentos anotados com a verdade absoluta, como pares de pergunta e resposta, anotação semântica e julgamento de passagem. Os dados ocultos nunca são liberados ou vistos por desenvolvedores e são usados para testar o sistema periodicamente para avaliar o desempenho em dados invisíveis. O teste em dados ocultos evita que a precisão seja manchada por excesso de ajuste em conjuntos de perguntas ou anotações conhecidas. Os resultados relatados devem vir somente de testes que são executados em dados ocultos. Veja também [dados de teste](/docs/services/watson-knowledge-studio/glossary.html#gloss_T) e [dados de treinamento](/docs/services/watson-knowledge-studio/glossary.html#gloss_T).

## C
{: #gloss_C}

- **concordância**

    Fornece uma maneira de assegurar que a mesma menção seja anotada com o mesmo tipo de entidade em todo o documento e em conjuntos de anotações. A concordância ajuda a assegurar a consistência entre múltiplas ocorrências de uma menção sem requerer que o anotador humano rotule manualmente cada ocorrência.

- **matriz de confusão**

    Uma tabela que fornece um detalhamento numérico de conjuntos de documentos anotados. A tabela é usada para comparar as anotações que foram incluídas por um modelo de aprendizado de máquina para as anotações na verdade absoluta. A tabela relata o número de [falsos positivos](/docs/services/watson-knowledge-studio/glossary.html#gloss_F), [falsos negativos](/docs/services/watson-knowledge-studio/glossary.html#gloss_F), [positivos verdadeiros](/docs/services/watson-knowledge-studio/glossary.html#gloss_T) e [negativos verdadeiros](/docs/services/watson-knowledge-studio/glossary.html#gloss_T).

- **correferência**

    Um relacionamento entre duas palavras ou frases em que ambos se referem à mesma pessoa ou coisa e um permanece como um antecedente linguístico da outra. Por exemplo, há uma correferência entre os dois pronomes na frase "Ela se ensinou", mas não na frase "Ela a ensinou". Uma correferência vincula duas entidades equivalentes no mesmo texto.

- **cadeia de correferência**

    Uma lista de entidades que foram anotadas como correferências. Quando você anota as menções como correferências, o sistema cria uma cadeia de correferências. A cadeia fornece uma maneira de você visualizar todas as menções no contexto e verificar se todas as ocorrências pertencem juntas sob o mesmo tipo de entidade.

- **corpus**

    Uma coleção de documentos de origem que foram incluídos em uma área de trabalho e usados para treinar um modelo de aprendizado de máquina.

- **curar**

    Selecionar, coletar, conservar e manter o conteúdo relevante para um tópico específico. A curadoria estabelece, mantém e inclui valor para dados; ela transforma dados em informações confiáveis e conhecimento.

## D
{: #gloss_D}

- **dicionário**

    Uma coleção de palavras que podem ser usadas para pré-anotar documentos. Uma nova anotação é criada para cada palavra no texto do documento que corresponde a um termo no dicionário. Um modelo de aprendizado de máquina pode ser configurado com um ou mais dicionários independentes, que são geralmente específicos do domínio, como um dicionário para farmacêutica e um dicionário para gerenciamento de riqueza. Veja também [lema](/docs/services/watson-knowledge-studio/glossary.html#gloss_L) e [forma superficial](/docs/services/watson-knowledge-studio/glossary.html#gloss_S).

- **pré-anotador de dicionário**

    Um componente que identifica menções em texto que correspondem a um conjunto específico de palavras. Usando a terminologia específica de domínio para pré-anotar texto, os pré-anotadores de dicionário podem acelerar a capacidade de um anotador humano de preparar um conjunto de documentos de verdade absoluta.

- **conjunto de documentos**

    Uma coleção de documentos. Os documentos que são importados juntos se tornam um conjunto de documentos. Os documentos anotados que são agrupados juntos para propósitos de treinamento (Teste, Treinamento, Oculto) são gerados como conjuntos de documentos.

## E
{: #gloss_E}

- **entidade**

    1. Uma menção que é anotada por um tipo de entidade.
    1. Uma pessoa, um objeto ou um conceito sobre os quais informações são armazenadas.
    1. Um conjunto de detalhes que são mantidos sobre um objeto do mundo real, como uma pessoa, local ou conta bancária. Uma entidade é um tipo de item.

- **tipo de entidade**

    O tipo de entidade que uma menção representa sem consideração para contexto. Por exemplo, a menção {{site.data.keyword.IBM_notm}} pode ser anotada pelo tipo de entidade ORGANIZATION.

    Em um modelo de relacionamento de entidade, um tipo de entidade é a coisa que está sendo modelada ou a coisa à qual uma menção se refere, como o nome de uma pessoa ou local. Tipos de entidade diferentes têm diferentes conjuntos de atributos, como "sobrenome" ou "cidade natal", e são conectados por meio de relacionamentos, como "vive em". Um tipo de entidade existe independentemente e pode ser identificado exclusivamente.

## F
{: #gloss_F}

- **Pontuação F1**

    Uma medida de precisão de um teste que considera a precisão e a rechamada para calcular a pontuação. A pontuação F1 pode ser interpretada como uma média ponderada dos valores de precisão e rechamada. Uma pontuação F1 atinge seu melhor valor em 1 e pior valor em 0.

- **falso negativo**

    Uma resposta ou anotação que é correta, mas estava prevista para ser incorreta.

- **falso positivo**

    Uma resposta ou anotação que está incorreta, mas estava prevista para ser correta.

- **recurso**

    Um membro de dados ou atributo de um tipo.

- **pontuação Fleiss Kappa**

    Uma medida de quão consistentemente a mesma anotação foi aplicada por múltiplos anotadores humanos em documentos de sobreposição. A pontuação Fleiss Kappa atinge seu melhor valor em 1 e pior valor em 0.

## G
{: #gloss_G}

- **verdade absoluta**

    O conjunto de dados examinados, consistindo em anotações incluídas por anotadores humanos, que é usado para adaptar o modelo de aprendizado de máquina para um domínio específico. A verdade absoluta é usada para treinar modelos de aprendizado de máquina, medir o desempenho do modelo (precisão e rechamada) e calcular a altura livre para decidir onde focar os esforços de desenvolvimento para melhorar o desempenho. A precisão da verdade absoluta é essencial porque as imprecisões na verdade absoluta serão correlacionadas com as imprecisões nos componentes que usam isso.

## H
{: #gloss_H}

- **análise de altura livre**

    O processo de determinar quantas melhorias na exatidão, precisão ou rechamada podem ser esperadas, abordando algumas classes de problemas que são identificados ao executar a análise de precisão.

- **anotador humano**

    Um especialista no assunto que revisa, modifica e aumenta os resultados de pré-anotação, identificando menções, relacionamentos de tipo de entidade e correferências de menção. Ao examinar o texto no contexto, um anotador humano ajuda a determinar a verdade absoluta e melhorar a precisão do modelo de aprendizado de máquina.

## I
{: #gloss_I}

- **concordância entre anotadores**

    Uma medida de quanto da mesma forma um documento em dois ou mais conjuntos de documentos é anotado.

## K
{: #gloss_K}

- **gráfico de conhecimento**

    Um modelo que consolida entidades de tipo, seus relacionamentos, suas propriedades e taxonomias hierárquicas para representar uma organização de conceitos de um determinado domínio. Após o armazenamento do gráfico de conhecimento ser carregado com entradas de origens de dados estruturados e não estruturados, os usuários e aplicativos podem acessar o gráfico de conhecimento para explorar os elementos chave de conhecimento para um domínio específico, explorar interações e descobrir relacionamentos adicionais.

## L
{: #gloss_L}

- **lema**

    A forma normalizada ou canônica de uma palavra. Normalmente, o lema é a forma não derivada e não flexionada de um substantivo ou um verbo. Por exemplo o lema dos termos 'organizando' e 'organizado' é 'organizar'. Veja também [dicionário](/docs/services/watson-knowledge-studio/glossary.html#gloss_D) e [forma superficial](/docs/services/watson-knowledge-studio/glossary.html#gloss_S).

## seg.
{: #gloss_M}

- **aprendizado de máquina**

    Um método de análise de dados que aprende iterativamente com dados passados e se adapta independentemente quando exposta a novos dados. O modelo matemático no núcleo do aprendizado de máquina é construído de entradas de verdade absoluta. Por meio do treinamento e refinamento de dados de entrada de exemplo, o modelo pode entregar resultados precisos e repetidos quando ele analisa novos dados.

- **anotador de aprendizado de máquina**

    Veja [modelo de aprendizado de máquina](/docs/services/watson-knowledge-studio/glossary.html#gloss_M).

- **modelo de aprendizado de máquina**

    Um componente que identifica entidades e relacionamentos de entidade de acordo com um modelo estatístico que é baseado na verdade absoluta. O modelo aplica experiência passada, como dados de treinamento, para determinar ou prever o resultado correto de experiências futuras com base nas características dos dados. Essas experiências passadas são capturadas na forma de um modelo, calculando pontuações de recurso para cada resposta ou evidência candidata e combinando isso com resultados conhecidos. Às vezes referido como *anotador de aprendizado de máquina*.

- **menção**

    Um período de texto que você considera relevante em seus dados de domínio. Por exemplo, em um sistema de tipos de veículos automotivos, as ocorrências de termos como "airbag", "Ford Explorer" e "sistema de retenção infantil" podem ser menções relevantes.

## N
{: #gloss_N}

- **entidade nomeada**

    Um conceito em um domínio que cai em uma categoria bem definida, como nomes de organizações, locais, autores ou doenças.

- **processamento de linguagem natural**

    Um campo de inteligência artificial e da linguística que estuda os problemas inerentes no processamento e manipulação de língua natural, com um objetivo de aumentar a capacidade dos computadores para entender linguagens humanas.

## O
{: #gloss_O}

- **ontologia**

    Uma especificação formal explícita da representação dos objetos, conceitos e outras entidades que podem existir em alguma área de interesse e os relacionamentos entre eles.

## P
{: #gloss_P}

- **parte do discurso (POS)**

    Em um dicionário, itens lexicais individuais são designados a tags de parte do discurso (POS). Por exemplo, a palavra 'voo' pode ser identificada como um verbo ou um substantivo.

- **desempenho**

    A medida de um sistema {{site.data.keyword.watson}} em termos de exatidão, precisão e rechamada, por exemplo, quando responder perguntas, descobrir relacionamentos ou anotar texto.

- **pré-anotação**

    O processo de anotar um conjunto de documentos anteriores à anotação humana. Os documentos podem ser pré-anotados usando um modelo baseado em regra, um modelo de aprendizado de máquina, {{site.data.keyword.nlufull}} ou um dicionário. A pré-anotação pode ajudar os anotadores humanos a prepararem mais rapidamente um conjunto de documentos de verdade absoluta.

- **precisão**

    Uma medida que especifica a proporção de resultados que são relevantes. A precisão, que é um valor preditivo positivo, é determinada pelo número de resultados positivos corretos dividido pelo número de todos os resultados positivos. A precisão é medida melhor usando ambos, a precisão e a rechamada. Veja também [precisão](/docs/services/watson-knowledge-studio/glossary.html#gloss_A) e [rechamada](/docs/services/watson-knowledge-studio/glossary.html#gloss_R).

- **archive de mecanismo de processamento (PEAR)**

    Um archive `.pear` que inclui um mecanismo de análise Unstructured Information Management Architecture (UIMA) e todos os recursos que são necessários para usá-lo para análise customizada.

## t
{: #gloss_R}

- **rechamada**

    Uma medida que especifica a porcentagem de resultados relevantes retornados dentre todos os resultados relevantes disponíveis. A rechamada, que é uma medida de sensibilidade, é determinada pelo número de resultados positivos corretos dividido pelo número de resultados positivos que deveriam ter sido retornados. A precisão é medida melhor usando ambos, a precisão e a rechamada. Veja também [precisão](/docs/services/watson-knowledge-studio/glossary.html#gloss_A) e [precisão](/docs/services/watson-knowledge-studio/glossary.html#gloss_P).

- **relação**

    Geralmente, um verbo que reflete como as entidades estão relacionadas entre si. Por exemplo, "vive em" é uma relação entre uma pessoa e uma cidade. Uma relação vincula duas entidades diferentes na mesma sentença.

- **tipo de relação**

    Um relacionamento binário e unidirecional entre duas entidades. Por exemplo, `Mary` `employedBy` {{site.data.keyword.IBM_notm}} é um relacionamento válido; {{site.data.keyword.IBM_notm}} `employedBy` `Mary` não é.

- **função**

    Um atributo que fornece um significado contextual de uma menção. Por exemplo, na frase "Fui para a {{site.data.keyword.IBM_notm}} hoje", {{site.data.keyword.IBM_notm}} é a menção, Organização é o tipo de entidade e Instalação é a função do tipo de entidade.

- **conjunto de regras**

    Um conjunto de regras que definem padrões para anotar texto. Se um padrão se aplica, as ações da regra são executadas nas anotações correspondidas. Uma regra normalmente especifica a condição que deve corresponder, um quantificador opcional, uma lista de restrições adicionais que o texto correspondido deve cumprir e as ações a serem tomadas quando uma correspondência ocorrer, como a criação de uma nova anotação ou a modificação de uma anotação existente.

## S
{: #gloss_S}

- **subtipo**

    Um tipo que estende ou implementa outro tipo; o supertipo.

- **forma superficial**

    A forma de uma palavra ou unidade de múltiplas palavras tal como ela está localizada no corpus. Por exemplo, algumas formas superficiais do lema 'organizar' são os termos 'organizando' e 'organizado'. Veja também [dicionário](/docs/services/watson-knowledge-studio/glossary.html#gloss_D) e [lema](/docs/services/watson-knowledge-studio/glossary.html#gloss_L).

## T
{: #gloss_T}

- **dados de teste**

    Um conjunto de documentos anotados que podem ser usados para avaliar as métricas do sistema após a ingestão e o treinamento. Veja também [dados ocultos](/docs/services/watson-knowledge-studio/glossary.html#gloss_B) e [dados de treinamento](/docs/services/watson-knowledge-studio/glossary.html#gloss_T).

- **treinar**

    O processo de configuração de uma instância do {{site.data.keyword.watson}} com componentes que permitem que o sistema funcione em um domínio específico (por exemplo: conteúdo do corpus, dados de treinamento que geram modelos de aprendizado de máquina, algoritmos programáticos ou outros componentes de verdade absoluta) e, em seguida, fazendo melhorias e atualizações para esses componentes com base na análise de precisão.

- **dados de treinamento**

    Um conjunto de documentos anotados que podem ser usados para treinar modelos de aprendizado de máquina. Veja também [dados ocultos](/docs/services/watson-knowledge-studio/glossary.html#gloss_B) e [dados de teste](/docs/services/watson-knowledge-studio/glossary.html#gloss_T).

- **negativo verdadeiro**

    Uma resposta ou anotação que é realmente incorreta e está prevista para ser incorreta.

- **positivo verdadeiro**

    Uma resposta ou anotação que é realmente correta e está prevista para ser correta.

- **sistema de tipos**

    O sistema de tipos define os tipos de objetos que podem ser descobertos em um documento. O sistema de tipos define todos os tipos de entidade possíveis e os relacionamentos entre os tipos de entidade. É possível definir qualquer número de tipos diferentes em um sistema de tipos. Os sistemas de tipos são geralmente específicos de domínio e específicos de aplicativo.
