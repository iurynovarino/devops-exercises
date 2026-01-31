# Kubernetes

<!-- {% raw %} -->

Qual é o seu objetivo?

* Eu gostaria de me preparar para a certificação CKA
  * Veja a página [CKA](CKA.md)
* Eu gostaria de aprender Kubernetes praticando material teórico e prático
  * Resolva [exercícios](#exercícios-de-kubernetes)
  * Resolva [perguntas](#perguntas-sobre-kubernetes)
* Eu gostaria de aprender Kubernetes na prática
  * Resolva [exercícios](#exercícios-de-kubernetes)

- [Kubernetes](#kubernetes)
  - [Exercícios de Kubernetes](#exercícios-de-kubernetes)
    - [Pods](#pods)
    - [Service](#service)
    - [ReplicaSet](#replicaset)
    - [Rótulos e Seletores](#rótulos-e-seletores)
    - [Scheduler](#scheduler)
    - [Kustomize](#kustomize)
  - [Perguntas sobre Kubernetes](#perguntas-sobre-kubernetes)
    - [Kubernetes 101](#kubernetes-101)
    - [Cluster e Arquitetura](#cluster-e-arquitetura)
      - [Kubelet](#kubelet)
      - [Comandos de Nós](#comandos-de-nós)
    - [Pods](#pods-1)
      - [Pods Estáticos](#pods-estáticos)
      - [Comandos de Pods](#comandos-de-pods)
      - [Solução de Problemas e Depuração de Pods](#solução-de-problemas-e-depuração-de-pods)
    - [Rótulos e Seletores](#rótulos-e-seletores-1)
    - [Deployments](#deployments)
      - [Comandos de Deployments](#comandos-de-deployments)
    - [Services](#services)
    - [Ingress](#ingress)
    - [ReplicaSets](#replicasets)
    - [DaemonSet](#daemonset)
      - [DaemonSet - Comandos](#daemonset---comandos)
    - [StatefulSet](#statefulset)
    - [Armazenamento](#armazenamento)
      - [Volumes](#volumes)
    - [Rede](#rede)
    - [Políticas de Rede](#políticas-de-rede)
    - [etcd](#etcd)
    - [Namespaces](#namespaces)
      - [Namespaces - comandos](#namespaces---comandos)
      - [Cota de Recursos](#cota-de-recursos)
    - [Operators](#operators)
    - [Secrets](#secrets)
    - [Volumes](#volumes-1)
    - [Controle de Acesso](#controle-de-acesso)
    - [Padrões](#padrões)
    - [CronJob](#cronjob)
    - [Diversos](#diversos)
    - [Gatekeeper](#gatekeeper)
    - [Teste de Políticas](#teste-de-políticas)
    - [Helm](#helm)
      - [Comandos](#comandos)
    - [Segurança](#segurança)
    - [Cenários de Solução de Problemas](#cenários-de-solução-de-problemas)
    - [Istio](#istio)
    - [Controladores](#controladores)
    - [Scheduler](#scheduler-1)
      - [Afinidade de Nó](#afinidade-de-nó)
    - [Taints](#taints)
    - [Limites de Recursos](#limites-de-recursos)
      - [Limites de Recursos - Comandos](#limites-de-recursos---comandos)
    - [Monitoramento](#monitoramento)
    - [Kustomize](#kustomize-1)
    - [Estratégias de Implantação](#estratégias-de-implantação)
    - [Cenários](#cenários)

## Exercícios de Kubernetes

### Pods

|Nome|Tópico|Objetivo & Instruções|Solução|Comentários|
|--------|--------|------|----|----|
| Meu Primeiro Pod | Pods | [Exercício](pods_01.md) | [Solução](solutions/pods_01_solution.md)
| "Matando" Contêineres | Pods | [Exercício](killing_containers.md) | [Solução](solutions/killing_containers.md)

### Service

|Nome|Tópico|Objetivo & Instruções|Solução|Comentários|
|--------|--------|------|----|----|
| Criando um Serviço | Service | [Exercício](services_01.md) | [Solução](solutions/services_01_solution.md)

### ReplicaSet

|Nome|Tópico|Objetivo & Instruções|Solução|Comentários|
|--------|--------|------|----|----|
| Criando um ReplicaSet | ReplicaSet | [Exercício](replicaset_01.md) | [Solução](solutions/replicaset_01_solution.md)
| Operando ReplicaSets | ReplicaSet | [Exercício](replicaset_02.md) | [Solução](solutions/replicaset_02_solution.md)
| Seletores de ReplicaSets | ReplicaSet | [Exercício](replicaset_03.md) | [Solução](solutions/replicaset_03_solution.md)

### Rótulos e Seletores

|Nome|Tópico|Objetivo & Instruções|Solução|Comentários|
|--------|--------|------|----|----|
| Rótulos e Seletores 101 | Rótulos, Seletores | [Exercício](exercises/labels_and_selectors/exercise.md) | [Solução](exercises/labels_and_selectors/solution.md)
| Seletores de Nó | Rótulos, Seletores | [Exercício](exercises/node_selectors/exercise.md) | [Solução](exercises/node_selectors/solution.md)


### Scheduler

|Nome|Tópico|Objetivo & Instruções|Solução|Comentários|
|--------|--------|------|----|----|
| Taints 101 | Taints | [Exercício](exercises/taints_101/exercise.md) | [Solução](exercises/taints_101/solution.md)

### Kustomize

|Nome|Tópico|Objetivo & Instruções|Solução|Comentários|
|--------|--------|------|----|----|
| rótulos comuns | Kustomize | [Exercício](exercises/kustomize_common_labels/exercise.md) | [Solução](exercises/kustomize_common_labels/solution.md)

## Perguntas sobre Kubernetes

### Kubernetes 101

<details>
<summary>O que é Kubernetes? Por que as organizações o estão usando?</summary><br><b>

Kubernetes é um sistema de código aberto que fornece aos usuários a capacidade de gerenciar, escalar e implantar aplicações em contêineres.

Para entender para que o Kubernetes é bom, vamos ver alguns exemplos:

* Você gostaria de executar uma determinada aplicação em um contêiner em vários locais diferentes e sincronizar as alterações em todos eles, não importa onde eles sejam executados
* Realizar atualizações e alterações em centenas de contêineres
* Lidar com casos em que a carga atual exige escalar para cima (ou para baixo)

</b></details>

<details>
<summary>Quando ou por que NÃO usar Kubernetes?</summary><br><b>

  - Se você gerencia infraestrutura de baixo nível ou bare metal, o Kubernetes provavelmente não é o que você precisa ou quer
  - Se você é uma equipe pequena (como menos de 20 engenheiros) executando menos de uma dúzia de contêineres, o Kubernetes pode ser um exagero (mesmo que você precise de escala, atualizações contínuas, etc.). Você ainda pode aproveitar os benefícios de usar um Kubernetes gerenciado, mas definitivamente deve pensar cuidadosamente sobre isso antes de tomar uma decisão sobre adotá-lo.

</b></details>

<details>
<summary>Quais são algumas das funcionalidades do Kubernetes?</summary><br><b>

  - Auto-recuperação: O Kubernetes usa verificações de saúde para monitorar contêineres e executar certas ações em caso de falha ou outro tipo de evento, como reiniciar o contêiner
  - Balanceamento de Carga: O Kubernetes pode dividir e/ou balancear requisições para aplicações em execução no cluster, com base no estado dos Pods que executam a aplicação
  - Operators: Aplicações empacotadas do Kubernetes que podem usar a API do cluster para atualizar seu estado e acionar ações com base em eventos e mudanças de estado da aplicação
  - Rollout Automatizado: Atualizações graduais são lançadas para as aplicações e há suporte para rollback caso algo dê errado
  - Escalonamento: Escalonamento horizontal (para baixo e para cima) com base em diferentes parâmetros de estado e critérios definidos pelo usuário
  - Secrets: você tem um mecanismo para armazenar nomes de usuário, senhas e endpoints de serviço de forma privada, onde nem todos que usam o cluster podem visualizá-los

</b></details>

<details>
<summary>Quais objetos do Kubernetes existem?</summary><br><b>

  * Pod
  * Service
  * ReplicationController
  * ReplicaSet
  * DaemonSet
  * Namespace
  * ConfigMap
  ...
</b></details>

<details>
<summary>Quais campos são obrigatórios em qualquer objeto do Kubernetes?</summary><br><b>

metadata, kind e apiVersion

</b></details>

<details>
<summary>O que é kubectl?</summary><br><b>

Kubectl é a ferramenta de linha de comando do Kubernetes que permite executar comandos contra clusters Kubernetes. Por exemplo, você pode usar o kubectl para implantar aplicações, inspecionar e gerenciar recursos do cluster e visualizar logs.

</b></details>

<details>
<summary>Quais objetos do Kubernetes você geralmente usa ao implantar aplicações no Kubernetes?</summary><br><b>

* Deployment - cria os Pods e os observa
* Service: roteia o tráfego para os Pods internamente
* Ingress: roteia o tráfego de fora do cluster

</b></details>

<details>
<summary>Por que não existe um comando como `kubectl get containers` no Kubernetes?</summary><br><b>

Porque contêiner não é um objeto do Kubernetes. A menor unidade de objeto no Kubernetes é um Pod. Em um único Pod, você pode encontrar um ou mais contêineres.

</b></details>

<details>
<summary>Quais ações ou operações você considera como melhores práticas quando se trata de Kubernetes?</summary><br><b>

  - Sempre certifique-se de que os arquivos YAML do Kubernetes são válidos. A aplicação de verificações e pipelines automatizados é recomendada.
  - Sempre especifique requisições e limites para evitar situações em que os contêineres usem toda a memória do cluster, o que pode levar a problemas de OOM (Out of Memory)
  - Especifique rótulos para agrupar logicamente Pods, Deployments, etc. Use rótulos para identificar o tipo da aplicação, por exemplo, entre outras coisas

</b></details>

### Cluster e Arquitetura

<details>
<summary>O que é um Cluster Kubernetes?</summary><br><b>

Definição da Red Hat: "Um cluster Kubernetes é um conjunto de máquinas de nós para executar aplicações em contêineres. Se você está executando Kubernetes, você está executando um cluster.
No mínimo, um cluster contém um nó de trabalho e um nó mestre."

Leia mais aqui
</b></details>

<details>
<summary>O que é um Nó?</summary><br><b>

Um nó é uma máquina virtual ou física que serve como um trabalhador para executar as aplicações.<br>
É recomendado ter pelo menos 3 nós em um ambiente de produção.
</b></details>

<details>
<summary>Pelo que o nó mestre é responsável?</summary><br><b>

O mestre coordena todos os fluxos de trabalho no cluster:

* Agendamento de aplicações
* Gerenciamento do estado desejado
* Lançamento de novas atualizações

</b></details>

<details>
<summary>Descreva brevemente e em alto nível, o que acontece quando você executa `kubectl get nodes`</summary><br><b>

1. Seu usuário é autenticado
2. A requisição é validada pelo kube-apiserver
3. Os dados são recuperados do etcd
</b></details>

<details>
<summary>Verdadeiro ou Falso? Todo cluster deve ter 0 ou mais nós mestres e pelo menos 1 trabalhador</summary><br><b>

Falso. Um cluster Kubernetes consiste em pelo menos 1 mestre e pode ter 0 trabalhadores (embora isso não seja muito útil...)

</b></details> 

<details>
<summary>Quais são os componentes do nó mestre (também conhecido como plano de controle)?</summary><br><b>

  * API Server - a API do Kubernetes. Todos os componentes do cluster se comunicam através dela
  * Scheduler - atribui uma aplicação a um nó de trabalho onde ela pode ser executada
  * Controller Manager - manutenção do cluster (replicações, falhas de nó, etc.)
  * etcd - armazena a configuração do cluster

</b></details>

<details>
<summary>Quais são os componentes de um nó de trabalho (também conhecido como plano de dados)?</summary><br><b>

  * Kubelet - um agente responsável pela comunicação do nó com o mestre.
  * Kube-proxy - balanceamento de carga de tráfego entre os componentes da aplicação
  * Container runtime - o motor que executa os contêineres (Podman, Docker, ...)

</b></details>

<details>
<summary>Coloque os componentes do lado direito da imagem no lugar certo no desenho<br>
<img src="images/cluster_architecture_exercise.png"/>
</summary><br><b>
<img src="images/cluster_architecture_solution.png"/>

</b></details>

<details>
<summary>Você está gerenciando múltiplos clusters Kubernetes. Como você alterna rapidamente entre os clusters usando o kubectl?</summary><br><b>

`kubectl config use-context`
</b></details>

<details>
<summary>Como você previne o alto uso de memória no seu cluster Kubernetes e possíveis problemas como vazamento de memória e OOM?</summary><br><b>

Aplique requisições e limites, especialmente em aplicações de terceiros (onde a incerteza é ainda maior)
</b></details>

<details>
<summary>Você tem experiência com a implantação de um cluster Kubernetes? Se sim, pode descrever o processo em alto nível?</summary><br><b>

1. Crie múltiplas instâncias que você usará como nós/trabalhadores do Kubernetes. Crie também uma instância para atuar como o Mestre. As instâncias podem ser provisionadas em uma nuvem ou podem ser máquinas virtuais em hosts bare metal.
2. Provisione uma autoridade de certificação que será usada para gerar certificados TLS para os diferentes componentes de um cluster Kubernetes (kubelet, etcd, ...)
  1. Gere um certificado e uma chave privada para os diferentes componentes
3. Gere kubeconfigs para que os diferentes clientes do Kubernetes possam localizar os servidores da API e se autenticar.
4. Gere uma chave de criptografia que será usada para criptografar os dados do cluster
5. Crie um cluster etcd
</b></details>

<details>
<summary>Qual comando listará todos os tipos de objeto em um cluster?</summary><br><b>

`kubectl api-resources`
</b></details>

<details>
<summary>O que `kubectl get componentstatus` faz?</summary><br><b>

Exibe o status de cada um dos componentes do plano de controle.
</b></details>

#### Kubelet

<details>
<summary>O que acontece com os pods em execução se você parar o Kubelet nos nós de trabalho?</summary><br><b>

Quando você para o serviço kubelet em um nó de trabalho, ele não será mais capaz de se comunicar com o servidor da API do Kubernetes. Como resultado, o nó será marcado como NotReady e os pods em execução nesse nó serão marcados como Unknown. O plano de controle do Kubernetes tentará então reagendar os pods para outros nós disponíveis no cluster. 
</b></details>

#### Comandos de Nós

<details>
<summary>Execute um comando para visualizar todos os nós do cluster</summary><br><b>

`kubectl get nodes`

Nota: Você pode querer criar um alias (`alias k=kubectl`) e se acostumar com `k get no`
</b></details>

<details>
<summary>Crie uma lista de todos os nós em formato JSON e armazene-a em um arquivo chamado "some_nodes.json"</summary><br><b>

`k get nodes -o json > some_nodes.json`
</b></details>

<details>
<summary>Verifique quais rótulos um dos seus nós no cluster possui</summary><br><b>

`k get no minikube --show-labels`
</b></details>

### Pods

<details>
<summary>Explique o que é um Pod</summary><br><b>

Um Pod é um grupo de um ou mais contêineres, com recursos de armazenamento e rede compartilhados, e uma especificação de como executar os contêineres.

Pods são as menores unidades de computação implantáveis que você pode criar e gerenciar no Kubernetes. 

</b></details>

<details>
<summary>Implante um pod chamado "my-pod" usando a imagem nginx:alpine</summary><br><b>

`kubectl run my-pod --image=nginx:alpine`

Se você é um iniciante em Kubernetes, deve saber que esta não é uma maneira comum de executar Pods. A maneira comum é executar um Deployment que, por sua vez, executa um(s) Pod(s).

Além disso, Pods e/ou Deployments são geralmente definidos em arquivos em vez de serem executados diretamente usando apenas os argumentos da CLI.
</b></details>

<details>
<summary>O que você pensa sobre "Pods não devem ser criados diretamente"?</summary><br><b>

Pods geralmente não são criados diretamente. Você notará que os Pods são geralmente criados como parte de outras entidades, como Deployments ou ReplicaSets.

Se um Pod morre, o Kubernetes não o trará de volta. É por isso que é mais útil, por exemplo, definir ReplicaSets que garantirão que um determinado número de Pods sempre será executado, mesmo após a morte de um certo Pod.
</b></details>

<details>
<summary>Quantos contêineres um pod pode conter?</summary><br><b>

Um pod pode incluir múltiplos contêineres, mas na maioria dos casos provavelmente será um contêiner por pod.

Existem alguns padrões onde faz sentido executar mais de um contêiner, como o padrão "side-car", onde você pode querer realizar logs ou alguma outra operação que é executada por outro contêiner em execução com o contêiner da sua aplicação no mesmo Pod.
</b></details>

<details>
<summary>Quais casos de uso existem para executar múltiplos contêineres em um único pod?</summary><br><b>

Uma aplicação web com componentes/adaptadores de log e monitoramento separados (= em seus próprios contêineres) é um exemplo.<br>
Um pipeline de CI/CD (usando Tekton, por exemplo) pode executar múltiplos contêineres em um Pod se uma Tarefa contiver múltiplos comandos.
</b></details>

<details>
<summary>Quais são as possíveis fases de um Pod?</summary><br><b>

  * Running (Em execução) - O Pod está vinculado a um nó e pelo menos um contêiner está em execução
  * Failed/Error (Falhou/Erro) - Pelo menos um contêiner no Pod terminou com uma falha
  * Succeeded (Bem-sucedido) - Todo contêiner no Pod terminou com sucesso
  * Unknown (Desconhecido) - O estado do Pod não pôde ser obtido
  * Pending (Pendente) - Os contêineres ainda não estão em execução (Talvez as imagens ainda estejam sendo baixadas ou o pod ainda não foi agendado)
</b></details>

<details>
<summary>Verdadeiro ou Falso? Por padrão, os pods são isolados. Isso significa que eles não podem receber tráfego de nenhuma fonte</summary><br><b>

Falso. Por padrão, os pods não são isolados = os pods aceitam tráfego de qualquer fonte.
</b></details>

<details>
<summary>Verdadeiro ou Falso? A fase "Pendente" significa que o Pod ainda não foi aceito pelo cluster Kubernetes, então o agendador não pode executá-lo a menos que seja aceito</summary><br><b>

Falso. "Pendente" é depois que o Pod foi aceito pelo cluster, mas o contêiner não pode ser executado por diferentes razões, como imagens ainda não baixadas.
</b></details>

<details>
<summary>Verdadeiro ou Falso? Um único Pod pode ser dividido entre múltiplos nós</summary><br><b>

Falso. Um único Pod pode ser executado em um único nó.
</b></details>

<details>
<summary>Você executa um pod e vê o status `ContainerCreating`</summary><br><b>
</b></details>

<details>
<summary>Verdadeiro ou Falso? Um volume definido em um Pod pode ser acessado por todos os contêineres desse Pod</summary><br><b>

Verdadeiro.
</b></details>

<details>
<summary>O que acontece quando você executa um Pod com o kubectl?</summary><br><b>

1. O Kubectl envia uma requisição ao servidor da API (kube-apiserver) para criar o Pod
   1. No processo, o usuário é autenticado e a requisição é validada.
   2. O etcd é atualizado com os dados
2. O Scheduler detecta que há um Pod não atribuído monitorando o servidor da API (kube-apiserver)
3. O Scheduler escolhe um nó para atribuir o Pod
   1. O etcd é atualizado com a informação
4. O Scheduler atualiza o servidor da API sobre qual nó ele escolheu
5. O Kubelet (que também monitora o servidor da API) percebe que há um Pod atribuído ao mesmo nó em que ele é executado e que esse Pod não está em execução
6. O Kubelet envia uma requisição ao motor de contêiner (ex: Docker) para criar e executar os contêineres
7. Uma atualização é enviada pelo Kubelet ao servidor da API (notificando que o Pod está em execução)
   1. O etcd é atualizado pelo servidor da API novamente
</b></details>

<details>
<summary>Como confirmar que um contêiner está em execução após executar o comando `kubectl run web --image nginxinc/nginx-unprivileged`</summary><br><b>

* Quando você executa `kubectl describe pods <NOME_DO_POD>`, ele informará se o contêiner está em execução:
`Status:       Running`
* Execute um comando dentro do contêiner: `kubectl exec web -- ls`
</b></details>

<details>
<summary>Após executar `kubectl run database --image mongo`, você vê o status "CrashLoopBackOff". O que poderia ter dado errado e o que você faz para confirmar?</summary><br><b>

"CrashLoopBackOff" significa que o Pod está iniciando, travando, iniciando... e assim se repete.<br>
Existem muitas razões diferentes para obter este erro - falta de permissões, má configuração do contêiner de inicialização, problema de conexão com volume persistente, etc.

Uma das maneiras de verificar por que isso aconteceu é executar `kubectl describe po <NOME_DO_POD>` e observar o código de saída


Outra maneira de verificar o que está acontecendo é executar `kubectl logs <NOME_DO_POD>`. Isso nos fornecerá os logs dos contêineres em execução nesse Pod.
</b></details>

<details>
<summary>Explique o propósito das seguintes linhas

</summary><br><b>

Essas linhas fazem uso de uma `sonda de atividade` (liveness probe). Ela é usada para reiniciar um contêiner quando ele atinge um estado não desejado.<br>
Neste caso, se o comando `cat /appStatus` falhar, o Kubernetes matará o contêiner e aplicará a política de reinicialização. O `initialDelaySeconds: 10` significa que o Kubelet esperará 10 segundos antes de executar o comando/sonda pela primeira vez. A partir desse ponto, ele o executará a cada 5 segundos, conforme definido com `periodSeconds`.
</b></details>

<details>
<summary>Explique o propósito das seguintes linhas

</summary><br><b>

Elas definem uma sonda de prontidão (readiness probe) onde o Pod não será marcado como "Pronto" antes que seja possível conectar-se à porta 2017 do contêiner. A primeira verificação/sonda começará após 15 segundos a partir do momento em que o contêiner começou a ser executado e continuará a executar a verificação/sonda a cada 20 segundos até conseguir se conectar à porta definida.
</b></details>

<details>
<summary>O que significa o status "ErrImagePull" de um Pod?</summary><br><b>

Não foi possível baixar a imagem especificada para executar o(s) contêiner(es). Isso pode acontecer se o cliente não se autenticou, por exemplo.<br>
Mais detalhes podem ser obtidos com `kubectl describe po <NOME_DO_POD>`.
</b></details>

<details>
<summary>O que acontece quando você deleta um Pod?</summary><br><b>

1. O sinal `TERM` é enviado para matar os processos principais dentro dos contêineres do Pod em questão
2. Cada contêiner recebe um período de 30 segundos para encerrar os processos de forma graciosa
3. Se o período de carência expirar, o sinal `KILL` é usado para matar os processos à força e os contêineres também
</b></details>

<details>
<summary>Explique as sondas de atividade (liveness probes)</summary><br><b>

Sondas de atividade são um mecanismo útil usado para reiniciar o contêiner quando uma certa verificação/sonda, que o usuário definiu, falha.<br>
Por exemplo, o usuário pode definir que o comando `cat /app/status` será executado a cada X segundos e no momento em que este comando falhar, o contêiner será reiniciado.

Você pode ler mais sobre isso em kubernetes.io
</b></details>

<details>
<summary>Explique as sondas de prontidão (readiness probes)</summary><br><b>

sondas de prontidão são usadas pelo Kubelet para saber quando um contêiner está pronto para começar a ser executado, aceitando tráfego.<br>
Por exemplo, uma sonda de prontidão pode ser conectar-se à porta 8080 em um contêiner. Assim que o Kubelet consegue se conectar, o Pod é marcado como pronto.

Você pode ler mais sobre isso em kubernetes.io
</b></details>

<details>
<summary>Como o status da sonda de prontidão afeta os Serviços quando eles são combinados?</summary><br><b>

Apenas contêineres cujo estado está definido como Sucesso poderão receber requisições enviadas ao Serviço.
</b></details>

<details>
<summary>Por que é comum ter apenas um contêiner por Pod na maioria dos casos?</summary><br><b>

Uma razão é que torna mais difícil escalar quando você precisa escalar apenas um dos contêineres em um determinado Pod.
</b></details>

<details>
<summary>Verdadeiro ou Falso? Uma vez que um Pod é atribuído a um nó de trabalho, ele só será executado naquele nó, mesmo que falhe em algum momento e inicie um novo Pod</summary><br><b>

Verdadeiro.
</b></details>

<details>
<summary>Verdadeiro ou Falso? Cada Pod, quando criado, recebe seu próprio endereço IP público</summary><br><b>

Falso. Cada Pod recebe um endereço IP, mas um interno e não acessível publicamente.

Para tornar um Pod acessível externamente, precisamos usar um objeto chamado Serviço no Kubernetes.
</b></details>

#### Pods Estáticos

<details>
<summary>O que são Pods Estáticos?</summary><br><b>

Kubernetes.io: "Pods Estáticos são gerenciados diretamente pelo daemon kubelet em um nó específico, sem que o servidor da API os observe. Ao contrário dos Pods que são gerenciados pelo plano de controle (por exemplo, um Deployment); em vez disso, o kubelet observa cada Pod estático (e o reinicia se ele falhar)."
</b></details>

<details>
<summary>Verdadeiro ou Falso? Assim como existem "Pods Estáticos", existem outros recursos estáticos como "deployments" e "replicasets"</summary><br><b>

Falso.
</b></details>

<details>
<summary>Quais são alguns casos de uso para usar Pods Estáticos?</summary><br><b>

Um caso de uso claro é a execução de Pods do Plano de Controle - executando Pods como kube-apiserver, scheduler, etc. Estes devem ser executados e operar independentemente de alguns componentes do cluster funcionarem ou não e devem ser executados em nós específicos do cluster.
</b></details>

<details>
<summary>Como identificar quais Pods são Pods Estáticos?</summary><br><b>

O sufixo dos Pods é o mesmo que o nome dos nós em que estão sendo executados.
TODO: verificar se isso é sempre o caso.
</b></details>

<details>
<summary>Qual dos seguintes não é um pod estático?:

* kube-scheduler
* kube-proxy
* kube-apiserver
</summary><br><b>

kube-proxy - é um DaemonSet (já que precisa estar presente em todos os nós do cluster). Não há um nó específico no qual ele precise ser executado.
</b></details>

<details>
<summary>Onde os manifestos dos Pods estáticos estão localizados?</summary><br><b>

Na maioria das vezes, está em /etc/kubernetes/manifests, mas você pode verificar com `grep -i static /var/lib/kubelet/config.yaml` para localizar o valor de `statisPodsPath`.

Pode ser que sua configuração esteja em um caminho diferente. Para verificar, execute `ps -ef | grep kubelet` e veja qual é o valor do argumento --config do processo `/usr/bin/kubelet`.

A chave em si para definir o caminho dos Pods estáticos é `staticPodPath`. Portanto, se sua configuração estiver em `/var/lib/kubelet/config.yaml`, você pode executar `grep staticPodPath /var/lib/kubelet/config.yaml`.
</b></details>

<details>
<summary>Descreva como você deletaria um Pod estático
</summary><br><b>

Localize o diretório de Pods estáticos (procure por `staticPodPath` no arquivo de configuração do kubelet).

Vá para esse diretório e remova o manifesto/definição do Pod estático (`rm <CAMINHO_DO_POD_ESTÁTICO>/<ARQUIVO_DE_DEFINIÇÃO_DO_POD>`)
</b></details>

#### Comandos de Pods

<details>
<summary>Como verificar em qual nó de trabalho os pods foram agendados? Em outras palavras, como verificar em qual nó um determinado Pod está sendo executado?</summary><br><b>

`kubectl get pods -o wide`
</b></details>

<details>
<summary>Como deletar um pod?</summary><br><b>

`kubectl delete pod nome_do_pod`
</b></details>

<details>
<summary>Liste todos os pods com o rótulo "env=prod"</summary><br><b>

`k get po -l env=prod`

Para contá-los: `k get po -l env=prod --no-headers | wc -l`
</b></details>

<details>
<summary>Como listar os pods no namespace atual?</summary><br><b>

`kubectl get po`
</b></details>

<details>
<summary>Como visualizar todos os pods em execução em todos os namespaces?</summary><br><b>

`kubectl get pods --all-namespaces`
</b></details>

#### Solução de Problemas e Depuração de Pods

<details>
<summary>Você tenta executar um Pod, mas ele está no estado "Pendente". Qual pode ser o motivo?</summary><br><b>

Um motivo possível é que o agendador, que deveria agendar Pods nos nós, não está em execução. Para verificar, você pode executar `kubectl get po -A | grep scheduler` ou verificar diretamente no namespace `kube-system`.
</b></details>

<details>
<summary>O que o comando `kubectl logs [nome-do-pod]` faz?</summary><br><b>

Imprime os logs de um contêiner em um pod.
</b></details>

<details>
<summary>O que o comando `kubectl describe pod [nome do pod]` faz?</summary><br><b>

Mostra detalhes de um recurso específico ou grupo de recursos.
</b></details>

<details>
<summary>Crie um pod estático com a imagem `python` que executa o comando `sleep 2017`</summary><br><b>

Primeiro, mude para o diretório rastreado pelo kubelet para criar um pod estático: `cd /etc/kubernetes/manifests` (você pode verificar o caminho lendo o arquivo de configuração do kubelet)

Agora crie a definição/manifesto nesse diretório
`k run some-pod --image=python --command sleep 2017 --restart=Never --dry-run=client -o yaml > static-pod.yaml`
</b></details>

### Rótulos e Seletores

<details>
<summary>Explique Rótulos</summary><br><b>

Kubernetes.io: "Rótulos são pares de chave/valor que são anexados a objetos, como pods. Os rótulos destinam-se a ser usados para especificar atributos de identificação de objetos que são significativos e relevantes para os usuários, mas não implicam diretamente semântica para o sistema principal. Os rótulos podem ser usados para organizar e selecionar subconjuntos de objetos. Os rótulos podem ser anexados a objetos no momento da criação e subsequentemente adicionados e modificados a qualquer momento. Cada objeto pode ter um conjunto de rótulos de chave/valor definido. Cada chave deve ser única para um determinado objeto."
</b></details>

<details>
<summary>Explique seletores</summary><br><b>

Kubernetes.io: "Ao contrário de nomes e UIDs, os rótulos não fornecem exclusividade. Em geral, esperamos que muitos objetos carreguem o(s) mesmo(s) rótulo(s).

Através de um seletor de rótulo, o cliente/usuário pode identificar um conjunto de objetos. O seletor de rótulo é a primitiva de agrupamento principal no Kubernetes.

A API atualmente suporta dois tipos de seletores: baseados em igualdade e baseados em conjunto. Um seletor de rótulo pode ser composto por múltiplos requisitos que são separados por vírgulas. No caso de múltiplos requisitos, todos devem ser satisfeitos, de modo que o separador de vírgula atua como um operador lógico E (&&)."
</b></details>

<details>
<summary>Forneça alguns exemplos reais de como os rótulos são usados</summary><br><b>

* Podem ser usados pelo agendador para colocar certos Pods (com certos rótulos) em nós específicos
* Usados por replicasets para rastrear pods que precisam ser escalados
</b></details>

<details>
<summary>O que são Anotações?</summary><br><b>

Kubernetes.io: "Você pode usar anotações do Kubernetes para anexar metadados arbitrários não identificadores a objetos. Clientes como ferramentas e bibliotecas podem recuperar esses metadados."
</b></details>

<details>
<summary>Como as anotações são diferentes dos rótulos?</summary><br><b>

Kuberenets.io: "Os rótulos podem ser usados para selecionar objetos e encontrar coleções de objetos que satisfazem certas condições. Em contraste, as anotações não são usadas para identificar e selecionar objetos. Os metadados em uma anotação podem ser pequenos ou grandes, estruturados ou não estruturados, e podem incluir caracteres não permitidos por rótulos."
</b></details>

<details>
<summary>Como visualizar os logs de um contêiner em execução em um Pod?</summary><br><b>

`k logs NOME_DO_POD`
</b></details>

<details>
<summary>Existem dois contêineres dentro de um Pod chamado "some-pod". O que acontecerá se você executar `kubectl logs some-pod`</summary><br><b>

Não funcionará porque existem dois contêineres dentro do Pod e você precisa especificar um deles com `kubectl logs NOME_DO_POD -c NOME_DO_CONTÊINER`
</b></details>

### Deployments

<details>
<summary>O que é um "Deployment" no Kubernetes?</summary><br><b>

Um Deployment do Kubernetes é usado para dizer ao Kubernetes como criar ou modificar instâncias dos pods que contêm uma aplicação em contêiner.
Os Deployments podem escalar o número de pods de réplica, permitir o lançamento de código atualizado de maneira controlada ou reverter para uma versão de implantação anterior, se necessário.

Um Deployment é uma declaração declarativa para o estado desejado para Pods e Replica Sets.
</b></details>

<details>
<summary>Como criar um deployment com a imagem "nginx:alpine"?</code></summary><br><b>

`kubectl create deployment my-first-deployment --image=nginx:alpine`

OU

</b></details>

<details>
<summary>Como verificar se um deployment foi criado?</code></summary><br><b>

`kubectl get deployments` ou `kubectl get deploy`

Este comando lista todos os objetos Deployment criados e existentes no cluster. Isso não significa que os deployments estão prontos e em execução. Isso pode ser verificado com as colunas "READY" e "AVAILABLE".
</b></details>

<details>
<summary>Como editar um deployment?</code></summary><br><b>

`kubectl edit deployment <NOME_DO_DEPLOYMENT>`
</b></details>

<details>
<summary>O que acontece depois que você edita um deployment e altera a imagem?</summary><br><b>

O pod será encerrado e outro, novo pod, será criado.

Além disso, ao olhar para o replicaset, você verá que a réplica antiga não tem nenhum pod e um novo replicaset é criado.
</b></details>

<details>
<summary>Como deletar um deployment?</summary><br><b>

Uma maneira é especificando o nome do deployment: `kubectl delete deployment [nome_do_deployment]`

Outra maneira é usando o arquivo de configuração do deployment: `kubectl delete -f deployment.yaml`
</b></details>

<details>
<summary>O que acontece quando você deleta um deployment?</summary><br><b>

O pod relacionado ao deployment será encerrado e o replicaset será removido.
</b></details>

<details>
<summary>O que acontece nos bastidores quando você cria um objeto Deployment?</summary><br><b>

O seguinte ocorre quando você executa `kubectl create deployment some_deployment --image=nginx`

1. Requisição HTTP enviada ao servidor da API do Kubernetes no cluster para criar um novo deployment
2. Um novo objeto Pod é criado e agendado para um dos nós de trabalho
3. O Kubelet no nó de trabalho percebe o novo Pod e instrui o motor de tempo de execução do contêiner a baixar a imagem do registro
4. Um novo contêiner é criado usando a imagem que acabou de ser baixada
</b></details>

<details>
<summary>Como tornar uma aplicação acessível em uma rede privada ou externa?</summary><br><b>

Usando um Serviço.
</b></details>

<details>
<summary>Você pode usar um Deployment para aplicações com estado (stateful)?</summary><br><b>
</b></details>

<details>
<summary>Corrija o seguinte manifesto de deployment

```yaml
apiVersion: apps/v1
kind: Deploy
metadata:
  creationTimestamp: null
  labels:
    app: dep
  name: dep
spec:
  replicas: 3
  selector:
    matchLabels:
      app: dep
  strategy: {}
  template:
    metadata:
      creationTimestamp: null
      labels:
        app: dep
    spec:
      containers:
      - image: redis
        name: redis
        resources: {}
status: {}

Mude kind: Deploy para kind: Deployment

```bash
apiVersion: apps/v1
kind: Deployment
metadata:
  creationTimestamp: null
  labels:
    app: dep
  name: dep
spec:
  replicas: 3
  selector:
    matchLabels:
      app: depdep
  strategy: {}
  template:
    metadata:
      creationTimestamp: null
      labels:
        app: dep
    spec:
      containers:
      - image: redis
        name: redis
        resources: {}
status: {}
```

O seletor não corresponde ao rótulo (dep vs depdep). Para resolver isso, corrija depdep para que seja dep.

## Comandos de Deployments
k create deploy dep -o yaml --image=redis --dry-run=client --replicas 3 > deployment.yaml

k delete deploy depdep

kubectl create deployment pluck --image=redis --replicas=5

-chamado "blufer"
-usando a imagem "python"
-executa 3 réplicas
-todos os pods serão colocados em um nó que tenha o rótulo "blufer"
kubectl create deployment blufer --image=python --replicas=3 -o yaml --dry-run=client > deployment.yaml

Adicione a seguinte seção (vi deployment.yaml):

```bash
spec:
  affinity:
    nodeAffinity:
      requiredDuringSchedlingIgnoredDuringExecution:
        nodeSelectorTerms:
        - matchExpressions:
          - key: blufer
            operator: Exists
```

kubectl apply -f deployment.yaml

Services
"Uma maneira abstrata de expor uma aplicação em execução em um conjunto de Pods como um serviço de rede." - leia mais aqui

Em palavras mais simples, permite adicionar conectividade interna ou externa a uma determinada aplicação em execução em um contêiner.

A maneira imperativa:

kubectl expose deployment alle --type=LoadBalancer --port 8080

Verdadeiro

kubectl get svc

ClusterIP - usado para comunicação interna.

ClusterIP
NodePort
LoadBalancer
ExternalName
Mais sobre este tópico aqui

A verdade é que eles não estão conectados. O Serviço aponta diretamente para o(s) Pod(s), sem se conectar ao Deployment de forma alguma.

Garantir que a targetPort do Serviço corresponda à containerPort do Pod
Garantir que o seletor corresponda a pelo menos um dos rótulos do Pod
O padrão é ClusterIP e é usado para expor uma porta internamente. É útil quando você deseja habilitar a comunicação interna entre Pods e impedir qualquer acesso externo.

kubctl describe service <NOME_DO_SERVIÇO>

É mais comum usar kubectl describe svc ...

```bash
kubectl expose rs some-replicaset --name=replicaset-svc --target-port=2017 --type=NodePort
```

Ele expõe um ReplicaSet criando um serviço chamado 'replicaset-svc'. A porta exposta é 2017 (esta é a porta usada pela aplicação) e o tipo de serviço é NodePort, o que significa que será alcançável externamente.

```bash
kubectl expose rs some-replicaset --name=replicaset-svc --target-port=2017 --type=NodePort
```

Falso. Será exposta em todos os nós do cluster e será roteada para um dos Pods (que pertencem ao ReplicaSet)

Execute kubectl describe service e veja se os IPs de "Endpoints" correspondem a algum IP da saída de kubectl get pod -o wide

```bash
apiVersion: v1
kind: Service
metadata:
  name: some-app
spec:
  type: NodePort
  ports:
  - port: 8080
    nodePort: 2017
    protocol: TCP
  selector:
    type: backend
    service: some-app
```
Ele cria um novo Serviço do tipo "NodePort", o que significa que pode ser usado para comunicação interna e externa com a aplicação. A porta da aplicação é 8080 e as requisições serão encaminhadas para esta porta. A porta exposta é 2017. Como nota, esta não é uma prática comum, especificar a nodePort. A porta usa TCP (em vez de UDP) e este também é o padrão, então você não precisa especificá-lo. O seletor é usado pelo Serviço para saber para quais Pods encaminhar as requisições. Neste caso, Pods com o rótulo "type: backend" e "service: some-app".

```bash
spec:
  selector:
    app: some-app
  ports:
    - protocol: TCP
      port: 8081
      targetPort: 8081
```
Adicionando type: LoadBalancer e nodePort

```bash
spec:
  selector:
    app: some-app
  type: LoadBalancer
  ports:
    - protocol: TCP
      port: 8081
      targetPort: 8081
      nodePort: 32412
```

Ingress

Verdadeiro

Principalmente quando você gostaria de combiná-lo com o balanceador de carga de um provedor de nuvem

Usando a diretiva 'ExternalName'.

O Kubectl envia uma requisição ao servidor da API para criar um Serviço
O controlador detecta que há um novo Serviço
Objetos de Endpoint são criados com o mesmo nome do serviço, pelo controlador
O controlador usa o seletor do Serviço para identificar os endpoints
O kube-proxy detecta que há um novo objeto de endpoint + novo serviço e adiciona regras de iptables para capturar o tráfego para a porta do Serviço e redirecioná-lo para os endpoints
O kube-dns detecta que há um novo Serviço e adiciona o registro do contêiner ao servidor dns
kubectl get ep <nome>

Você pode executar kubectl exec <NOME_DO_POD> -- env que lhe dará algumas variáveis de ambiente relacionadas ao Serviço. Variáveis como [NOME_DO_SERVIÇO]_SERVICE_HOST, [NOME_DO_SERVIÇO]_SERVICE_PORT, ...

O contêiner olha para o nameserver definido em /etc/resolv.conf
O contêiner consulta o nameserver para que o endereço seja resolvido para o IP do Serviço
Requisições enviadas para o IP do Serviço são encaminhadas com regras de iptables (ou outro software escolhido) para o(s) endpoint(s).
Explicação de quem os adicionou:

O nameserver no contêiner é adicionado pelo kubelet durante o agendamento do Pod, usando o kube-dns
O registro DNS do serviço é adicionado pelo kube-dns durante a criação do Serviço
As regras de iptables são adicionadas pelo kube-proxy durante a criação do Endpoint e do Serviço
O Kubectl envia uma requisição à API do Kubernetes para criar um objeto de Serviço
O Kubernetes solicita ao provedor de nuvem (ex: AWS, GCP, Azure) para provisionar um balanceador de carga
O balanceador de carga recém-criado encaminha o tráfego de entrada para o(s) nó(s) de trabalho relevante(s) que encaminha(m) o tráfego para os contêineres relevantes
Você pode executar curl <IP_DO_SERVIÇO>:<PORTA_DO_SERVIÇO> para examinar a saída.

Um balanceador de carga interno no Kubernetes é chamado de Serviço e um balanceador de carga externo é Ingress

Ingress
Dos documentos do Kubernetes: "O Ingress expõe rotas HTTP e HTTPS de fora do cluster para serviços dentro do cluster. O roteamento de tráfego é controlado por regras definidas no recurso Ingress."

Leia mais aqui
```bash
metadata:
  name: someapp-ingress
spec:
```
```bash
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: someapp-ingress
spec:
  rules:
  - host: my.host
    http:
      paths:
      - backend:
          serviceName: someapp-internal-service
          servicePort: 8080
```
```bash
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: someapp-ingress
spec:
  rules:
  - host: my.host
    http:
      paths:
      - backend:
          serviceName: someapp-internal-service
          servicePort: 8080
```

host é o ponto de entrada do cluster, então basicamente um endereço de domínio válido que mapeia para o endereço IP do nó do cluster a linha http é usada para especificar que as requisições de entrada serão encaminhadas para o serviço interno usando http. backend está referenciando o serviço interno (serviceName é o nome sob metadata e servicePort é a porta sob a seção de portas).

A razão pela qual você não deve usar um valor curinga em um host (como - host: *) é porque você basicamente diz ao seu cluster Kubernetes para encaminhar todo o tráfego para o contêiner onde você usou este ingress. Isso pode fazer com que todo o cluster caia.

Uma implementação para o Ingress. É basicamente outro pod (ou conjunto de pods) que avalia e processa as regras do Ingress e, assim, gerencia todos os redirecionamentos.

Existem várias implementações de Ingress Controller (a do Kubernetes é o Kubernetes Nginx Ingress Controller).

Múltiplos subdomínios (múltiplas entradas de host, cada uma com seu próprio serviço)
Um domínio com múltiplos serviços (múltiplos caminhos onde cada um é mapeado para um serviço/aplicação diferente)
kubectl get ingress

Ele especifica o que fazer com uma requisição de entrada para o cluster Kubernetes que não está mapeada para nenhum backend (= nenhuma regra para mapear a requisição para um serviço). Se o serviço de backend padrão não for definido, é recomendado definir um para que os usuários ainda vejam algum tipo de mensagem em vez de nada ou um erro pouco claro.

Crie um recurso de Serviço que especifique o nome do backend padrão, conforme refletido em kubectl describe ingress ... e a porta na seção de portas.

Adicione as entradas tls e secretName.

```bash
spec:
  tls:
  - hosts:
    - some_app.com
    secretName: someapp-secret-tls
```

Verdadeiro

Políticas de Rede

Para executar duas instâncias da aplicação?

kubectl scale deployment <NOME_DO_DEPLOYMENT> --replicas=2

Você pode especificar qualquer outro número, desde que sua aplicação saiba como escalar.

ReplicaSets
kubernetes.io: "O propósito de um ReplicaSet é manter um conjunto estável de Pods de réplica em execução a qualquer momento. Como tal, é frequentemente usado para garantir a disponibilidade de um número especificado de Pods idênticos."

Em palavras mais simples, um ReplicaSet garantirá que o número especificado de réplicas de Pods esteja em execução para um Pod selecionado. Se houver mais Pods do que o definido no ReplicaSet, alguns serão removidos. Se houver menos do que o definido no ReplicaSet, mais réplicas serão adicionadas.

```bash
spec:
  replicas: 2
  selector:
    matchLabels:
      type: backend
  template:
    metadata:
      labels:
        type: backend
    spec:
      containers:
      - name: httpd-yup
        image: httpd
```

Ele define um replicaset para Pods cujo tipo está definido como "backend", de modo que a qualquer momento haverá 2 Pods concorrentes em execução.

O ReplicaSet criará um novo Pod para atingir o número desejado de réplicas.

Falso. Ele encerrará um dos Pods para atingir o estado desejado de 2 réplicas.

O cliente (ex: kubectl) envia uma requisição ao servidor da API para criar um ReplicaSet
O Controlador detecta que há um novo evento solicitando um ReplicaSet
O controlador cria novas definições de Pod (o número exato depende do que está definido na definição do ReplicaSet)
O agendador detecta Pods não atribuídos e decide para quais nós atribuir os Pods. Esta informação é enviada para o servidor da API
O Kubelet detecta que dois Pods foram atribuídos ao nó em que está sendo executado (pois está constantemente observando o servidor da API)
O Kubelet envia requisições ao motor de contêiner, para criar os contêineres que fazem parte do Pod
O Kubelet envia uma requisição ao servidor da API para notificá-lo de que os Pods foram criados
kubectl get rs

Sim, com --cascade=false.

kubectl delete -f rs.yaml --cascade=false

1

NOME DESEJADO ATUAL PRONTO IDADE web 2 2 0 2m23s

O replicaset web tem 2 réplicas. Parece que os contêineres dentro do(s) Pod(s) ainda não estão em execução, pois o valor de PRONTO é 0. Isso pode ser normal, pois leva tempo para alguns contêineres iniciarem e pode ser devido a um erro. Executar kubectl describe po NOME_DO_POD ou kubectl logs NOME_DO_POD pode nos dar mais informações.

Falso. Os Pods podem já estar em execução e inicialmente podem ser criados por qualquer objeto. Isso não importa para o ReplicaSet e não é um requisito para ele adquiri-los e monitorá-los.

Falso. Ele cuidará de executar os Pods ausentes.

O campo template na seção spec é obrigatório. Ele é usado pelo ReplicaSet para criar novos Pods quando necessário.

kubectl describe rs <Nome do ReplicaSet>

Isso será visível em Events (as últimas linhas)

Verdadeiro (e não apenas os Pods, mas qualquer outra coisa que ele criou).

Verdadeiro. Quando o rótulo, usado por um ReplicaSet no campo seletor, é removido de um Pod, esse Pod não é mais controlado pelo ReplicaSet e o ReplicaSet criará um novo Pod para compensar o que "perdeu".

kubectl scale deploy <NOME_DO_DEPLOYMENT> --replicas=8

Falso. Pode levar algum tempo, dependendo do que exatamente você está executando. Para ver se eles estão em funcionamento, execute kubectl get rs e observe a coluna 'READY'.

kubectl expose rs <Nome do ReplicaSet> --name=<Nome do Serviço> --target-port=<Porta a ser exposta> --type=NodePort

Algumas notas:

a porta de destino depende de qual porta a aplicação está usando no contêiner
o tipo pode ser diferente e não precisa ser especificamente "NodePort"

```bash
apiVersion: apps/v1
kind: ReplicaCet
metadata:
  name: redis
  labels:
    app: redis
    tier: cache
spec:
  selector:
    matchLabels:
      tier: cache
  template:
    metadata:
      labels:
        tier: cachy
    spec:
      containers:
      - name: redis
        image: redis
```

kind deve ser ReplicaSet e não ReplicaCet :)

```bash
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: redis
  labels:
    app: redis
    tier: cache
spec:
  selector:
    matchLabels:
      tier: cache
  template:
    metadata:
      labels:
        tier: cachy
    spec:
      containers:
      - name: redis
        image: redis
```
O seletor não corresponde ao rótulo (cache vs cachy). Para resolver isso, corrija cachy para que seja cache.

k describe rs repli | grep -i image

k describe rs repli | grep -i "Pods Status"

k delete rs rori

k edit rs rori

k scale rs rori --replicas=5

k scale rs rori --replicas=1

DaemonSet
Kubernetes.io: "Um DaemonSet garante que todos (ou alguns) Nós executem uma cópia de um Pod. À medida que os nós são adicionados ao cluster, os Pods são adicionados a eles. À medida que os nós são removidos do cluster, esses Pods são coletados como lixo. Deletar um DaemonSet limpará os Pods que ele criou."

O propósito de um ReplicaSet é manter um conjunto estável de Pods de réplica em execução a qualquer momento. Um DaemonSet garante que todos os Nós executem uma cópia de um Pod.

Monitoramento: Você gostaria de realizar monitoramento em todos os nós que fazem parte do cluster. Por exemplo, o pod do datadog é executado em todos os nós usando um daemonset
Logging: Você gostaria de ter o logging configurado em todos os nós que fazem parte do seu cluster
Rede: há um componente de rede que você precisa em todos os nós para que todos os nós se comuniquem entre si
Historicamente, até a versão 1.12, era feito com o atributo NodeName.

A partir da versão 1.12, é alcançado com o agendador regular e afinidade de nó.

DaemonSet - Comandos
kubectl get ds

StatefulSet
StatefulSet é o objeto da API de carga de trabalho usado para gerenciar aplicações com estado. Gerencia a implantação e o escalonamento de um conjunto de Pods e fornece garantias sobre a ordenação e a exclusividade desses Pods.Saiba mais

Armazenamento
Volumes
Um diretório acessível pelos contêineres dentro de um determinado Pod e contêineres. O mecanismo responsável por criar o diretório, gerenciá-lo, ... depende principalmente do tipo de volume.

emptyDir: criado quando um Pod é atribuído a um nó e deixa de existir quando o Pod não está mais em execução nesse nó
hostPath: monta um caminho do próprio host. Geralmente não é usado devido a riscos de segurança, mas tem vários casos de uso onde é necessário, como acesso a alguns caminhos internos do host (/sys, /var/lib, etc.)
Compartilhamento de arquivos entre contêineres em execução no mesmo Pod
O armazenamento em contêineres é efêmero - geralmente não dura muito. Por exemplo, quando um contêiner trava, você perde todos os dados no disco. Certos volumes permitem gerenciar tal situação por meio de volumes persistentes
Os tipos de volume efêmeros têm o tempo de vida de um pod, em oposição aos volumes persistentes que existem além do tempo de vida de um Pod.

emptyDir
hostPath
EmptyDir: Você precisa de dados temporários que pode se dar ao luxo de perder se o Pod for excluído. Por exemplo, dados de curta duração necessários para operações únicas.
hostPath: Você precisa de acesso a caminhos no próprio host (como dados de /sys ou dados gerados em /var/lib)
Rede
Falso. Por padrão, dois Pods em dois namespaces diferentes podem se comunicar um com o outro.

Tente você mesmo:

kubectl run test-prod -n prod --image ubuntu -- sleep 2000000000 kubectl run test-dev -n dev --image ubuntu -- sleep 2000000000

k describe po test-prod -n prod para obter o IP do Pod test-prod.

Acesse o Pod dev: kubectl exec --stdin --tty test-dev -n dev -- /bin/bash

E faça ping no IP do Pod test-prod que você obteve anteriormente. Você verá que há comunicação entre os dois pods, em dois namespaces separados.

Políticas de Rede
kubernetes.io: "NetworkPolicies são uma construção centrada na aplicação que permite especificar como um pod pode se comunicar com várias "entidades" de rede..."

Em palavras mais simples, as Políticas de Rede especificam como os pods podem/não podem se comunicar entre si e/ou com outros endpoints de rede.

Segurança: Você quer impedir que todos se comuniquem com um certo pod por razões de segurança
Controle de tráfego de rede: Você gostaria de negar o fluxo de rede entre dois nós específicos
Falso. Por padrão, os pods não são isolados.

Negado. Ambas as políticas de origem e destino precisam permitir o tráfego para que ele seja permitido.

etcd

etcd
etcd é um armazenamento de chave-valor distribuído de código aberto usado para manter e gerenciar as informações críticas que os sistemas distribuídos precisam para continuar funcionando.

Leia mais aqui

Verdadeiro

Verdadeiro

Verdadeiro

Quando escolhido como o armazenamento de dados, o etcd era (e ainda é, claro):

Altamente Disponível - você pode implantar múltiplos nós
Totalmente Replicado - qualquer nó no cluster etcd é um nó "primário" e tem acesso total aos dados
Consistente - as leituras retornam os dados mais recentes
Seguro - suporta tanto TLS quanto SSL
Velocidade - armazenamento de dados de alto desempenho (10k escritas por segundo!)
Namespaces
Namespaces permitem que você divida seu cluster em clusters virtuais onde você pode agrupar suas aplicações de uma forma que faça sentido e seja completamente separada dos outros grupos (para que você possa, por exemplo, criar uma aplicação com o mesmo nome em dois namespaces diferentes)

Ao usar apenas o namespace padrão, torna-se difícil com o tempo ter uma visão geral de todas as aplicações que você gerencia em seu cluster. Os namespaces facilitam a organização das aplicações em grupos que fazem sentido, como um namespace para todas as aplicações de monitoramento e um namespace para todas as aplicações de segurança, etc.

Os namespaces também podem ser úteis para gerenciar ambientes Azul/Verde, onde cada namespace pode incluir uma versão diferente de uma aplicação e também compartilhar recursos que estão em outros namespaces (namespaces como logging, monitoramento, etc.).

Outro caso de uso para namespaces é um cluster, várias equipes. Quando várias equipes usam o mesmo cluster, elas podem acabar pisando nos calos umas das outras. Por exemplo, se elas acabarem criando uma aplicação com o mesmo nome, isso significa que uma das equipes sobrescreveu a aplicação da outra equipe, porque não pode haver duas aplicações no Kubernetes com o mesmo nome (no mesmo namespace).

Falso. Quando um namespace é deletado, os recursos nesse namespace também são deletados.

default
kube-system
kube-public
kube-node-lease
Processos do Mestre e do Kubectl
Processos do sistema
Verdadeiro. Tente criar dois pods em dois namespaces separados, por exemplo, e você verá que há uma conexão entre os dois.

Namespaces - comandos
kubectl get namespaces OU kubectl get ns

k create ns alle

k get ns --no-headers | wc -l

k get po -n dev

Se o namespace ainda não existir: k create ns dev

k run kratos --image=redis -n dev

k get po -A | grep atreus

Um configmap, que contém informações do cluster
Dados acessíveis publicamente
kubectl config view | grep namespace

Ele contém informações sobre os heartbeats dos nós. Cada nó recebe um objeto que contém informações sobre sua disponibilidade.

Verdadeiro. Com namespaces você pode limitar o uso de CPU, RAM e armazenamento.

kubectl config set-context --current --namespace=some-namespace e valide com kubectl config view --minify | grep namespace:

OU

kubens some-namespace

Cota de Recursos
A cota de recursos fornece restrições que limitam o consumo agregado de recursos por namespace. Ela pode limitar a quantidade de objetos que podem ser criados em um namespace por tipo, bem como a quantidade total de recursos de computação que podem ser consumidos por recursos nesse namespace.

kubectl create quota some-quota --hard-cpu=2,pods=2

Serviços.

```bash
apiVersion: v1
kind: ConfigMap
metadata:
  name: some-configmap
data:
  some_url: samurai.jack
```
Está referenciando o serviço "samurai" no namespace chamado "jack".

Volume e Nó.

kubectl api-resources --namespaced=true

Uma maneira é especificando --namespace assim: kubectl apply -f my_component.yaml --namespace=some-namespace Outra maneira é especificando no próprio YAML:

```bash
apiVersion: v1
kind: ConfigMap
metadata:
  name: some-configmap
  namespace: some-namespace
```
e você pode verificar com: kubectl get configmap -n some-namespace

kubectl exec some-pod -it -- ls

kubectl expose deploy some-deployment --port=80 --target-port=8080

kubectl run nginx --image=nginx --restart=Never --port 80 --expose

kubectl api-resources --namespaced=false

kubectl delete pods --field-selector=status.phase!='Running'

kubectl top pod

Comece inspecionando o status dos pods. podemos usar o comando kubectl get pods (--all-namespaces para pods no namespace do sistema)

Se virmos o status "Error", podemos continuar a depuração executando o comando kubectl describe pod [nome]. Caso ainda não vejamos nada útil, podemos tentar o stern para acompanhar os logs.

Caso descubramos que houve um problema temporário com o pod ou o sistema, podemos tentar reiniciar o pod com o seguinte kubectl scale deployment [nome] --replicas=0

Definir as réplicas para 0 irá desligar o processo. Agora inicie-o com kubectl scale deployment [nome] --replicas=1

Eles se tornam candidatos à terminação.

Falso. A CPU é um recurso compressível, enquanto a memória é um recurso não compressível - uma vez que um contêiner atinge o limite de memória, ele será encerrado.

Operators
Explicado aqui

"Operators são extensões de software para o Kubernetes que fazem uso de recursos personalizados para gerenciar aplicações e seus componentes. Os Operators seguem os princípios do Kubernetes, notadamente o ciclo de controle."

Em palavras mais simples, você pode pensar em um operator como um ciclo de controle personalizado no Kubernetes.

O processo de gerenciamento de aplicações com estado (stateful) no Kubernetes não é tão direto quanto o gerenciamento de aplicações sem estado (stateless), onde atingir o status desejado e as atualizações são tratadas da mesma forma para cada réplica. Em aplicações com estado, a atualização de cada réplica pode exigir um tratamento diferente devido à natureza com estado da aplicação, cada réplica pode estar em um status diferente. Como resultado, muitas vezes precisamos de um operador humano para gerenciar aplicações com estado. O Kubernetes Operator deve ajudar com isso.

Isso também ajuda a automatizar um processo padrão em múltiplos clusters Kubernetes.

CRD (Custom Resource Definition) - Você está familiarizado com recursos do Kubernetes como Deployment, Pod, Service, etc. CRD também é um recurso, mas um que você ou o desenvolvedor do operator define.
Controller - Ciclo de controle personalizado que é executado contra o CRD
CRD é Custom Resource Definitions (Definições de Recursos Personalizados). É um componente personalizado do Kubernetes que estende a API do K8s.

TODO(abregman): adicionar mais informações.

Ele usa o ciclo de controle usado pelo Kubernetes em geral. Ele observa as mudanças no estado da aplicação. A diferença é que ele usa um ciclo de controle personalizado.

Além disso, ele também faz uso de CRDs (Custom Resources Definitions), então basicamente ele estende a API do Kubernetes.

Verdadeiro

kit de ferramentas de código aberto usado para gerenciar aplicações nativas do k8s, chamadas operators, de maneira automatizada e eficiente.

Operator SDK - permite que os desenvolvedores construam operators
Operator Lifecycle Manager - ajuda a instalar, atualizar e gerenciar geralmente o ciclo de vida de todos os operators
Operator Metering - Permite o relatório de uso para operators que fornecem serviços especializados
É parte do Operator Framework, usado para gerenciar o ciclo de vida dos operators. Basicamente, ele estende o Kubernetes para que um usuário possa usar uma maneira declarativa de gerenciar operators (instalação, atualização, ...).

Ele inclui:

catalog-operator - Resolvendo e instalando ClusterServiceVersions, o recurso que eles especificam.
olm-operator - Implanta aplicações definidas pelo recurso ClusterServiceVersion
Um arquivo kubeconfig é um arquivo usado para configurar o acesso ao Kubernetes quando usado em conjunto com a ferramenta de linha de comando kubectl (ou outros clientes). Use arquivos kubeconfig para organizar informações sobre clusters, usuários, namespaces e mecanismos de autenticação.

Depende do escopo e da maturidade do Operator. Se ele cobre principalmente a instalação e atualizações, o Helm pode ser suficiente. Se você quer ir para o gerenciamento do ciclo de vida, insights e piloto automático, é aqui que você provavelmente usaria Go.

Este é mais baseado na experiência pessoal e gosto...

Operator Framework
Kubebuilder
Controller Runtime ...
Secrets
Os segredos permitem que você armazene e gerencie informações sensíveis (senhas, chaves ssh, etc.)

kubectl create secret generic some-secret --from-literal=password='donttellmypassword'

kubectl create secret generic some-secret --from-file=/some/file.txt

Opaque é o tipo padrão usado para pares chave-valor.

Falso. Alguns mecanismos de segurança conhecidos como "criptografia" não são habilitados por padrão.

```bash
apiVersion: v1   
kind: Secret
metadata:
    name: some-secret
type: Opaque
data:
    password: mySecretPassword
```
A senha não está criptografada. Você deve executar algo como: echo -n 'mySecretPassword' | base64 e colar o resultado no arquivo em vez de usar texto simples.

```bash
spec:
  containers:
    - name: USER_PASSWORD
      valueFrom:
        secretKeyRef:
          name: some-secret
          key: password
```
A variável de ambiente USER_PASSWORD armazenará o valor da chave de senha no segredo chamado "some-secret" Em outras palavras, você referencia um valor de um Segredo do Kubernetes.

Um processo possível seria o seguinte:

Você cria um segredo do Kubernetes (mas não faz commit)
Você o criptografa usando algum projeto de terceiros (por exemplo, kubeseal)
Você aplica o segredo selado/criptografado
Você faz commit do segredo selado no Git
Você implanta uma aplicação que requer o segredo e ele pode ser descriptografado automaticamente usando, por exemplo, um controlador Bitnami Sealed Secrets
Volumes
Falso

Volumes Persistentes nos permitem salvar dados, então basicamente eles fornecem armazenamento que não depende do ciclo de vida do pod.

Verdadeiro

NFS
iSCSI
CephFS
...
Os snapshots de volume permitem que você crie uma cópia do seu volume em um ponto específico no tempo.

Falso

A principal diferença reside no momento em que você deseja configurar o armazenamento. Por exemplo, se você precisar pré-popular dados em um volume, você escolhe o provisionamento estático. Por outro lado, se você precisar criar volumes sob demanda, você opta pelo provisionamento dinâmico.

Retain (Reter)
Recycle (Reciclar)
Delete (Deletar)
Controle de Acesso
RBAC no Kubernetes é o mecanismo que permite configurar conjuntos de permissões refinados e específicos que definem como um determinado usuário, ou grupo de usuários, pode interagir com qualquer objeto do Kubernetes no cluster, ou em um Namespace específico do cluster.

A diferença entre eles é que uma Role é usada em nível de namespace, enquanto uma ClusterRole é para todo o cluster.

Kubernetes.io: "Uma conta de serviço fornece uma identidade para processos que são executados em um Pod."

Um exemplo de quando usar uma: Você define um pipeline que precisa construir e enviar uma imagem. Para ter permissões suficientes para construir e enviar uma imagem, esse pipeline exigiria uma conta de serviço com permissões suficientes.

O pod é automaticamente atribuído à conta de serviço padrão (no namespace onde o pod está sendo executado).

Contas de usuário são globais, enquanto as contas de serviço são únicas por namespace
Contas de usuário são para humanos ou processos de cliente, enquanto as contas de serviço são para processos que são executados em pods
kubectl get serviceaccounts

kubernetes.io: "Um contexto de segurança define as configurações de privilégio e controle de acesso para um Pod ou Contêiner."

Padrões
CronJob
Um CronJob cria Jobs em uma programação repetida. Um objeto CronJob é como uma linha de um arquivo crontab (tabela cron). Ele executa um job periodicamente em uma determinada programação, escrita no formato Cron.

```bash
apiVersion: batch/v1beta1
kind: CronJob
metadata:
  name: some-cron-job
spec:
  schedule: '*/1 * * * *'
  startingDeadlineSeconds: 10
  concurrencyPolicy: Allow
```

Se o cron job falhar, o próximo job não substituirá o anterior devido ao valor "concurrencyPolicy" que é "Allow". Ele continuará gerando novos jobs e, eventualmente, o sistema ficará cheio de cron jobs com falha. Para evitar tal problema, o valor "concurrencyPolicy" deve ser "Replace" ou "Forbid".

```bash
apiVersion: batch/v1beta1
kind: CronJob
metadata:
  name: "some-cron-job"
spec:
  schedule: '*/1 * * * *'
jobTemplate:
  spec:
    template:
      spec:
      restartPolicy: Never
      concurrencyPolicy: Forbid
      successfulJobsHistoryLimit: 1
      failedJobsHistoryLimit: 1
```

As seguintes linhas estão colocadas sob o template:

```bash
concurrencyPolicy: Forbid
successfulJobsHistoryLimit: 1
failedJobsHistoryLimit: 1
```
Como resultado, esta configuração não faz parte da especificação do cron job, portanto, o cron job não tem limites, o que pode causar problemas como OOM e potencialmente levar à queda do servidor da API. Para corrigir isso, essas linhas devem ser colocadas na especificação do cron job, acima ou abaixo da diretiva "schedule" no exemplo acima.

Diversos
Namespaces permitirão limitar recursos e também garantir que não haja colisões entre equipes ao trabalhar no cluster (como criar uma aplicação com o mesmo nome).

Separa a configuração dos pods. É bom para casos em que você pode precisar alterar a configuração em algum momento, mas não quer reiniciar a aplicação ou reconstruir a imagem, então você cria um ConfigMap e o conecta a um pod, mas externamente ao pod.

No geral, é bom para:

Compartilhar a mesma configuração entre diferentes pods
Armazenar a configuração externa ao pod
Crie-o (a partir de chave e valor, um arquivo ou um arquivo env)
Anexe-o. Monte um configmap como um volume
Falso. Use um segredo.

No Kubernetes, um HorizontalPodAutoscaler atualiza automaticamente um recurso de carga de trabalho com o objetivo de escalar automaticamente a carga de trabalho para corresponder à demanda.

O componente do plano de controle kube-scheduler faz as seguintes perguntas,

O que agendar? Ele tenta entender as especificações da definição do pod
Em qual nó agendar? Ele tenta determinar o melhor nó com recursos disponíveis para iniciar um pod
Vincula o Pod a um determinado nó
Veja mais aqui

Guaranteed (Garantido)
Burstable (Expansível)
BestEffort (Melhor Esforço)
Os rótulos do Kubernetes são pares chave-valor que podem conectar metadados de identificação com objetos do Kubernetes.

Gatekeeper
Documentação do Gatekeeper: "O Gatekeeper é um webhook de validação (mutating TBA) que impõe políticas baseadas em CRD executadas pelo Open Policy Agent"

Em cada requisição enviada ao cluster Kubernetes, o Gatekeeper envia as políticas e os recursos para o OPA (Open Policy Agent) para verificar se viola alguma política. Se violar, o Gatekeeper retornará a mensagem de erro da política. Se não violar nenhuma política, a requisição chegará ao cluster.

Teste de Políticas
O Conftest permite que você escreva testes contra arquivos estruturados. Você pode pensar nele como uma biblioteca de testes para recursos do Kubernetes. É mais usado em ambientes de teste, como pipelines de CI ou ganchos locais.

Assim como o Conftest, ele é usado para teste e aplicação de políticas. A diferença é que ele vem com políticas integradas.

Helm
Gerenciador de pacotes para o Kubernetes. Basicamente, a capacidade de empacotar arquivos YAML e distribuí-los para outros usuários e aplicá-los no(s) cluster(s).

Como conceito, é bastante comum e pode ser encontrado em muitas plataformas e serviços. Pense, por exemplo, nos gerenciadores de pacotes em sistemas operacionais. Se você usa Fedora/RHEL, seria o dnf. Se você usa Ubuntu, então, o apt. Se você não usa Linux, então uma pergunta diferente deveria ser feita e é por quê? mas isso é outro tópico :)

Às vezes, quando você gostaria de implantar uma certa aplicação em seu cluster, você precisa criar múltiplos arquivos/componentes YAML como: Secret, Service, ConfigMap, etc. Isso pode ser uma tarefa tediosa. Então, faria sentido facilitar o processo introduzindo algo que nos permitirá compartilhar esses pacotes de YAMLs toda vez que quisermos adicionar uma aplicação ao nosso cluster. Esse algo é chamado de Helm.

Um cenário comum é ter múltiplos clusters Kubernetes (prod, dev, staging). Em vez de aplicar individualmente diferentes YAMLs em cada cluster, faz mais sentido criar um Chart e instalá-lo em cada cluster.

Outro cenário é, você gostaria de compartilhar o que você criou com a comunidade. Para que pessoas e empresas possam implantar facilmente sua aplicação em seus clusters.

Helm Charts são um pacote de arquivos YAML. Um pacote que você pode consumir de repositórios ou criar o seu próprio e publicá-lo nos repositórios.

É útil para cenários onde você tem múltiplas aplicações e todas são semelhantes, então há pequenas diferenças em seus arquivos de configuração e a maioria dos valores são os mesmos. Com o Helm, você pode definir um blueprint comum para todas elas e os valores que não são fixos e mudam podem ser placeholders. Isso é chamado de arquivo de template e se parece com o seguinte

```bash
apiVersion: v1
kind: Pod
metadata:
  name: {[ .Values.name ]}
spec:
  containers:
  - name: {{ .Values.container.name }}
  image: {{ .Values.container.image }}
  port: {{ .Values.container.port }}
```
Os próprios valores estarão em um arquivo separado:

```bash
name: some-app
container:
  name: some-app-container
  image: some-app-image
  port: 1991
```
- Implantar a mesma aplicação em múltiplos ambientes diferentes
- CI/CD

someChart/ -> o nome do chart Chart.yaml -> meta informações sobre o chart values.yaml -> valores para arquivos de template charts/ -> dependências do chart templates/ -> arquivos de templates :)

O Helm permite que você atualize, remova e reverta para versões anteriores dos charts. Na versão 2 do Helm, isso era feito com o que é conhecido como "Tiller". Na versão 3, ele foi removido devido a preocupações com a segurança.

Comandos
helm search hub [alguma_palavra_chave]

Ou diretamente na linha de comando: helm install --set alguma_chave=algum_valor

helm ls ou helm list

helm rollback NOME_DO_LANÇAMENTO ID_DA_REVISÃO

helm history NOME_DO_LANÇAMENTO

helm upgrade NOME_DO_LANÇAMENTO NOME_DO_CHART

Segurança
Proteger a comunicação entre serviços (uma maneira é usar o Istio para fornecer mTLS)
Isolar diferentes recursos em namespaces separados com base em alguns grupos lógicos
Usar um tempo de execução de contêiner suportado (se você usa Docker, abandone-o porque está obsoleto. Você pode querer usar CRI-O como motor e podman para CLI)
Testar adequadamente as alterações no cluster (por exemplo, considere usar o Datree para evitar configurações incorretas do Kubernetes)
Limitar quem pode fazer o quê (usando, por exemplo, o OPA gatekeeper) no cluster
Usar NetworkPolicy para aplicar segurança de rede
Considerar o uso de ferramentas (por exemplo, Falco) para monitorar ameaças
Cenários de Solução de Problemas
Um caminho possível é executar kubectl describe pod <nome do pod> para obter mais detalhes. Você pode ver um dos seguintes:

O cluster está cheio. Nesse caso, expanda o cluster.
Os limites de ResourcesQuota foram atingidos. Nesse caso, você pode querer modificá-los
Verifique se a montagem do PersistentVolumeClaim está pendente
Se nada do acima ajudou, execute o comando (get pods) com -o wide para ver se o nó está atribuído a um nó. Se não, pode haver um problema com o agendador.

Um caminho possível é começar verificando o status do Pod.

O Pod está pendente? se sim, verifique o motivo com kubectl describe pod <nome do pod> TODO: terminar isso...
Istio
O Istio é uma malha de serviço de código aberto que ajuda as organizações a executar aplicações distribuídas baseadas em microsserviços em qualquer lugar. O Istio permite que as organizações protejam, conectem e monitorem microsserviços, para que possam modernizar suas aplicações empresariais de forma mais rápida e segura.

Controladores
Kubernetes.io: "No Kubernetes, os controladores são ciclos de controle que observam o estado do seu cluster e, em seguida, fazem ou solicitam alterações quando necessário. Cada controlador tenta mover o estado atual do cluster para mais perto do estado desejado."

Controlador de Nó: gerencia os nós de um cluster. Entre outras coisas, o controlador é responsável por monitorar a saúde dos nós - se o nó ficar subitamente inacessível, ele evacuará todos os pods em execução nele e marcará o status do nó de acordo.
Controlador de Replicação - monitora o status das réplicas de pod com base no que deveria estar em execução. Ele garante que o número de pods que deveriam estar em execução esteja realmente em execução
Kube-Controller-Manager

Explicado aqui

Observar - identificar o estado atual do cluster
Diferença - Identificar se existe uma diferença entre o estado atual e o estado desejado
Agir - Levar o estado atual do cluster ao estado desejado (basicamente, alcançar um estado onde não há diferença)
Scheduler
Falso. Embora o agendador seja responsável por escolher o nó no qual o Pod será executado, o Kubelet é quem realmente executa o Pod.

k run some-pod --image=redix -o yaml --dry-run=client > pod.yaml

vi pod.yaml e adicione:

```bash
spec:
  nodeName: node1
```
k apply -f pod.yaml

Nota: se você não tiver um node1 em seu cluster, o Pod ficará preso no estado "Pendente".

Afinidade de Nó
vi pod.yaml

```bash
affinity:
  nodeAffinity:
    requiredDuringSchedlingIgnoredDuringExecution:
      nodeSelectorTerms:
      - matchExpressions:
        - key: region
          operator: In
          values:
          - asia
          - emea
```
vi pod.yaml

```bash
affinity:
  nodeAffinity:
    requiredDuringSchedlingIgnoredDuringExecution:
      nodeSelectorTerms:
      - matchExpressions:
        - key: region
          operator: NotIn
          values:
          - neverland
```
Verdadeiro

Falso. O agendador tenta encontrar um nó que atenda aos requisitos/regras e, se não encontrar, agendará o Pod de qualquer maneira.

Sim, é possível. Você pode executar outro pod com um comando semelhante a:

```bash
spec:
  containers:
  - command:
    - kube-scheduler
    - --address=127.0.0.1
    - --leader-elect=true
    - --scheduler-name=some-custom-scheduler
...
```
Executando kubectl get events, você pode ver qual agendador foi usado.

Adicione o seguinte à especificação do Pod:

```bash
spec:
  schedulerName: some-custom-scheduler
```

Taints
k describe no master | grep -i taints

k taint node minikube app=web:NoSchedule

k describe no minikube | grep -i taints

O Pod permanecerá no status "Pendente" devido ao único nó no cluster ter um taint de "app=web".

kubectl edit po some-pod e adicione o seguinte

```bash
  - effect: NoSchedule
    key: app
    operator: Equal
    value: web
```
Saia e salve. O pod deve estar no estado Em Execução agora.

k taint node minikube app=web:NoSchedule-

NoSchedule: impede que recursos sejam agendados em um determinado nó PreferNoSchedule: preferirá agendar recursos em outros nós antes de recorrer ao agendamento do recurso no nó escolhido (no qual o taint foi aplicado) NoExecute: Aplicar "NoSchedule" não removerá Pods (ou outros recursos) já em execução do nó, ao contrário de "NoExecute", que removerá qualquer recurso já em execução do Nó

Limites de Recursos
Você sabe quanta RAM e/ou CPU sua aplicação deve consumir e qualquer coisa acima disso não é válida
Você gostaria de garantir que todos possam executar suas aplicações no cluster e que os recursos não sejam usados exclusivamente por um tipo de aplicação
Falso. É por contêiner e não por Pod.

Limites de Recursos - Comandos
kubectl describe po <NOME_DO_POD> | grep -i limits

kubectl run yay --image=python --dry-run=client -o yaml > pod.yaml

vi pod.yaml

```bash
spec:
  containers:
  - image: python
    imagePullPolicy: Always
    name: yay
    resources:
      requests:
        cpu: 250m
        memory: 64Mi
```

kubectl apply -f pod.yaml

kubectl run yay2 --image=python --dry-run=client -o yaml > pod.yaml

vi pod.yaml

```bash
spec:
  containers:
  - image: python
    imagePullPolicy: Always
    name: yay2
    resources:
      limits:
        cpu: 500m
        memory: 128Mi
      requests:
        cpu: 250m
        memory: 64Mi
```

kubectl apply -f pod.yaml

Monitoramento
Existem muitos tipos de soluções de monitoramento para o Kubernetes. Algumas de código aberto, algumas em memória, algumas delas custam dinheiro, ... aqui está uma pequena lista:

metrics-server: monitoramento de código aberto em memória
datadog: $$$
promethues: solução de monitoramento de código aberto
Isso depende muito do que você escolheu usar. Vamos abordar algumas das soluções:

metrics-server: uma solução de monitoramento gratuita e de código aberto que usa o componente cAdvisor do kubelet para recuperar informações sobre o cluster e seus recursos e os armazena na memória. Uma vez instalado, após algum tempo, você pode executar comandos como kubectl top node e kubectl top pod para visualizar métricas de desempenho em nós, pods e outros recursos.
TODO: adicionar mais soluções de monitoramento

Kustomize
Você tem um helm chart de uma aplicação usada por várias equipes em sua organização e há um requisito para adicionar uma anotação à aplicação especificando o nome da equipe proprietária da aplicação
Sem o Kustomize, você precisaria copiar os arquivos (template do chart neste caso) e modificá-lo para incluir as anotações específicas que precisamos
Com o Kustomize, você não precisa copiar todo o repositório ou arquivos
Pedem para você aplicar uma alteração/patch em alguma aplicação sem modificar os arquivos originais da aplicação
Com o Kustomize, você pode definir um arquivo kustomization.yml que define essas personalizações para que você não precise tocar nos arquivos originais da aplicação
Você adiciona o arquivo kustomization.yml na pasta da aplicação que você gostaria de personalizar.
Você define as personalizações que gostaria de realizar
Você executa kustomize build CAMINHO_DA_APP onde seu kustomization.yml também reside
Estratégias de Implantação
Implantações Azul/Verde: Você implanta uma nova versão de sua aplicação, enquanto a versão antiga ainda está em execução, e começa a redirecionar o tráfego para a nova versão da aplicação
Implantações Canário: Você implanta uma nova versão de sua aplicação e começa a redirecionar uma porção de seus usuários/tráfego para a nova versão. Assim, a migração para a nova versão é muito mais gradual
Etapas da implantação Azul/Verde:

O tráfego vindo dos usuários através de um balanceador de carga para a aplicação que está atualmente na versão 1
Usuários -> Balanceador de Carga -> App Versão 1

Uma nova versão 2 da aplicação é implantada (enquanto a versão 1 ainda está em execução)
Usuários -> Balanceador de Carga -> App Versão 1 App Versão 2

Se a versão 2 funcionar corretamente, o tráfego é trocado para ela em vez da versão 1
Usuário -> Balanceador de Carga App versão 1 -> App Versão 2

Se a versão antiga é removida ou mantida em execução, mas sem que os usuários sejam redirecionados para ela, é baseado na decisão da equipe ou da empresa
Prós:

Podemos reverter/trocar rapidamente para a versão anterior a qualquer momento Contras:
Em caso de problema com a nova versão, TODOS os usuários são afetados (em vez de uma pequena porção/porcentagem)
Etapas da implantação Canário:

O tráfego vindo dos usuários através de um balanceador de carga para a aplicação que está atualmente na versão 1
Usuários -> Balanceador de Carga -> App Versão 1

Uma nova versão 2 da aplicação é implantada (enquanto a versão 1 ainda está em execução) e parte do tráfego é redirecionado para a nova versão
Usuários -> Balanceador de Carga ->(95% do tráfego) App Versão 1 ->(5% do tráfego) App Versão 2

Se a nova versão (2) funcionar bem, mais tráfego é redirecionado para ela
Usuários -> Balanceador de Carga ->(70% do tráfego) App Versão 1 ->(30% do tráfego) App Versão 2

Se tudo funcionar bem, em algum momento todo o tráfego é redirecionado para a nova versão
Usuários -> Balanceador de Carga -> App Versão 2

Prós:

Se houver algum problema com a nova versão da aplicação implantada, apenas uma parte dos usuários é afetada, em vez de todos eles Contras:
O teste da nova versão é necessariamente no ambiente de produção (já que o tráfego do usuário existe apenas lá)
Existem várias maneiras. Uma delas é o Argo Rollouts.

Cenários
Namespaces. Veja a seguinte pergunta e resposta sobre namespaces para mais informações.

O contêiner falhou ao ser executado (por diferentes razões) e o Kubernetes tenta executar o Pod novamente após algum atraso (= tempo de BackOff).

Algumas razões para falhar:

Configuração incorreta - erro de digitação, valor não suportado, etc.
Recurso não disponível - nós inativos, PV não montado, etc.
Algumas maneiras de depurar:

kubectl describe pod NOME_DO_POD
Foque em State (que deve ser Waiting, CrashLoopBackOff) e Last State, que deve dizer o que aconteceu antes (ou seja, por que falhou)
Execute kubectl logs mypod
Isso deve fornecer uma saída precisa de
Para um contêiner específico, você pode adicionar -c NOME_DO_CONTÊINER
Sim, usando taints, poderíamos executar o seguinte comando e isso impediria que todos os recursos com o rótulo "app=web" fossem agendados no node1: kubectl taint node node1 app=web:NoSchedule

Usando ResourceQuotas


