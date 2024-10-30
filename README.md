# TCC Deploy - GitOps e Argo CD

Este repositório contém os arquivos de configuração de **deploy** para as aplicações do projeto de TCC. Ele é responsável pela **Entrega Contínua** (CD) utilizando práticas de **GitOps** com o **Argo CD** para automatizar e gerenciar o deploy das aplicações no cluster Kubernetes.

## Estrutura do Repositório

- `argocd/` - Configuração do `ApplicationSet` do Argo CD, que define o deploy de todas as aplicações.
- `apps/` - Diretório com os manifests Kubernetes (YAML) para cada aplicação:
  - `backend-api/` - Manifests de deployment e service do backend.
  - `frontend/` - Manifests de deployment e service do frontend.
  - `mongodb/` - Manifests de deployment, service e PVC para MongoDB.
  - `redis/` - Manifests de deployment, service e PVC para Redis.

## Deploy Automático com GitOps

Com as práticas de **GitOps** implementadas, o **Argo CD** monitora este repositório e aplica as mudanças automaticamente ao cluster Kubernetes. As principais funcionalidades do deploy incluem:
1. **Sincronização Automatizada**: Toda alteração commitada neste repositório é monitorada pelo Argo CD, que garante que o estado do cluster Kubernetes corresponda ao estado desejado, descrito nos manifests YAML.
2. **Rollback Automático**: Em caso de falhas, o Argo CD permite reverter o deploy para uma versão anterior de forma segura e rápida.
3. **Versionamento de Configurações**: As configurações de deploy são versionadas no Git, oferecendo rastreabilidade total sobre as mudanças.

## Como Utilizar

1. Clone este repositório e edite os arquivos de configuração conforme necessário.
2. Aplique o manifesto do **ApplicationSet** em seu cluster Kubernetes para configurar o Argo CD:

   ```bash
   kubectl apply -f https://raw.githubusercontent.com/<github-username>/<repository-name>/path/to/argocd/applicationset.yaml
   ```

3. Commite e faça push das alterações para que o Argo CD sincronize as mudanças com o cluster Kubernetes automaticamente.

## Contato

Qualquer dúvida ou sugestão, entre em contato pelo e-mail: [marciosbicigo@alunos.fho.edu.br](mailto:marciosbicigo@alunos.fho.edu.br).
