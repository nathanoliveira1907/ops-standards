---
name: " Post-Mortem / Incident RCA"
about: "Criar uma issue para conduzir a análise de causa raiz de um incidente."
title: "[RCA] SEV-X: <Título do Incidente>"
labels: "incident, post-mortem, sre"
assignees: ""
---

## 📌 Informações Gerais
* **Data do Incidente:** YYYY-MM-DD
* **Severidade:** [SEV-1 / SEV-2 / SEV-3]
* **Incident Commander:** @usuario
* **Link da Sala de Crise / Canal:** 

---

## 📝 Resumo do Impacto
Descreva sucintamente o que falhou, o impacto gerado para os clientes e o tempo necessário para mitigar a falha.

---

## ⏱️ Métricas Principais
- **MTTD:** X mins
- **MTTR:** Y mins
- **SLO Impactado:** 

---

## 🔍 Checklist de Conclusão do RCA
- [ ] Linha do tempo estruturada em formato UTC.
- [ ] Análise dos 5 Porquês documentada.
- [ ] Plano de Ação criado com responsáveis e prazos alocados.
- [ ] Documento anexado ao repositório central em `docs/02-incident-management/`.