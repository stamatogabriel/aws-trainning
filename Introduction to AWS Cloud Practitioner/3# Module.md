# MODULE 3: GLOBAL INFRASTRUCTURE AND RELIABILITY

## Learning objectives

In this module, you will learn how to:

- Summarize the benefits of the AWS Global Infrastructure.
- Describe the basic concept of Availability Zones.
- Describe the benefits of Amazon CloudFront and edge locations.
- Compare different methods for provisioning AWS services.

## Alta disponibilidade
Digamos que você queira tomar uma xícara de café na cafeteria, mas hoje não é apenas um dia normal em nossa cidade. Hoje, há um desfile vindo para marchar por nossa rua em celebração a todas as migrações de nuvem maravilhosas que tiveram sucesso. Este desfile vai marchar bem na frente da nossa loja. Isso é ótimo porque quem não gosta de olhar para carros alegóricos e balões e ter alguém jogando doces neles da rua? Mas isso também é ruim porque enquanto o desfile está descendo a rua, nossos clientes que estão dirigindo para vir buscar um café serão desviados e não poderão parar na loja. Isso reduzirá as vendas e também deixará os clientes insatisfeitos.

Felizmente para nós, pensamos no futuro. Há muito tempo, pensamos no que aconteceria se, por algum motivo, nossos clientes não pudessem entrar na loja temporariamente. Como se houvesse um desfile ou se houvesse uma enchente ou algum outro evento que nos impede de entrar na loja? Bem, não importa o motivo, precisamos estar altamente disponíveis para nossos clientes.

Então, vou te contar um segredo. Este não é o único local da nossa cafeteria. O café é na verdade uma rede e temos locais por toda a cidade. Assim, se houver um desfile na rua ou se houver queda de energia no nosso quarteirão, não se preocupe. Os clientes ainda podem tomar seu café visitando uma de nossas lojas a apenas alguns quarteirões de distância. Ainda ganhamos dinheiro e eles recebem seu café. Tudo está bem.

A AWS fez algo semelhante com a forma como a infraestrutura global da AWS é configurada. Não é bom o suficiente ter um data center gigante onde estão todos os recursos. Se algo acontecesse com esse data center, como uma queda de energia ou um desastre natural, os aplicativos de todos cairiam de uma vez. Você precisa de alta disponibilidade e tolerância a falhas.

Acontece que não é nem bom o suficiente para ter dois data centers gigantes. Em vez disso, a AWS opera em todos os tipos de áreas diferentes ao redor do mundo, chamadas de regiões. Vamos falar sobre isso em detalhes nos próximos vídeos. Enquanto isso, vou sentar aqui e relaxar, porque sei que meu negócio está altamente disponível, independentemente de qualquer desfile bloqueando a rua.

## AWS Globa Infrastruture

Para entender a infraestrutura global da AWS, quero começar com sua necessidade comercial fundamental. Você tem um aplicativo que precisa ser executado, ou o conteúdo que precisa ser armazenado, ou os dados que precisa ser analisados. Basicamente, você tem coisas que precisam viver e operar em algum lugar. Agora, historicamente, as empresas tinham que executar aplicativos em seus próprios data centers, porque não tinham escolha. Depois que a AWS se tornou disponível, empresas como a sua agora podiam executar seus aplicativos em outros data centers que não eram realmente seus.

Mas a conversa é muito mais do que isso, porque eu quero que você entenda um problema fundamental com qualquer data center, não importa quem o construiu ou quem o possui. Podem ocorrer eventos que podem fazer com que você perca a conexão com esse prédio. Se você administra seu próprio data center, precisa descobrir como responder à pergunta sobre o que você fará quando um desastre atingir seu prédio. Você poderia operar um segundo data center, mas os preços dos imóveis por si só poderiam impedi-lo, muito menos todas as despesas duplicadas de hardware, funcionários, eletricidade, aquecimento e refrigeração, segurança. A maioria das empresas simplesmente acaba armazenando backups em algum lugar e, então, espera que o desastre nunca aconteça. E a esperança não é um bom plano de negócios.


