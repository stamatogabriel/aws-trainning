# Introduction to AWS Cloud Practitioner Essentials

## Objectives

- Summarize the benefits of AWS
- Describe differeces between on-demand delivery and cloud deployments
- Sumarize the pay-asyou-go pricing model

## AWS service offerings

- Compute
- Storage
- Network Security
- Blockchain
- Machi learning
- AI
- Robot development
- Video production
- Orbital satelites

## Fundamentals

No início da computação moderna, os servidores seguiram o `client-center model`.

Podemos comparar os serviços da AWS à uma cafeteria.

Quando o cliente chega, ele faz um pedido à barista (a request).

No mundo computacional acontece a mesma coisa, não importa o serviço, ele sempre iniciará com uma requisição.

A barista do nosso exemplo pode ser o servidor (server), e na AWS, ela pode representar o Amazon Elastic Compute Cloud (EC2), uma instância, um servidor virtual.

No mundo real, isso é um pouco mais complexo. Uma empresa/produto mais maduro terá mais de um servidor.

### key concept AWS
- Only pay for what you use: Seguindo o exemplo da cafeteria, se a barista não trabalhar, ela não será paga. Mas se a cafeteria precisar de mais baristas, pagará pelas horas que eles trabalharem.
- Pay for what you need


## What is cloud computing
`Cloud Computing`: The on-demand delivvery of IT resources over the internet with pay-as-you-go pricing. 
A entrega sob demanda de recursos de TI pela Internet com preços pré-pagos.

`On-demand delivery:` Você tem os recursos que você precisa, quando precisa
`IT resources:` É hoje uma grande parte da filosofia da AWS. Qual banco de dados usar, ou como vc armazena seus arquivos não faz da empresa iferencial para o concorrente, mas sim, os dados nessas tabelas e o fácil acesso a eles. 
`Over the internet:` Não importa onde vc esteja, vc terá acesso aos serviços
`Pay-as-you-go pricing:` e pagará somente o que usar

## Deployment models for cloud computing

Quando escolhemos nossa cloud strategy, a empresa deve considerar diversos fatores como os requisitos da aplicação, preferencias de gerenciamento, e qualquer estrutura legada.

Existem três tipos de modelos de deploy

### Cloud-based: 
- Execute todas as partes do aplicativo na nuvem.
- Migre os aplicativos existentes para a nuvem.
- Projete e crie novos aplicativos na nuvem.

Em um modelo de implementação baseado em nuvem, você pode migrar os aplicativos existentes para a nuvem ou pode projetar e construir novos aplicativos na nuvem. Você pode construir esses aplicativos em uma infraestrutura de baixo nível que requer que sua equipe de TI os gerencie. Como alternativa, você pode criá-los usando serviços de nível superior que reduzem os requisitos de gerenciamento, arquitetura e dimensionamento da infraestrutura central.

Por exemplo, uma empresa pode criar um aplicativo que consiste em servidores virtuais, bancos de dados e componentes de rede totalmente baseados na nuvem.

### On-premises deployment
- Implemente recursos usando ferramentas de virtualização e gerenciamento de recursos.
- Aumente a utilização de recursos usando gerenciamento de aplicativos e tecnologias de virtualização.

A implementação local também é conhecida como impllementação de nuvem privada. Neste modelo, os recursos são implementados no local usando ferramentas de virtualização e gerenciamento de recursos.

Por exemplo, você pode ter aplicativos executados em tecnologia totalmente mantida em seu datacenter local. Embora esse modelo seja muito parecido com a infraestrutura de TI legada, sua incorporação de tecnologias de gerenciamento de aplicativos e virtualização ajuda a aumentar a utilização de recursos.

### Hybrid Deployment
- Conecte recursos baseados em nuvem à infraestrutura local.
- Integre recursos baseados em nuvem com aplicativos de TI legados.

Em uma implantação híbrida, os recursos baseados em nuvem são conectados à infraestrutura local. Você pode querer usar essa abordagem em várias situações. Por exemplo, você tem aplicativos legados que são melhor mantidos no local ou as regulamentações governamentais exigem que sua empresa mantenha determinados registros no local.

Por exemplo, suponha que uma empresa deseja usar serviços em nuvem que podem automatizar o processamento e análise de dados em lote. No entanto, a empresa possui vários aplicativos legados que são mais adequados no local e não serão migrados para a nuvem. Com uma implantação híbrida, a empresa seria capaz de manter os aplicativos legados no local, enquanto se beneficia dos serviços de dados e analíticos executados na nuvem.

## Benefits of cloud computing
- Menor custo
- Mais agilidade e economia para aumentar recursos quando necessário
- Agilidade na entrega de serviços

## Summary

### What is cloud computing?
The correct response option is On-demand delivery of IT resources and applications through the internet with pay-as-you-go pricing.

The other response options are incorrect because:

It is possible to back up files to the cloud, but this response option does not describe cloud computing as a whole.
Deploying applications connected to on-premises infrastructure is a sample use case for a hybrid cloud deployment. Remember that cloud computing also has cloud and on-premises (or private cloud) deployment models.
AWS Lambda is an AWS service that lets you run code without needing to manage or provision servers. This description does not describe cloud computing as a whole. AWS Lambda is explained in greater detail later in the course.

### What is another name for on-premises deployment?
The correct response option is Private cloud deployment.

The other response options are incorrect because:

Cloud-based applications are fully deployed in the cloud and do not have any parts that run on premises.
A hybrid deployment connects infrastructure and applications between cloud-based resources and existing resources that are not in the cloud, such as on-premises resources. However, a hybrid deployment is not equivalent to an on-premises deployment because it involves resources that are located in the cloud.
The AWS Cloud offers three cloud deployment models: cloud, hybrid, and on-premises. This response option is incorrect because the AWS Cloud is not equivalent to only an on-premises deployment.


### How does the scale of cloud computing help you to save costs?
The correct response option is The aggregated cloud usage from a large number of customers results in lower pay-as-you-go prices.

This answer describes how customers can benefit from massive economies of scale in cloud computing.

The other response options are incorrect because:
Not having to invest in technology resources before using them relates to Trade upfront expense for variable expense.
Accessing services on-demand to prevent excess or limited capacity relates to Stop guessing capacity.
Quickly deploying applications to customers and providing them with low latency relates to Go global in minutes.