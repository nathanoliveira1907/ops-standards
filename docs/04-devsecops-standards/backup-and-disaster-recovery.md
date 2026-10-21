# Diretrizes de Backup, Patches de Segurança e Disaster Recovery

---

## 1. Gestão de Patches e Vulnerabilidades

1. **Varredura Contínua no CI/CD:**
   * **SAST (Static Application Security Testing):** Análise estática no código fonte.
   * **SCA (Software Composition Analysis):** Análise automatizada de dependências e bibliotecas vulneráveis.
2. **SLA de Aplicação de Patches para CVEs:**
   * **Crítica / Alta (CVE $\ge 8.0$):** Aplicação de patch e deploy em até **24 a 48 horas**.
   * **Média / Baixa:** Correção dentro da sprint regular de desenvolvimento.

---

## 2. Estratégia de Backup Imutável (WORM)

* **Automação:** Backups diários com retenção configurada conforme exigência regulatória (ex.: LGPD/GDPR).
* **Imutabilidade (WORM - Write Once, Read Many):** Configuração de *Object Lock* em storage para impedir alteração ou exclusão do backup por sequestro de credenciais (Ransomware).

---

## 3. Testes de Recuperação e Chaos Engineering (GameDays)

* **GameDays Trimestrais:** Execução regular de simulações de recuperação de desastres (restauração a partir do zero em um ambiente isolado).
* **Engenharia de Caos:** Injeção controlada de falhas em ambiente de staging e produção (derrubada de pods, simulação de latência de rede) para validar resiliência do ecossistema.