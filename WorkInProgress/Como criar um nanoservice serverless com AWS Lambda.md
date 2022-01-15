# Como criar um nanoservice serverless com AWS Lambda

![Luiz Duarte](https://www.gravatar.com/avatar/93a9abccc4d85eefdb90b62bd810342e?d=mm&s=128)

Escrito por [**Luiz Duarte**](https://www.luiztools.com.br/post/author/luiztools/)em 25/12/2020

##### JUNTE-SE A MAIS DE 22 MIL PROFISSIONAIS DE TI

### Entre para minha lista e receba conteúdos exclusivos e com prioridade

Enviar

***Este tutorial tem versão em videoaula no meu [curso Web FullStack JS](https://www.luiztools.com.br/curso-fullstack?utm_source=google&utm_medium=cpc&utm_campaign=12231680300&utm_content=121325240551&utm_term=node lambda&gclid=Cj0KCQiAubmPBhCyARIsAJWNpiO10LsnBKWew-pCpw9R_5KV7jI7Fkp4gphJURespHLOkT6kmzsR8XgaAst5EALw_wcB)!***

Caso você esteja bem por fora, tem alguns anos que a Amazon e outros players de cloud têm investido forte no conceito de Serverless. Serverless basicamente se trata de aplicações, ou melhor, funções, que rodam na nuvem sem a necessidade de um servidor para provisioná-los. Quando esta função é acionada, geralmente a partir de um gatilho, mas pode ser um [endpoint REST](https://www.luiztools.com.br/post/criando-uma-webapi-com-nodejs-e-mysql/) também, a infra é automaticamente provisionada, ela executa e depois é encerrada.

Simples assim.

Falando especificamente do [AWS Lambda](https://aws.amazon.com/pt/lambda/), que é o produto de serverless da Amazon, você é cobrado somente pelo tempo que sua função leva para executar multiplicado pela quantidade de recursos que essa execução consome (principalmente memória RAM).

Ou seja, esqueça ter de ficar pagando EC2 ou [LightSail](https://www.luiztools.com.br/post/como-enviar-emails-em-node-js-usando-o-aws-ses-amazon/) o mês inteiro para deixar seus [micro serviços](https://www.luiztools.com.br/post/o-que-e-um-micro-servico-ou-microservice/) disponíveis, com nano serviços você paga somente o uso e essa é uma das principais vantagens e atrativos desta forma de programar, enquanto que a outra é a escalabilidade, uma vez que você não está “preso” aos recursos de uma máquina ou mesmo um cluster de máquinas. Seus nano serviços são provisionados um para cada requisição ad infinitum.

Dentre as desvantagens podemos citar a complexidade de se gerenciar uma arquitetura baseada em gatilhos/eventos, que é o que resulta do uso intenso de nanoservices. Ter de usar filas para mensageria (como o [AWS SQS](https://www.luiztools.com.br/post/tutorial-de-node-js-com-filas-na-aws-sqs/) e o [RabbitMQ](https://www.luiztools.com.br/post/processamento-assincrono-de-tarefas-com-filas-no-rabbitmq-e-node-js/)) são comuns e outra desvantagem é que você tem de ficar de olho no consumo, pois ele é extremamente variável.

Também vale citar que operações de computação intensiva não são muito recomendadas para serverless, uma vez que existe uma limitação de consumo de memória em 3GB e também porque pendurar uma função Lambda por mais do que alguns segundos repetidamente vai te gerar uma conta bem grande no final do mês.

### Criando sua primeira Lambda

Mas chega de teoria, que tal ver na prática como criar uma Lambda muito simples?

Vou considerar aqui que você já sabe [programar em Node.js a nível básico](https://www.luiztools.com.br/curso-nodejs?utm_source=google&utm_medium=cpc&utm_campaign=12231680300&utm_content=121325240551&utm_term=node lambda&gclid=Cj0KCQiAubmPBhCyARIsAJWNpiO10LsnBKWew-pCpw9R_5KV7jI7Fkp4gphJURespHLOkT6kmzsR8XgaAst5EALw_wcB) e vou partir para a configuração da aplicação serverless em si.

O primeiro passo é instalar o [framework serverless](https://www.serverless.com/) globalmente na sua máquina, você precisará de permissão de administrador para isso. A partir dele teremos uma série de utilitários para criar nanoserviços, deploy, etc independente de cloud inclusive.

| 1    | **npm** i -g serverless |
| ---- | ----------------------- |
|      |                         |

Com o Serverless framework instalado, é hora de usarmos ele para criar sua primeira aplicação serverless, usando o comando abaixo dentro da pasta do seu novo projeto.

| 1    | serverless create --template aws-nodejs |
| ---- | --------------------------------------- |
|      |                                         |

Aqui estou criando a partir do template da AWS para Node.js, sendo que outros templates variam bastante em tecnologia, como Java, Python, etc.

Ao término da criação do projeto, você terá um handler.js, com a função Lambda que será disparada toda vez que esta aplicação serverless for acionada (falaremos disso mais tarde) e um arquivo serverless.yml que tem as informações de provisionamento da infraestrutura necessária para esta aplicação serverless na Amazon.

Esta função Lambda é um simples olá mundo que recebe o evento que originou o seu disparo e devolve um objeto. Qualquer coisa que você faria em uma função Node.js você pode fazer aqui, mas para fins deste tutorial, vamos ficar com o Hello mesmo.

Mas antes de fazermos deploy na AWS, vamos precisar de mais algumas configurações, caso seja a primeira vez que usa AWS no seu computador.

[![img](https://www.luiztools.com.br/wp-content/uploads/2021/06/banner-ebooks-node.jpg)](https://www.luiztools.com.br/mongodb-ou-mysql/)

### Configurando a AWS

Primeiro, você vai precisar do AWS CLI, o utilitário de linha de comando que permite gerenciar a sua conta da AWS e todos os serviços dela facilmente pelo seu terminal. Acesse o site do [AWS CLI](https://aws.amazon.com/pt/cli/) e baixe o executável para o seu sistema operacional, instalando-o logo na sequência.

Para que o AWS CLI funcione plugado na sua conta, vamos precisar de chaves de acesso para ele. Estas chaves podem ser obtidas acessando a sua conta da Amazon e clicando no seu nome no canto superior direito e acessando a página Credenciais de Segurança ou Security Credentials.

![img](https://www.luiztools.com.br/wp-content/uploads/2020/12/aws-lambda-7-480x273.png)

Uma vez nesta área, na seção Chaves de Acesso você consegue gerar um par de chaves composta por key e secret. Baixe e armazene em algum lugar seguro, você não terá uma segunda chance de saber o secret novamente, se perder, terá de recriar o par.

![img](https://www.luiztools.com.br/wp-content/uploads/2020/12/aws-lambda-6.png)

Com esse par de key e secret em mãos, abra o terminal e rode o comando abaixo para configurarmos nosso AWS CLI.

| 1    | aws configure |
| ---- | ------------- |
|      |               |

O setup de configuração vai te questionar das credenciais, da região da sua infraestrutura na Amazon (fica no canto superior direito da sua conta também, ao lado do seu nome) e o formato de dados que vai usar (JSON).

Caso tenha qualquer dúvida com esse processo, consulte o [manual de configuração do AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html).

[![Curso Node.js e MongoDB](https://www.luiztools.com.br/wp-content/uploads/2020/08/curso-nodejs-e1618510190832.png)](https://www.luiztools.com.br/curso-nodejs?utm_source=google&utm_medium=cpc&utm_campaign=12231680300&utm_content=121325240551&utm_term=node lambda&gclid=Cj0KCQiAubmPBhCyARIsAJWNpiO10LsnBKWew-pCpw9R_5KV7jI7Fkp4gphJURespHLOkT6kmzsR8XgaAst5EALw_wcB)

### Fazendo o Deploy

Agora que você está com o Olá Mundo criado e com o AWS CLI configurado, rode o comando abaixo (dentro da pasta da aplicação) para fazer deploy na AWS.

| 1    | **serverless** deploy |
| ---- | --------------------- |
|      |                       |

Neste exato instante o CLI do Serverless vai ler o seu serverless.yml e provisionar os serviços da Amazon necessários para executar a sua função Lambda usando principalmente um serviço chamado [Cloud Formation](https://aws.amazon.com/pt/cloudformation/) que, a partir de templates, provisiona infraestruturas completas rápida e facilmente, usando um conceito chamado IaC (Infrastructure as Code ou Infraestrutura como Código).

Quando o processo terminar, você poderá acessar no seu console da AWS, no serviço AWS Lambda, as suas funções criadas.

![img](https://www.luiztools.com.br/wp-content/uploads/2020/12/aws-lambda-5.png)

Clique na que você acabou de criar e você terá acesso aos detalhes da mesma, como o gatilho que a dispara, o evento posterior à ela, a aba de monitoramento com gráficos e logs de disparos e até mesmo o código fonte dela.

![img](https://www.luiztools.com.br/wp-content/uploads/2020/12/aws-lambda-4.png)

Se você clicar em Adicionar gatilho, vai ver que existem várias opções de gatilhos que a AWS te fornece. Por exemplo, você pode dizer que esta função vai ser disparada toda vez que um novo arquivo for armazenado em um bucket do S3, ou através de uma requisição ao seu AWS API Gateway. Ou ainda quando uma mensagem entrar na fila do [SQS](https://www.luiztools.com.br/post/tutorial-de-node-js-com-filas-na-aws-sqs/) ser processada. Enfim, o céu é o limite e o evento que originou o disparo tem todas as suas informações passadas para sua função no argumento event que ele recebe.

Do outro lado, você pode enviar o resultado da sua lambda para outro serviço (destino), que segue uma ideia similar dos gatilhos.

TUDO que acontece na sua lambda é armazenado no [CloudWatch](https://aws.amazon.com/pt/cloudwatch/), que é o serviço de logs da AWS, o que lhe permite ter alta rastreabilidade e também pode ser mapeado para disparar eventos de acordo com o tipo de log, usando o [AWS Event Bridge](https://aws.amazon.com/pt/eventbridge/). Enfim, dá pra fazer coisas MUITO profissionais usando estas tecnologias.

[![img](https://www.luiztools.com.br/wp-content/uploads/2021/05/banner-curso-bot.jpg)](https://www.luiztools.com.br/curso-beholder?utm_source=google&utm_medium=cpc&utm_campaign=12231680300&utm_content=121325240551&utm_term=node lambda&gclid=Cj0KCQiAubmPBhCyARIsAJWNpiO10LsnBKWew-pCpw9R_5KV7jI7Fkp4gphJURespHLOkT6kmzsR8XgaAst5EALw_wcB)

### Testando a Lambda

Enquanto eu não quero me enviesar em alguma integração específica com AWS Lambda, vamos usar a ferramenta de teste que a própria AWS fornece, para fazer o disparo e ver o que acontece.

No canto superior direito da sua Lambda tem um botão Testar.

![img](https://www.luiztools.com.br/wp-content/uploads/2020/12/aws-lambda-3-720x128.png)

Aqui você vai configurar um evento de teste que vai disparar a sua Lambda. Basicamente o mais importante é definir o JSON que será passado como parâmetro pra Lambda.

![img](https://www.luiztools.com.br/wp-content/uploads/2020/12/aws-lambda-2-720x390.png)

Como resultado, você terá um JSON de retorno, além dos logs coletados.

![img](https://www.luiztools.com.br/wp-content/uploads/2020/12/aws-lambda.jpg)

Isso lhe permitirá entender facilmente se a Lambda está ou não está se comportando bem, dando uma entrada de parâmetros que você definiu no teste.

E com isso encerramos este tutorial. Querendo saber mais de serverless na prática, usamos este recurso de maneira bem profissional no [curso full stack JS](https://www.luiztools.com.br/curso-fullstack?utm_source=google&utm_medium=cpc&utm_campaign=12231680300&utm_content=121325240551&utm_term=node lambda&gclid=Cj0KCQiAubmPBhCyARIsAJWNpiO10LsnBKWew-pCpw9R_5KV7jI7Fkp4gphJURespHLOkT6kmzsR8XgaAst5EALw_wcB) (banner abaixo), mas sugira pautas relacionadas nos comentários que vou ver o que consigo escrever a respeito aqui no blog.

Um abraço e sucesso.