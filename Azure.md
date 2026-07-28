# Microsoft Azure

Azure é a plataforma de nuvem da Microsoft, com forte adoção em empresas que já usam o ecossistema Microsoft (Windows Server, Active Directory, .NET, Microsoft 365). É a segunda maior nuvem pública do mundo e se destaca pela integração híbrida com datacenters on-premises via Azure Arc e Azure Stack.

## Conceitos principais
- **Azure Virtual Machines**: instâncias de computação sob demanda, equivalentes ao EC2 da AWS, com suporte nativo a Windows e Linux.
- **Azure Storage (Blob, File, Queue, Table)**: família de serviços de armazenamento, sendo o Blob Storage o equivalente ao S3.
- **Azure Virtual Network (VNet)**: rede virtual isolada para provisionar recursos, com subnets, NSGs (Network Security Groups) e peering.
- **Azure Active Directory (Entra ID)**: serviço de identidade e gerenciamento de acesso integrado ao ecossistema Microsoft, essencial para SSO corporativo.
- **Azure SQL Database e Cosmos DB**: banco relacional gerenciado e banco NoSQL multimodelo com distribuição global.
- **Azure Functions**: computação serverless orientada a eventos, equivalente ao Lambda.
- **Resource Groups**: unidade lógica que agrupa recursos relacionados para gerenciamento, cobrança e controle de acesso conjunto.
- **ARM Templates / Bicep**: infraestrutura como código nativa da Azure para provisionamento declarativo.
- **Azure Monitor**: plataforma unificada de métricas, logs e alertas, com Application Insights para APM.

## Na prática
Empresas que migram de datacenters Windows Server tradicionalmente escolhem Azure pela compatibilidade com Active Directory e licenciamento Microsoft (Hybrid Benefit). Aplicações corporativas .NET costumam usar App Service (PaaS) para deploy simplificado, com Azure SQL Database como backend. Cenários híbridos usam Azure Arc para gerenciar servidores on-premises com as mesmas ferramentas da nuvem.

## Pontos de atenção
- Confundir Resource Groups com fronteiras de rede — eles são apenas organizacionais/administrativos, não isolam tráfego.
- NSGs mal configurados podem expor portas de gerenciamento (RDP/SSH) publicamente.
- Custos de licenciamento (SQL Server, Windows Server) se somam ao custo de infraestrutura e são frequentemente subestimados.
- Não aproveitar Azure Policy e Azure Blueprints para governança resulta em ambientes inconsistentes entre times.
