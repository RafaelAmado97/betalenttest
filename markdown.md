### Plano de Testes - Sauce Demo

### 1 Introdução

Este documento detalha o plano de testes, os resultados obtidos, as sugestões de melhorias e os problemas encontrados na plataforma Sauce Demo. O objetivo é garantir que os principais fluxos estejam funcionando corretamente antes da aplicação ser lançada em produção.

### 2 Plano de Testes

### 2.1 Objetivo

Validar os principais fluxos da aplicação Sauce Demo, identificar erros funcionais e problemas de experiência do usuário (UX/UI) que possam impactar a usabilidade e eficiência do sistema.

### 2.2 Escopo dos Testes

Os seguintes cenários foram abordados:

Login com diferentes tipos de usuários.
Ordenação e filtragem de produtos.
Fluxo completo de compra.
Remoção de itens do carrinho.
Navegação entre páginas.
Logout.

### 2.3 Ambiente de Teste

URL: https://www.saucedemo.com
Navegadores testados: Chrome, Firefox.
Dispositivos: Desktop (Windows/Mac), Mobile (opcional).
Dados de Teste:
Usuários: standard_user, locked_out_user, problem_user, performance_glitch_user, error_user, visual_user
Senha: secret_sauce

### 3 Resultados dos Testes

### 3.1 Cenário 1: Login com diferentes tipos de usuários

Problema encontrado: Ao tentar logar com senha ou usuário inválido, a mensagem de erro não exibe o emoji corretamente, mostrando "Epic sadface: ...".
Usuário 1 (standard_user): Login bem-sucedido.
Usuário 2 (locked_out_user): Mensagem correta, mas sem exibição do emoji.
Usuário 3 (problem_user): Login bem-sucedido, mas com problemas de navegação e UI detalhados a seguir.
Usuário 4 (performance_glitch_user): Login lento, mas bem-sucedido.
Usuário 5 (error_user): Login bem-sucedido, mas apresentou problemas específicos em filtros e carrinho.
Usuário 6 (visual_user): Login bem-sucedido, mas com desalinhamentos na interface.

### 3.2 Cenário 2: Ordenação e filtragem de produtos

A ordenação só funciona no filtro padrão carregado pela página: "Name (A to Z)".
Para o usuário error_user, a tentativa de ordenação exibe a mensagem de erro:
"Sorting is broken! This error has been reported to Backtrace."

### 3.3 Cenário 3: Fluxo completo de compra

Usuários 3, 5: Campos de formulário (Last Name) afetam outros campos (First Name) no checkout, tornando impossível concluir a compra.
O campo "Zip-code" aceita entradas inválidas devido à ausência de máscara de validação.

### 3.4 Cenário 4: Problemas gerais de UI/UX

Produtos com descrições contendo funções não traduzidas, como Test.allTheThings().
Produtos com fotos inconsistentes (usuário problem_user).
Desalinhamento de botões e ícones no menu (visual_user).

### 4. Sugestões de Melhorias

### 4.1 Funcionais

Implementar máscaras nos campos de formulário, especialmente "Zip-code".
Revisar mensagens de erro no login para exibir emojis corretamente.
Garantir que todos os produtos sejam selecionáveis no carrinho.

### 4.2 Visuais

Alinhar botões e ícones no menu e no checkout.
Corrigir descrições e nomes de produtos para evitar exibição de código não traduzido.

### 5. Lista de Bugs Encontrados

Mensagens de erro sem emojis: "Epic sadface: ...".
Fotos inconsistentes em produtos: Todos os produtos exibem a foto de um cachorro (problem_user).
Filtros de ordenação quebrados: Apenas o filtro padrão funciona.
Desalinhamento de UI: Ícones e botões desalinhados (visual_user).
Formulário de checkout: Campos interferem uns nos outros, impossibilitando a conclusão da compra.
Ausência de máscaras em campos de formulário: O campo "Zip-code" aceita entradas inválidas.

### 6. Análise de Riscos:

### 6.1 Risco:

        Mensagens de erro pouco informativas.
       Impacto:
        Média
       Probabilidade:
        Alta
       Mitigação:
        Ajustar conteúdo das mensagens

### 6.2 Risco:

         Problemas no checktout.
        Impacto:
         Alta
        Probabilidade:
         Alta
        Mitigação:
         Revisar lógica do fórmulário

### 6.3 Risco:

         Falhas em filtros e ordenação.
        Impacto:
         Alta
        Probabilidade:
         Média
        Mitigação:
         Testar e corrigir todos os filtros.
