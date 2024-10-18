# Atividade Prática de Kubernetes 

Este projeto faz parte de uma atividade prática que consiste em desenvolver uma aplicação simples, construir e publicar uma imagem Docker, realizar o deploy da aplicação em um cluster Kubernetes utilizando Minikube, e configurar uma pipeline CI/CD no GitHub Actions para automatizar o build e push da imagem para o Docker Hub.

## Descrição Geral

### Dockerfile

A atividade inclui a criação de um **Dockerfile** que usa a abordagem de **multistage build**.
O Dockerfile foi configurado para:
- Instalar as dependências da aplicação.
- Copiar o código-fonte e artefatos da aplicação.
- Expor a porta 3000, que é onde a aplicação está escutando.
- Executar a aplicação com o comando `npm start`.

### Deployment YAML

O **Deployment YAML** foi criado para fazer o deploy da aplicação no Kubernetes. Ele define que a aplicação deve rodar com uma réplica. O deployment utiliza a imagem publicada no Docker Hub.

Além disso, o deployment especifica o uso da porta 3000 no container, e o Kubernetes cuida do gerenciamento das réplicas e da distribuição da carga entre elas.

### Service YAML

O **Service YAML** foi criado para expor a aplicação fora do cluster Kubernetes, utilizando o tipo **NodePort**. Esse serviço permite que a aplicação seja acessada através de uma porta específica no nó do cluster. No caso desta atividade, a aplicação foi exposta na porta 30007.

### Pipeline CI/CD com GitHub Actions

Foi configurada uma pipeline CI/CD no **GitHub Actions** para automatizar o build da imagem Docker e o push para o Docker Hub. Sempre que há um push na branch `main`, a pipeline é acionada automaticamente. A pipeline realiza as seguintes etapas:

1. Faz o checkout do código do repositório.
2. Constrói a imagem Docker usando o Dockerfile.
3. Faz login no Docker Hub utilizando as credenciais armazenadas nos **Secrets** do GitHub.
4. Faz o push da imagem para o Docker Hub.
5. Faz logout do Docker Hub após a conclusão do processo.
---

**Autor**: Analice Battisti
