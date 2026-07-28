# Google Cloud Platform (GCP)

O Google Cloud é a nuvem pública do Google, reconhecida pela forte base em dados, análise em larga escala e machine learning — herança direta da infraestrutura que sustenta Google Search, YouTube e Gmail. É frequentemente escolhido por empresas com cargas intensivas de dados, containers (o Google criou o Kubernetes) e IA.

## Conceitos principais
- **Compute Engine**: máquinas virtuais sob demanda, equivalente ao EC2/Azure VMs, com granularidade fina de custom machine types.
- **Cloud Storage**: armazenamento de objetos equivalente ao S3, com classes de armazenamento (Standard, Nearline, Coldline, Archive) para otimizar custo por frequência de acesso.
- **VPC do Google Cloud**: rede virtual global (diferente da AWS/Azure, uma VPC pode abranger múltiplas regiões nativamente).
- **IAM do GCP**: controle de acesso baseado em papéis (roles) atribuídos a contas de serviço, usuários e grupos, com granularidade em nível de recurso.
- **BigQuery**: data warehouse serverless para consultas SQL analíticas em petabytes de dados, sem gerenciamento de infraestrutura.
- **GKE (Google Kubernetes Engine)**: serviço gerenciado de Kubernetes, referência de mercado por ser mantido pelos criadores do projeto.
- **Cloud Functions / Cloud Run**: computação serverless orientada a eventos e containers serverless, respectivamente.
- **Projetos (Projects)**: unidade fundamental de organização e cobrança no GCP, análoga a contas/subscriptions em outros provedores.
- **Cloud Monitoring e Cloud Logging (ex-Stackdriver)**: observabilidade nativa integrada a todos os serviços.

## Na prática
Empresas de dados e analytics escolhem BigQuery para consultas ad-hoc sobre grandes volumes sem precisar gerenciar clusters. Times que já usam Kubernetes intensivamente preferem GKE pela maturidade e integração nativa. Cloud Run é muito usado para containers stateless que precisam escalar a zero, reduzindo custo em cargas intermitentes.

## Pontos de atenção
- A estrutura de Projetos pode gerar sprawl (excesso de projetos) sem uma boa organização hierárquica (Organization > Folders > Projects).
- Custos de BigQuery são cobrados por dado escaneado — queries sem filtro em tabelas particionadas podem gerar custos altos inesperados.
- Papéis de IAM muito amplos (como `roles/owner`) concedidos por conveniência violam o menor privilégio.
- Menor presença de datacenters físicos em algumas regiões comparado a AWS/Azure pode impactar latência e requisitos de residência de dados.
