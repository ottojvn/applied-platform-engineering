# **Aceleração de Carreira em Engenharia de Plataforma**

## **Visão Geral**

Este repositório documenta um programa de capacitação técnica intensiva focado em Engenharia de Plataforma, DevOps e SRE (Site Reliability Engineering). O objetivo deste projeto não é apenas o estudo teórico, mas a construção de competência verificável através da resolução de problemas reais de infraestrutura, sistemas operacionais e orquestração de sistemas distribuídos.

A metodologia aplicada segue uma abordagem de "Primeiros Princípios", priorizando o entendimento profundo de Linux Internals e Redes (TCP/IP) antes da abstração de ferramentas de nuvem.

## **Estrutura do Repositório**

A organização deste repositório reflete o fluxo de trabalho de um time de engenharia de alta performance:

* **/docs**: Contém a documentação estratégica e o roteiro técnico.  
  * context/: Armazena o roadmap completo e o contrato de mentoria técnica que rege a execução das tarefas.  
* **/study\_journal**: Registros diários de aprendizado e evidências técnicas.  
  * LEARNING\_LOG.md: Diário técnico cronológico detalhando desafios enfrentados e soluções investigadas.  
  * LAB\_EVIDENCE.md: Repositório de evidências (logs, capturas de tela, diffs) que comprovam a execução bem-sucedida dos laboratórios práticos.  
* **/capstone**: O projeto final de graduação (Google Online Boutique).  
  * Contém a implementação de infraestrutura (IaC), configuração de Kubernetes, pipelines de CI/CD e monitoramento.  
* **.github**: Configurações de automação e comportamento do assistente de IA.

## **Metodologia de Mentoria Assistida por IA**

Este repositório utiliza uma configuração personalizada do GitHub Copilot para atuar como um **Staff Platform Engineer**. O assistente de IA foi instruído para operar sob um modelo socrático rigoroso:

1. **Sem Respostas Prontas**: A IA atua como um Tech Lead, recusando-se a fornecer soluções diretas para problemas de aprendizado.  
2. **Validação por Evidência**: O progresso só é reconhecido mediante a apresentação de logs, métricas ou código funcional.  
3. **Foco em Design**: Ênfase em decisões arquiteturais documentadas (ADRs) e justificativas técnicas, não apenas em código funcional.

## **Projeto Capstone: Arquitetura de Microserviços e GitOps**

O treinamento culmina na orquestração da aplicação **Google Online Boutique**, composta por 11 microserviços poliglotas. A infraestrutura é desenhada com "overengineering estratégico" para demonstrar domínio de padrões corporativos:

* **Infraestrutura como Código (IaC)**: Terraform com gerenciamento de estado remoto e locking (S3/DynamoDB).  
* **Containerização**: Otimização de imagens utilizando Multi-stage Builds e imagens Distroless focadas em segurança.  
* **GitOps**: Sincronização de estado do cluster via ArgoCD (Modelo Pull).  
* **Observabilidade**: Instrumentação baseada no Método RED (Rate, Errors, Duration) utilizando Prometheus e Grafana.

## **Status do Projeto**

Este projeto está em desenvolvimento ativo, seguindo as fases definidas no Roadmap Técnico localizado em docs/context/FULL\_ROADMAP.md.