A AWS responde à pergunta sobre o que acontece quando ocorre um desastre, construindo nossos data centers em grandes grupos que chamamos de Regiões, e é assim que ele é projetado.

Em todo o mundo, a AWS cria regiões para ficar mais perto de onde o tráfego de negócios exige. Locais como Paris, Tóquio, São Paulo, Dublin, Ohio. Dentro de cada região, temos vários data centers que possuem todos os serviços de computação, armazenamento e outros de que você precisa para executar seus aplicativos. Cada região pode ser conectada a outra região por meio de uma rede de fibra de alta velocidade, controlada pela AWS, uma operação verdadeiramente global de ponta a ponta, se você precisar. Agora, antes de entrarmos na arquitetura de como cada região é construída, é importante saber que você, o tomador de decisões de negócios, pode escolher de qual região deseja ficar sem. E cada região é isolada de todas as outras regiões no sentido de que absolutamente nenhum dado entra ou sai de seu ambiente naquela região sem que você conceda explicitamente permissão para que esses dados sejam movidos. Esta é uma conversa crítica de segurança.

Por exemplo, você pode ter requisitos de conformidade do governo para que suas informações financeiras em Frankfurt não possam sair da Alemanha. Bem, esta é absolutamente a maneira como a AWS opera fora da caixa. Quaisquer dados armazenados na região de Frankfurt nunca saem da região de Frankfurt, ou dados na região de Londres nunca saem de Londres, ou Sydney nunca sai de Sydney, a menos que você explicitamente, com as credenciais e permissões corretas, solicite que os dados sejam exportados.

A soberania dos dados regionais é parte do design crítico das regiões da AWS. Com os dados sujeitos às leis e estatutos locais do país onde a Região vive. Portanto, com esse entendimento de que seus dados, seu aplicativo, residem e são executados em uma região, uma das primeiras decisões que você toma é qual região você escolhe? Existem quatro fatores de negócios envolvidos na escolha de uma região.

Número um, conformidade. Antes de qualquer outro fator, você deve primeiro examinar seus requisitos de conformidade. Você tem um requisito de que seus dados estejam dentro dos limites do Reino Unido? Então você deve escolher a região de Londres, ponto final. Nenhuma das outras opções importa. Ou digamos que você deva correr dentro das fronteiras chinesas. Pois bem, você deve escolher uma das nossas regiões chinesas. A maioria das empresas, porém, não é regida por essas regulamentações estritas. Portanto, se você não tiver um controle de conformidade ou regulatório que dite sua região, pode examinar os outros fatores.

Número dois, proximidade. O quão perto você está de sua base de clientes é um fator importante porque a velocidade da luz, ainda a lei do universo. Se a maioria de seus clientes morar em Cingapura, considere sair da região de Cingapura. Agora você certamente pode ficar sem Virgínia, mas o tempo que leva para a informação ser enviada, ou latência, entre os EUA e Cingapura sempre será um fator. Agora podemos estar desenvolvendo computação quântica, mas redes quânticas, ainda a alguns passos de distância. O tempo que a luz leva para viajar pelo mundo é sempre uma consideração. Localizando perto de sua base de clientes, geralmente a chamada certa.

Número três, disponibilidade de recursos. Às vezes, a região mais próxima pode não ter todos os recursos da AWS que você deseja. Agora, aqui está uma das coisas legais sobre a AWS. Estamos constantemente inovando em nome de nossos clientes. Todos os anos, a AWS lança milhares de novos recursos e produtos especificamente para atender às solicitações e necessidades dos clientes. Mas às vezes esses novos serviços exigem muito hardware físico novo que a AWS precisa construir para tornar o serviço operacional. E às vezes isso significa que temos que desenvolver o serviço em uma região de cada vez. Então, digamos que seus desenvolvedores queiram brincar com o Amazon Braket, nossa nova plataforma de computação quântica. Pois bem, eles têm que ser executados nas Regiões que já possuem o hardware instalado. Eventualmente, podemos esperar que seja em todas as regiões? Bem, sim, é uma boa expectativa, mas se você quiser usá-lo hoje, então esse pode ser o seu fator decisivo.

