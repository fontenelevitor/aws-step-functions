#  Desafio DIO - AWS Step Functions

Este projeto faz parte do desafio da **Digital Innovation One (DIO)** sobre workflows automatizados com **AWS Step Functions**.  
O objetivo é demonstrar a orquestração de serviços AWS em um fluxo prático e simples.

---

##  Objetivo do Projeto
- Criar um workflow automatizado com Step Functions.  
- Integrar Lambda, DynamoDB e SNS.  


---

##  Cenário Simulado

Fluxo de **validação de pedidos**:
1. Usuário envia um pedido (JSON fictício).  
2. O Step Functions inicia o workflow.  
3. Uma função **Lambda** valida os dados do pedido.  
   - Se válido → grava no **DynamoDB**.  
   - Se inválido → envia notificação via **SNS**.  
4. O workflow termina com sucesso ou erro.

---

##  Arquitetura do Fluxo

```text
[Usuário / Aplicação]
        ↓
[S3 Bucket - Pedidos]
        ↓ Trigger
[AWS Step Functions Workflow]
 ├──→ [Lambda: Validar Pedido]
 ├──→ [DynamoDB: Registrar Pedido] (se válido)
 └──→ [SNS: Notificação de Erro] (se inválido)
