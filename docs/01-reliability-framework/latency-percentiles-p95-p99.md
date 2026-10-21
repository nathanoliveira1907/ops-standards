# Gestão de Latência com Percentis (p95 e p99)

---

## 1. Por que NÃO utilizar Média de Latência?

A média oculta falhas críticas e comportamentos extremos. Em arquiteturas de microserviços, uma única requisição de um usuário pode depender de dezenas de chamadas internas. Se a cauda de alta latência for ignorada, a experiência do usuário se degrada drasticamente.

---

## 2. Definição de Percentis

* **p50 (Mediana):** 50% das requisições são mais rápidas que este valor. Representa a experiência do usuário comum.
* **p95:** 95% das requisições são mais rápidas que este valor. Identifica lentidões sistêmicas antes que afetem a maioria.
* **p99:** 99% das requisições são mais rápidas que este valor. Captura os piores cenários (*tail latency*), essenciais para debugging em larga escala.

---

## 3. Metas Recomendadas por Tier de Aplicação

| Tier | Métrica | Alvo Latência (p95) | Alvo Latência (p99) |
| :--- | :--- | :--- | :--- |
| **APIs de Leitura** | Tempo de Resposta HTTP | $< 100\text{ms}$ | $< 300\text{ms}$ |
| **APIs de Escrita/Processamento** | Tempo de Resposta HTTP | $< 250\text{ms}$ | $< 800\text{ms}$ |
| **Worker / Filas Assíncronas** | Tempo de Processamento | $< 2.000\text{ms}$ | $< 5.000\text{ms}$ |

---

## 4. Alertas Baseados em Percentis (PromQL)

Exemplo de consulta Prometheus para disparar alerta caso o p99 exceda 500ms por mais de 5 minutos:

```promql
histogram_quantile(0.99, sum(rate(http_request_duration_seconds_bucket[5m])) by (le)) > 0.5
```