# O que é ?AWS Serverless Application Model(AWS SAM)?

[PDF](https://docs.aws.amazon.com/pt_br/serverless-application-model/latest/developerguide/serverless-application-model.pdf#what-is-sam)

[RSS](https://docs.aws.amazon.com/pt_br/serverless-application-model/latest/developerguide/serverless-application-model-updates.rss)



OAWS Serverless Application Model(AWS SAM) é uma estrutura de código aberto que você pode usar para criar o[aplicativos sem servidor](http://aws.amazon.com/serverless/)noAWS.

A**Aplicativo sem servidor da**O é uma combinação de funções do Lambda, fontes de eventos e outros recursos que trabalham juntos para realizar tarefas. Observe que um aplicativo sem servidor é mais do que apenas uma função do Lambda, pode incluir recursos adicionais como APIs, bancos de dados e mapeamentos da fonte do evento.

Você pode usar oAWS SAMPara definir aplicativos sem servidor.AWS SAMO  consiste nos seguintes componentes:

- **AWS SAMespecificação do modelo**. Use essa especificação para definir seu aplicativo sem servidor. Ele fornece uma sintaxe simples e limpa para descrever as funções, APIs, permissões, configurações e eventos que compõem um aplicativo sem servidor. Você usa umAWS SAMpara operar em uma única entidade implantável e versionada que seja seu aplicativo sem servidor. Para o completoAWS SAMespecificação do modelo, consulte[AWS Serverless Application Model(AWS SAM) Especificação](https://docs.aws.amazon.com/pt_br/serverless-application-model/latest/developerguide/sam-specification.html).

   

- **AWS SAMinterface da linha de comando do (AWS SAMCLI)**. Utilize esta ferramenta para criar aplicações sem servidor que são definidas peloAWS SAMModelos do. A CLI fornece comandos que permitem que você verifique seAWS SAMsão escritos de acordo com a especificação, invocar funções do Lambda localmente, funções de depuração passo a passo do Lambda, empacotar e implantar aplicativos sem servidor para oAWSNuvem, e assim por diante. Para saber detalhes sobre como usar oAWS SAMCLI, incluindo oAWS SAMReferência de comandos da CLI do, consulte[AWS SAMReferência de comando da CLI](https://docs.aws.amazon.com/pt_br/serverless-application-model/latest/developerguide/serverless-sam-reference.html#serverless-sam-cli).

Este guia mostra como usar oAWS SAMpara definir, testar e implantar um aplicativo simples sem servidor. Ele também fornece um[Aplicativo de exemplo](https://docs.aws.amazon.com/pt_br/serverless-application-model/latest/developerguide/serverless-getting-started-hello-world.html)que você pode baixar, testar localmente e implantar noAWSNuvem. Você pode usar esse aplicativo de exemplo como um ponto inicial para desenvolver seus próprios aplicativos sem servidor.

## Benefícios do usoAWS SAM

ComoAWS SAMO se integra com outros doAWS, criando aplicativos sem servidor comAWS SAMO fornece os seguintes benefícios:

- **Configuração de implantação única**.AWS SAMO facilita a organização de componentes e recursos relacionados e opera em uma única pilha de. Você pode usar oAWS SAMpara compartilhar configuração (como memória e timeouts) entre recursos e implantar todos os recursos relacionados juntos como uma única entidade versionada.

   

- **Extensão doAWS CloudFormation**. ComoAWS SAMO é uma extensão doAWS CloudFormation, você obtém os recursos de implantação confiáveis doAWS CloudFormation. Você pode definir recursos usandoAWS CloudFormationNo seuAWS SAMTemplate Template Além disso, você pode usar o conjunto completo de recursos, funções intrínsecas e outros recursos de modelo que estão disponíveis noAWS CloudFormation.

   

- **Práticas recomendadas integradas**. Você pode usar oAWS SAMpara definir e implantar sua infraestrutura como configuração. Isso permite que você use e imponha práticas recomendadas, como revisões de código. Além disso, com algumas linhas de configuração, você pode habilitar implantações seguras por meio do CodeDeploy e habilitar o rastreamento usandoAWS X-Ray.

   

- **Depuração local e teste**. OAWS SAMA CLI permite criar, testar e depurar localmente aplicativos sem servidor definidos peloAWS SAMModelos do. A CLI fornece um ambiente de execução semelhante ao Lambda localmente. Ele ajuda você a detectar problemas antecipadamente, fornecendo paridade com o ambiente real de execução do Lambda. Para percorrer e depurar seu código para entender o que o código está fazendo, você pode usarAWS SAMporAWSkits de ferramentas como o[AWS Toolkit for JetBrains](https://docs.aws.amazon.com/toolkit-for-jetbrains/latest/userguide/),[AWSToolkit for PyCharm](http://aws.amazon.com/pycharm/),[AWSToolkit for IntelliJ](http://aws.amazon.com/intellij/), e[AWSToolkit for Visual Studio Code](http://aws.amazon.com/visualstudiocode/). Isso aperta o loop de feedback, possibilitando que você encontre e solucione problemas que você possa encontrar na nuvem.

   

- **Integração profunda com ferramentas de desenvolvimento**. Você pode usar oAWS SAMcom um conjunto deAWSFerramentas para a criação de aplicativos sem servidor. Você pode descobrir novos aplicativos no[AWS Serverless Application Repository](https://docs.aws.amazon.com/serverlessrepo/latest/devguide/). Para criação, teste e depuraçãoAWS SAM— baseados em aplicativos sem servidor, você pode usar o[AWS Cloud9IDE DA](https://docs.aws.amazon.com/cloud9/latest/user-guide/). Para criar um pipeline de implantação para seus aplicativos sem servidor, você pode usar[CodeBuild](https://docs.aws.amazon.com/codebuild/latest/userguide/),[CodeDeploy](https://docs.aws.amazon.com/codedeploy/latest/userguide/), e[CodePipeline](https://docs.aws.amazon.com/codepipeline/latest/userguide/). Você também pode usar[AWS CodeStar](https://docs.aws.amazon.com/codestar/latest/userguide/)para começar a usar uma estrutura de projeto, um repositório de código e um pipeline CI/CD configurado automaticamente para você. Para implantar seu aplicativo sem servidor, você pode usar o[Plug-in Jenkins](https://plugins.jenkins.io/aws-sam/). Você pode usar o[Toolkit do Stackery.io](https://www.stackery.io/product/aws-sam/)para criar aplicativos prontos para produção.