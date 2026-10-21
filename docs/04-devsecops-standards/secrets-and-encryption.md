# Gestão de Segredos, TLS e Criptografia

---

## 1. Gestão de Segredos e Credenciais

* **Proibição de Segredos Estáticos:** Nenhuma senha, token ou chave privada pode estar contida diretamente no código fonte ou nos arquivos de configuração.
* **Gerenciamento Centralizado:** Uso obrigatório de cofres de segredos dinâmicos (HashiCorp Vault, AWS Secrets Manager ou Azure Key Vault).
* **Rotação Automática:** Todas as credenciais de bancos de dados e chaves de API devem ser rotacionadas automaticamente a cada 30 a 90 dias.

---

## 2. Padrões de Criptografia

```text
  [ Cliente ] 
      |  ( TLS 1.3 / mTLS )
      v
  [ Ingress / API Gateway ]
      |  ( mTLS via Service Mesh - Istio )
      v
  [ Microsserviço ] 
      |  ( AES-256 no armazenamento )
      v
  [ Banco de Dados Encrypt-at-Rest ]
```

### Dados em Trânsito (In Transit)
* **Tráfego Externo:** Exigência de **TLS 1.3** (mínimo TLS 1.2 com ciphers seguros).
* **Tráfego Interno (Service-to-Service):** Obrigatoriedade de **mTLS (Mutual TLS)** via Service Mesh.

### Dados em Repouso (At Rest)
* Padrão de criptografia **AES-256** para volumes de disco (EBS), snapshots, buckets S3 e colunas de dados sensíveis no banco de dados.