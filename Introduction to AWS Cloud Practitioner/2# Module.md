# Compute in cloud

## Objectives
- Describe the benefits of Amazon EC2 at a basic level.
- Identify the different Amazon EC2 instance types.
- Differentiate between the various billing options for Amazon EC2.
- Summarize the benefits of Amazon EC2 Auto Scaling.
- Summarize the benefits of Elastic Load Balancing.
- Give an example of the uses for Elastic Load Balancing.
- Summarize the differences between Amazon Simple Notification Service (Amazon SNS) and Amazon Simple Queue Service (Amazon SQS).
- Summarize additional AWS compute options.

## EC2
No exemplo da cafeteria, o cliente fazia uma requisição, a barista recebia e executava a ação, e retornava algo (response). Isso é uma cafeteria, mas se encaixa em quaisquer negócios.

Quando trabalhamos com a AWS, utilizamos servidores virtuais, e esse serviço é chamado de EC2.

Com o EC2, não temos a necessidade de ervidores físicos, uma vez que podemos criar quantas instâncias forem necessárias, pelo tempo que for necessário e interromper ou terminar o serviços das mesmas, pagando apenas pelo tempo de utilização.

`Multitenancy`: Compartilhamento de hardware indesejado entre máquinas virtuais.

O hypervisor é o responsável por gerenciar o escalonamentos das máquinas virtuais da AWS, gerenciando o melhor uso do hardware, compartilhando-o entre as máquinas virtuais e mantendo os serviços das mesmas isolado e seguro.

Com o EC2, temos facilidade em configurar e gerenciar instâncias. Quando instanciamos um EC2, podemos escolher nosso sistema operacional e configurá-lo de acordo com a necessidade do serviço. Temos completo controle com o que acontece na instância.

Instâncias EC2 são dimensionáveis, podemos começar com uma instância pequena, e aumentar conforme a necessidade, e vice-versa. Isso é `Escalonamento vertical (Vertical scaling)`.

Podemos controlar a rede pertencente ao EC2, podendo torná-la de acesso público ou privado.

CaaS (Computer as a Service): é um modelo de computação em nuvem que permite aos usuários implantar e gerenciar aplicações por meio da abstração baseada em containers, seja em datacenters on-premise ou na nuvem.

## Amazon EC2 instance types

Se usarmos a analogia da cafeteria, veremos que podemos ter diversos tipos de atendentes: aquele que todo mundo gosta, o especializado em um tipo de café, aquele que é especialista na decoração da xícara, etc. Em qualquer negócio, temos diversas tarefas para resolver, e precisamos de diferentes necessidades ou skills. Portanto, assim como uma empresa possui funcionários com diferentes expertises, existem EC2 que atendem as mais diferentes necessidades.

`Each Amazon EC2 instace type is grouped under an instance family`

- General purpose: foca no melhor balanceamento dos recursos de memória, rede e processamento. Atende diversos serviços, como web servers ou repositórios
- Compute optimized: foca no processamento intensivo de tarefas. Ex: Servidor de games, Computação de auta performance (HPC) e modelagem científica
- Memory optimize: foca nas tarefas que precisam do uso de memória intensiva. 
- Acelerate computing: ideal para cálculos de números complexos, processamento de gráficos e Data pattern maching
- Storage optimize: ideal para armazenamento de arquivos que necessitam de alta performance

## Amazon EC2 pricing
- On-Demand: paga o que usa, podendo ser por hora ou por segundo, variando de região e sistema operacional.
- Savings Plan: oferece preços baixos no uso do EC2 em troca de um compromisso com uma quantidade consistente de uso medida em dólares por hora por um período de um ou três anos.
- Reserved instances: eles são adequados para cargas de trabalho em estado estacionário ou com uso previsível e oferecem até 75% de desconto em relação ao preço On-Demand.
- Spot instances: Eles permitem que você solicite capacidade de computação sobressalente do Amazon EC2 com até 90% de desconto sobre o preço sob demanda. O problema aqui é que a AWS pode recuperar a instância a qualquer momento que precisar, dando a você um aviso de dois minutos para terminar o trabalho e salvar o estado.
- Dedicated hosts: hosts dedicados exclusivamete para seu uso. Geralmente, são para atender a determinados requisitos de conformidade e ninguém mais compartilhará a locação desse host.

