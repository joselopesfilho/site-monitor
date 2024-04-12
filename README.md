# Site Checker Telegram Bot
Este é um script Python que verifica o status HTTP de um site especificado e envia uma mensagem para um bot no Telegram.

## 1. Funcionalidades

1. Verifica o status HTTP de um site especificado.
2. Envia uma mensagem para um bot do Telegram com o código HTTP e a descrição desse código.
3. Pode ser configurado para executar periodicamente a verificação do status do site. (Nesse projeto, utilizei um servidor virtual privado - VPS Linux + Cron Job para automatizar a verificação e enviar as mensagens de tempos em tempos automaticamente).

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

## 6. Configurando um Cron Job em um VPS Linux

Caso deseje fazer esse processo, você deverá ter um servidor Linux disponível 24/7. No meu caso, contratei esse serviço com uma empresa de hospedagem.

### 6.1. Logando em um VPS Linux:

Para acessar um servidor VPS (Virtual Private Server) Linux, você precisará de um cliente SSH. No terminal do seu computador local, use o seguinte comando:

```
ssh nome_de_usuario@endereco_do_vps
```

Substitua `nome_de_usuario` pelo nome de usuário do seu servidor e `endereco_do_vps` pelo endereço IP ou nome de domínio do seu servidor. Você também pode precisar especificar a porta, se não for a porta padrão 22.

Por exemplo:

```
ssh usuario@192.0.2.0
```

Você será solicitado a inserir a senha do seu usuário no servidor. Após inserir a senha correta, você estará conectado ao seu VPS.

### 6.2. Criando um diretório:

Depois de logar no seu VPS, você pode criar um diretório usando o comando `mkdir`. Por exemplo, para criar um diretório chamado `meu_diretorio`, execute:

```
mkdir meu_diretorio
```

### 6.3. Copiando um arquivo Python para o diretório no VPS:

Para copiar um arquivo Python do seu computador para o VPS, você pode usar o comando `scp`. Por exemplo, se o seu arquivo Python se chama `monitor.py` e está no diretório atual do seu computador local e você deseja copiá-lo para o diretório `meu_diretorio` no VPS, execute:

```
scp monitor.py nome_de_usuario@endereco_do_vps:/caminho/para/meu_diretorio/
```

Substitua `monitor.py` pelo nome do seu arquivo Python, `nome_de_usuario` pelo seu nome de usuário no servidor, `endereco_do_vps` pelo endereço IP ou nome de domínio do seu servidor, e `/caminho/para/meu_diretorio/` pelo caminho completo para o diretório no VPS.

### 6.4. Configurando um Cron Job para executar o script periodicamente:

Para configurar um cron job, você pode usar o comando `crontab -e` para editar o cron job do seu usuário. Adicione uma linha ao arquivo crontab com o seguinte formato:

```
minuto hora * * * python3 /caminho/para/meu_diretorio/monitor.py
```

Substitua `minuto` e `hora` pelos minutos e horas em que deseja que o script seja executado. Use `*` para indicar "qualquer" valor. Substitua `/caminho/para/meu_diretorio/monitor.py` pelo caminho completo para o seu script Python no VPS.

Por exemplo, para executar o script todos os dias às 3 da manhã, a linha seria:

```
0 3 * * * python3 /caminho/para/meu_diretorio/monitor.py
```

Depois de adicionar essa linha ao arquivo crontab e salvar as alterações, o cron job será configurado para executar o script Python periodicamente.

## 7. Contribuição

Contribuições são bem-vindas! Sinta-se à vontade para abrir uma issue ou enviar um pull request.

## 8. Licença

Este projeto é licenciado sob a MIT License.
