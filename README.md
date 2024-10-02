# Panfletero 2

Reedição do bot **Panfletero** usado no Twitter e Mastodon em meados de 2020 para distribuir conteúdo jornalístico independente.
A nova edição contará com milhares de novas fontes jornalísticas livres, permitirá filtragem por Estado e cidade, bem como por fontes de artigos e período.

## Proposta

O bot irá servir, de um repositório de mídias digitais curado por seu mantenedor, links para artigos publicados por essas mídias, sob demanda (através de comandos) e automaticamente, utilizando como interface a rede social Bluesky, através de perfis (@s) criados nessa rede para esse propósito. A demanda e suas configurações serão feitas através da função de Chat (DM) do perfil. Os links serão organizados em posts isolados e enviados automaticamente em períodos fixos do dia, todos os dias da semana.

## Arquitetura

[Em construção]

## Como usar o bot
- **Cada UF terá uma @ diferente, você poderá seguir as @s que tem interesse.**
    - As @s vão possuir o handler *UF.panfletero.piratariaonline.dev*, sendo "UF" o estado em questão.
        - Exemplo: *@MG.panfletero.piratariaonline.dev*
    - Por limitações técnicas, por enquanto só será possível se cadastrar para uma cidade por estado.
- **O bot não segue de volta, portanto sua @ precisa permitir receber DMs.**
    - Na interface do Bluesky, em *"Configurações"*, escolha *"Configurações de chat"* e na sessão *"Permitir mensagens de"*, escolha *"Usuário que eu sigo"* ou *"Todo mundo"*.
    - Se o bot não puder te responder por questões de configuração, seus comandos serão ignorados.
- **Os comandos devem ser usados na DM.**
    - Envie um comando por vez, apenas. Vários comandos encadeados serão ignorados, apenas o primeiro será considerado.
    - A API pode levar até 15 segundos para responder, seja paciente.
    - Há um sistema anti-spam, muitos comandos dados sequencialmente ou em intervalos de tempo exato/repetido suspende a atenção do bot ao usuário por algumas horas.
    - Se o comando for inválido, o bot não responderá nada.
    - Escreva o comando da forma exata descrita abaixo; isso é necessário para evitar manipulação de seu comportamento.
    - Qualquer mensagem enviada para o bot na DM que não seja os comandos abaixo, será ignorada.
    - Qualquer mensagem enviada sem estar seguindo o bot, será ignorada, mesmo que seja um comando.
- **Cardápio de comandos possíveis:**
    - `COMANDOS`: Use para receber essa lista de comandos. 
    - `LISTAR CIDADES`: Use para listar as cidades disponíveis no Estado em uma lista enumerada.
    - `CIDADE:X;Y;Z...`: Use para configurar o bot para te enviar artigos daquelas cidades quando solicitado (X,Y,Z... = os números das cidades na lista dada por `LISTAR CIDADES`).
    - `PERIODO:DD/MM;DD/MM`: Use para configurar o bot para filtrar os artigos por período; envie duas datas em formato DD/MM separadas por ponto-e-vírgula (aceita as palavras `hoje`, `ontem` ou `anteontem` no lugar da data). Ano máximo é o ano corrente.
    - `TERMOS:ABC;DEF;GHI...`: Use para configurar o bot para filtrar artigos por palavras chave; envie palavras separadas por ponto-e-vírgula.
    - `LISTAR FONTES`: Use para listar as mídias disponíveis para a cidade em uma lista enumerada.
    - `FONTES:X;Y;Z...`: Use para configurar o bot para filtrar as fontes dos artigos; não definir essa configuração faz o bot usar todas as fontes disponíveis, que pode gerar uma lista bem longa dependendo da(s) cidade(s).
    - `BUSCAR`: Use para receber a lista de artigos, de acordo com as configurações feitas; A lista pode ser bem grande; se atingir os limites de caracteres, será enviado mais de uma mensagem.

### Como contribuir
- **Você pode enviar um e-mail para panfleterobot@gmail.com com o título *"COLABORAÇÃO UF"*, trocando UF pelo estado, ou *"COLABORAÇÃO BOT"* para contribuição técnica;**
- **Cidades**
	- Envie novas entradas de cidades ou regiões da UF que você julga estar faltando no bot.
	- A entrada deve conter o nome completo da cidade conforme inscrito no IBGE.
	- Você precisa enviar junto, pelo menos uma fonte verificável, caso a cidade ainda não exista na listagem.
	- Revise também cidades que já existem e faltam fontes.
	- A adição ou revisão da cidade depende de revisão manual e não há prazo para conclusão nem certeza de aceite.
- **Fontes**
	- Envie fontes que você julga estar faltando na listagem do bot para determinada cidade ou região.
	- Revise fontes que já existem mas não estão funcionando, ou possuem conteúdo suspeito/impróprio.
	- A fonte deve ter um nome e um link acessível, de conteúdo público e livre, que não dependa de assinatura ou criação de conta para visualizar conteúdo.
	- A adição ou revisão da fonte depende de revisão manual e não há prazo para conclusão nem certeza de aceite.
- **Contrib. Técnica**
	- Será disponibilizado canal no repositório para envio de PRs.
	- Só serão revisados PRs relacionados a e-mail enviado conforme o primeiro item dessa sessão.
	- Inicialmente o repositório não permitirá cadastro de Issue.
- **Doação**
	- O bot é comandado por software hospedado em ambiente cloud, que implica em custo por hora e carga de funcionamento.
	- Qualquer quantia será bem vinda para ajudar no custeio da infraestrutura.
	- Se o custeio ultrapassar muito o valor doado, o funcionamento do bot poderá ser suspenso.
	- As doações poderão ser feitas pelos canais descritos no perfil de cada bot.
