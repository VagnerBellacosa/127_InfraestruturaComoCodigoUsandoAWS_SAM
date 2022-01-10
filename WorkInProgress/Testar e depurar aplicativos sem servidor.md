# Testar e depurar aplicativos sem servidor

[PDF](https://docs.aws.amazon.com/pt_br/serverless-application-model/latest/developerguide/serverless-application-model.pdf#serverless-test-and-debug)

[RSS](https://docs.aws.amazon.com/pt_br/serverless-application-model/latest/developerguide/serverless-application-model-updates.rss)



Com oAWS SAMinterface de linha de comando (CLI), você pode testar localmente e depurar seus aplicativos sem servidor antes de fazer o upload do aplicativo para oAWSNuvem. Você pode verificar se seu aplicativo está se comportando como esperado, depurar o que está errado e corrigir quaisquer problemas, antes de seguir as etapas de empacotamento e implantação do aplicativo.

Quando você invoca localmente uma função do Lambda no modo de depuração dentro doAWS SAMCLI, você pode anexar um depurador a ele. Com o depurador, você pode percorrer seu código linha por linha, ver os valores de várias variáveis e corrigir problemas da mesma maneira que faria para qualquer outro aplicativo.

**nota**

Se seu aplicativo incluir uma ou mais camadas, quando você executar e depurar localmente seu aplicativo, o pacote de camadas será baixado e armazenado em cache em seu host local. Para mais informações, consulte [Como as camadas são armazenadas em cache localmente](https://docs.aws.amazon.com/pt_br/serverless-application-model/latest/developerguide/serverless-sam-cli-layers.html#local-testing-with-layers).

**Tópicos**

- [Invocar funções localmente](https://docs.aws.amazon.com/pt_br/serverless-application-model/latest/developerguide/serverless-sam-cli-using-invoke.html)
- [Executando API Gateway localmente](https://docs.aws.amazon.com/pt_br/serverless-application-model/latest/developerguide/serverless-sam-cli-using-start-api.html)
- [Integração com testes automatizados](https://docs.aws.amazon.com/pt_br/serverless-application-model/latest/developerguide/serverless-sam-cli-using-automated-tests.html)
- [Gerando cargas de exemplo de eventos](https://docs.aws.amazon.com/pt_br/serverless-application-model/latest/developerguide/serverless-sam-cli-using-generate-event.html)
- [Depuração passo a passo funções do Lambda localmente](https://docs.aws.amazon.com/pt_br/serverless-application-model/latest/developerguide/serverless-sam-cli-using-debugging.html)
- [Passando argumentos de depuração de runtime adicionais](https://docs.aws.amazon.com/pt_br/serverless-application-model/latest/developerguide/serverless-sam-cli-using-debugging-additional-arguments.html)