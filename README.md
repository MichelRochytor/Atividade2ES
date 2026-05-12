# Entregas da Parte 1 (Aula 1)

## Tarefa 1.1, Proposta de Tema

**Domínio:** Gestão de Inventário e Manutenção Preventiva para Equipes de Robótica de Competição.

**Descrição:** O sistema resolve a desorganização no rastreio de componentes eletrônicos de alto valor e a ausência de um histórico centralizado de manutenção dos robôs. Em equipes de robótica universitária, a alta rotatividade de membros e o uso compartilhado de laboratórios geram perda constante de peças e falhas críticas em competições por falta de um plano de manutenção preventiva.

**Usuários Principais:** Diretores de categoria e membros técnicos da equipe de hardware.

**Relevância:** O controle eficiente garante a confiabilidade do hardware em eventos de alto desempenho, reduz custos com reposição de itens "perdidos" e preserva o conhecimento técnico entre diferentes gestões da equipe.

**Minha reflexão:**
Ao escolher este tema, busquei um domínio com delimitação clara de escopo, evitando sistemas genéricos. A complexidade aqui não reside no volume de dados, mas na criticidade da integridade dos componentes; um erro no inventário ou a falta de uma manutenção registrada pode significar uma falha mecânica fatal durante uma competição nacional.


## Tarefa 1.2, Planejamento de Entrevista

**Objetivo da entrevista:**
O objetivo desta entrevista é compreender detalhadamente os gargalos no gerenciamento de hardware da equipe de robótica. Buscamos identificar como o controle atual sobre os componentes eletrônicos afeta as rotinas de montagem, a manutenção preventiva e o tempo de resposta a falhas, a fim de projetar um sistema que mitigue a perda de peças e a perda de conhecimento técnico entre as diferentes gestões da equipe.

**Roteiro de Entrevista:**

*Perguntas de Compreensão do Problema:*
1. Como você descreveria o processo que ocorre hoje quando você precisa localizar um componente específico (como um driver de motor ou sensor) que teoricamente a equipe já possui em estoque?
2. Quais são os principais motivos, na sua visão, que levam à perda física ou à queima não documentada de componentes críticos durante o desenvolvimento de um projeto?
3. Como o desconhecimento sobre o estado atual das peças (se estão funcionando perfeitamente, com defeito parcial ou emprestadas) impacta o prazo de montagem e entrega do robô para as competições?

*Perguntas de Fluxos de Trabalho e Rotinas:*
1. Quando você está no laboratório e constata que um componente queimou durante os testes práticos, qual é o fluxo exato que você segue hoje para relatar essa baixa e solicitar reposição?
2. Qual é a rotina atual da sua categoria para fazer a conferência (check-in/check-out) dos materiais de hardware antes de viajar para um evento e logo após o retorno?

*Perguntas de Frustrações e Limitações:*
1. Pensando nas ferramentas usadas hoje para controle de ativos (como planilhas soltas ou mensagens perdidas em grupos), qual é a maior limitação delas no seu dia a dia técnico?
2. Qual é a sua maior frustração ao tentar realizar a manutenção corretiva em um robô que foi projetado e montado por membros de gestões passadas sem nenhuma documentação atualizada de hardware?

*Pergunta de Encerramento:*
1. Se o novo sistema pudesse automatizar ou facilitar de forma impecável apenas uma única etapa do seu trabalho com a gestão de hardware da equipe, qual recurso seria o mais valioso para você?

**Minha reflexão:**
A elaboração deste roteiro evidenciou que o desafio não é estritamente financeiro (a simples compra de novas peças), mas sim de fluxo de informação e retenção de conhecimento institucional. As perguntas focadas em rotinas e frustrações tentam mapear o ponto exato onde o método manual atual falha – geralmente na pressa do laboratório, durante a transição de membros ou na ausência de documentação de legado. O roteiro foi desenhado para extrair não apenas "o que" o usuário quer, mas "como" ele interage com o hardware físico na prática, garantindo que o software a ser desenvolvido se adapte ao fluxo real da oficina, evitando as respostas genéricas e o distanciamento do problema real propostos pelo enunciado da atividade.

## Tarefa 1.3, Histórias de Usuário

**História 1: Busca e Localização de Componentes**
**Como** Membro de Hardware, **quero** consultar a disponibilidade e a localização física exata de um componente (ex: driver TB6612FNG) no laboratório **para** agilizar a montagem do robô da categoria VSSS.
* **Critérios de Aceitação:**
  * O sistema deve permitir a busca por nome técnico ou por categoria do item (ex: Motores, Sensores).
  * O resultado da busca deve exibir a quantidade total em estoque e a quantidade atualmente disponível.
  * O sistema deve indicar a localização física registrada do item (ex: "Armário 2, Gaveta B").
* **Prioridade:** Alta. Justificativa: É a funcionalidade central do sistema; sem ela, os membros continuarão perdendo tempo procurando peças fisicamente no laboratório, o que trava o fluxo de montagem.

**História 2: Registro de Falha ou Queima de Hardware**
**Como** Integrante da Equipe, **quero** registrar a queima de um componente anexando uma breve descrição do defeito **para** alertar a diretoria sobre a necessidade imediata de reposição ou reparo.
* **Critérios de Aceitação:**
  * O usuário deve conseguir selecionar o item defeituoso a partir do inventário ativo.
  * O formulário deve conter um campo obrigatório para descrever as circunstâncias da falha.
  * O status do item no sistema deve ser atualizado automaticamente para "Defeituoso/Queimado".
