# Apenas Um Readme

### Bem-vindo, ao meu Readme de estudos!

Esse é um Readme que decidi fazer para estudos, para conseguir massificar as informações que tenho estudado ultimamente e lapidar alguns conceitos que já conhecia.<br>
Meu objetivo é ter tudo na ponta da lingua e saber explicar sem travar em nenhum momento, sobre todos os tópicos abordados.<br>
Com o tempo eu vou adicionando mais tópicos conforme vou estudando sobre mais assuntos que ao meu ver parecem interessantes.<br>
Tudo escrito na unha. :grinning:

### Tópicos 

- [Apache Kafka](#apache-kafka-v04)
- [DDD](#ddd-v02)
- [TDD](#tdd)
- [BDD](#bdd)
- [Scrum](#scrum)
- [SOLID](#solid-v01)
- [Diferença entre interface e classe abstrata no Java](#diferença-entre-interface-e-classe-abstrata-no-java)
- [Arquitetura Hexagonal](#arquitetura-hexagonal)
- [Spring Security](#spring-security)
- [Ferramentas de pagamento](#ferramentas-de-pagamento)
- [Tipos de atribuições de valores](#tipos-de-atribuições-de-valores)
- [O que é a memória HEAP?](#o-que-é-a-memória-heap)
- [WebFlux](#Webflux)
- [Padrões de projeto](#padrões-de-projeto)
  
## Apache Kafka v0.4

### <strong> Use Cases - Apache Kafka: </strong> <br>
[Source](https://kafka.apache.org/uses) <br><br>
1 - Mensageria: <br>
O Kafka funciona bem como substituto para brokers de mensagens tradicionais. Os brokers de mensagens são usados por diversas razões (para separar o processamento dos produtores de dados, para armazenar mensagens não processadas, etc).
Em comparação com a maioria dos sistemas de mensagens, o Kafka possui a melhor taxa de transferência, particionamento incorporado, replicação e tolerância a falhas, o que torna uma boa solução para aplicativos de processamento de mensagens de larga escala.
Esse uso é comparável a sistemas de mensagens tradicionais, como ActiveMQ ou RabbitMQ.<br>
2 - Rastreamento de atividades de sites: <br>
O caso de uso original do Kafka era reconstruir um pipeline de rastreamento de atividades do usuário como um conjunto de feeds de publicação e assinatura em tempo real. Isso significa que as atividades do site (visualizações de página, pesquisas ou ações que os usuários possam fazer) são publicadas em tópicos centrais, com um tópico por tipo de atividade. Esses feeds estão disponíveis para assinatura em uma variedade de casos de uso, incluindo processamento em tempo real, monitoramento em tempo real e carregamento em sistemas Hadoop ou data warehouses offline para processamento em relatórios offline.
O rastreamento de atividades geralmente gera um grande volume de mensagens, pois muitas mensagens de atividades são geradas para cada visualização de página do usuário. <br>
3 - Métricas: <br>
O Kafka é frequentemente usado para dados de monitoramento operacional. Isso envolve a agregação de estatísticas de aplicativos distribuídos para produzir feeds centralizados de dados operacionais.
4 - Agregação de logs: <br>
Muitas pessoas usam o Kafka como substituto para uma solução de agregação de logs. A agregação de logs geralmente coleta arquivos de log físicos de servidores e os coloca em um local centralizado (um servidor de arquivos ou HDFS, por exemplo) para processamento.
O Kafka abstrai os detalhes dos arquivos e fornece uma abstração mais limpa dos dados de log ou evento como um fluxo de mensagens. Isso permite processamento com latência reduzida e suporte mais fácil para várias fontes de dados e consumo de dados distribuído.
Em comparação com sistemas centrados em logs como Scribe ou Flume, o Kafka oferece desempenho igualmente bom, garantias de durabilidade mais fortes devido à replicação e latência de ponta a ponta muito menor. <br>
5 - Processamento de fluxo: <br>
Muitos usuários do Kafka processam dados em pipelines de processamento compostos por vários estágios, nos quais os dados brutos de entrada são consumidos a partir de tópicos do Kafka e, em seguida, agregados, enriquecidos ou transformados de outras formas em novos tópicos para consumo ou processamento subsequente. Por exemplo, <br> 
um pipeline de processamento para recomendar artigos de notícias pode coletar o conteúdo do artigo de feeds RSS e publicá-lo em um tópico "artigos"; <br>
um processamento posterior pode normalizar ou deduplicar esse conteúdo e publicar o conteúdo do artigo depurado em um novo tópico;<br>
uma etapa final de processamento pode tentar recomendar esse conteúdo aos usuári9os.<br>
Esses pipeline de processamento criam gráficos de fluxos de dados em tempo real com base nos tópicos individuais. A partir da versão 0.10.0.0, uma biblioteca de processamento de fluxo leve, porém poderosa, chamdaa Kafka Streams, está disponível no Apache Kafka para realizar esse processamento de fluxo de código aberto alternativas incluem o Apache storm e o Apache Samza. <br>
6 - Event Sourcing: <br>
Event sourcing é um estilo de design de aplicativo no qual as alterações de estado são registradas como uma sequência de registros ordenados por tempo. O suporte do Kafka para armazenamento de log muito grande o torna um excelente backend para um aplicativo construído nesse estilo. <br>
7 - Log de confirmação: <br>
O Kafka pode servir como um tipo de log de confirmação externo para um sistema distribuído. O log ajuda a replicar dados entre nós e atua como um mecanismo de ressincronização para nós com falha restaurarem seus dados. O recurso de compactação de log no Kafka ajuda a suportar esse uso. Nesse caso, o Kafka é semelhante ao projeto Apache BookKeeper.


## DDD v0.2
  <small><em>"Se os programadores não estão interessados no domínio, eles aprendem apenas o que a aplicação deve fazer, não os princípios por trás dela."<br> - Eric Evans</em></small>
  
O DDD, Domain-Driven Design ou simplesmente Design Orientado ao Domínio, é uma abordagem para a modelagem de software que tem como foco principal a criação de um modelo de domínio. <br> 
Baseia-se na implementação de modelos que refletem as competências e a complexidade do negócio da organização.<br>
Essa abordagem oferece ferramentas de modelagem estratégica e tática, com o objetivo de entregar um software de alta qualidade. <br> 
É especialmente útil no desenvolvimento de aplicações que lidam com processos de negócios complexos, proporcionando uma aceleração no seu desenvolvimento.</br> Pode ser utilizado independente da linguagem. <br>
<strong> Não é: forma de organizar pastas, organização de código, tecnologia, framework, arquitetura ou metodologia. Também não impõe processos rígidos ao time. </strong> <br>

Alguns dos termos utilizados são: Design estratégico e design tático.

Começando pelo design tático ou modelagem tática, é basicamente a implementação utilizando o Domain Model Pattern <br>
(uma abordagem que diz como escrever as classes que irão mapear os modelos do mundo real e implementar os comportamentos do negócio). <br>
Padrões no design tático: Entities e Value Objects definem os conceitos do domínio. Domain Service assume a responsabilidade que não se encaixa em outros projetos. Aggregates que define fronteiras entre objetos. Factory e repositories que lida com a criação e armazenamento de objetos.

O design estratégico ou modelagem estratégica, é a parte teórica. As informações abaixo fazem parte do padrão estratégico.
 <small><em>"O Design Estratégico é como fazer o rascunho antes de entrar nos detalhes da implementação. Que ele destaca o que é estrategicamente importante para o negócio; como dividir o trabalho por importância; e como fazer integrações da melhor maneira"<br> - Vaughn Vernon</em></small>
 
Diferente da hospedagem de sites, o domínio abordado nesse tópico é o negócio da sua empresa ou o assunto do seu projeto. Então, precisa necessariamente entender o negócio para ser possível
de implementar o DDD em um projeto. Nessa implementação existem 2 papeis: <strong> o time de desenvolvimento e os domain experts </strong> <br>

Existem alguns pilares no DDD:
1. <strong> Linguagem Ubíqua: </strong> utilizada por toda a equipe do projeto. Criada justamente para facilitar a comunicação e o entendimento dos termos específicos utilizados tantos
pelo time de desenvolvimento quanto pelo domain experts, onde cada entidade possui termos onde são necessários "uma tradução" para haver uma comunicação clara entre ambos os times.
2. <strong> Bounded Context: </strong> delimitação do contexto. Uma vez que todo domínio é colocado em um modelo, para evitar que seja complexo demais, delimitará esses contextos baseados nas intenções de negócio.
Cada bounded context pode ter sua linguagem ubíqua, sua abordagem de arquitetura, de armazenamento de dados e até a própria equipe de desenvolvimento.
Para criar esse modelo e entender como os bounded contexts se relacionam e como se comunicam é utilizado o <strong>Context map</strong>(um modelo que dará uma visão geral do software,
geralmente um desenho simples que da para ser feito com uma caneta e um quadro branco).
Existem alguns padrões de relacionamento entre os bounded contexts e implicam diretamente na estratégia de como os times de projeto irão trabalhar. Na dependência entre eles, na arquitetura e até na
estratégia de comunicação. Os principais tipos de relacionamentos entre os contextos são:
Shared Kernel: Quando vários bounded contexts, compartilham do mesmo domínio. Alterando-o, afetará todas as equipes.<br>

Customer-Supplier Development: quando existe um relacionamento de cliente-fornecedor, ou, Downstream e Upstream. A Equipe Upstream pode ter êxito interdependente da equipe Downstream.
Um contexto é o fornecedor do serviço e o outro é o consumidor. As equipes definirão testes de aceitação automatizados que irão validar as interfaces que a equipe de Upstream fornece, com isso as equipes
de fornecedores poderá fazer as modificações sem se preocupar em quebrar o sistema.
Tipos de relacionamentos Customer-Supplier Development:
1. Conformist: relacionamento onde o bounded context downstream se conforma que o modelo upstream não atende suas necessidades e as modificações realizadas por ele impactam diretamente em seu contexto. Mas ele se vira.
2. Partner: nesse relacionamento os bounded contexts parceiros, unidos por uma dependência mutua e deverão trabalhar em conjunto.
3. Anticorruption Layer: ja nesse relacionamento a equipe downstream cria uma camada para proteger o seu contexto das modificações do upstream (comum em sistemas legados).



## TDD



## BDD



## Scrum



## SOLID v0.1

<h5>O que é SOLID? </h5>
SOLID é um acrônimo de 5 definições que são aplicadas para obter boas práticas nos projetos.

<h5>Quais são as 5 definições? </h5>
1. S -> Single Responsibility Principle (Princípio da responsabilidade única)
2. O -> Open-Closed Principle (Princípio Aberto-Fechado)
3. L -> Liskov Subtitution Principle (Princípio da substituição de Liskov)
4. I -> Interface Segregation Principle (Princípio da Segregação da Interface)
5. D -> Dependency Inversion Principle (Princípio da inversão de dependência)

<h5>O que são exatamente cada um desses princípios? </h5>
1. 



## Diferença entre interface e classe abstrata no Java

Interfaces:
- Só pode ter métodos abstratos.
- Definem apenas a assinatura dos métodos que as classes devem implementar.
- Uma classe pode implementar várias interfaces, herdando o comportamento.
- Não pode ter construtores.
- É um contrato que define os métodos que uma classe deve implementar, não pode ser instanciada.
- Necessária quando é pra definir um contrato comum a um grupo de classes não necessariamente relacionadas, permitindo que compartilhem de comportamentos independentemente de sua hierarquia.



Classes Abstratas:
- Pode ter métodos abstratos(sem implementação) e métodos concretos.
- Pode ser estendida por uma ou várias classes.
- Pode ter construtores.
- Pode ser instanciada.
- Necessária quando é pra fornecer uam implementação padrão para um conjunto de classes relacionadas e que também deseja permitir que essas classes personalizem partes específicas do comportamento.



## Arquitetura Hexagonal



## Spring Security



## Ferramentas de pagamento

Ferramentas para trabalhar com integração de pagamento: <br>
Internacional: Stripe <br>
Nacional: PagSeguro / Pagar.me <br>



## Tipos de atribuições de valores
1. Atribuição por valor - Quando o valor real da variável é copiado e atribuído a outra variável ou passado como argumento para uma função. Variáveis com cópia independente de seus valores. <br>
2. Atribuição por referência - Quando um ponteiro ou referência para a memória em que o valor está armazenado é copiado. Duas variáveis referenciando um mesmo objeto na memória e, portanto, qualquer alteração em uma variável afetará a outra. <br>

Agora em relação ao Java...



## O que é a memória HEAP?
Memória HEAP é uma memória usada para armazenar objetos e instâncias de classes, com alocação e desalocação controladas pelo programador. <br>
Por outro lado, temos a memória stack que é usada para armazenar variáveis locais e dados relacionados às chamadas de função, com alocação e
desalocação automáticas. <br>
No Java, a memória heap é usada para alocar objetos e é gerenciada automaticamente pelo garbage collector.<br>
Já a memória stack é usada para armazenar variáveis locais e referências a objetos.



## Webflux

## Padrões de projeto
 <small><em>"Cada padrão descreve um problema que ocorre frequentemente em seu ambiente, e então descreve o cerne da solução para aquele problema, de um modo tal que você pode usar esta solução milhões de vezes, sem nunca fazer a mesma coisa repetida."<br> - Christopher Alexander</em></small> <br><br>
Estou estudando 3 tipos de padrões de projeto: Criacionais, Estruturais e Comportamentais. <br>
Primeiramente vou começar com um breve resumo sobre cada um. <br>
<strong> Padrões de projetos Criacionais </strong> basicamente existem diversos mecanismos para criar um objeto. Ao invés de utilizar diretamente o operador "new", podemos utilizar algum padrão que nos forneça mais flexibilidade no código. <br>
<strong> Padrões de projetos Estruturais </strong> mostra como objetos podem se unir em estruturas maiores, porém de forma organizada, facilitando possíveis extensões. <br>
<strong> Padrões de projetos Comportamentais </strong> organiza a forma de comunicação entre os objetos.<br><br>
Anotação para organização futura: <br>
Padrões de projeto Criacionais: Factory Method, Abstract Factory, Singleton, Monostate, Builder, Prototype. <br>
Padrões de projeto Estruturais: Adapter, Bridge, Composite, Decorator, Facade, Flyweight, Proxy. <br>
Padrões de projeto Comportamentais: Chain of Responsability, Memento, Command, Iterator, Mediator, Observer, State, Strategy, Template Method. <br>
