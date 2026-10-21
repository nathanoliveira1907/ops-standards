# Diretrizes de Confiabilidade: SLI, SLO, SLA e Error Budgets

---

## 1. Mapeamento de Conceitos

* **SLI (Service Level Indicator):** A métrica contínua do comportamento real do sistema.
  * *Fórmula de Disponibilidade:* 
    $$\text{SLI} = \left( \frac{\text{Requisições com Sucesso}}{\text{Requisições Totais}} \right) \times 100$$
* **SLO (Service Level Objective):** O alvo interno definido e mantido pela equipe de engenharia.
* **SLA (Service Level Agreement):** O contrato formal com o cliente. Caso violado, há penalidades contratuais ou reembolso.

---

## 2. Matriz de Serviços e Objetivos

| Tier do Serviço | Descrição | SLO de Disponibilidade | SLA (Externo) | Janela de Avaliação |
| :--- | :--- | :--- | :--- | :--- |
| **Tier 0 (Core/Crítico)** | Autenticação, Checkout, Pagamentos | **99.99%** | **99.9%** | 30 dias móveis |
| **Tier 1 (Negócio)** | Catálogo, Notificações, Busca | **99.9%** | **99.5%** | 30 dias móveis |
| **Tier 2 (Interno)** | Relatórios, Admin, Analytics | **99.0%** | N/A | 30 dias móveis |

---

## 3. Política de Error Budget (Orçamento de Erro)

O **Error Budget** é o espaço tolerável para falhas ($100\% - \text{SLO}$).

$$\text{Error Budget (Minutos/Mês para 99.9\%)} = (1 - 0.999) \times 43\,200 \text{ min} = 43.2 \text{ minutos de downtime}$$

### Regras de Engajamento por Consumo de Error Budget:
* **Consumo < 50%:** Operação normal; novos deploys e funcionalidades liberados.
* **Consumo entre 50% e 80%:** Alerta de risco; priorização de tarefas de débito técnico.
* **Consumo > 80%:** *Deploy Freeze* de funcionalidades não críticas. Todo a capacidade do time se volta para resiliência e correções.