# Apenas Um Readme

### Bem-vindo, ao meu Readme de estudos!

Esse é um Readme que decidi fazer para estudos, para conseguir massificar as informações que tenho estudado ultimamente e lapidar alguns conceitos que já conhecia.<br>
Meu objetivo é ter tudo na ponta da lingua e saber explicar sem travar em nenhum momento, sobre todos os tópicos abordados.<br>
Com o tempo eu vou adicionando mais tópicos conforme vou estudando sobre mais assuntos que ao meu ver parecem interessantes.<br>
Todos os tópicos serão atualizados frequentemente conforme vou estudando mais sobre eles. <br>
Tudo escrito na unha. :grinning:

### Tópicos 
- [Algoritmos de busca e de ordenação](#Algoritmos-de-busca-e-ordenação)
- [Apache Kafka](#apache-kafka-v04)
- [Arquitetura Hexagonal](#arquitetura-hexagonal)
- [Banco de imagens](#Banco-de-imagens)
- [BDD](#bdd)
- [Clean Architecture](#clean-architecture)
- [DDD](#ddd-v02)
- [Design Patterns](#Design-Patterns)
- [Diferença entre interface e classe abstrata no Java](#diferença-entre-interface-e-classe-abstrata-no-java)
- [Ferramentas de pagamento](#ferramentas-de-pagamento)
- [NoSQL](#NoSQL)
- [O que é a memória HEAP?](#o-que-é-a-memória-heap)
- [O que são triggers e procedures?](#o-que-são-triggers-e-procedures)
- [Padrões de projeto](#padrões-de-projeto)
- [Paleta de cores](#Paleta-de-cores)
- [Para que serve o Serializable?](#para-que-serve-o-serializable)
- [REST x SOAP](#rest-x-soap)
- [SOLID](#solid-v01)
- [Scrum](#scrum)
- [Spring Security](#spring-security)
- [STRATEGY: Sequence vs Identity](#strategy-sequence-vs-identity)
- [TDD](#tdd)
- [Tipos de atribuições de valores](#tipos-de-atribuições-de-valores)
- [VO x DTO x DAO x BO x Bean](#Vo-x-DTO-x-DAO-x-BO-x-Bean)
- [WebFlux](#webflux)
- [XPages](#XPages)

## Algoritmos de busca e ordenação

## Apache Kafka v0.4

### <strong> Use Cases - Apache Kafka: </strong> <br>
[Source](https://kafka.apache.org/uses) <br><br>
1 - <strong> Mensageria: </strong> <br>
O Kafka funciona bem como substituto para brokers de mensagens tradicionais. Os brokers de mensagens são usados por diversas razões (para separar o processamento dos produtores de dados, para armazenar mensagens não processadas, etc).
Em comparação com a maioria dos sistemas de mensagens, o Kafka possui a melhor taxa de transferência, particionamento incorporado, replicação e tolerância a falhas, o que torna uma boa solução para aplicativos de processamento de mensagens de larga escala.
Esse uso é comparável a sistemas de mensagens tradicionais, como ActiveMQ ou RabbitMQ.<br>
2 - <strong> Rastreamento de atividades de sites: </strong> <br>
O caso de uso original do Kafka era reconstruir um pipeline de rastreamento de atividades do usuário como um conjunto de feeds de publicação e assinatura em tempo real. Isso significa que as atividades do site (visualizações de página, pesquisas ou ações que os usuários possam fazer) são publicadas em tópicos centrais, com um tópico por tipo de atividade. Esses feeds estão disponíveis para assinatura em uma variedade de casos de uso, incluindo processamento em tempo real, monitoramento em tempo real e carregamento em sistemas Hadoop ou data warehouses offline para processamento em relatórios offline.
O rastreamento de atividades geralmente gera um grande volume de mensagens, pois muitas mensagens de atividades são geradas para cada visualização de página do usuário. <br>
3 - <strong> Métricas: </strong> <br>
O Kafka é frequentemente usado para dados de monitoramento operacional. Isso envolve a agregação de estatísticas de aplicativos distribuídos para produzir feeds centralizados de dados operacionais.<br>
4 - <strong> Agregação de logs: </strong> <br>
Muitas pessoas usam o Kafka como substituto para uma solução de agregação de logs. A agregação de logs geralmente coleta arquivos de log físicos de servidores e os coloca em um local centralizado (um servidor de arquivos ou HDFS, por exemplo) para processamento.
O Kafka abstrai os detalhes dos arquivos e fornece uma abstração mais limpa dos dados de log ou evento como um fluxo de mensagens. Isso permite processamento com latência reduzida e suporte mais fácil para várias fontes de dados e consumo de dados distribuído.
Em comparação com sistemas centrados em logs como Scribe ou Flume, o Kafka oferece desempenho igualmente bom, garantias de durabilidade mais fortes devido à replicação e latência de ponta a ponta muito menor. <br>
5 - <strong> Processamento de fluxo: </strong> <br>
Muitos usuários do Kafka processam dados em pipelines de processamento compostos por vários estágios, nos quais os dados brutos de entrada são consumidos a partir de tópicos do Kafka e, em seguida, agregados, enriquecidos ou transformados de outras formas em novos tópicos para consumo ou processamento subsequente. Por exemplo, <br> 
um pipeline de processamento para recomendar artigos de notícias pode coletar o conteúdo do artigo de feeds RSS e publicá-lo em um tópico "artigos"; <br>
um processamento posterior pode normalizar ou deduplicar esse conteúdo e publicar o conteúdo do artigo depurado em um novo tópico;<br>
uma etapa final de processamento pode tentar recomendar esse conteúdo aos usuári9os.<br>
Esses pipeline de processamento criam gráficos de fluxos de dados em tempo real com base nos tópicos individuais. A partir da versão 0.10.0.0, uma biblioteca de processamento de fluxo leve, porém poderosa, chamdaa Kafka Streams, está disponível no Apache Kafka para realizar esse processamento de fluxo de código aberto alternativas incluem o Apache storm e o Apache Samza. <br>
6 - <strong> Event Sourcing: </strong> <br>
Event sourcing é um estilo de design de aplicativo no qual as alterações de estado são registradas como uma sequência de registros ordenados por tempo. O suporte do Kafka para armazenamento de log muito grande o torna um excelente backend para um aplicativo construído nesse estilo. <br>
7 - <strong> Commit Log: </strong> <br>
O Kafka pode servir como um tipo de log de confirmação externo para um sistema distribuído. O log ajuda a replicar dados entre nós e atua como um mecanismo de ressincronização para nós com falha restaurarem seus dados. O recurso de compactação de log no Kafka ajuda a suportar esse uso. Nesse caso, o Kafka é semelhante ao projeto Apache BookKeeper.<br>


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

É uma prática iterativa em que primeiro são feitos os testes unitários para depois realizar a implementação no código de produção refatorando até todas as funcionalidades sejam corretamente implementadas.

## BDD



## Scrum

### Backlog do Produto
É uma lista contendo tudo o que deseja que seja contemplado pelo projeto para chegar em um produto. Contém os requisitos do sistema.<br>
<strong>História do Usuário/User story</strong><br>
É cada requisito registrado no Backlog do Produto.<br>
### Sprint
É cada interação que ocorre com períodos fixos para ser trabalhado no desenvolvimento de um produto entregável. Geralmente tem duração de 2 a 4 semanas. <br>
Durante a sprint é retalizado uma lista de requisitos(retirados do backlog do produto) a serem trabalhados que foram previamente acordados e essa lista é chamada de <strong>Sprint Backlog</strong>
que é definida no início de cada sprint durante o evento que é chamado de <strong>Spring Planning</strong>(planejamento da sprint).<br>
Ao longo da sprint é comum que a equipe realize reuniões dirárias que são chamadas de <strong>Daily Scrum</strong> ou <strong>Daily Stand-up</strong> onde é discutido o processo, o que foi concluído desde a última reunião e quaisquer impedimentos que estejam afetando o trabalho.<br>
Ao final da Sprint ocorre o processo que é chamado de <strong>Sprint Review</strong> onde é feita a demonstração do incremento do produto à equipe de <strong>Stakeholders</strong> e recebe feedback.<br>
Após a Sprint Review, ocorre o <strong>Sprint Retrospective</strong> uma reunião em que a equipe reflete sobre o processo de trabalho da sprint anterior e indetifica oportunidades de melhoria para a próxima sprint.<br>


## SOLID v0.1

<h5>O que é SOLID? </h5>
SOLID é um acrônimo de 5 definições que são aplicadas para obter boas práticas nos projetos.

<h5>Quais são as 5 definições? </h5>
1. <strong>S</strong> -> Single Responsibility Principle (Princípio da responsabilidade única)<br>
2. <strong>O</strong> -> Open-Closed Principle (Princípio Aberto-Fechado)<br>
3. <strong>L</strong> -> Liskov Subtitution Principle (Princípio da substituição de Liskov)<br>
4. <strong>I</strong> -> Interface Segregation Principle (Princípio da Segregação da Interface)<br>
5. <strong>D</strong> -> Dependency Inversion Principle (Princípio da inversão de dependência)<br>

<h5>O que são exatamente cada um desses princípios? </h5>
1. <strong>S - Princípio da Responsabilidade Única:</strong><br>
Este princípio afirma que uma classe deve ter apenas uma única responsabilidade ou motivo para mudar. Em outras palavras, uma classe deve ter apenas uma tarefa ou função bem definida. Isso torna a classe mais coesa e facilita a manutenção e evolução do código.<br>
2. <strong>O - Princípio Aberto-Fechado:</strong><br>
Este princípio defende que uma classe deve estar aberta para extensão mas fechada para modificação. Isso significa que você pode estender o comportamento da classe adicionando novas funcionalidades sem modificar o código existente. Isso promove um código mais flexível e reutilizável.<br>
3. <strong>L - Princípio da Substituição de Liskov:</strong><br>
Este princípio afirma que objetos de uma classe derivada devem poder ser substituídos pelos objetos da classe base sem alterar a corretude do programa. Isso Significa que uma subclasse deve ser substituível por sua classe base sem afetar o comportamento esperado do programa.<br>
4. <strong>I - Princípio da Segregação da Interface:</strong><br>
Este princípio prega que uma classe não deve ser forçada a implementar interfaces que não utiliza. Em vez disso, é melhor ter interfaces menores e mais específicas, para que as classes possam implementar apenas o que é relevante para elas.<br>
5. <strong>D - Princípio da Inversão de Dependência:</strong><br>
Este princípio sugere que as classes de alto nível não devem depender de classes de baixo nível diretamente, mas sim depender de abstrações. Além disso, as abstrações não devem depender de detalhes mas os detalhes devem depender das abstrações. Isso promove um desacoplamento entre as classes e facilita a manutenção e a extensão do sistema.<br>


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
Anotações: Spring Security gera o usuário user com senha aleatória sempre que é executado, caso não seja configurado no application.properties o usuário e a senha. Também é criado na url localhost:8080/login o formulário de login padrão do spring security


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

## Listas

### ArrayList
Utilizar quando precisar de uma lista redimensionável, onde você adiciona e remove elementos com frequência e não precisa de acesso rápido aleatório aos elementos.

### LinkedList
Utilizar quando precisar de uma lista onde você adiciona e remove elementos frequentemente do início ou do final da lista ou quando precisa de acesso rápido a elementos próximos.

### HashSet
Utilizar quando precisar de uma coleção que não permite duplicatas e a ordem dos elementos não é importante.

### TreeSet
Utilizar quando precisar de uma coleção que não permite duplicatas e os elementos devem estar em ordem natural ou definida por um comparador.

### LinkedHashSet
Utilizar quando precisar de uma coleção que não permite duplicatas e você deseja manter a ordem de inserção dos elementos.

### HashMap
Utilizar quando precisar associar chaves a valores e a ordem das chaves não é importante. É uma boa escolha para buscar rapidamente por chaves.

### TreeMap
Utilizar quando precisar associar chaves a valores e as chaves devem estar em ordem natural ou definida por um comparador.

### LinkedHashMap
Utilizar quando precisar associar chaves a valores e desejar manter a ordem de inserção das chaves

### Dicas:
List: 

Set: Interface. Não permite duplicatas.
Map: Interface. Associa chaves a valores.
HashSet: Classe.
HashMap: Classe.

'Tree': Elementos em ordem natural ou definida por um comparador.
'Hash': Ordem dos elementos não é importante.
'LinkedHash': Mantem a ordem de inserção das chaves.


## Clean Architecture

Clean Architecture, ou arquitetura limpa, é um conceito de design semelhante a arquitetura hexagonal (possui algumas diferenças). <br>
O design dessa arquitetura é composto por várias camadas concêntricas, cada uma representando um nível de abstração e isolando diferentes tipos de responsabilidades. <br>
Os níveis de abstrações dessa arquitetura visa a separação clara entre regras de negócio e detalhes de implementação técnica. É uma abordagem que busca manter o núcleo das regras de negócio independente de frameworks, banco de dados e outros detalhes externos, promovendo modularidade, testabilidade e evolução sustentável do software ao longo do tempo.<br>
As camadas internas, como Entidades e Casos de Uso, concentram-se na lógica de negócios, enquanto as camadas externas, como Adaptadores de Interface e Frameworks, tratam dos aspectos técnicos e de interação com o ambiente.


## Rest x Soap

## Para que serve o Serializable?

## STRATEGY: Sequence vs Identity

## O que são triggers e procedures?

## NoSQL

Colunas / Chave-valor / Grafos / Documentos <br>
[Lista de banco de dados NoSQL](https://hostingdata.co.uk/nosql-database/)

## VO x DTO x DAO x BO x Bean

<strong> DTO - Data Transfer Object </strong> <br>
Exemplo de DTO: <br>
User - id, login, senha (model) </strong> <br>
UserDTO - id, login <br>
Postman HTTP GET -> retorna objeto sem a senha do usuário.

<strong> DAO - Data Access Object </strong> <br>
Dados relacionados aos SQL, DAO é mais próximo do banco de dados.<br>
Geralmente para cada classe de modelo, criar uma classe 'modeloDAO'.

<strong> BO - Business Object </strong> <br>
Pode ter tanto a camada de entidade quanto a de persistência na mesma classe, e sim, fere o SOLID.

<strong> Bean - </strong> <br>
Primeira camada que se comunica com a interface da aplicação.

<strong> VO - </strong> <br>
É um DTO só com atributos fixos. Strings ou Enums.
Não sei se pode forçar e jogar um 'int id';

## Design Patterns

## XPages


## Banco de imagens
[Giphy](https://giphy.com/) <br>
[Pexels](https://www.pexels.com/pt-br/) <br>
[Flaticon](https://www.flaticon.com/br/) <br>
[Freepik](https://br.freepik.com/) <br>
[Noun Project](https://thenounproject.com/) <br>
[Brasil com S](https://www.brasilcoms.com.br/) <br>

## Paleta de cores
[Adobe Color](https://color.adobe.com/pt/)
