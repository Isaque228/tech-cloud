# Storage (Armazenamento em Nuvem)

Storage é a categoria de serviços responsável por guardar dados de forma durável e acessível na nuvem, com diferentes formatos otimizados para diferentes padrões de acesso: arquivos, blocos ou objetos. Escolher o tipo certo de storage impacta diretamente custo, performance e complexidade da arquitetura.

## Conceitos principais
- **Object Storage**: armazena dados como objetos (arquivo + metadados) acessados via API HTTP, ideal para arquivos não estruturados em larga escala (S3, Azure Blob, Cloud Storage).
- **Block Storage**: volumes de disco de baixa latência anexados a instâncias de computação, usados para sistemas de arquivos e bancos de dados (EBS, Azure Disks, Persistent Disk).
- **File Storage**: sistemas de arquivos compartilhados via protocolos como NFS/SMB, acessíveis por múltiplas instâncias simultaneamente (EFS, Azure Files).
- **Classes de armazenamento (tiers)**: níveis de custo/performance baseados na frequência de acesso — hot, cool/infrequent, archive/cold.
- **Durabilidade vs. disponibilidade**: durabilidade mede a chance de não perder o dado (ex: 99,999999999%); disponibilidade mede o tempo em que o dado está acessível.
- **Replicação**: cópia de dados entre zonas ou regiões para resiliência (replicação local, entre zonas, geo-redundante).
- **Ciclo de vida (lifecycle policies)**: regras automáticas para mover ou expirar dados entre tiers conforme a idade ou uso.
- **Criptografia em repouso e em trânsito**: proteção dos dados armazenados e durante a transferência, nativa na maioria dos serviços.

## Na prática
Sites estáticos e backups usam object storage pela durabilidade e custo baixo. Bancos de dados e VMs usam block storage para volumes de baixa latência. Ambientes com múltiplos servidores que precisam compartilhar arquivos (ex: CMS, renderfarms) usam file storage. Data lakes modernos são construídos quase inteiramente sobre object storage (S3, GCS, ADLS) combinados com ferramentas de catálogo e query engine.

## Pontos de atenção
- Deixar buckets/containers de object storage com acesso público sem necessidade é uma das causas mais recorrentes de incidentes de segurança.
- Não configurar lifecycle policies resulta em dados antigos acumulando custo em tiers caros indefinidamente.
- Confundir durabilidade com backup: dados corrompidos ou deletados por erro humano ainda podem ser perdidos sem versionamento ativado.
- Latência de block storage de rede pode ser um bottleneck não percebido até a carga de produção aumentar.
