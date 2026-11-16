================================================================================
SISTEMA DE GESTÃO COMUNITÁRIA DE MANTIMENTOS — AMABE (BAIRRO ESPERANÇA)
================================================================================
Associação de Moradores e Amigos do Bairro Esperança (AMABE)
Alinhamento Social: ODS 2 (Fome Zero e Agricultura Sustentável - Meta 2.1)
================================================================================

1. SOBRE O PROJETO
--------------------------------------------------------------------------------
O MVP da AMABE é uma aplicação web responsiva desenvolvida para digitalizar o 
controle de entrega de cestas básicas no galpão comunitário. O sistema substitui 
as fichas manuais de papel, agiliza o atendimento no balcão (meta < 90 segundos 
por família) e garante justiça distributiva através de uma trava automática que 
impede retiradas duplicadas no mesmo mês.

2. ESTRUTURA DO PROJETO E TELAS
--------------------------------------------------------------------------------
- Tela 1 (Menu Inicial): Ponto de entrada limpo com duas ações prioritárias 
  ("Atender Beneficiário" e "Novo Cadastro") e controle de sessão ("Sair").
- Tela 2 (Execução Central): Busca instantânea por CPF, visualização do 
  titular, registro da entrega da cesta e cadastro rápido de novas famílias.
- Tela 3 (Alertas e Resultados): Comprovante visual da operação (Sucesso ou 
  Bloqueio por Carência Mensal), contador mensal de cestas e botão de retorno.
- Banco de Dados (`amabe_database.sql`): Estrutura relacional MySQL 8.0+ com 
  índices de performance e restrição única mensal (`uk_trava_carencia_mensal`).

3. REQUISITOS TÉCNICOS E INSTALAÇÃO (AMBIENTE LOCAL / SERVIDOR)
--------------------------------------------------------------------------------
3.1. Pré-requisitos:
     - Servidor Web / Backend (Python FastAPI/Flask ou Node.js)
     - SGBD MySQL 8.0 ou superior
     - Navegador moderno (Chrome, Edge, Safari) em Smartphone, Tablet ou PC

3.2. Configuração do Banco de Dados:
     1) Acesse seu terminal MySQL ou cliente (MySQL Workbench / DBeaver).
     2) Execute o script `amabe_database.sql` para criar o banco `amabe_mvp`, 
        as tabelas (`operadores`, `beneficiarios`, `retiradas`) e os dados 
        iniciais de teste.
     3) Configure as variáveis de ambiente da aplicação com o usuário e senha 
        do banco de dados.

4. MANUAL RÁPIDO DE USO OPERACIONAL (GUIA PARA VOLUNTÁRIOS)
--------------------------------------------------------------------------------
PASSO 1 — ACESSO AO SISTEMA (TELA 1)
  1. Abra o sistema no navegador do celular ou computador do balcão.
  2. Informe seu usuário e senha de voluntário (ex.: `maria.gracas`).
  3. Na tela inicial, toque no cartão grande "ATENDER BENEFICIÁRIO".

PASSO 2 — CONSULTA E REGISTRO DE ENTREGA (TELA 2)
  1. Digite apenas os números do CPF do morador no campo "Buscar Beneficiário 
     por CPF" (a pontuação é inserida automaticamente).
  2. Toque no botão azul "PESQUISAR".
  3. Confira o nome completo do titular exibido na tela.
     * Nota: Se o CPF não estiver cadastrado, preencha os dados básicos na 
       seção "DADOS DO NOVO CADASTRO" na mesma tela.
  4. Toque no botão de confirmação na seção "REGISTRAR RETIRADA".

PASSO 3 — CONFERÊNCIA E PRÓXIMO ATENDIMENTO (TELA 3)
  1. Observe o banner central na tela:
     - BANNER VERDE ("Sucesso na Entrega"): Entrega autorizada! Libere a 
       cesta básica para o morador.
     - BANNER DE ALERTA ("Cesta já retirada neste mês"): Entrega bloqueada! 
       Informe ao morador que já consta uma retirada no mês atual e oriente-o 
       sobre a data do próximo mês.
  2. Toque no botão verde "NOVO ATENDIMENTO" para atender a próxima pessoa da fila.
  3. Ao encerrar o expediente, toque em "Sair" no canto superior direito.

5. ACESSIBILIDADE E BOAS PRÁTICAS (RNF04)
--------------------------------------------------------------------------------
- Todos os botões possuem área ampliada (>= 44x44px) para facilitar o toque.
- O sistema pode ser operado inteiramente via teclado utilizando a tecla `Tab` 
  e `Enter`.
- Nunca utilize dados reais de moradores em ambientes de demonstração ou teste.
================================================================================
