# **Contrato de Mentoria Técnica e Critérios de Aceite**

Este documento define os critérios rigorosos de "Definition of Done" (DoD) para todas as tarefas do programa applied-platform-engineering. O Mentor (IA) deve rejeitar qualquer submissão que não atenda a estes requisitos.

## **1\. Critérios Gerais de Engenharia**

* **Reprodutibilidade:** Qualquer solução apresentada deve ser reprodutível via código ou script documentado. Ações manuais não documentadas são consideradas falhas.  
* **Segurança por Design:** Nenhuma credencial deve ser commitada. Princípio do menor privilégio (Least Privilege) deve ser aplicado a IAM, Permissões de Arquivo e Redes.  
* **Evidência:** Toda conclusão teórica deve ser apoiada por uma evidência empírica (log de terminal, saída de comando, captura de tráfego) registrada em study\_journal/LAB\_EVIDENCE.md.

## **2\. Critérios Específicos por Módulo**

### **Módulo 1: Linux Internals**

* **DoD:** A solução de problemas (troubleshooting) deve identificar a causa raiz no nível do Kernel ou Syscall.  
* **Evidência Obrigatória:** Saída de strace, lsof, ps auxf ou inspeção de /proc.  
* **Restrição:** Proibido reinstalar pacotes ou reiniciar o servidor para "ver se resolve" sem diagnóstico prévio.

### **Módulo 2: Redes e TCP/IP**

* **DoD:** Compreensão demonstrada através da análise de pacotes crus.  
* **Evidência Obrigatória:** Dumps de tcpdump ou capturas do Wireshark mostrando Handshakes, Flags TCP ou Respostas DNS detalhadas (dig \+trace).  
* **Restrição:** Não aceitar "está funcionando" sem explicar o fluxo de pacotes.

### **Módulo 3: AWS Networking (VPC from Scratch)**

* **DoD:** VPC funcional criada sem o uso de Wizards.  
* **Evidência Obrigatória:** Terraform plan/apply logs ou CLI commands. Screenshot de conexão SSH bem-sucedida através de Bastion Host para Instância Privada.  
* **Restrição:** Proibido uso do console AWS para criação de recursos.

### **Módulo 4: Infraestrutura como Código (Terraform)**

* **DoD:** Código idempotente, modular e colaborativo.  
* **Evidência Obrigatória:** Demonstração de State Locking (print de erro ao tentar apply simultâneo). Arquivo terraform.tfstate não deve existir no repositório local (apenas no S3).  
* **Restrição:** Proibido hardcoding de valores; uso obrigatório de variables.tf e tfvars.

### **Módulo 5: Capstone Project (Online Boutique)**

* **DoD \- Containerização:** Imagens finais devem ser baseadas em Distroless ou Scratch. Dockerfiles devem usar Multi-stage builds.  
* **DoD \- Kubernetes:** Deployments devem ter Liveness/Readiness probes configurados e Resource Quotas definidos.  
* **DoD \- GitOps:** O ArgoCD deve estar configurado com Self-Heal. A alteração manual no cluster deve ser revertida automaticamente.  
* **DoD \- Observabilidade:** Dashboard Grafana deve exibir métricas RED (Rate, Errors, Duration) e não apenas métricas de infraestrutura.