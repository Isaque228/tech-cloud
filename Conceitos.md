# Conceitos Fundamentais de Computação em Nuvem

Computação em nuvem é o modelo de entrega de recursos de TI (processamento, armazenamento, rede, bancos de dados, etc.) sob demanda, via internet, com cobrança baseada em uso. Em vez de comprar e manter hardware físico, empresas alugam capacidade de provedores como AWS, Azure e Google Cloud, ganhando agilidade, elasticidade e redução de custo operacional. Entender os modelos de serviço e de implantação é a base para todo o resto da área.

## Conceitos principais
- **IaaS (Infrastructure as a Service)**: fornece máquinas virtuais, redes e storage brutos; o cliente gerencia o sistema operacional e acima (ex: EC2, Azure VMs).
- **PaaS (Platform as a Service)**: fornece uma plataforma de execução (runtime, banco de dados gerenciado) sem o cliente precisar administrar servidores (ex: Elastic Beanstalk, App Engine).
- **SaaS (Software as a Service)**: entrega o software completo, pronto para uso final, via navegador ou API (ex: Gmail, Salesforce).
- **Modelo de responsabilidade compartilhada**: o provedor cuida da segurança "da nuvem" (infraestrutura física), o cliente cuida da segurança "na nuvem" (configuração, dados, acessos).
- **Elasticidade e escalabilidade**: capacidade de aumentar ou reduzir recursos automaticamente conforme a demanda, pagando só pelo que se usa.
- **Multi-tenancy**: vários clientes compartilham a mesma infraestrutura física de forma isolada logicamente.
- **Regiões e zonas de disponibilidade (AZs)**: unidades geográficas de infraestrutura usadas para reduzir latência e aumentar resiliência.
- **Nuvem pública, privada, híbrida e multicloud**: diferentes estratégias de onde e como os recursos são hospedados e combinados.
- **Pay-as-you-go**: modelo de cobrança por consumo real, sem investimento inicial em hardware (CapEx vira OpEx).

## Na prática
Empresas migram sistemas legados para IaaS como primeiro passo (lift-and-shift), depois evoluem para PaaS e serviços gerenciados para reduzir esforço operacional. Startups costumam nascer 100% em nuvem, usando serviços serverless e gerenciados desde o início para focar no produto em vez de infraestrutura. Bancos e governos frequentemente adotam nuvem híbrida, mantendo dados sensíveis on-premises e usando nuvem pública para cargas elásticas.

## Pontos de atenção
- Confundir "estar na nuvem" com "estar seguro por padrão" — a responsabilidade compartilhada exige configuração correta do cliente.
- Subestimar custos de saída de dados (data egress) ao mover grandes volumes entre provedores ou para on-premises.
- Não planejar a arquitetura para elasticidade real, replicando o modelo de datacenter fixo dentro da nuvem (deixando de aproveitar autoscaling).
- Vendor lock-in: uso excessivo de serviços proprietários pode dificultar migração futura entre provedores.
