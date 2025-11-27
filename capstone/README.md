# **Especificação Técnica: Cloud Native E-Commerce Infrastructure**

## **1\. Visão Executiva**

O projeto Capstone consiste na orquestração, implantação e operação da aplicação **Google Online Boutique**, uma plataforma de e-commerce baseada em microserviços.

O objetivo desta implementação não é o desenvolvimento de funcionalidades de software, mas sim a demonstração de competência em **Engenharia de Plataforma**. A infraestrutura deve suportar alta disponibilidade, segurança de supply chain, imutabilidade de deploy e observabilidade avançada, simulando um ambiente de produção crítico (Tier 1).

## **2\. Arquitetura da Aplicação**

A aplicação é composta por 11 microserviços poliglotas comunicando-se via gRPC.

* **Frontend (Go):** Expõe serviço HTTP/REST e comunica-se com serviços internos.  
* **CartService (C\#):** Gerencia o carrinho de compras utilizando Redis (Stateful).  
* **ProductCatalog (Go):** Fornece listagem de produtos.  
* **CurrencyService (Node.js):** Converte valores monetários.  
* **PaymentService (Node.js):** Processa pagamentos (Mock).  
* **ShippingService (Go):** Calcula frete.  
* **EmailService (Python):** Envia confirmações.  
* **CheckoutService (Go):** Orquestrador de transações.  
* **RecommendationService (Python):** Calcula recomendações de produtos.  
* **AdService (Java):** Serve anúncios contextuais.  
* **Redis:** Armazenamento de dados efêmero/cache.

## **3\. Requisitos Não Funcionais (Constraints)**

A implementação deve aderir estritamente às seguintes restrições de engenharia. Soluções que violem estes princípios serão rejeitadas durante o Code Review.

### **3.1 Containerização e Segurança**

* **Imagem Base:** Todas as imagens finais de produção devem utilizar distroless (Google) ou scratch para minimizar superfície de ataque. É proibido o uso de imagens com shell (alpine, ubuntu) em produção.  
* **Otimização:** Uso obrigatório de Multi-stage Builds para garantir que compiladores e ferramentas de build não existam na imagem final.  
* **Privilégio:** Containers devem, sempre que possível, rodar como usuário não-root (User 1000+).

### **3.2 Infraestrutura como Código (IaC)**

* **Ferramenta:** Terraform.  
* **Gestão de Estado:** Backend remoto obrigatório (S3) com State Locking (DynamoDB).  
* **Isolamento:** Uso de módulos para componentes de rede e computação.  
* **Proibição:** Nenhum recurso deve ser criado manualmente via console (ClickOps).

### **3.3 Orquestração (Kubernetes)**

* **Namespaces:** Separação lógica entre monitoring, argocd e boutique-app.  
* **Resiliência:** Todos os Deployments devem possuir LivenessProbe e ReadinessProbe configurados com thresholds realistas.  
* **Proteção de Recursos:** Definição obrigatória de requests e limits (CPU/RAM) para todos os containers para evitar "Noisy Neighbor".  
* **Exposição:** Uso de Ingress Controller para expor o Frontend.

### **3.4 GitOps e CI/CD**

* **Modelo de Deploy:** Pull-based via ArgoCD.  
* **Imutabilidade:** O ArgoCD deve ter SelfHeal habilitado. Alterações manuais no cluster (Drift) devem ser revertidas automaticamente.  
* **Pipeline de Integração (GitHub Actions):**  
  * Linting de Dockerfiles e Manifestos K8s.  
  * Scan de vulnerabilidades (Trivy) com bloqueio de build em caso de CVEs críticas.  
  * Autenticação em Cloud Providers via OIDC (Sem Long-lived Access Keys).

### **3.5 Observabilidade (SRE)**

* **Metodologia:** Implementação do **Método RED** (Rate, Errors, Duration).  
* **Stack:** Prometheus (coleta) e Grafana (visualização).  
* **Entregável:** Um dashboard unificado exibindo a saúde dos serviços críticos (Frontend, Checkout, Payment), permitindo correlação visual entre deploy e degradação de performance.

## **4\. Fases de Implementação**

### **Fase 1: Hardening de Containers**

Refatoração dos Dockerfiles originais do Google para aderir aos padrões de segurança Distroless e Multi-stage.

### **Fase 2: Provisionamento de Infraestrutura**

Criação do cluster Kubernetes e infraestrutura de rede (VPC) utilizando Terraform modular.

### **Fase 3: Pipeline de Entrega**

Configuração do GitHub Actions para CI (Build/Test/Scan) e ArgoCD para CD (Sync).

### **Fase 4: Operação e Monitoramento**

Instalação da stack de observabilidade e criação de Dashboards as Code.

## **5\. Critérios de Aceite (Definition of Done)**

O projeto será considerado concluído apenas mediante a apresentação das seguintes evidências no diretório docs/evidence:

1. **Relatório de Vulnerabilidades:** Output do Trivy limpo para CVEs críticas/altas.  
2. **Prova de GitOps:** Vídeo ou GIF demonstrando o ArgoCD revertendo uma exclusão manual de um Service.  
3. **Snapshot de Observabilidade:** Screenshot do Grafana mostrando métricas RED sob carga (gerada pelo LoadGenerator).  
4. **Documentação Arquitetural:** ADRs (Architecture Decision Records) justificando a escolha das ferramentas e estratégias de particionamento de infraestrutura.