Número quatro, preço. Mesmo quando o hardware é igual de uma região para outra, alguns locais são mais caros para operar, por exemplo, no Brasil. Agora, a estrutura tributária do Brasil é tal que custa à AWS significativamente mais operar os mesmos serviços lá do que em muitos outros países. Exatamente a mesma carga de trabalho em São Paulo pode ser, digamos, 50% mais cara do que sair de Oregon, nos Estados Unidos. O preço pode ser determinado por muitos fatores, portanto, a AWS tem preços granulares muito transparentes que continuaremos a discutir nesta aula. Mas saiba que cada região tem uma tabela de preços diferente. Portanto, se o orçamento é sua principal preocupação, mesmo que seus clientes vivam no Brasil, você ainda pode querer operar em um país diferente, novamente, se o preço for sua principal motivação.

Portanto, quatro fatores principais para escolher uma região: 
- conformidade
- proximidade
- disponibilidade de recursos 
- preço

Se uma região é onde todas as partes e partes de seu aplicativo vivem, alguns de vocês podem estar pensando que nunca resolvemos o problema que apresentamos no último vídeo. Deixe-me reafirmar o problema. Você não quer executar seu aplicativo em um único prédio porque um único prédio pode falhar por uma série de razões inevitáveis.

Você pode estar pensando, se meu negócio precisa ser à prova de desastres, então ele não pode funcionar em apenas um local. Bem, você está absolutamente correto. A AWS concorda com essa declaração e é por isso que nossas regiões não são um local. Para começar, a AWS tem data centers, muitos data centers, em todo o mundo, e cada região é composta de vários data centers.

A AWS chama um único data center ou um grupo de data centers, uma zona de disponibilidade ou AZ. Cada zona de disponibilidade é um ou mais datacenters discretos com energia, rede e conectividade redundantes. Quando você inicia uma instância do Amazon EC2, ele inicia uma máquina virtual em um hardware físico instalado em uma zona de disponibilidade. Isso significa que cada região da AWS consiste em várias zonas de disponibilidade isoladas e fisicamente separadas dentro de uma região geográfica.

Mas não construímos Zonas de disponibilidade lado a lado, porque se um incidente de grande escala ocorresse, como um desastre natural, por exemplo, você poderia perder a conectividade com tudo nessa zona de disponibilidade. A questão do que acontece no caso de um desastre é importante e, se você estiver familiarizado com o planejamento de recuperação de desastre, pode até ter uma ideia de onde estamos indo com isso.


Se você executar apenas uma instância do EC2, ela será executada em apenas um edifício ou uma Zona de disponibilidade e ocorrer um desastre em grande escala, seu aplicativo ainda será capaz de executar e servir ao seu negócio? A solução óbvia para isso é executar várias instâncias do EC2, como mostramos no exemplo de dimensionamento anterior. Mas o principal é não colocá-los no mesmo prédio. Nem mesmo coloque-os na mesma rua, afaste-os o máximo que puder antes que a velocidade da luz diga para você parar, se ainda quiser comunicação de baixa latência. Acontece que a velocidade da luz nos permitirá mover essas Zonas de Disponibilidade a dezenas de milhas uma da outra e ainda manter uma latência de um milissegundo de um dígito entre essas Zonas de Disponibilidade. Agora, se ocorrer um desastre, seu aplicativo continuará bem, porque esse desastre apenas afetou parte de sua capacidade, não tudo.

E, como vimos na última seção, você pode aumentar rapidamente mais capacidade nas zonas de disponibilidade restantes, permitindo que seu negócio continue operando sem interrupção. E como prática recomendada com AWS, sempre recomendamos que você execute pelo menos duas zonas de disponibilidade em uma região. Isso significa implantar redundantemente sua infraestrutura em duas AZs diferentes.

