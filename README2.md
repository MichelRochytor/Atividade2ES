# Entregas da Parte 2 (Aula 2)

## Tarefa 2.1, Definição da Arquitetura

**Padrão Arquitetural Escolhido:** MVC (Model-View-Controller)

**Justificativa:**
O padrão MVC é ideal para este sistema pois separa a lógica de persistência de dados (Google Sheets) da interface de interação com o membro da equipe (Terminal/CLI). Como o sistema será o único ponto de entrada para a planilha, o Controller atua como um "porteiro", garantindo que apenas dados validados cheguem ao Model. Além disso, essa estrutura permite que, no futuro, a View seja substituída por uma interface gráfica ou web sem a necessidade de reescrever a lógica de gerenciamento de estoque.

**Representação dos Componentes e Relacionamentos:**
1.  **View (Interface):** Solicita dados ao usuário (ex: ID da peça) e exibe as respostas processadas.
2.  **Controller (Lógica):** Recebe o comando da View, valida se a quantidade em estoque é suficiente ou se o ID existe, e aciona o Model.
3.  **Model (Dados):** Contém a lógica de conexão com a API do Google Sheets e realiza as operações de leitura e escrita nas colunas da planilha.

**Principais Componentes e Responsabilidades:**
* `InventarioView`: Gerencia o menu interativo e a formatação de tabelas no terminal.
* `EstoqueController`: Processa as regras de negócio (ex: não permitir baixa de item com estoque zero) e coordena o fluxo entre View e Model.
* `GoogleSheetsModel`: Encapsula a autenticação e as chamadas de API para o Google Drive/Sheets, tratando os dados brutos da planilha como objetos do sistema.

**Limitação ou Trade-off da Arquitetura:**
O principal trade-off do MVC neste contexto é a dependência de uma conexão síncrona com a API externa no Model. Como a View aguarda a resposta do Controller (que por sua vez aguarda o Model terminar a gravação no Google Sheets), qualquer instabilidade na rede ou latência na API do Google trava a interface do usuário, impedindo que o membro da equipe realize outras consultas enquanto a operação de escrita não é finalizada.

**Minha reflexão:**
Ao optar pelo MVC, priorizei a organização e a facilidade de manutenção para as próximas gestões da roboAp. Embora existam arquiteturas mais leves, o MVC força uma disciplina de código que evita o "código espaguete", onde regras de banco de dados e prints de tela ficam misturados. Isso garante que o software possa crescer de forma sustentável à medida que novas categorias da equipe passem a utilizá-lo.