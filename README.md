# Apenas Um Readme

### Bem-vindo, ao meu Readme de estudos!

Esse é um Readme que decidi fazer para estudos, para conseguir massificar as informações que tenho estudado ultimamente e lapidar alguns conceitos que já conhecia.<br>
Meu objetivo é ter tudo na ponta da lingua e saber explicar sem travar em nenhum momento, sobre todos os tópicos abordados.<br>
Com o tempo eu vou adicionando mais tópicos conforme vou estudando sobre mais assuntos que ao meu ver parecem interessantes.<br>
Tudo escrito na unha. :grinning:

### Tópicos 

- [Apache Kafka](#apache-kafka-v03)
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
  
## Apache Kafka v0.3

<h5> O que é o Kafka? </h5>
Plataforma de código aberto de streaming de eventos que trabalha de forma distribuída. Com ele é possível de publicar, armazenar, processar e consumir um grande fluxo de dados.
O Apache Kafka é mais que um sistema de filas ou um sistema de mensageria.
É trabalhado no formato de filas.

<h5>Por que precisamos do Apache Kafka? </h5>
Trabalhar com stream de dados. Hoje em dia quase todos os sistemas são orientados a eventos.
Quando se tem um dado/informação e o objetivo é passar a informação de um sistema para o outro, armazenar para consultas futuras, pegar a informação e transformar para jogar em outros sistemas, etc.
O Apache Kafka é mais que um sistema de filas. 

<h5>Qual trabalho que o Apache Kafka tem? </h5>
Pega todos os eventos que acontecem e salvam os dados. Além de manipular todas essas informações ele guarda as informações para utilizá-las futuramente, tanto para trabalhar com estatísticas, fazer médias, agrupar informações, etc.

<h5>Vantagens do Apache Kafka: </h5>
Ele aguenta processar uma quantidade exagerada de informações e ainda assim trabalhar com uma latência baixíssima (abaixo de 2ms). 
É escalável.
Tem como opção de guardar permanentemente as informações ou de acordo com o período configurado.
Ele oferece grande disponibilidade.
Grande tolerância a falhas.

<h5>Algumas empresas que utilizam o Kafka: </h5>
- Netflix    - Twitter   - Paypal  <br>
- LinkedIn   - Dropbox   - Spotify <br>
- Uber       - E vários bancos <br>


<br><br>
// v0.2 <br>
Events first: Abordagem que da ênfase aos eventos. Evento é uma mudança significativa em um estado, por exemplo, usuário fazendo alteração do endereço cadastrado. <br>
os eventos são armazenados de forma similar ao log, trazendo, além das informações do estado, a associação ao tempo de que o evento ocorreu. Formado por chave, valor e timestamp. <br>

Event streaming: Forma de capturar, analisar e responder aos eventos em tempo real. Garante um fluxo contínuo e interpretação dos dados, para que as informações certas estejam no lugar certo e na hora certa. <br>

Tem 3 objetivos chaves: publicar e observar streams de eventos(similar a fila de mensagens), armazenar streams de eventos de maneira durável e tolerante a falhas e processar eventos de streams enquanto ocorre ou retrospectivamente. <br>
Faz tudo isso de maneira distribuida, escalável, elástica, tolerante a falhas e segura.
Usado para aplicações que necessitam de pipeline de dados de streaming em tempo real que obtêm dados entre sistemas ou aplicativos de maneira confiável. Ou, aplicações de streaming em tempo real que transformam ou reagem ao fluxo de dados. <br>
Oferece o poder de criar aplicações para streaming de informações em tempo real, entre diversos sistemas, em diversas plataformas e em diversos formatos. Podendo processar informações em tempo real, seja para operações aritméticas, agrupamento, etc. <br>

Arquitetura clusterizada que permite que funciona em um ou mais servidores(brokers, é o nome que o kafka chama os servidores).<br>
Os brokers(servidores) do apache kafka podem utilizar entre eles os conceitos principais de sistemas distribuídos: mecanismo de tolerância a falhas, disponibilidade, confiabilidade e segurança.<br>
A arquitetura do kafka é composta por um sistema fonte que fornece os dados de entrada, produtor gera os dados, processos core gestao de todo o processo e o consumidor que se inscreve(le e processa os dados gerados para disponibilizá-los para um outro sistema).

As aplicações ou produtores enviam mensagens para o nó do kafka e elas são armazenadas em um tópico e os consumidores se inscrevem nos tópicos para receber as novas mensagens. As trocas de mensagens são feitas via protocolo TCP simples. <br>

Produtor é responsável por produzir e enviar dados para o kafka. Exemplo de dados: Json, email, tweet, sms, etc. E também deve informar para qual tópico e broker que enviar as informações. o Kafka se encarrega de distrbuí-las e armazená-las.

*Tópicos: são onde os eventos são organizados e armazenados, conjuntos de dados imutáveis, todos têm um nome atribuído exemplo: 'codigofonte.topico'. Cada tópico é <strong>Multi-producer</strong> e <strong>Multi-subscriber</strong>, ou seja,
pode ter 0, 1, ou vários produtores escrevendo eventos nele e pode ter 0, 1 ou vários consumidores inscritos nesse tópico. Os eventos de um tópico podem ser lidos quantas vezes for preciso, são apagados caso seja configurado para apagar e no tempo especificado.
O desempenho do kafka é constante em relaç~~ao a quantidade e ao tamanho dos dados.
Os tópicos são divididos em partições com tamanho menor para desempenho e escabilidade. Por definição, uma partição é uma sequencia ordenada e imutável de registros anexada continuamente a um log. cada partição recebe um conjunto de informações dentro daquele tópico.
O kafka garante que todas as mensagens dentro da partição são ordenadas na sequência que elas chegaram.
todo registro que é armazenado dentro da partição pertence unica e exclusivamente a ela. Um dado armazenado no offset 3 da partição 1 não tem relação ao offset 3 da partição 0.
Os dados são entregues ao tópico e não a uma partição. O kafka que gerencia em qual partição será gravada. No entanto podemos passar uma chave na mensagem e com a chave garantir que a informação será armazenada sempre na mesma partição (quem decide a partição é o kafka também).

Consumidores leem os dados armazenados em um tópico e se conectam ao broker para ler as informações. Não se deve ter mais consumidores que partições. Pode existir vários consumidores para um tópico, tanto grupo quanto individualmente ( o kafka balanceia a leitura de dados). 
Um grupo de consumidor permite a leitura de dados de forma rápida e dinâmica, se houver um tópico com 3 partições e 3 consumidores é possível ler as 3 partições simultaneamente e paralelamente.
O kafka armazena qual offset o consumidor está lendo, caso o processo caia ele vai saber onde parou e volta o consumo de onde parou.

O kafka fornece, além da utilização de linhas de comando para gerenciamento e configuração, algumas apis:

producer api, permite que uma aplicação publique um fluxo de informações em um ou mais tópicos do kafka.
consumer api, permite que uma aplicação se inscreva ou assine um ou mais tópicos e processe o fluxo de dados produzidos para ele.
streams api, permite que uma aplicação atue como processador de fluxo consumindo os dados e gerando resultados processados em outro tópico.
conector api, permite criar e executar produtores ou consumidores reutilizáveis que conectam os tópicos do kafka em sistemas existentes. Exemplo: um conector para um banco de dados relacional captura todas as alterações em uma tabela. 
admin api, gerencia e inspeciona tópicos, brokers e outros objetos do kafka.

<strong>Curiosidade:</strong> atua na camada de implementação da arquitetura orientada a eventos. É adotado principalmente na arquitetura: Event-driven Architectures (EDA).
EDA: Resumidamente, é um modelo de arquitetura de software onde os componentes de captura, comunicação, processamento e armazenamento de eventos formam a estrutura básica da solução.

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
Estou estudando 3 tipos de padrões de projeto: Criacionais, Estruturais e Comportamentais. <br>
Primeiramente vou começar com um breve resumo sobre cada um. <br>
Padrões de projetos Criacionais basicamente existem diversos mecanismos para criar um objeto. Ao invés de utilizar diretamente o operador "new", podemos utilizar algum padrão que nos forneça mais flexibilidade no código. <br>
Padrões de projetos Estruturais mostra como objetos podem se unir em estruturas maiores, porém de forma organizada, facilitando possíveis extensões. <br>
Padrões de projetos Comportamentais organiza a forma de comunicação entre os objetos.
