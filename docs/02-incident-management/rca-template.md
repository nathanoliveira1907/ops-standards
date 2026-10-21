# [RCA] Análise de Causa Raiz: [Nome do Incidente]

> **Status:** [Rascunho | Em Revisão | Aprovado]  
> **Data do Incidente:** YYYY-MM-DD  
> **Nível de Severidade:** [SEV-1 / SEV-2 / SEV-3]  
> **Incident Commander:** @usuario  
> **Autores do RCA:** @usuario  

---

## 1. Resumo Executivo
Descrição objetiva sobre a falha, impacto nos negócios e nos usuários finais, e a solução adotada para restaurar os serviços.

* **Serviços Impactados:**
* **Impacto ao Negócio:** (ex.: X% das transações falharam durante o período de instabilidade)
* **Status do SLO/SLA:** [Violado / Preservado]

---

## 2. Métricas de Resposta ao Incidente

| Métrica | Horário (UTC) / Valor |
| :--- | :--- |
| **Início da Falha** | YYYY-MM-DD HH:MM |
| **Detecção (MTTD)** | X minutos |
| **Restauração (MTTR)** | Y minutos |
| **RTO Atingido** | HH:MM |
| **RPO Atingido** | (Ex.: 0 dados perdidos) |

---

## 3. Linha do Tempo (Timeline UTC)

* **HH:MM** - Ocorre o evento gatilho inicial.
* **HH:MM** - Alerta automático dispara nos canais de monitoramento.
* **HH:MM** - Início da resposta pela equipe de plantão (Incident Commander assume a sala de crise).
* **HH:MM** - Causa primária identificada.
* **HH:MM** - Ação de mitigação/rollback executada.
* **HH:MM** - Métricas e latência reestabelecidas dentro da normalidade.

---

## 4. Análise dos 5 Porquês (5 Whys)

1. **Por que o serviço ficou indisponível?**
   * *Resposta:* 
2. **Por que [Resposta 1] ocorreu?**
   * *Resposta:* 
3. **Por que [Resposta 2] ocorreu?**
   * *Resposta:* 
4. **Por que [Resposta 3] ocorreu?**
   * *Resposta:* 
5. **Por que [Resposta 4] ocorreu? (Causa Raiz)**
   * *Resposta:* 

---

## 5. Plano de Ação Preventivo e Corretivo

| ID | Ação | Categoria | Responsável | Prazo | Status |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **ACT-01** | | [Correção Imediata / Prevenção / Alertas] | @usuario | YYYY-MM-DD | PENDENTE |
| **ACT-02** | | [Correção Imediata / Prevenção / Alertas] | @usuario | YYYY-MM-DD | PENDENTE |

---

## 6. Lições Aprendidas
* **O que funcionou bem:**
* **O que não funcionou bem:**
* **Onde tivemos sorte:**