Mas há mais regiões do que apenas locais para executar o EC2. Muitos dos serviços da AWS são executados no nível da região, o que significa que são executados de forma síncrona em várias AZs sem nenhum esforço adicional de sua parte. Veja o ELB de que falamos anteriormente. Esta é na verdade uma construção regional. Ele é executado em todas as zonas de disponibilidade, comunicando-se com as instâncias do EC2 que estão sendo executadas em uma zona de disponibilidade específica. Os serviços regionais, por definição, já estão altamente disponíveis, sem nenhum custo adicional de esforço de sua parte.

Portanto, ao planejar para alta disponibilidade, qualquer serviço listado como um serviço com escopo regional, você já terá essa caixa marcada.

### Which statement best describes an Availability Zone?
The correct response option is A single data center or group of data centers within a Region.

The other response options are incorrect because:

- A Region is a geographical area that contains AWS resources.
- An edge location is a data center that an AWS service uses to perform service-specific operations. Edge locations are examined in the next section of this module.
- AWS Outposts is a service that you can use to run AWS infrastructure, services, and tools in your own on-premises data center in a hybrid approach. AWS Outposts is explored later in this module.

## Edge Locations
Uma das melhores coisas sobre a infraestrutura global da AWS é a maneira como ela foi projetada para ajudá-lo a atender melhor seus clientes. Lembre-se de que, ao selecionar uma região, um dos principais critérios era a proximidade com seus clientes, mas e se você tiver clientes em todo o mundo ou em cidades que não sejam próximas a uma de nossas regiões? Bem, pense em nossa cafeteria. Se você tem uma boa base de clientes em uma nova cidade, pode construir uma loja satélite para atender esses clientes.

Você não precisa construir uma sede inteiramente nova ou de uma perspectiva de TI, se tiver clientes em Mumbai que precisam acessar seus dados, mas os dados são hospedados fora da região de Tóquio, em vez de ter todos os clientes baseados em Mumbai , envie solicitações até Tóquio, para acessar os dados, basta colocar uma cópia localmente ou armazenar em cache uma cópia em Mumbai. O armazenamento em cache de cópias de dados mais perto dos clientes em todo o mundo usa o conceito de redes de distribuição de conteúdo, ou CDNs.

Os CDNs são comumente usados ​​e, na AWS, chamamos nosso CDN de Amazon CloudFront. Amazon CloudFront é um serviço que ajuda a fornecer dados, vídeos, aplicativos e APIs para clientes em todo o mundo com baixa latência e altas velocidades de transferência. O Amazon CloudFront usa os chamados locais de Borda, em todo o mundo, para ajudar a acelerar a comunicação com os usuários, não importa onde eles estejam.

Os locais de borda são separados das regiões, então você pode enviar conteúdo de dentro de uma região para uma coleção de locais de borda em todo o mundo, a fim de acelerar a comunicação e entrega de conteúdo. Os locais do AWS Edge também executam mais do que apenas o CloudFront. Eles executam um serviço de nome de domínio, ou DNS, conhecido como Amazon Route 53, ajudando a direcionar os clientes aos locais corretos da web com baixa latência confiável.

Mas e se sua empresa quiser usar os serviços da AWS dentro de seu próprio prédio? Claro. A AWS pode fazer isso por você. Apresentando AWS Outposts, onde a AWS basicamente instalará uma minirregião totalmente operacional, dentro do seu próprio data center. Isso pertence e é operado pela AWS, usando 100% da funcionalidade da AWS, mas isolado em seu próprio prédio. Não é uma solução que a maioria dos clientes precisa, mas se você tiver problemas específicos que só podem ser resolvidos ficando em seu próprio prédio, entendemos, AWS Outposts pode ajudar.

Tudo bem, há muito mais que podemos dizer sobre a infraestrutura global da AWS, mas vamos mantê-lo simples e parar por aqui. 

Então, aqui estão os pontos principais. 

