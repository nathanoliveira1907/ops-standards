# Guia de Eliminação de Pontos Únicos de Falha (SPOF)

---

## 1. Princípios de Redundância e Isolamento

Para atingir arquiteturas altamente disponíveis, nenhum componente isolado (seja de hardware, rede, banco de dados ou código) pode causar a parada total do sistema.

---

## 2. Checklist de Eliminação por Camada

### 🛜 Camada de Rede e Roteamento
* [ ] Roteamento Multi-AZ com Load Balancers de alta disponibilidade (AWS ALB/NLB ou Cloudflare Proxy).
* [ ] Failover DNS automatizado via Health Checks em nível de aplicação.
* [ ] Proteção DDoS de Borda ativa (AWS Shield / Cloudflare WAF).

### 🖥️ Camada de Computação e Servidores
* [ ] Clusterização de microsserviços em Kubernetes distribuídos em no mínimo **3 Zonas de Disponibilidade (AZs)**.
* [ ] Configuração explícita de `podAntiAffinity` para evitar agrupamento de pods no mesmo nó físico.
* [ ] Polícias de Auto-scaling atreladas ao p95 de latência e consumo de CPU/Memória.

### 💾 Camada de Dados e Persistência
* [ ] Bancos de dados configurados em modelo Primary-Secondary Multi-AZ com *Automatic Failover*.
* [ ] Instâncias de Leitura (*Read Replicas*) distribuídas para aliviar a carga no banco primário.
* [ ] Estratégias de *Circuit Breakers* e *Graceful Degradation* no acesso a caches e bancos.

---

## 3. Padrão Arquitetural: Circuit Breaker

```text
[ Aplicação ] ---> ( Estado: CLOSED ) ---> [ Dependência ]
      |
      +---> ( Falhas consecutivas > Limite ) ---> [ Estado: OPEN ]
                                                      |
                                          ( Descarta chamadas / Fallback )
```