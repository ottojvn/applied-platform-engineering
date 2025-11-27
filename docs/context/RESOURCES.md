# **Biblioteca de Recursos Curados**

Este documento contém a lista oficial de referências técnicas, laboratórios e documentação que suportam o currículo de Engenharia de Plataforma. O Mentor IA deve utilizar estes links para recomendar leituras ou validar se o aluno está utilizando as fontes autorizadas.

## **Módulo 1: Linux Internals & Troubleshooting**

### **Laboratórios Práticos (SadServers)**

* **Plataforma Principal:** [SadServers.com](https://sadservers.com/)  
* **Cenário "Saint John" (Disk Full):** [Link do Lab](https://sadservers.com/scenario/saint-john)  
  * *Conceito:* Inodes, File Descriptors e processos segurando arquivos deletados.  
* **Cenário "Saskatoon" (Log Analysis):** [Link do Lab](https://sadservers.com/scenario/saskatoon)  
  * *Conceito:* Manipulação de streams de texto de alta performance (awk, sort, uniq).  
* **Cenário "Taipei" (Networking/Security):** [Link do Lab](https://sadservers.com/scenarios/topic/hacking) (Procurar por Taipei)  
  * *Conceito:* Iptables, regras dinâmicas e Port Knocking.

### **Leitura Técnica (Deep Dive)**

* **Ciclo de Vida de Processos:** [Elastic Blog: Linux Process Model](https://www.elastic.co/blog/linux-process-and-session-model-as-part-of-security-alerting-and-monitoring)  
* **Permissões e Octais:** [Linux File Permissions Explained](https://www.webasha.com/blog/linux-file-permissions-explained-complete-guide-with-octal-cheatsheet-and-commands)  
* **Systemd Unit Files:** [Red Hat: Optimizing Systemd](https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/8/pdf/using_systemd_unit_files_to_customize_and_optimize_your_system/Red_Hat_Enterprise_Linux-8-Using_systemd_unit_files_to_customize_and_optimize_your_system-en-US.pdf)

## **Módulo 2: Redes Avançadas**

### **Laboratórios Práticos (TryHackMe)**

* **Trilha Network Fundamentals:** [TryHackMe Module](https://tryhackme.com/module/network-fundamentals)  
  * *Foco:* "Packets & Frames", "Extending Your Network".  
* **Simulador de Rede:** [Network Simulator](https://static-labs.tryhackme.cloud/sites/net-simulator/?config=introtonetworking)

### **Leitura Técnica**

* **TCP Handshake Visualization:** [Fortinet: What is TCP/IP?](https://www.fortinet.com/resources/cyberglossary/tcp-ip)  
* **DNS Debugging (Dig \+trace):** [IBM: Using dig \+trace](https://www.ibm.com/think/tutorials/using-dig-trace)  
* **Subnetting Practice:** [Subnetting.org](https://www.subnetting.org/)

## **Módulo 3: Cloud Architecture (AWS)**

### **Laboratórios Oficiais**

* **AWS Networking Workshop:** [Workshop Oficial](https://networking.workshop.aws/)  
  * *Nota:* Focar nos laboratórios de VPC e Routing. Ignorar seções de Transit Gateway na fase inicial.  
* **VPC from Scratch Guide:** [AWS Docs: Create VPC](https://docs.aws.amazon.com/vpc/latest/userguide/create-vpc.html)

## **Módulo 4: Infraestrutura como Código (Terraform)**

### **Melhores Práticas**

* **Estrutura de Diretórios:** [Terraform Best Practices](https://www.terraform-best-practices.com/examples/terraform/medium-size-infrastructure)  
* **State Locking (S3 \+ DynamoDB):** [HashiCorp: S3 Backend](https://developer.hashicorp.com/terraform/language/backend/s3)  
* **Modularização:** [Gruntwork: How to create reusable modules](https://blog.gruntwork.io/how-to-create-reusable-infrastructure-with-terraform-modules-25526d65f73d)

## **Módulo 5: Capstone Project (Stack Moderna)**

### **Aplicação Alvo**

* **Google Online Boutique:** [GitHub Repository](https://github.com/GoogleCloudPlatform/microservices-demo)  
  * *Atenção:* Utilizar este repo como fonte da aplicação, mas refatorar a infraestrutura do zero.

### **Containerização (Hardening)**

* **Distroless Images:** [GoogleContainerTools/distroless](https://github.com/GoogleContainerTools/distroless)  
* **Multi-stage Builds:** [Docker Docs](https://docs.docker.com/build/building/multi-stage/)

### **GitOps (ArgoCD)**

* **Instalação e Setup:** [ArgoCD Getting Started](https://argo-cd.readthedocs.io/en/stable/getting_started/)  
* **Sync Policies (Self-Heal):** [ArgoCD Automated Sync](https://argo-cd.readthedocs.io/en/stable/user-guide/auto_sync/)

### **Observabilidade (SRE)**

* **The RED Method:** [Grafana Labs Blog](https://grafana.com/blog/2018/08/02/the-red-method-how-to-instrument-your-services/)  
* **Prometheus Recording Rules:** [Prometheus Docs](https://prometheus.io/docs/prometheus/latest/configuration/recording_rules/)