- Em primeiro lugar, as regiões são áreas geograficamente isoladas, onde você pode acessar os serviços necessários para administrar sua empresa. 
- Número dois, as regiões contêm Zonas de disponibilidade, que permitem que você percorra edifícios separados fisicamente, dezenas de quilômetros de separação, enquanto mantém seu aplicativo logicamente unificado. As zonas de disponibilidade ajudam a resolver cenários de alta disponibilidade e recuperação de desastres, sem nenhum esforço adicional de sua parte, e 
- número três, os locais do AWS Edge executam o Amazon CloudFront para ajudar a obter o conteúdo mais perto de seus clientes, não importa onde eles estejam no mundo.

## How to procision AWS resources

Falamos sobre alguns recursos diferentes da AWS, bem como sobre a infraestrutura global da AWS. Você pode estar se perguntando, como realmente interajo com esses serviços? E a resposta são APIs. Na AWS, tudo é uma chamada de API. Uma API é uma interface de programação de aplicativo. E o que isso significa é que existem maneiras predeterminadas para você interagir com os serviços da AWS. E você pode invocar ou chamar essas APIs para provisionar, configurar e gerenciar seus recursos da AWS.

Por exemplo, você pode iniciar uma instância EC2 ou pode criar uma função AWS Lambda. Cada uma dessas seriam diferentes solicitações e diferentes chamadas de API para a AWS. Você pode usar o AWS Management Console, a AWS Command Line Interface, os AWS Software Development Kits ou várias outras ferramentas, como AWS CloudFormation, para criar solicitações de envio para APIs da AWS para criar e gerenciar recursos da AWS.

Primeiro, vamos falar sobre o AWS Management Console. O AWS Management Console é baseado em navegador. Por meio do console, você pode gerenciar seus recursos da AWS visualmente e de uma maneira fácil de digerir. Isso é ótimo para começar e construir seu conhecimento dos serviços. Também é útil para criar ambientes de teste ou visualizar contas da AWS, visualizar monitoramento e trabalhar com outros recursos não técnicos. O AWS Management Console é provavelmente o primeiro lugar que você irá quando estiver aprendendo sobre a AWS.

No entanto, uma vez que você está instalado e funcionando em um ambiente de tipo de produção, você não quer depender do estilo apontar e clicar que o console oferece para criar e gerenciar seus recursos AWS. Por exemplo, para criar uma instância do Amazon EC2, você precisa clicar em várias telas, definir todas as configurações desejadas e, em seguida, iniciar sua instância. Se mais tarde você quisesse iniciar outra instância do EC2, você precisaria voltar ao console e clicar nessas telas novamente para colocá-la em funcionamento. Ao ter humanos fazendo esse tipo de provisionamento manual, você está se abrindo para erros em potencial. É muito fácil esquecer de marcar uma caixa de seleção ou digitar algo errado quando você está fazendo tudo manualmente.

A resposta para esse problema é usar ferramentas que permitem criar scripts ou programar chamadas de API. Uma ferramenta que você pode usar é a AWS Command Line Interface ou CLI. A CLI permite que você faça chamadas de API usando o terminal de sua máquina. Isso é diferente do estilo de navegação visual do console de gerenciamento. Escrever comandos usando a CLI torna as ações programáveis ​​e repetíveis. Portanto, você pode escrever e executar seus comandos para iniciar uma instância EC2. E se você quiser iniciar outro, basta executar o comando pré-escrito novamente. Isso o torna menos suscetível a erros humanos. E você pode fazer com que esses scripts sejam executados automaticamente, como em uma programação ou acionados por outro processo.

A automação é muito importante para ter uma implantação de nuvem previsível e bem-sucedida ao longo do tempo. Outra forma de interagir com a AWS é por meio dos kits de desenvolvimento de software ou SDKs da AWS. Os SDKs permitem que você interaja com os recursos da AWS por meio de várias linguagens de programação. Isso torna mais fácil para os desenvolvedores criarem programas que usem AWS sem usar as APIs de baixo nível, além de evitar a criação manual de recursos de que acabamos de falar.

