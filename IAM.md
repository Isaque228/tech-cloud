# IAM (Identity and Access Management)

IAM é o conjunto de serviços e práticas que controlam quem (identidade) pode fazer o quê (permissão) sobre quais recursos na nuvem. É a camada de segurança mais crítica de qualquer ambiente cloud, já que a maioria dos incidentes de segurança na nuvem tem origem em configurações de acesso incorretas, não em falhas de infraestrutura do provedor.

## Conceitos principais
- **Usuários, grupos e roles (papéis)**: identidades individuais, coleções de usuários e conjuntos de permissões que podem ser assumidos temporariamente por pessoas ou serviços.
- **Políticas (policies)**: documentos (geralmente JSON) que definem quais ações são permitidas ou negadas sobre quais recursos.
- **Princípio do menor privilégio**: conceder apenas as permissões estritamente necessárias para a função, nada além disso.
- **MFA (Multi-Factor Authentication)**: camada adicional de autenticação além da senha, essencial para contas privilegiadas.
- **Service accounts / roles de serviço**: identidades usadas por aplicações e serviços (não pessoas) para acessar outros recursos de forma segura.
- **Federação de identidade e SSO**: integração com provedores externos (Active Directory, Okta, Google Workspace) para autenticação centralizada.
- **Credenciais temporárias (STS/token)**: tokens de curta duração usados no lugar de chaves de acesso permanentes, reduzindo risco de exposição.
- **Políticas baseadas em recurso vs. baseadas em identidade**: permissões atribuídas diretamente ao recurso (ex: bucket policy) versus atribuídas ao usuário/role.
- **Auditoria de acessos**: logs de quem fez o quê e quando (AWS CloudTrail, Azure Activity Log, Cloud Audit Logs).

## Na prática
Aplicações rodando em EC2/VMs devem usar roles/service accounts anexadas à instância em vez de chaves de acesso fixas no código. Equipes corporativas integram IAM com Active Directory/Entra ID via federação para que o mesmo login corporativo controle acesso à nuvem. Ambientes com múltiplas contas usam roles assumidas entre contas (cross-account) para permitir acesso controlado sem duplicar usuários.

## Pontos de atenção
- Chaves de acesso (access keys) hardcoded em código ou repositórios são uma das causas mais comuns de comprometimento de contas na nuvem.
- Conceder permissões de administrador "temporariamente" e nunca revogar é um padrão recorrente de risco acumulado.
- Contas root/de conta principal devem ter MFA obrigatório e uso restrito apenas a operações que realmente exigem esse nível.
- Falta de revisão periódica de permissões (access review) permite que privilégios desnecessários se acumulem ao longo do tempo.
