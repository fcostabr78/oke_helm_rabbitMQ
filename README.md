# RabbitMQ @ OKE

## Objetivo

O objetivo desse how-to é demonstrar a instalação do RabbitMQ dentro de um cluster kubernetes. Através desse empacotamento é possível deixar em execução o Rabbit dentro de um cluster OKE. 

## Pré-requisito

1. Cluster Kubernetes provisiondo no Oracle Cloud Infrastruture <br>
   https://docs.oracle.com/pt-br/iaas/Content/ContEng/Concepts/contengoverview.htm

1.1 OCI CLI instalado e kubeconfig criado localmente

2. helm instalado localmente


## Etapas

Abra o Terminal e ingresse os seguintes comandos:

```
$ alias k=kubectl
```

```
$ helm init --service-account tiller --history-max 200 --upgrade
```

```
$ helm repo add rabbitmq-oke 'https://raw.githubusercontent.com/fcostabr78/oke_helm_rabbitMQ/master/' 
```

```
$ helm repo update
```

```
$ k create ns rabbitmq
```

```
$ helm install rabbitmq-oke rabbitmq-oke/oke-helm-rabbitMQ --namespace rabbitmq
```

Será apresentado o status seguinte com comando acima:

```
WARNING: Kubernetes configuration file is group-readable. This is insecure. Location: /home/fernando/.kube/config
WARNING: Kubernetes configuration file is world-readable. This is insecure. Location: /home/fernando/.kube/config
NAME: rabbitmq-oke
LAST DEPLOYED: Mon Apr  5 17:15:37 2021
NAMESPACE: rabbitmq
STATUS: deployed
REVISION: 1
TEST SUITE: None
```

<b>O processo completo de provisionamento de todos os recursos no OKE deve demorar 4min</b>

## Acessar o RabbitMQ UI

Para obter o IP Externo (external-ip) de acesso ao RabbitMQ, ingresse o seguinte comando via Terminal:

```
$ k get service/rabbitmq-client -n rabbitmq
```

Abra o navegador e ingresse o IP externo obtido no comando acima, seguido da porta 15672. Exemplo: http://IP:15671. Será aberto uma interface solicitando o usuário e senha. <br>



:heartpulse:


