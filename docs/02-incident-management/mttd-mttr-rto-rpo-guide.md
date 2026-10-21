# Métricas de Operação de Incidentes e Recuperação

---

## 1. Métricas de Operação (MTTD e MTTR)

```text
[ Surgimento da Falha ] ---> ( MTTD ) ---> [ Detecção ] ---> ( MTTR ) ---> [ Restauração ]
```

* **MTTD (Mean Time to Detect):** Tempo médio desde a ocorrência do erro até sua confirmação e abertura de incidente.
  * *Meta Enterprise:* $\le 5\text{ minutos}$ (exige monitoramento sintético e alertas acionados por métricas do sistema).
* **MTTR (Mean Time to Resolve/Restore):** Tempo médio entre a confirmação do incidente e o retorno da aplicação à normalidade.
  * *Meta Enterprise:* $\le 30\text{ minutos}$ (via automação de rollback, *feature flags* ou isolamento de nós).

---

## 2. Métricas de Desastre e Continuidade (RTO e RPO)

* **RTO (Recovery Time Objective):** Tempo máximo tolerável de indisponibilidade do sistema após uma falha catastrófica.
* **RPO (Recovery Point Objective):** Volume máximo tolerável de dados perdidos, medido em tempo transcorrido desde o último ponto de restauração.

---

## 3. Matriz por Tier de Criticidade

| Tier | MTTD Meta | MTTR Meta | RTO Alvo | RPO Alvo | Estratégia de Backup / DR |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Tier 0** | $< 2\text{ min}$ | $< 15\text{ min}$ | $< 15\text{ min}$ | **RPO = 0** | Multi-Region Active-Active com replicação síncrona |
| **Tier 1** | $< 5\text{ min}$ | $< 30\text{ min}$ | $< 1\text{ hora}$ | $\le 5\text{ min}$ | Continuous Data Protection (PITR) / Replicação Assíncrona |
| **Tier 2** | $< 15\text{ min}$ | $< 2\text{ horas}$ | $< 24\text{ horas}$ | $\le 24\text{ horas}$ | Backups diários automatizados e testados em snapshot |