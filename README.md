# Site Checker Telegram Bot
Este é um simples script Python que verifica o status de um site especificado e envia uma mensagem para um bot do Telegram com informações sobre o status do site.

## 1. Funcionalidades

1. Verifica o status de um site especificado.
2. Envia uma mensagem para um bot do Telegram com informações sobre o status do site.
3. Pode ser configurado para executar periodicamente a verificação do status do site.

## 2. Pré-requisitos

* Python 3.x instalado.
* Biblioteca Python: requests.
* Telegram Bot: BotFather.

## 3. Instalação

3.1. Clone este repositório: [(https://github.com/joselopesfilho/site-monitor)](https://github.com/joselopesfilho/site-monitor.git). Você também pode fazer isso usando o comando abaixo:

```
git clone https://github.com/joselopesfilho/site-monitor.git
```

3.2. Instale a biblioteca requests.<br/>
*Essa biblioteca já vem instalada por padrão no python. Porém, se por algum motivo sua instalação não vier com essa biblioteca, basta instalá-la usando o comando abaixo:*

```
pip3 install requests
```

## 4. Configuração

### 4.1. Criando um Bot no Telegram e obtendo o Token de acesso:

1. Abra o aplicativo Telegram e pesquise por "BotFather".
2. Clique em "Iniciar" ou envie uma mensagem com o comando `/start`.
3. Envie o comando `/newbot` para criar um novo bot.
4. Siga as instruções do BotFather para dar um nome ao seu bot e escolher um nome de usuário para ele. Após a conclusão, o BotFather fornecerá um token de acesso para o seu bot.
5. Anote o `Token de acesso` para uso em seu código.

### 4.2. Encontrando o Chat ID:

1. Envie uma mensagem para o seu bot no Telegram.
2. Abra o seguinte URL no seu navegador da web, substituindo 'SEU_TOKEN' pelo token do seu bot: `https://api.telegram.org/botSEU_TOKEN/getUpdates`. Assegure-se que o Bot foi devidamente inicializado no seu telegram, caso contrário você não terá nenhum retorno.
3. Procure pelo campo `"chat"` em algum lugar na resposta JSON. O valor do campo `"id"` neste objeto é o seu `chat_id`.
4. Anote o `chat_id` para uso em seu código.

Parabéns. Você configurou com sucesso seu bot no Telegram para receber notificações sobre o status do seu site!

### 4.3. Edite o arquivo monitor.py, procure as variáveis ´bot_token´ e ´bot_chatID´ e insira o token do bot e o seu ID de chat obtidos no processo de criação do BotFather.

```
bot_token = 'YOUR_REAL_TOKEN'  # Substitua pelo seu token real
bot_chatID = 'YOUR_REAL_CHATID'  # Substitua pelo seu chatID real
```

### 4.4. Procure a variável ´website_url´ e insira a URL completa do site que você deseja monitorar.

```
website_url = 'http://www.YOUR-WEBSITE-HERE.com'
```

## 5. Uso
Execute o script monitor.py:

```
python main.py
```

O script verificará o status do site especificado e enviará uma mensagem para o bot do Telegram com as informações.

## 6. Contribuição

Contribuições são bem-vindas! Sinta-se à vontade para abrir uma issue ou enviar um pull request.

## 7. Licença

Este projeto é licenciado sob a MIT License.
