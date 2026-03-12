# Descomplicando_kubernete
Curso da LinuxTips 
☸️ Aprendendo Kubernetes - Day 1 (KINDS)

Kubernetes Lab: Descomplicando o Kubernetes (Day 1)

Repositório de estudos práticos realizados durante o curso "Descomplicando o Kubernetes" da LINUXtips. Este laboratório foca na criação de infraestrutura local utilizando Kind e manipulação de objetos com kubectl.

Nesta etapa, aprendi a interagir com o cluster Kubernetes utilizando o kubectl e a gerenciar o ciclo de vida básico de um Pod.

🛠️ Tecnologias Utilizadas

    Ubuntu Linux: Sistema operacional base.

    Docker: Engine de containers para hospedar os nós do cluster.

    Kind (Kubernetes in Docker): Ferramenta para rodar clusters Kubernetes locais.

    kubectl: CLI para interação com o cluster.

    ## 📅 Cronograma de Estudos

| Dia | Conteúdo Principal | Documentação Prática |
| :--- | :--- | :--- |
| **Day 1** | Instalação de Cluster (Kind) e comandos básicos | [Visualizar](./README.md) |
| **Day 2** | Pods, YAML, Multi-containers e Resources | [Acessar Laboratório](./Day2/) |

---
    
🚀 Passo a Passo Realizado
1. Preparação do Ambiente
Instalação das ferramentas necessárias e configuração de permissões do Docker para execução sem sudo.

 # Verificação do Docker
docker ps
 # Instalação do kubectl (via Snap)
sudo snap install kubectl --classic

2. Criação do Cluster Multi-Node com Kind
Criação de um arquivo de configuração YAML para definir a topologia do cluster (1 Control Plane e 2 Workers).
Arquivo: kind-cluster.yaml

kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
- role: control-plane
- role: worker
- role: worker

Comando de criação:
kind create cluster --config kind-cluster.yaml --name giropops

3. Gerenciamento de Pods e Namespaces

Exploração de comandos para visualizar a saúde do cluster e rodar aplicações.

    Listar nós: kubectl get nodes

    Listar namespaces: kubectl get namespaces

    Ver pods em todos os namespaces: kubectl get pods -A -o wide
    
4. Execução e Exposição de Aplicações
   Criação de um Pod Nginx e exposição via Service (ClusterIP) para comunicação interna.

   # Criando um template YAML de forma declarativa
   kubectl run meu-nginx --image nginx --port 80 --dry-run=client -o yaml > pod-template.yaml

   # Aplicando o Pod
   kubectl create -f pod-template.yaml

   # Expondo o Pod como um Service
   kubectl expose pod meu-nginx

   📊 Resultados Finais:
   Ao final do laboratório, o ambiente apresentava um Service ativo e um Pod rodando no cluster giropops.
     Nome do Recurso    Tipo       Porta       Status
     pod/meu-nginx,     Pod        80/TCP      Running
    service/meu-nginx   ClusterIP  80/TCp      Active
   
💡 Aprendizados Adquiridos:
   Diferença entre edição imperativa (kubectl run) e declarativa (kubectl apply -f).
   Resolução de erros comuns de edição no terminal (Vim vs Nano).
   Conceito de Nodes, Pods e Services no ecossistema Kubernetes.  
    
