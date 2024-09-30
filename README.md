# Panfletero 2

Reedição do bot **Panfletero** usado no Twitter e Mastodon em meados de 2020 para distribuir conteúdo jornalístico independente.
A nova edição contará com milhares de novas fontes jornalísticas livres, permitirá filtragem por Estado e cidade, bem como por fontes de artigos e período.

## Proposta

O bot irá servir, de um repositório de mídias digitais curado por seu mantenedor, links para artigos publicados por essas mídias, sob demanda, utilizando como interface a rede social Bluesky, através de perfis (@s) criados nessa rede para esse propósito. A inscrição, demanda e outras configurações adicionais serão feitas através da função de Chat (DM) do perfil. Os links serão organizados em lista e enviados automaticamente em períodos fixos do dia, todos os dias da semana, de acordo com configurações feitas pelo usuário em interação com o bot, até que a inscrição seja desfeita.

## Arquitetura

[Em construção]

## Utilização
1. ### Como se inscrever no bot
- **Cada UF terá uma @ diferente, você poderá seguir as @s que tem interesse.**
    - As @s vão possuir o handler *UF.panfletero.piratariaonline.dev*, sendo "UF" o estado em questão.
        - Exemplo: *@MG.panfletero.piratariaonline.dev*
    - Por limitações técnicas, por enquanto só será possível se cadastrar para uma cidade por estado.
- O bot não segue de volta, portanto sua @ precisa permitir receber DMs.
    - Na interface do Bluesky, em *"Configurações"*, escolha *"Configurações de chat"* e na sessão *"Permitir mensagens de"*, escolha *"Usuário que eu sigo"* ou *"Todo mundo"*.
    - Se o bot não puder te responder por questões de configuração, seus comandos serão ignorados.
	
- **A primeira ação após seguir a @ do bot, é enviar uma DM ao mesmo com o comando `LISTAR CIDADES`** *(veja item da sessão "Como usar o bot").*
    - O bot retornará uma lista de cidades enumeradas, você deve escolher uma e responder `CIDADE:X`, onde `X` é o número da cidade.
	- Se `CIDADE:X` não tiver sido executado nenhuma vez, outros comandos serão ignorados (exceto `LISTAR CIDADES` e `ENCERRAR`).
	- Se uma cidade válida tiver sido selecionada, o bot responde confirmando a inscrição.
	
- **Após escolher uma cidade, você já está cadastrado para receber notícias dela.**
	- Por padrão, você receberá uma lista de links com título e um pequeno resumo (se disponível), de domingo a domingo, 1x ao dia, pela DM.
	- Argumentos para a escolha da entrega por DM, ao invés da TL:
		- A DM não possui limite de caracteres, é possível enviar uma longa listagem numa só requisição.
		- Os rotuladores do Bluesky que monitoram bots são mais sensíveis a comportamento de spam na TL.
		- A TL ficará reservada para serviços públicos (anúncios [não comerciais], comunicados, futuras implementações como "destaques do dia por região", etc).
		- É possível criar um feed compacto das 5 noticias mais atuais do dia usando o comando `NOTICIAS` na TL, uma vez por dia *(veja item da sessão "Como usar o bot")*.
	- Essa decisão pode mudar com o tempo, caso seja avaliada outra abordagem melhor.
2. ### Como usar o bot:
- **Os comandos devem ser usados na DM, exceto `NOTICIAS`.**
- **Cardápio de comandos possíveis:**
	- `LISTAR CIDADES`: Use para listar as cidades disponíveis no Estado em uma lista enumerada.
	- `CIDADE:X`: Use para iniciar a inscrição e escolher UMA cidade da lista criada por `LISTAR CIDADES`.
	- `FREQUENCIA:X` - Use para definir a frequência com a qual receberá a lista de artigos por dia (de 1 a 3). A 1a rodada ocorre às 7:00, a segunda às 14:00 e a terceira às 21:00.
	- `PERIODO:DD/MM/YYYY;DD/MM/YYYY`: Use para filtrar os artigos por período; envie duas datas em formato DD/MM/YYYY separadas por ponto-e-vírgula (aceita as palavras `hoje`, `ontem` ou `anteontem` no lugar da data).
	- `TERMOS:ABC;DEF;GHI...`: Use para filtrar os artigos por palavras chave; envie palavras separadas por ponto-e-vírgula; não use aspas ou outros delimitadores, apenas as palavras.
	- `LISTAR FONTES`: Use para listar as mídias disponíveis para a cidade em uma lista enumerada.
	- `FONTES:X;Y;Z;...`: Use para escolher UMA OU MAIS fontes de artigos; não definir essa configuração faz o bot usar todas as fontes disponíveis, que pode gerar uma lista bem longa dependendo da cidade.
	- `ENCERRAR`: Use para encerrar a inscrição; o comando limpa todas as configurações e o bot para de enviar noticias. Ao dar unfollow na @ do bot, esse comando é executado automaticamente.
	- `NOTICIAS`: Use na TL, mencionado o bot numa postagem; ele responde com os 5 links mais atuais da sua cidade, filtrado pelas configurações. Só pode ser usado uma vez por dia. Não funciona se `ENCERRAR` já foi usado ou se `CIDADE:X` nunca foi usado.
- **Os comandos devem ser escritos isoladamente, um por mensagem, da exata maneira disposta no item acima.**
	- Se o comando for inválido, o bot não responderá nada.
	- Se mais de uma palavra for enviada no comando, apenas as primeiras serão consideradas.
	- O bot despreza caixa alta ou baixa e acentuação no comando, podendo ser escrito de qualquer forma desde que a palavra esteja correta.
	- Qualquer mensagem enviada para o bot na DM que não seja os comandos acima, será ignorada.
	- Qualquer mensagem enviada sem estar seguindo o bot, será ignorada, mesmo que seja um comando.
	- Por limitações técnicas, o bot pode levar até 15 segundos para responder.
3. ### Como contribuir
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
