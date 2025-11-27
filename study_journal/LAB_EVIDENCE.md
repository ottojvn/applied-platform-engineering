# **Evidências de Laboratório e Validação Técnica**

⚠️ ATENÇÃO: O Mentor de IA está instruído a rejeitar qualquer tarefa como "Concluída" se não houver prova técnica neste arquivo.  
Links para screenshots devem ser relativos (ex: ../assets/evidence\_01.png) ou hospedados externamente. Logs de texto devem usar blocos de código.

## **Módulo 1: Linux Internals**

### **Lab 1.1: SadServer "Saint John" (Disk Full)**

**Status:** \[Pendente / Concluído\]

#### **1\. Diagnóstico Inicial**

*Saída do comando df \-h mostrando disco cheio:*

\# Cole aqui o log

#### **2\. Investigação (O "Invisible Layer")**

*Saída do comando lsof ou inspeção de /proc mostrando o arquivo deletado ainda aberto:*

\# Cole aqui a evidência do File Descriptor aberto

#### **3\. Resolução**

*Comando usado para truncar o arquivo ou matar o processo:*

\# Cole aqui o comando

## **Módulo 2: Redes e TCP/IP**

### **Lab 2.1: TCP Handshake Analysis**

**Status:** \[Pendente / Concluído\]

#### **1\. Captura de Pacotes**

*Snippet do output do tcpdump ou screenshot do Wireshark mostrando SYN, SYN-ACK, ACK:*

\# Cole aqui o dump dos pacotes

#### **2\. Análise de Flags**

*Explicação de qual flag indica o início e o fim da conexão na captura acima.*

## **Módulo 3: AWS Networking (VPC from Scratch)**

### **Lab 3.1: Construção da VPC Manual**

**Status:** \[Pendente / Concluído\]

#### **1\. Arquitetura Lógica**

*Descrição dos CIDR Blocks escolhidos:*

* VPC CIDR: 10.0.0.0/16  
* Public Subnet: ...  
* Private Subnet: ...

#### **2\. Prova de Conectividade**

*Log de terminal mostrando conexão SSH no Bastion Host e, de lá, para a Instância Privada:*

user@laptop$ ssh \-i key.pem ec2-user@BASTION\_IP  
\[ec2-user@bastion\]$ ssh \-i key.pem ec2-user@PRIVATE\_IP  
\[ec2-user@private-ip\]$ ping google.com  
\# Mostrar sucesso (via NAT Gateway)

## **Módulo 4: Infraestrutura como Código (Terraform)**

### **Lab 4.1: State Locking**

**Status:** \[Pendente / Concluído\]

#### **1\. Evidência de Bloqueio**

*Log de erro do Terraform impedindo execução simultânea devido ao DynamoDB Lock:*

Error: Error acquiring the state lock  
Lock Info:  
  ID:        ...  
  Path:      ...  
  Operation: OperationTypeApply

## **Módulo 5: Capstone Project**

### **Lab 5.1: Docker Optimization**

**Comparativo de Tamanho de Imagem:**

REPOSITORY          TAG                 SIZE  
boutique-frontend   original            ...MB  
boutique-frontend   distroless          ...MB

### **Lab 5.2: GitOps Self-Healing**

Link para GIF ou Vídeo curto mostrando o ArgoCD revertendo uma mudança manual:  
\[Link para evidência\]

### **Lab 5.3: Observabilidade RED**

Screenshot do Dashboard Grafana sob carga:  
\[Link para Screenshot\]