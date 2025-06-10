README - Monitoramento de Inadimplência por Proximidade Geográfica
Visão Geral
Este notebook identifica veículos com serviços de inadimplência abertos que estão fisicamente próximos às filiais (dentro de 500 metros), gerando alertas para os gestores regionais via Microsoft Teams.

Pré-requisitos
Acesso ao Google BigQuery

Python 3.7+

Pacotes necessários:

bash
pip install google-cloud-bigquery pymsteams
Funcionalidades Principais
1. Cálculo de Distância Geográfica
Utiliza a fórmula de Haversine para calcular distâncias entre coordenadas

Considera um raio de 0.5km (500 metros) como critério de proximidade

2. Fluxo de Processamento
Consulta no BigQuery por serviços de inadimplência abertos no dia atual

Compara localização dos veículos com as coordenadas das filiais

Identifica veículos próximos às filiais

Agrupa resultados por gestor regional

Envia notificações via Microsoft Teams

3. Estrutura de Dados
filiais_mottu: Lista completa de todas as filiais com suas coordenadas geográficas

mapeamento_gestores: Relacionamento entre filiais e gestores regionais

webhooks_gestores: URLs para envio de mensagens no Teams

Configurações
RAIO_KM = 0.5: Define o raio de proximidade (em quilômetros)

A consulta SQL filtra por:

Serviços do tipo "Inadimplência"

Status "Aberto"

Data atual

Saída do Sistema
Para cada gestor regional, o sistema envia uma mensagem contendo:

Número de filiais com veículos próximos

Total de veículos identificados

Lista detalhada por filial, incluindo:

Placa do veículo

Distância da filial (em km)

Personalização
Para adaptar o código:

Atualize filiais_mottu com novas filiais/coordenadas

Ajuste mapeamento_gestores conforme mudanças organizacionais

Modifique RAIO_KM para alterar o critério de proximidade

Atualize webhooks_gestores com novos canais de comunicação

Execução
O notebook é projetado para execução diária, analisando os dados do dia corrente.
