# 🚀 Day 2: Explorando a fundo os Pods

Neste segundo dia do curso **Descomplicando Kubernetes**, o foco foi entender a unidade básica do K8s: o **Pod**. Saímos da criação rápida via linha de comando para a estruturação profissional via arquivos YAML.

## 📝 O que foi aprendido:

* **O que é um Pod:** A menor unidade implantável no Kubernetes, que pode conter um ou mais containers.
* **Criação de Pods:**
    * Via CLI (Imperativo).
    * Via YAML (Declarativo) - a forma correta para produção.
* **Multi-container Pods:** Implementação de mais de um container compartilhando o mesmo ciclo de vida e rede.
* **Resource Management:** Configuração de limites de **CPU** e **Memória** para garantir a saúde do nó.
* **Volumes (EmptyDir):** Criação de volumes temporários para compartilhamento de dados entre containers do mesmo Pod.

## 🛠️ Comandos Principais Utilizados:

```bash
# Criar um pod a partir de um arquivo YAML
kubectl apply -f meu-pod.yaml

# Listar os pods e ver em qual nó estão rodando
kubectl get pods -o wide

# Ver detalhes e logs de um pod específico
kubectl describe pod <nome-do-pod>
kubectl logs <nome-do-pod>
