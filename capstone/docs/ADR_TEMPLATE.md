# **ADR-\[NNN\]: \[Título Curto e Descritivo da Decisão\]**

* **Status:** \[Proposto | Aceito | Deprecado | Rejeitado\]  
* **Data:** \[AAAA-MM-DD\]  
* **Autor:** \[Seu Nome\]  
* **Revisores:** \[Mentor IA\]

## **1\. Contexto e Problema**

Descreva o desafio técnico ou o requisito de negócio que motivou esta decisão.

* Qual é a dor atual?  
* Quais são as restrições (custo, latência, segurança, tempo)?  
* Por que a abordagem padrão/trival não é suficiente?

## **2\. Decisão**

Descreva a solução técnica escolhida de forma clara e direta.

* Qual ferramenta, padrão ou arquitetura será utilizada?  
* Como ela será configurada em alto nível?

## **3\. Alternativas Consideradas**

Liste as opções que foram avaliadas mas **não** foram escolhidas. Para um engenheiro sênior, explicar por que *não* usar algo é tão importante quanto explicar o que usar.

* **Opção A:** \[Descrição\]  
  * *Motivo da rejeição:* (Ex: "Complexidade operacional muito alta para o benefício trazido", "Custo proibitivo", "Não suporta HA").  
* **Opção B:** \[Descrição\]  
  * *Motivo da rejeição:* ...

## **4\. Consequências (Trade-offs)**

Toda decisão de arquitetura tem custos. Liste os impactos positivos e negativos.

### **Positivas (Ganhos)**

* \[Ex: Aumenta a segurança da cadeia de suprimentos removendo o shell\]  
* \[Ex: Reduz o tempo de recuperação de desastres (RTO)\]

### **Negativas (Custos/Riscos)**

* \[Ex: Aumenta a complexidade de debugging (não há ssh no container)\]  
* \[Ex: Introduz uma nova dependência de infraestrutura\]  
* \[Ex: Curva de aprendizado da equipe\]

## **5\. Alinhamento com os Princípios do Projeto**

Verifique se a decisão respeita as restrições do projeto Capstone:

* \[ \] **IaC:** A solução é totalmente declarativa e gerenciável via Terraform/Helm?  
* \[ \] **Imutabilidade:** A solução evita configuração manual (ClickOps)?  
* \[ \] **Segurança:** A solução respeita o princípio do menor privilégio?  
* \[ \] **Observabilidade:** A solução expõe métricas para o Prometheus?

## **6\. Referências**

Links para documentação oficial, artigos técnicos ou POCs que embasaram a decisão.