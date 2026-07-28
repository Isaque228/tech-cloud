# Amazon Web Services (AWS)

AWS é o provedor de nuvem pública com maior participação de mercado, oferecendo mais de 200 serviços que cobrem desde infraestrutura básica até inteligência artificial. Lançada em 2006 com S3 e EC2, se tornou referência de arquitetura em nuvem e é frequentemente o ponto de partida para quem estuda cloud computing.

## Conceitos principais
- **EC2 (Elastic Compute Cloud)**: máquinas virtuais sob demanda, com diversos tipos de instância otimizados para CPU, memória, GPU ou custo.
- **S3 (Simple Storage Service)**: armazenamento de objetos altamente durável (11 noves), usado para backups, data lakes e hospedagem de arquivos estáticos.
- **VPC (Virtual Private Cloud)**: rede virtual isolada onde os recursos são provisionados, com sub-redes, tabelas de rotas e gateways.
- **IAM (Identity and Access Management)**: controle granular de quem pode acessar o quê, via usuários, grupos, roles e políticas.
- **RDS e DynamoDB**: bancos relacionais gerenciados (RDS) e banco NoSQL serverless de alta performance (DynamoDB).
- **Lambda**: computação serverless que executa código em resposta a eventos, sem provisionar servidores.
- **CloudFormation / CDK**: infraestrutura como código para provisionar recursos de forma declarativa e repetível.
- **Regiões, Zonas de Disponibilidade e Edge Locations**: estrutura geográfica global usada por CloudFront (CDN) e para arquiteturas resilientes.
- **CloudWatch**: serviço nativo de métricas, logs e alarmes para observabilidade.

## Na prática
Um caso típico é uma aplicação web com EC2 ou containers em ECS/EKS atrás de um Application Load Balancer, dados em RDS, arquivos estáticos e backups em S3, e Route 53 para DNS. Startups usam Lambda + API Gateway + DynamoDB para arquiteturas serverless de baixo custo operacional. Empresas com grandes volumes de dados usam S3 como data lake integrado a Athena, Glue e Redshift para analytics.

## Pontos de atenção
- Configurar buckets S3 como públicos por engano é uma das causas mais comuns de vazamento de dados na nuvem.
- Instâncias EC2 esquecidas rodando (orphaned resources) geram custo desnecessário — usar tags e Cost Explorer para monitorar.
- Políticas IAM excessivamente permissivas (uso de `*` em Action/Resource) violam o princípio do menor privilégio.
- Ignorar Reserved Instances, Savings Plans ou Spot Instances quando a carga é previsível resulta em gasto muito acima do necessário.
