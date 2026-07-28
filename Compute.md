# Compute (Computação em Nuvem)

Compute é a categoria de serviços que fornece capacidade de processamento — CPU, memória e execução de código — sob demanda. É o núcleo de qualquer nuvem, com opções que vão de máquinas virtuais tradicionais até funções serverless que executam por milissegundos, cada uma com um trade-off diferente entre controle, custo e esforço operacional.

## Conceitos principais
- **Máquinas Virtuais (VMs)**: unidades de computação com sistema operacional completo, controle total sobre o ambiente (ex: EC2, Azure VM, Compute Engine).
- **Containers**: empacotam aplicação e dependências em uma unidade leve e portátil, compartilhando o kernel do host (Docker é o padrão de fato).
- **Orquestração de containers**: ferramentas como Kubernetes (EKS, AKS, GKE) gerenciam deploy, escalonamento e recuperação de containers em cluster.
- **Serverless / FaaS (Function as a Service)**: código executado em resposta a eventos, sem gerenciar servidores, com cobrança por execução (Lambda, Azure Functions, Cloud Functions).
- **PaaS de aplicação**: plataformas que abstraem infraestrutura para deploy direto de código (App Service, Elastic Beanstalk, App Engine).
- **Autoscaling**: ajuste automático da quantidade de instâncias/recursos com base em métricas de carga.
- **Bare metal na nuvem**: servidores físicos dedicados oferecidos por alguns provedores para cargas que exigem isolamento total ou licenciamento específico.
- **Spot/Preemptible instances**: capacidade computacional ociosa vendida com grande desconto, sujeita a interrupção pelo provedor.

## Na prática
Aplicações legadas costumam ser hospedadas em VMs por compatibilidade. Microsserviços modernos tendem a usar containers orquestrados por Kubernetes para portabilidade e escalonamento fino. Cargas orientadas a eventos (processamento de imagem, webhooks, ETL leve) se beneficiam de serverless pelo custo quase zero em ociosidade. Workloads batch tolerantes a falha (treinamento de ML, processamento de big data) frequentemente usam Spot Instances para reduzir custo em até 90%.

## Pontos de atenção
- Cold start em funções serverless pode adicionar latência perceptível em aplicações sensíveis a tempo de resposta.
- Superdimensionar VMs "por segurança" é uma das principais causas de desperdício de custo em nuvem.
- Containers sem limites de CPU/memória definidos podem competir por recursos e degradar todo o cluster (noisy neighbor).
- Usar Spot Instances para cargas stateful sem estratégia de checkpoint pode causar perda de trabalho quando a instância é revogada.