## Scaling EC2
Esse é um dos maiores benefícios da AWS: Escalabilidade e elasticidade.

Quando temos um servidor físico, temos o seguinte dilema: Ou trabalhamos com um servidor que atende a média de uso, deixando o serviço a desejar em momentos de pico, ou consideramos ter uma máquina que atenda esses momentos, gerando auto custo de manutenção de máquina que não está sendo utilizada.

Com EC2, podemos provisionar nossas máquinas de acordo com os picos de utilização, aumentando ou diminuido os recursos de acordo com a necessidade.

O primeiro problema que podemos resolver é o desastre: 

`Everything fails all the time, so plan for failure and nothing fails - Werner Vogels`

Se perdermos uma instância, podemos facilmente substituí-la por uma cópia exata, através do mesmo processo de programação que criou a primeira.

```Amazon EC2 Auto Scaling enables you to automatically add or remove Amazon EC2 instances in response to changing application demand. By automatically scaling your instances in and out as needed, you are able to maintain a greater sense of application availability.```

```Within Amazon EC2 Auto Scaling, you can use two approaches: dynamic scaling and predictive scaling.```

```Dynamic scaling responds to changing demand. ```
```Predictive scaling automatically schedules the right number of Amazon EC2 instances based on predicted demand.```

Quando temos muitas requisições, devemos escalar verticalmente, porque não adianta termos poder computacional, se não conseguimos atender todas as requisições. o Auto scaling do EC2 provisiona o número exato de instâncias que determinado serviço precisa para executar as requisições que recebe.

## Directing traffic with Elastic Load Balancing

Resolvendo o problema da escala, precisamos também resolver o problema do tráfego. Não adianta eu ter várias baristas se somente uma recebe os pedidos. Em uma cafeteria, para resolver esse problema, podemos colocar alguém na porta para direcionar os clientes para serem atendidos da melhor maneira. No nosso caso, o porteiro é o Load Balancer.

```Um Load Balancer é um aplicativo que recebe solicitações e as encaminha para as instâncias a serem processadas.```

Tráfego devidamento deistribuido
- Auta performance
- Custo eficiente (inteligente)
- Alta disponibilidade
- Escalonamento automatico

### Elastic Load Balancer
É escalável automaticamente, ou seja, com o aumento do tráfego ele escala automaticamente mais máquinas EC2, afim de não aumentar os custos de forma desordenada e mantendo a disponibilidade do serviço. Se o tŕafego diminui, ele retira as máquinas adicionadas do processo.

ELB pode ser usado para requisições entre servidores e não só para requests externas. O ELB possui um único URL, facilitando a programação do direcionamento das requisições.

## Messaging and queuing
voltando a cafeteria, as atendentes pegam os pedidos e os baristas praparam os pedidos. Imagine a situação em que a atendente anota os pedidos e leva ao barista, mas o barista está trabalhando em outro pedido, então a barista fica segurando o pedido aguardando o barista terminar o que está fazendo e pegar o papel. Em certo momento a atendente pode perder a ordem e ir atender outro cliente.

No nosso exemplo, a atendente pode melhorar isso utilizando um quadro para ir colocando os pedidos, criando assim um buffer ou uma fila (queue).

Assim como no exemplo, as aplicações se comunicam diretamente por mensagens.

### Amazon Simple Queue Service (SQS) and Amazon Simple Notification Service (SNS)
- SQS: envia, recebe e armazena mensagens entre software componentes de qualquer volume
  - Payload: conteudo de uma mensagem SQS
  - Resumo: onde mensagens ficam aguardando processamento
- SNS: envia mensagens de notificação aos usuários
  - SNS Topic: canal de mensagen a serem enviadas

