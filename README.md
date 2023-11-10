# Helm Chart para API REST & Async Worker
##### Este Helm chart instala a aplicação API REST e o Async Worker em um cluster Kubernetes.

## Pré-requisitos
Kubernetes 1.19+  
minikube v1.30.1+  
Helm 3.0+  

## Instalação
Para instalar o chart com o nome de meu-release:

```
helm install meu-release path/to/chart-directory
```

O comando acima instala a aplicação no Kubernetes cluster com os valores padrão de configuração.

## Valores dos pods

| Parâmetro                     | Descrição                             | Valor Padrão               |
|-------------------------------|---------------------------------------|----------------------------|
| `apiRest.image.repository`    | Imagem Docker da API REST             | `kwaark/api_rest`          |
| `apiRest.image.tag`           | Tag da imagem Docker                  | `v1.0`                     |
| `asyncWorker.image.repository`| Imagem Docker do Async Worker         | `kwaark/async_worker`      |
| `asyncWorker.image.tag`       | Tag da imagem Docker                  | `v1.0`                     |
| `kafka.image.repository`      | Imagem Docker do Kafka                | `bitnami/kafka`            |
| `kafka.image.tag`             | Tag da imagem Docker                  | `latest`                   |
| `zookeeper.image.repository`  | Imagem Docker do Zookeeper            | `bitnami/zookeeper`        |
| `zookeeper.image.tag`         | Tag da imagem Docker                  | `latest`                   |
## Valores dos services
| Parâmetro                     | Descrição                             | Valor Padrão               |
|-------------------------------|---------------------------------------|----------------------------|
| `apiRest.service.type`        | Tipo de serviço para expor a API REST | `NodePort`                 |
| `apiRest.service.port`        | Porta para o serviço da API REST      | `443`                      |
| `kafka.service.type`          | Tipo de serviço para expor o kafka    | `ClusterIP`                |
| `kafka.service.port`          | Porta para o serviço kafka            | `9092`                     |
| `zookeeper.service.type`      | Tipo de serviço para expor o zookeeper| `ClusterIP`                |
| `zookeeper.service.port`      | Porta para o serviço zookeeper        | `2181`                     |



## Comandos que podem ajudar:

Navegue até a a pasta onde fica o Chart.yaml e use o comando para iniciar o cluster:
```
helm install meu-cluster .
```
Navegue até a a pasta onde fica o Chart.yaml e use o comando para atualizar o cluster:
```
helm upgrade meu-cluster .
```
Use esse comando para deletar o cluster:
```
helm delete meu-cluster
```

## Acessando a API REST
Após a instalação, a API REST estará acessível dentro do cluster na porta do serviço api-rest.

## Acessando a API REST Localmente:
Use o comando para listar os services e pegar a porta do service API-REST:
```
kubectl get srv
```
Veja o ip do cluster:
```
minikube ip
```

Acesse a API no seu navegador:
`[Link]:[porta]/items/[1]`

exemplo:
`http://192.168.49.2:32115/items/1`
