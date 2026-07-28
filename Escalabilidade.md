# Escalabilidade em Nuvem

Escalabilidade é a capacidade de um sistema ajustar sua capacidade de processamento para atender variações de demanda, sem degradar performance nem desperdiçar recursos. Na nuvem, escalabilidade é uma das principais promessas de valor: pagar apenas pelo necessário e crescer (ou reduzir) de forma quase instantânea.

## Conceitos principais
- **Escalabilidade vertical (scale up/down)**: aumentar ou reduzir a capacidade de uma única instância (mais CPU/memória), com limite físico e geralmente exige reinicialização.
- **Escalabilidade horizontal (scale out/in)**: adicionar ou remover instâncias/réplicas para distribuir a carga, sem limite prático e sem downtime.
- **Autoscaling**: mecanismo automático que adiciona ou remove recursos com base em métricas (CPU, memória, fila, requisições por segundo).
- **Load balancing**: pré-requisito para escalabilidade horizontal eficaz, distribuindo tráfego entre as instâncias disponíveis.
- **Stateless vs. stateful**: aplicações sem estado local são muito mais fáceis de escalar horizontalmente do que aplicações que guardam estado na instância.
- **Escalonamento preditivo vs. reativo**: reativo responde a métricas em tempo real; preditivo antecipa picos com base em padrões históricos (ex: Black Friday).
- **Throttling e rate limiting**: controle de taxa de requisições para proteger o sistema contra sobrecarga, mesmo com autoscaling ativo.
- **Escalabilidade de dados**: sharding, partitioning e réplicas de leitura para escalar bancos de dados além de um único servidor.

## Na prática
Aplicações web tipicamente usam Auto Scaling Groups (AWS), VM Scale Sets (Azure) ou Managed Instance Groups (GCP) atrás de um load balancer, escalando com base em CPU ou requisições por segundo. Sistemas de mensageria (SQS, Service Bus, Pub/Sub) desacoplam produtores e consumidores, permitindo que o processamento escale independentemente da ingestão. Bancos de dados como DynamoDB e Cosmos DB escalam horizontalmente de forma nativa via particionamento automático.

## Pontos de atenção
- Aplicações stateful (sessão guardada em memória local) impedem escalonamento horizontal eficaz — mover estado para cache externo (Redis) resolve.
- Autoscaling mal configurado (thresholds muito sensíveis) pode causar oscilação constante de instâncias (flapping), aumentando custo e instabilidade.
- Escalar computação sem escalar o banco de dados na mesma proporção move o bottleneck, não o resolve.
- Testes de carga (load testing) antes de eventos de pico são essenciais — autoscaling não é instantâneo e tem tempo de provisionamento.