* **Prioridade:** Alta. Justificativa: Evita que componentes avariados sejam acidentalmente reutilizados em novos projetos, o que poderia causar falhas em cascata no circuito do robô.

**História 3: Consulta ao Histórico de Manutenção**
**Como** Diretor de Categoria, **quero** visualizar o histórico de trocas de peças de um robô específico **para** identificar se há um problema elétrico crônico causando queimas frequentes.
* **Critérios de Aceitação:**
  * O sistema deve listar cronologicamente todas as intervenções e substituições feitas em um robô.
  * Cada registro deve identificar o membro responsável pela manutenção e a data da ocorrência.
  * Deve ser possível filtrar o histórico por componente específico.
* **Prioridade:** Média. Justificativa: É essencial para a análise técnica e o diagnóstico de falhas de projeto a longo prazo, mas não impede a operação básica diária de controle de estoque.

**História 4: Gestão de Ativos para Competições (Check-out/Check-in)**
**Como** Líder de Projeto, **quero** gerar uma lista de check-out dos componentes e ferramentas levados para a Copa Pinhão **para** garantir que todos os itens retornem ao laboratório após o evento.
* **Critérios de Aceitação:**
  * O sistema deve permitir a criação de um evento temporário e a alocação de itens a ele.
  * Deve possuir caixas de seleção (checkboxes) separadas para a saída (check-out) e para o retorno (check-in).
  * O sistema deve gerar um alerta visual para itens que saíram, mas não tiveram o retorno confirmado.
* **Prioridade:** Média. Justificativa: Tem altíssimo valor logístico durante a temporada de competições para evitar a perda definitiva de patrimônio, mas é utilizada com menor frequência durante o semestre letivo.

**História 5: Cadastro Técnico de Novos Lotes**
**Como** Diretor de Categoria, **quero** cadastrar um novo lote de peças vinculando o link do datasheet **para** garantir que os calouros e novos membros tenham acesso rápido às especificações técnicas corretas.
* **Critérios de Aceitação:**
  * O formulário de cadastro deve exigir os campos de nome, modelo, fabricante e quantidade inicial.
  * O sistema deve possuir um campo de URL válido para a inserção da documentação técnica (datasheet).
  * O sistema deve gerar e atribuir um código de identificação (ID) único para o lote cadastrado.
* **Prioridade:** Alta. Justificativa: É o requisito estrutural do sistema; sem a entrada correta de dados técnicos, as demais histórias de usuário não possuem informações precisas para operar.

**Minha reflexão:**
Ao redigir estas histórias baseadas nas respostas da entrevista, percebi que o sistema precisa ir além de um simples "contador de estoque". As histórias refletem uma necessidade de rastreabilidade e de retenção de conhecimento institucional (como anexar datasheets e registrar históricos de queima). Isso resolve a dor específica mapeada no roteiro de entrevistas: a perda de controle causada pela alta rotatividade de membros da equipe e a falta de documentação de legado.

## Tarefa 1.4, Validação de Requisitos

**Técnica aplicada:** Verificação de completude e consistência.

**Análise da História 2: Registro de Falha ou Queima de Hardware**
**Ambiguidades nos critérios de aceitação:** O termo "breve descrição" é vago. É necessário definir se será um campo de texto livre (sujeito a descrições incompletas como "parou de funcionar") ou uma lista padronizada de sintomas (ex: "curto-circuito", "dano físico"). Além disso, o critério de atualizar o status automaticamente não define se o item continua contabilizado no patrimônio total da equipe.
**Conflitos potenciais:** Pode haver conflito com a **História 1**. Se o item for marcado como "Defeituoso", ele deve desaparecer completamente da busca de disponibilidade ou aparecer com uma tag de alerta? Se desaparecer, a equipe pode achar que não possui a peça e comprar outra desnecessariamente.
**Informações a elucidar com o usuário:** Precisamos confirmar com a diretoria se qualquer membro tem permissão para "dar baixa" em um componente ou se o registro feito por um membro comum exige a aprovação posterior de um Diretor de Hardware para evitar baixas acidentais.

**Análise da História 4: Gestão de Ativos para Competições (Check-out/Check-in)**
**Ambiguidades nos critérios de aceitação:** A história menciona "caixas de seleção (checkboxes)" para o retorno. Isso pressupõe devoluções binárias (devolveu tudo ou não devolveu nada), mas não cobre o cenário de devolução parcial (ex: levaram 10 sensores ópticos, mas retornaram apenas 8). 
**Conflitos potenciais:** Durante o período em que os itens estão em "check-out" para o evento, como eles devem ser exibidos na **História 1**? Há um risco do sistema apontar que a peça está no armário quando, na verdade, está em viagem.
**Informações a elucidar com o usuário:** Qual é a tolerância de tempo após o término da competição para que o sistema gere o alerta de "item não retornado"? E quem recebe esse alerta (o líder do projeto ou todos os diretores)?

**Minha reflexão:**
**Revisão Crítica:** Dentre as 5 histórias mapeadas, se o escopo precisasse ser reduzido pela metade, eu removeria a **História 4 (Gestão de Ativos para Competições)**.Embora o controle logístico para viagens seja valioso, a ausência dessa funcionalidade pode ser mitigada temporariamente com planilhas de controle durante as raras semanas de eventos. Remover qualquer uma das outras histórias comprometeria a integridade do inventário diário e do histórico de manutenção do laboratório, que são o núcleo de valor do software para a sobrevivência técnica dos projetos da equipe.

