# Padrões de Segurança: Zero Trust e Princípio do Menor Privilégio (PoLP)

---

## 1. Arquitetura Zero Trust

Sob a premissa de que a rede interna não é inerentemente confiável, todas as conexões (internas ou externas) devem ser autenticadas, autorizadas e criptografadas antes do acesso ser concedido.

---

## 2. Princípio do Menor Privilégio (PoLP)

* **Permissões Mínimas Necessárias:** Nenhuma conta de usuário ou serviço deve ter acesso superior ao estritamente necessário para sua função.
* **Acesso Just-in-Time (JIT):** Elevações de acesso de desenvolvedores ao ambiente de produção devem ser temporárias, automatizadas e com auditoria atrelada a um chamado de incidente ou mudança.
* **Proibição de Chaves Permanentes:** Eliminação do uso de `AWS_ACCESS_KEY_ID` permanentes em ambientes locais ou repositórios.

---

## 3. Matriz de Controle de Acesso Baseada em Papéis (RBAC)

| Papel / Role | Ambiente | Nível de Acesso | Método de Autenticação |
| :--- | :--- | :--- | :--- |
| **Desenvolvedor** | Staging / Dev | Read / Write | IdP com MFA Obrigatório |
| **Desenvolvedor** | Produção | Read-Only (Logs/Métricas) | IdP com MFA + SSO em Vault |
| **Pipeline de CI/CD** | Produção | Deployment de Artefatos | OIDC (OpenID Connect / Short-lived Tokens) |
| **SRE On-Call** | Produção | Admin Temporário (JIT) | Aprovação Automática via Chamado/Incident |