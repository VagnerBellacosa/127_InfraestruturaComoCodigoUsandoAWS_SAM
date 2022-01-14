# Docker

Publicado em: 9 de janeiro de 2018•7 minutos (tempo de leitura)



Copiar URL

IR PARA SEÇÃO

- [O que é Docker?](https://www.redhat.com/pt-br/topics/containers/what-is-docker#o-que-é-docker)
- [Como o Docker funciona?](https://www.redhat.com/pt-br/topics/containers/what-is-docker#como-o-docker-funciona)
- [Comparação: Docker e containers Linux](https://www.redhat.com/pt-br/topics/containers/what-is-docker#comparação-docker-e-containers-linux)
- [Vantagens do Docker](https://www.redhat.com/pt-br/topics/containers/what-is-docker#vantagens-do-docker)
- [Há limitações no uso do Docker?](https://www.redhat.com/pt-br/topics/containers/what-is-docker#há-limitações-no-uso-do-docker)

## O que é Docker?

O termo Docker se refere a muitas coisas: um projeto da comunidade open source; as ferramentas resultantes desse projeto; a empresa Docker Inc., principal apoiadora do projeto; e as ferramentas compatíveis formalmente com a empresa. O fato de que as tecnologias e a empresa têm o mesmo nome pode causar uma certa confusão.

Veja uma simples explicação:

- O software de TI "Docker” é uma tecnologia de containerização para criação e uso de [containers Linux®](https://www.redhat.com/pt-br/topics/containers).
- A [comunidade open source do Docker](https://forums.docker.com/) trabalha gratuitamente para melhorar essas tecnologias para todos os usuários.
- A empresa [Docker Inc.](https://www.docker.com/) se baseia no trabalho realizado pela comunidade do Docker, tornando-o mais seguro, e compartilha os avanços com a comunidade em geral. Depois, ela oferece aos clientes corporativos o suporte necessário para as tecnologias que foram aprimoradas e fortalecidas.

Com o Docker, é possível lidar com os containers como se fossem máquinas virtuais modulares e extremamente leves. Além disso, os containers oferecem maior flexibilidade para você criar, implantar, copiar e migrar um container de um ambiente para outro. Isso [otimiza as aplicações na nuvem](https://www.redhat.com/pt-br/topics/cloud-native-apps).

[O que são containers Linux?](https://www.redhat.com/pt-br/topics/containers/whats-a-linux-container)

## Como o Docker funciona?

A tecnologia Docker usa o kernel do Linux e recursos do kernel como Cgroups e [namespaces](https://lwn.net/Articles/528078/) para segregar processos. Assim, eles podem ser executados de maneira independente. O objetivo dos containers é criar essa independência: a habilidade de executar diversos processos e aplicações separadamente para utilizar melhor a infraestrutura e, ao mesmo tempo, [manter a segurança](https://www.redhat.com/pt-br/topics/security) que você teria em sistemas separados.

As ferramentas de container, incluindo o Docker, fornecem um modelo de implantação com base em imagem. Isso facilita o compartilhamento de uma aplicação ou conjunto de serviços, incluindo todas as dependências deles em vários ambientes. O Docker também automatiza a implantação da aplicação (ou de conjuntos de processos que constituem uma aplicação) dentro desse ambiente de container.

Essas ferramentas baseadas nos containers Linux (o que faz com que o Docker seja exclusivo e fácil de usar) oferecem aos usuários acesso sem precedentes a aplicações, além da habilidade de implantar com rapidez e de ter total controle sobre as versões e distribuição.

![img](https://www.redhat.com/cms/managed-files/styles/max_size/s3/ilustracion_ots_1.png?itok=aF_jCITC)

#### Webinars gratuitos

Assista a série de webinars da Red Hat e descubra como impulsionar a inovação tecnológica usando modelos colaborativos.

[Assista on demand](https://www.redhat.com/pt-br/open-tech-sessions?intcmp=7013a000002ptzhAAA)

## Comparação: Docker e containers Linux

Não, a tecnologia Docker foi desenvolvida inicialmente com base na tecnologia [LXC](https://linuxcontainers.org/), que a maioria das pessoas associa aos containers Linux "tradicionais". No entanto, desde então, essa tecnologia tornou-se independente. O LXC era útil como uma [virtualização](https://www.redhat.com/pt-br/topics/virtualization) leve, mas não oferecia uma boa experiência para usuários e desenvolvedores. A tecnologia Docker oferece mais do que a habilidade de executar containers: ela também facilita o processo de criação e construção de containers, o envio e o controle de versão de imagens, dentre outras coisas.

![img](https://www.redhat.com/cms/managed-files/styles/wysiwyg_full_width/s3/traditional-linux-containers-vs-docker_0.png?itok=oO46m7hv)

Os containers Linux tradicionais usam um sistema init capaz de gerenciar vários processos. Isso significa que aplicações inteiras são executadas como uma. A tecnologia Docker incentiva que as aplicações sejam segregadas em processos separados e oferece as ferramentas para fazer isso. Essa abordagem granular tem algumas vantagens.

## Vantagens do Docker

### Modularidade

A abordagem do Docker para a containerização se concentra na habilidade de desativar uma parte de uma aplicação, seja para reparo ou atualização, sem interrompê-la totalmente. Além dessa abordagem baseada em microsserviços, é possível compartilhar processos entre várias aplicações da mesma maneira como na [arquitetura orientada a serviço](https://www.redhat.com/pt-br/topics/cloud-native-apps/what-is-service-oriented-architecture) (SOA).

### Camadas e controle de versão de imagens

Cada arquivo de imagem Docker é composto por uma série de camadas. Elas são combinadas em uma única imagem. Uma nova camada é criada quando há alteração na imagem. Toda vez que um usuário especifica um comando, como *executar* ou *copiar*, uma nova camada é criada.

O Docker reutiliza essas camadas para a construção de novos containers, o que torna o processo de criação muito mais rápido. As alterações intermediárias são compartilhadas entre imagens, o que melhora ainda mais a [velocidade, o tamanho e a eficiência](https://developers.redhat.com/blog/2016/03/09/more-about-docker-images-size). O controle de versões é inerente ao uso de camadas. Sempre que é realizada uma nova alteração, é gerado um changelog integrado, o que fornece controle total sobre as imagens do container.

### Reversão

Talvez a melhor vantagem da criação de camadas seja a habilidade de reverter quando necessário. Toda imagem possui camadas. Não gostou da iteração atual de uma imagem? Simples, basta reverter para a versão anterior. Esse processo é compatível com uma abordagem de desenvolvimento ágil e possibilita as práticas de [integração e implantação contínuas (CI/CD)](https://www.redhat.com/pt-br/topics/devops/what-is-ci-cd) em relação às ferramentas.

### Implantação rápida

Antigamente, colocar novo hardware em funcionamento, provisionado e disponível, levava dias. E as despesas e esforço necessários para mantê-lo eram onerosos. Os containers baseados em docker podem reduzir o tempo de implantação de horas para segundos. Ao criar um container para cada processo, é possível compartilhar rapidamente esses processos similares com novos aplicativos. Como não é necessário inicializar um sistema operacional para adicionar ou mover um container, o tempo de implantação é substancialmente menor. Além disso, com a velocidade de implantação, é possível criar dados e destruir os criados pelos containers sem nenhuma preocupação e com facilidade e economia.

Em resumo, a tecnologia Docker é uma abordagem mais granular, controlável e baseada em microsserviços que valoriza a eficiência.

## Há limitações no uso do Docker?

Por si só, o Docker é excelente para gerenciar containers únicos. No entanto, quando você começa a usar cada vez mais containers e aplicações em containers segregados em centenas de partes, o gerenciamento e a orquestração podem se tornar um grande desafio. Eventualmente, será necessário recuar e agrupar os containers para oferecer serviços como rede, segurança, telemetria etc. em todos eles. É aí que o Kubernetes entra em cena.

[O que é Kubernetes?](https://www.redhat.com/pt-br/topics/containers/what-is-kubernetes)[O que é orquestração de containers?](https://www.redhat.com/pt-br/topics/containers/what-is-container-orchestration)

O Docker não fornece as mesmas funcionalidades parecidas com UNIX que os containers Linux tradicionais oferecem. Isso inclui a capacidade de usar processos como cron ou syslog dentro do container, junto à aplicação. O Docker também tem algumas limitações em questões como a limpeza de processos netos (grandchild) após o encerramento dos processos filhos (child), algo que é processado de forma natural nos containers Linux tradicionais. Essas desvantagens podem ser mitigadas ao modificar o arquivo de configuração e configurar essas funcionalidade desde o início, algo que não está imediatamente óbvio em um primeiro momento.

Além disso, há outros subsistemas e dispositivos do Linux sem espaço de nomes. Incluindo os dispositivos [SELinux](https://www.redhat.com/pt-br/topics/linux/what-is-selinux), Cgroups e /dev/sd*. Isso significa que, se um invasor adquirir controle sobre esses subsistemas, o host será comprometido. Para manter-se leve, o compartilhamento do kernel do host com os [containers gera a possibilidade dessa vulnerabilidade na segurança](https://www.redhat.com/pt-br/topics/security/container-security). Isso é diferente nas máquinas virtuais, que são mais firmemente segregadas a partir do sistema host.

[Os containers Docker são realmente seguros?](https://opensource.com/business/14/7/docker-security-selinux)

O [daemon do Docker](https://docs.docker.com/engine/reference/commandline/dockerd/) também pode representar uma vulnerabilidade à segurança. Para usar e executar os containers Docker, é provável que você use o daemon do Docker, um ambiente de execução persistente para containers. O daemon do Docker requer privilégios de raiz. Portanto, é necessário ter um cuidado maior ao escolher as pessoas que terão acesso a esse processo e o local onde ele residirá. Por exemplo, um daemon local tem menos chances de sofrer um ataque do que um daemon em um local mais público, como um servidor web.

[Introdução aos novos recursos de segurança do Docker](https://opensource.com/business/14/9/security-for-docker)

### Conteúdo relacionado:

- Ebook:[ Desenvolva apps modernos com containers Linux](https://www.redhat.com/pt-br/resources/building-modern-apps-with-containers-ebook)
- Checklist:[ Desenvolvimento de containers: 5 tópicos para abordar com sua equipe](https://www.redhat.com/pt-br/resources/developing-container-apps-manager-checklist)
- Artigo: [Introdução aos containers Linux](https://www.redhat.com/pt-br/topics/containers)
- Artigo: [O que é um container Linux?](https://www.redhat.com/pt-br/topics/containers/whats-a-linux-container)
- Artigo: [O que é Kubernetes?](https://www.redhat.com/pt-br/topics/containers/what-is-kubernetes)
- Artigo: [O que é Kubernetes cluster?](https://www.redhat.com/pt-br/topics/containers/what-is-a-kubernetes-cluster)
- Artigo: [O que é um pod do kubernetes?](https://www.redhat.com/pt-br/topics/containers/what-is-kubernetes-pod)
- Artigo: [Por que escolher a Red Hat na adoção de containers?](https://www.redhat.com/pt-br/topics/containers/why-choose-red-hat-containers)
- Artigo: [Plataforma de aplicações em containers da Red Hat](https://www.redhat.com/pt-br/technologies/cloud-computing/openshift)
- Artigo: [Segurança de containers](https://www.redhat.com/pt-br/topics/security/container-security)
- Artigo: [Red Hat OpenShift vs Kubernete](https://www.redhat.com/pt-br/topics/containers/red-hat-openshift-kubernetes)[s](https://www.redhat.com/pt-br/topics/containers/red-hat-openshift-kubernetes)
- Blog:[ Red Hat® Red Hat Developers](https://developers.redhat.com/)
- Blog:[ Red Hat Enterprise Linux](https://www.redhat.com/en/blog/channel/red-hat-enterprise-linux)