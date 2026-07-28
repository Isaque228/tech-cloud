# Redes em Nuvem

Redes na nuvem definem como os recursos se comunicam entre si, com a internet e com ambientes on-premises. Diferente de datacenters físicos, a rede na nuvem é virtualizada e definida por software (SDN), permitindo criar topologias complexas e seguras via configuração, sem cabos ou switches físicos.

## Conceitos principais
- **VPC/VNet (Virtual Private Cloud/Network)**: rede virtual isolada e privada onde os recursos do cliente são provisionados.
- **Subnets**: divisões de uma VPC, geralmente separadas em públicas (com acesso à internet) e privadas (sem acesso direto).
- **Gateways**: Internet Gateway (saída/entrada pública), NAT Gateway (saída de recursos privados sem exposição de entrada).
- **Security Groups / NSGs / Firewall Rules**: regras de firewall aplicadas a instâncias ou subnets para controlar tráfego de entrada e saída.
- **Load Balancers**: distribuem tráfego entre múltiplas instâncias para escalabilidade e resiliência (ALB/NLB, Azure Load Balancer, Cloud Load Balancing).
- **VPN e Direct Connect/ExpressRoute**: conexões seguras entre a nuvem e ambientes on-premises, via internet criptografada ou circuito dedicado.
- **Peering e Transit Gateway**: conectam múltiplas VPCs/VNets entre si ou centralizam a conectividade em topologias complexas (hub-and-spoke).
- **DNS gerenciado**: serviços como Route 53, Azure DNS e Cloud DNS resolvem nomes de domínio e podem implementar roteamento inteligente (latência, geolocalização).
- **CDN (Content Delivery Network)**: distribui conteúdo em cache próximo ao usuário final para reduzir latência (CloudFront, Azure CDN, Cloud CDN).

## Na prática
Uma arquitetura típica de três camadas usa subnets públicas para load balancers, subnets privadas para aplicação e subnets isoladas para banco de dados, com NAT Gateway permitindo saída à internet sem exposição. Empresas com múltiplas contas/ambientes usam Transit Gateway ou hub-and-spoke para centralizar conectividade e políticas de segurança. Aplicações com usuários globais usam CDN combinado a DNS com roteamento por latência.

## Pontos de atenção
- Expor bancos de dados ou instâncias de gerenciamento diretamente em subnets públicas é um erro crítico e recorrente.
- Regras de firewall abertas (0.0.0.0/0) em portas sensíveis (22, 3389, 3306) são um vetor de ataque comum.
- Overlap de blocos CIDR entre VPCs dificulta ou impede peering futuro — planejar o range de IPs desde o início.
- Custos de transferência de dados entre zonas/regiões e de NAT Gateway são frequentemente subestimados no orçamento.