### Monolithic applications and microservices
Applications are made of multiple components. The components communicate with each other to transmit data, fulfill requests, and keep the application running. 

Suppose that you have an application with tightly coupled components. These components might include databases, servers, the user interface, business logic, and so on. This type of architecture can be considered a monolithic application. 

In this approach to application architecture, if a single component fails, other components fail, and possibly the entire application fails.

To help maintain application availability when a single component fails, you can design your application through a microservices approach.

In a microservices approach, application components are loosely coupled. In this case, if a single component fails, the other components continue to work because they are communicating with each other. The loose coupling prevents the entire application from failing. 

When designing applications on AWS, you can take a microservices approach with services and components that fulfill different functions. Two services facilitate application integration: Amazon Simple Notification Service (Amazon SNS) and Amazon Simple Queue Service (Amazon SQS).

Amazon Simple Notification Service (Amazon SNS)

Amazon Simple Notification Service (Amazon SNS) is a publish/subscribe service. Using Amazon SNS topics, a publisher publishes messages to subscribers. This is similar to the coffee shop; the cashier provides coffee orders to the barista who makes the drinks.

In Amazon SNS, subscribers can be web servers, email addresses, AWS Lambda functions, or several other options. 

Amazon Simple Notification Service (Amazon SNS)

Amazon Simple Notification Service (Amazon SNS) is a publish/subscribe service. Using Amazon SNS topics, a publisher publishes messages to subscribers. This is similar to the coffee shop; the cashier provides coffee orders to the barista who makes the drinks.

In Amazon SNS, subscribers can be web servers, email addresses, AWS Lambda functions, or several other options. 

### Which AWS service is the best choice for publishing messages to subscribers?
The correct response option is Amazon Simple Notification Service (Amazon SNS).

Amazon SNS is a publish/subscribe service. Using Amazon SNS topics, a publisher publishes messages to subscribers.

The other response options are incorrect because:

Amazon Simple Queue Service (Amazon SQS) is a message queuing service. It does not use the message subscription and topic model that is involved with Amazon SNS.
Amazon EC2 Auto Scaling enables you to automatically add or remove Amazon EC2 instances in response to changing application demand.
Elastic Load Balancing is the AWS service that automatically distributes incoming application traffic across multiple resources, such as Amazon EC2 instances.

## Aditional compute services
Até agora vimos as facilidades e os benefícos do EC2. Porém, somoes responsáveis pelas atualizações de SO e software e configurações de escalabilidade. Existem serviços que demandam menos gerencias: os Serverless.

Serverless: você não pode ver ou acessar a infraestrutura subjacente

Todo o foco fica na aplicação

### AWS Lambda
Todo o código da aplicação fica em um Lambda function e um trigger é configurado. O trigger recebe a requisição e o código é executado automaticamente por um ambiente de gerenciamento automaticamente escalado. Labdas fora desenvolvidos para rodar processos de até 15 minutos. 

### Amazon Elastic Container Services (ECS) / Amazon Elastic Kubernetes Service (EKS)
Ambos são orquestradores de containers (Docker). Os containers rodam em instancias EC2, isolados um do outro (como em máquinas virtuais).

ECS foi criado para auxiliar no escalonamento de conteineres que contenham o seu software.

EKS foi criado para orquestrar containeres de serviços diferentes.

Both Amazon ECS and Amazon EKS can run on top of EC2. But if you don't want to even think about using EC2s to host your containers because you either don't need access to the underlying OS or you don't want to manage those EC2 instances, you can use a compute platform called AWS Fargate.

### AWS Fargate
Fargate é uma plataforma serverless para ECS e EKS.

`EC2`: hospedar aplicações tradicionais, acesso total ao SO
`Lambda`: rodar funções curtas, serviço orientado a aplicações, aplicativos orientados a eventos, sem aprovisionamento ou gerenciamento de serviços
`ECS ou EKS`: rodar containers com carga de trabalho na base da AWS
  - EC2 gerenciado por você
  - AWS Fargate gerenciado para você

