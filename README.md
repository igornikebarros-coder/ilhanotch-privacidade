# Política de Privacidade da Ilha

**Última atualização:** 3 de novembro de 2026

A **Ilha** é um aplicativo gratuito e de código aberto (licença MIT) para Windows 10 e 11 que mostra uma "ilha dinâmica" no topo da tela. Código-fonte: <https://github.com/igornikebarros-coder/Ilha>.

**Resumo:** a Ilha **não tem conta, não tem servidor próprio, não tem anúncios e não envia seus dados para o desenvolvedor.** Tudo o que ela guarda fica no seu computador. A única comunicação com a internet é a consulta de clima, descrita abaixo.

## O que a Ilha acessa e para quê

| Recurso | O que é lido | Para quê | Onde fica |
| --- | --- | --- | --- |
| **Área de transferência** | Textos e imagens que você copia, enquanto a Ilha está aberta | Mostrar o histórico na aba **Cópias** | Somente no seu computador, em `%AppData%\Ilha` (`clips.json` e a pasta `clips`), **sem criptografia**. Você pode apagar itens pela própria Ilha ou excluir a pasta. Se você copia senhas ou dados sensíveis, lembre-se de que eles podem aparecer nesse histórico. |
| **Notificações do Windows** | App, título, texto e hora das notificações, **somente se você ativar** a aba **Notificações** e autorizar o Windows a liberar o acesso | Espelhar as notificações na ilha | Ficam na memória do aplicativo enquanto ele está aberto; **não são gravadas em disco e não saem do computador**. Você pode revogar a permissão em *Configurações do Windows → Privacidade e segurança → Notificações*. |
| **Mídia em reprodução** | Título, artista e capa da mídia que o Windows informa como "tocando agora"; volume do sistema | Controles de música e volume | Apenas na memória. Nada é gravado nem enviado. |
| **Dados do PC** | Uso de processador, memória, armazenamento, bateria e rede | Aba **PC** | Apenas na memória. Nada é gravado nem enviado. |
| **Arquivos da aba Arquivos** | Os caminhos dos arquivos que você arrasta para a Ilha | Mostrar a "prateleira" de arquivos | Somente no seu computador (`shelf.json`). Os arquivos **não são copiados nem enviados**; só o caminho é guardado. |
| **Lembretes, preferências** | O que você digita nos lembretes e suas configurações (tema, cidade etc.) | Funcionamento do app | Somente no seu computador (`reminders.json`, `settings.json`). |
| **Hora e data** | Relógio do sistema | Aba **Hoje** | Apenas na memória. |

## Comunicação com a internet

A Ilha faz **uma única** conexão externa: ao consultar o clima, ela envia o **nome da cidade que você escolheu** (e, depois, as coordenadas dessa cidade) para a API pública gratuita **Open-Meteo** (`geocoding-api.open-meteo.com` e `api.open-meteo.com`) e recebe a previsão. Ela **não** usa o GPS nem a sua localização real: só a cidade que você digitou nas configurações. O Open-Meteo trata essas requisições conforme a política dele (<https://open-meteo.com/en/terms>), e, como em qualquer acesso à internet, ele pode registrar o seu endereço IP.

A Ilha **não** tem telemetria, análise de uso, relatório de falhas automático, rastreadores ou publicidade. Nada é vendido nem compartilhado com terceiros.

## Registro de erros

Quando algo dá errado, a Ilha pode escrever uma mensagem técnica em `%AppData%\Ilha\erro.log`, no seu computador. Esse arquivo **nunca é enviado automaticamente**. Se você abrir um relato de problema no GitHub, só compartilhe o conteúdo dele se quiser.

## Início com o Windows

Se você ligar **"Iniciar com o Windows"**, a Ilha registra isso no Windows (tarefa de inicialização do pacote ou chave de inicialização do seu usuário). Você pode desligar a qualquer momento nas configurações da Ilha ou em *Configurações do Windows → Aplicativos → Inicialização*.

## Seus controles

- **Apagar dados:** exclua a pasta `%AppData%\Ilha` (na versão da Microsoft Store, desinstalar o app também remove os dados dele).
- **Notificações:** desligue a aba Notificações ou revogue a permissão no Windows.
- **Área de transferência:** limpe o histórico pela aba Cópias ou apague `clips.json` e a pasta `clips`.

## Crianças

A Ilha não coleta dados pessoais, de ninguém, incluindo crianças.

## Mudanças nesta política

Se a Ilha passar a tratar dados de outra forma, esta página será atualizada antes e a data acima mudará. O histórico fica visível no repositório do GitHub.

## Contato

Dúvidas sobre privacidade: abra um tópico em <https://github.com/igornikebarros-coder/Ilha/issues>.
