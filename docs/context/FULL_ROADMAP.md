# **Roadmap de Engenharia de Plataforma: Currículo Baseado em Primeiros Princípios**

Nível: Staff/Principal Engineer Track  
Foco: Fundamentos, Resiliência e Operação em Escala  
Metodologia: "Construir para quebrar" e "Overengineering Estratégico"

## **Fase 1: Fundamentação Operacional (The Invisible Layer)**

*Objetivo: Dominar o substrato onde o software roda antes de abstraí-lo.*

### **Módulo 1.1: Linux Internals & Troubleshooting**

A competência sênior não é saber comandos, é entender como o Kernel gerencia recursos.

* **Tópicos Core:**  
  * **Ciclo de Vida de Processos:** Syscalls fork(), exec(), wait(). Estados de processo (R, S, D, Z). Diferença entre SIGTERM e SIGKILL.  
  * **File Descriptors & Inodes:** O conceito de "tudo é um arquivo". Hard vs Soft links. Como rm funciona (unlink) vs espaço em disco real.  
  * **Systemd:** Units, Targets, gerenciamento de dependências e isolamento de recursos (cgroups básico).  
* **Recursos Obrigatórios (Prática):**  
  * **Plataforma:** SadServers (Cenários Reais).  
  * **Cenário "Saint John":** Diagnóstico de disco cheio com arquivo deletado (uso de lsof e /proc).  
  * **Cenário "Saskatoon":** Análise de logs de alta volumetria usando streams (awk, sort, uniq).  
  * **Cenário "Taipei":** Port Knocking e regras dinâmicas de iptables.  
* **Validação Técnica (Mental Check):**  
  * Você consegue explicar por que um processo entra em estado "Uninterruptible Sleep" (D)?  
  * Você sabe recuperar um arquivo deletado que ainda está aberto por um processo?

### **Módulo 1.2: Redes Avançadas e Análise de Tráfego**

A nuvem é apenas rede. Se você não entende TCP, você não entende a Nuvem.

* **Tópicos Core:**  
  * **Modelo OSI (Prático):** Foco nas camadas 3 (IP), 4 (TCP/UDP) e 7 (HTTP/DNS). Encapsulamento.  
  * **TCP Handshake:** SYN, SYN-ACK, ACK. Sequence Numbers e Flags (RST, FIN).  
  * **DNS:** Recursividade, Autoridade, Tipos de Registro (A, CNAME, NS, TXT). Ferramentas de diagnóstico real (dig \+trace).  
  * **Subnetting:** Cálculo de CIDR (/24, /16), Máscaras de rede e Gateway.  
* **Recursos Obrigatórios (Prática):**  
  * **Plataforma:** TryHackMe (Trilha "Network Fundamentals").  
  * **Ferramentas:** Wireshark (análise de pcaps), tcpdump, dig.  
* **Validação Técnica (Mental Check):**  
  * Você consegue identificar uma perda de pacote ou retransmissão olhando apenas um dump de TCP?  
  * Você sabe diferenciar um erro de DNS de um erro de firewall apenas usando curl \-v?

## **Fase 2: Infraestrutura como Código e Nuvem (Building the Road)**

*Objetivo: Construir infraestrutura auditável, reprodutível e escalável.*

### **Módulo 2.1: Arquitetura AWS (VPC from Scratch)**

Proibido o uso de Wizards. Entendimento da topologia lógica é obrigatório.

* **Tópicos Core:**  
  * **VPC Anatomy:** Blocos CIDR, Subnets Públicas vs Privadas.  
  * **Roteamento:** Route Tables manuais. O papel do Internet Gateway (IGW) vs NAT Gateway.  
  * **Segurança:** Security Groups (Stateful) vs Network ACLs (Stateless).  
* **Desafio Prático:**  
  * Construir uma arquitetura de rede completa manualmente via CLI ou Terraform (sem console).  
  * Configurar um Bastion Host para acesso seguro a instâncias privadas.  
* **Validação Técnica (Mental Check):**  
  * Qual a diferença de custo e arquitetura entre um NAT Gateway e uma NAT Instance?  
  * Por que o tráfego de retorno é permitido em um Security Group mas pode ser bloqueado em uma NACL?

### **Módulo 2.2: Terraform em Escala Enterprise**

Saia do "Hello World" e entre na colaboração em time.

* **Tópicos Core:**  
  * **State Management:** Backend Remoto (S3) e State Locking (DynamoDB).  
  * **Modularização:** Separação entre Definição de Módulo (reutilizável) e Implementação Live (ambiente).  
  * **Estrutura de Diretórios:** modules/ vs prod/ vs stage/.  
* **Desafio Prático:**  
  * Implementar State Locking e demonstrar o bloqueio de concorrência.  
  * Refatorar um código monolítico (main.tf gigante) em módulos.

## **Fase 3: Containerização e Orquestração (The Engine)**

*Objetivo: Gerenciar cargas de trabalho com eficiência e segurança.*

### **Módulo 3.1: Docker Otimizado e Segurança**

Imagens pequenas são imagens seguras e rápidas.

* **Tópicos Core:**  
  * **Multi-stage Builds:** Separação de ambiente de build vs runtime.  
  * **Distroless Images:** Uso de imagens sem shell/package managers (Google Distroless).  
  * **Layer Caching:** Ordenação de instruções no Dockerfile para otimizar build time.  
* **Validação Técnica (Mental Check):**  
  * Como você debuga um container que não tem /bin/sh? (Conceito de Ephemeral Containers).

### **Módulo 3.2: Kubernetes Internals**

Desmistificando a mágica dos controladores.

* **Tópicos Core:**  
  * **Primitivos:** Pods, Deployments, StatefulSets, DaemonSets.  
  * **Networking K8s:** Services (ClusterIP, NodePort, LoadBalancer), Ingress Controllers, CNI Plugins.  
  * **Config:** ConfigMaps, Secrets, Resource Quotas e Limits.

## **Fase 4: Capstone Project \- Google Online Boutique**

*Objetivo: Integração total de conhecimentos em uma aplicação de microserviços complexa.*

**Contexto:** Orquestração da aplicação demo "Online Boutique" (11 microserviços, gRPC, Redis, Poliglota).

### **Tarefa 4.1: Pipeline de CI Moderno (GitHub Actions)**

* Implementar pipelines que utilizam OIDC para autenticação na nuvem (sem chaves estáticas).  
* Matriz de testes e Caching de dependências.  
* Scan de vulnerabilidades (Trivy) bloqueando o build.

### **Tarefa 4.2: GitOps com ArgoCD**

* Implementação do modelo "Pull" de deploy.  
* Configuração de **Self-Heal**: O cluster deve reverter alterações manuais automaticamente.  
* Padrão "App of Apps" para gestão do cluster.

### **Tarefa 4.3: Observabilidade e SRE**

* **Método RED:** Instrumentação de dashboards focados em Rate, Errors e Duration para os serviços críticos.  
* **Prometheus:** Configuração de Recording Rules para métricas pesadas.  
* **Grafana:** Dashboards as Code (JSON versionado).

## **Referências Bibliográficas (Deep Research)**

Este roadmap foi construído com base na análise dos seguintes documentos curados:

1. *Curadoria DevOps: Recursos de Estudo Avançados* (Foco em Linux Kernel, TCP Handshake, Distroless).  
2. *Treinamento Técnico: Pesquisa de Recursos* (Foco em SadServers, TryHackMe, Google Online Boutique).