Tudo bem, vamos continuar falando sobre como interagir com a AWS. Você tem o AWS Management Console, o CLI e os SDKs, que são formas de você mesmo provisionar e gerenciar seu ambiente AWS. Se quiser provisionar um recurso, você pode fazer login no console e apontar e clicar, pode escrever alguns comandos ou pode escrever alguns programas para fazer isso. Existem também outras maneiras de gerenciar seu ambiente AWS usando ferramentas gerenciadas como AWS Elastic Beanstalk e AWS CloudFormation.

O AWS Elastic Beanstalk é um serviço que ajuda a provisionar ambientes baseados no Amazon EC2. Em vez de clicar no console ou escrever vários comandos para construir sua rede, instâncias EC2, dimensionamento e balanceadores de carga elástica. Em vez disso, você pode fornecer o código do seu aplicativo e as configurações desejadas ao serviço AWS Elastic Beanstalk, que então pega essas informações e constrói seu ambiente para você. O AWS Elastic Beanstalk também facilita salvar as configurações do ambiente, para que possam ser implantadas novamente com facilidade. O AWS Elastic Beanstalk oferece a conveniência de não ter que provisionar e gerenciar todas essas peças separadamente, ao mesmo tempo em que oferece a visibilidade e o controle dos recursos subjacentes. Você consegue se concentrar em seu aplicativo de negócios, não na infraestrutura.

Outro serviço que você pode usar para ajudar a criar implantações automatizadas e repetíveis é o AWS CloudFormation. AWS CloudFormation é uma infraestrutura como ferramenta de código que permite definir uma ampla variedade de recursos da AWS de forma declarativa usando documentos baseados em texto JSON ou YAML chamados modelos CloudFormation. Um formato declarativo como este permite que você defina o que deseja construir sem especificar os detalhes de como construir exatamente. O CloudFormation permite que você defina o que deseja e o mecanismo do CloudFormation se preocupará com os detalhes da chamada de APIs para ter tudo construído.

Também não se limita apenas às soluções baseadas em EC2. O CloudFormation oferece suporte a muitos recursos diferentes da AWS de armazenamento, bancos de dados, análises, aprendizado de máquina e muito mais. Depois de definir seus recursos em um modelo CloudFormation, o CloudFormation analisará o modelo e começará a provisionar todos os recursos definidos em paralelo. CloudFormation gerencia todas as chamadas para as APIs AWS de back-end para você. Você pode executar o mesmo modelo CloudFormation em várias contas ou regiões, e ele criará ambientes idênticos entre eles. Há menos espaço para erro humano, pois é um processo totalmente automatizado.

Para recapitular, o AWS Management Console é ótimo para aprender e fornecer um visual para o usuário. O AWS Management Console é uma ferramenta manual. Então, de cara, não é uma ótima opção para automação. Em vez disso, você pode usar a CLI para criar um script de suas interações com a AWS usando o terminal. Você pode usar os SDKs para escrever programas para interagir com a AWS para você ou pode usar ferramentas de gerenciamento como AWS Elastic Beanstalk ou AWS CloudFormation.

## Sumary
Coisas incríveis, quero dizer, cobrimos muito terreno aqui. E não quero dizer isso apenas porque falamos sobre a infraestrutura global da AWS.

Mas, falando sério, cobrimos como os clusters lógicos de data centers constituem as zonas de disponibilidade, as zonas de disponibilidade, por sua vez, constituem as regiões e estão espalhadas globalmente. Em seguida, você escolhe quais regiões e zonas de disponibilidade deseja operar e, como prática recomendada, deve sempre implantar a infraestrutura em pelo menos duas zonas de disponibilidade. E alguns serviços da AWS como Elastic Load Balancing, Amazon SQS e Amazon SNS já fazem isso para você.

Também falamos sobre os locais do Edge e como você pode implantar conteúdo lá para acelerar a entrega aos seus clientes. Nós até abordamos dispositivos de ponta como AWS Outposts, que permitem que você execute a infraestrutura da AWS diretamente em seu próprio data center.

Outra coisa que discutimos foi como provisionar recursos da AWS por meio de várias opções, como o AWS Management Console, o SDK, CLI, AWS Elastic Beanstalk e AWS CloudFormation, onde você aprendeu como configurar sua infraestrutura como código.
