# Política de Privacidade da Ilha

**Última atualização:** 9 de novembro de 2026

A **Ilha** (IlhaNotch) é um aplicativo para Windows 10 e 11 que mostra uma "ilha dinâmica" no topo da tela. © 2026 Igor Barros.

**Resumo:** a Ilha **não tem conta, não tem servidor próprio, não tem anúncios e não envia seus dados para o desenvolvedor.** Tudo o que ela guarda fica no seu computador. A comunicação com a internet se limita à consulta de clima e, se você deixar ligada, à busca de letras de música, descritas abaixo.

## O que a Ilha acessa e para quê

| Recurso | O que é lido | Para quê | Onde fica |
| --- | --- | --- | --- |
| **Área de transferência** | Textos e imagens que você copia, enquanto a Ilha está aberta | Mostrar o histórico na aba **Cópias** | Somente no seu computador, em `%AppData%\Ilha` (`clips.json` e a pasta `clips`), **sem criptografia**. Você pode apagar itens pela própria Ilha ou excluir a pasta. Se você copia senhas ou dados sensíveis, lembre-se de que eles podem aparecer nesse histórico. |
| **Notificações do Windows** | App, título, texto e hora das notificações, **somente se você ativar** a aba **Notificações** e autorizar o Windows a liberar o acesso | Espelhar as notificações na ilha | Ficam na memória do aplicativo enquanto ele está aberto; **não são gravadas em disco e não saem do computador**. Você pode revogar a permissão em *Configurações do Windows → Privacidade e segurança → Notificações*. |
| **Mídia em reprodução** | Título, artista e capa da mídia que o Windows informa como "tocando agora"; volume do sistema | Controles de música e volume | Apenas na memória. Nada é gravado nem enviado. |
| **Som que sai do PC (barras do player)** | Apenas o **nível** do áudio que o Windows está tocando (captura de loopback), **só enquanto há música tocando** e a opção "Barras ao vivo" está ligada | Fazer as barras do player e da pílula reagirem à música | Apenas na memória, transformado em números de intensidade na hora. **Nada é gravado, guardado nem enviado.** |
| **Pomodoro, café e sons de foco** | As durações que você escolhe; o som de foco é **gerado pelo próprio app** | Timer de foco e sons ambientes | Somente no seu computador (`settings.json`). Os sons **não usam internet** nem arquivos de terceiros. |
| **Dados do PC** | Uso de processador, memória, armazenamento, bateria e rede | Aba **PC** | Apenas na memória. Nada é gravado nem enviado. |
| **Arquivos da aba Arquivos** | Os caminhos dos arquivos que você arrasta para a Ilha | Mostrar a "prateleira" de arquivos | Somente no seu computador (`shelf.json`). Os arquivos **não são copiados nem enviados**; só o caminho é guardado. |
| **Lembretes, preferências** | O que você digita nos lembretes e suas configurações (tema, cidade etc.) | Funcionamento do app | Somente no seu computador (`reminders.json`, `settings.json`). |
| **Hora e data** | Relógio do sistema | Aba **Hoje** | Apenas na memória. |
| **Agenda do Windows** (1.2.7) | Assunto, horário, duração e local dos compromissos dos próximos 7 dias, **somente leitura** e **somente se você permitir** o acesso ao calendário no Windows | Mostrar os próximos eventos e a contagem para a próxima reunião na aba **Hoje** | Apenas na memória. **Nada é gravado, alterado nem enviado.** Desligue em *Configurações → Hoje* ou revogue em *Configurações do Windows → Privacidade e segurança → Calendário*. |
| **Bateria de dispositivos Bluetooth** (1.2.7) | Nome e nível de bateria que fones, mouses e controles pareados informam ao Windows | Lista na aba **PC** e aviso ao conectar | Apenas na memória. Nada é gravado nem enviado. |
| **Wi-Fi e Bluetooth (ações rápidas)** (1.2.7) | Se os rádios de Wi-Fi e Bluetooth estão ligados | Botões de ligar/desligar na aba **Hoje** | Apenas na memória. |
| **Estatísticas de foco** (1.2.7) | Quantos focos do Pomodoro você concluiu por dia e por quantos minutos | Contagem por dia/semana, sequência e gráfico | Somente no seu computador (`focus-stats.json`). Pode ser zerado em *Configurações → Música e foco*. |
| **Envio por QR code** (1.2.7) | O arquivo que você escolher enviar | Permitir que o celular baixe o arquivo pela sua rede local | O app abre um servidor temporário **só na rede local** (Wi-Fi), com um link aleatório de uso único que aceita apenas aparelhos da rede local e se desliga após o download ou em 10 minutos. **Nada passa pela internet nem por servidores do desenvolvedor.** |
| **Compartilhar do Windows** (1.2.7) | O arquivo que você escolher enviar | Abrir o painel Compartilhar do Windows | O Windows e o app que você escolher no painel (por exemplo, Compartilhamento por proximidade ou Phone Link) recebem o arquivo, conforme as políticas deles. |
| **Letras de música** (1.2.7) | Título, artista, álbum e duração da faixa que está tocando | Buscar a letra sincronizada | Veja "Comunicação com a internet". As letras recebidas ficam em cache no seu computador (`%AppData%\Ilha\lyrics`) e podem ser apagadas em *Configurações → Música e foco*. |

## Comunicação com a internet

A Ilha faz somente estas conexões externas:

1. **Clima (Open-Meteo).** Ao consultar o clima, ela envia o **nome da cidade que você escolheu** (e, depois, as coordenadas dessa cidade) para a API pública gratuita **Open-Meteo** (`geocoding-api.open-meteo.com` e `api.open-meteo.com`) e recebe a previsão (atual, por hora e dos próximos minutos, usada no aviso de "chuva chegando"). Ela **não** usa o GPS nem a sua localização real: só a cidade que você digitou nas configurações. O Open-Meteo trata essas requisições conforme a política dele (<https://open-meteo.com/en/terms>).
2. **Letras de música (LRCLIB), opcional e ligada por padrão.** Quando uma música toca, a Ilha envia para `lrclib.net` **apenas o título, o artista, o álbum e a duração da faixa** e recebe a letra. Nenhum dado seu (conta, nome, arquivos, histórico) é enviado. A letra fica em cache no seu PC para não ser buscada de novo. Você pode desligar em *Configurações → Música e foco → Letras sincronizadas*. O LRCLIB é um serviço público de terceiros (<https://lrclib.net>).

Como em qualquer acesso à internet, esses serviços podem registrar o seu endereço IP. Os sons de foco são gerados no seu PC e **não** acessam a internet. O envio por QR code acontece **só na sua rede local**.

A Ilha **não** tem telemetria, análise de uso, relatório de falhas automático, rastreadores ou publicidade. Nada é vendido nem compartilhado com terceiros.

## Registro de erros

Quando algo dá errado, a Ilha pode escrever uma mensagem técnica em `%AppData%\Ilha\erro.log`, no seu computador. Esse arquivo **nunca é enviado automaticamente**. Se você pedir suporte, só compartilhe o conteúdo dele se quiser.

## Início com o Windows

Se você ligar **"Iniciar com o Windows"**, a Ilha registra isso no Windows (tarefa de inicialização do pacote ou chave de inicialização do seu usuário). Você pode desligar a qualquer momento nas configurações da Ilha ou em *Configurações do Windows → Aplicativos → Inicialização*.

## Seus controles

- **Apagar dados:** exclua a pasta `%AppData%\Ilha` (na versão da Microsoft Store, desinstalar o app também remove os dados dele).
- **Notificações:** desligue a aba Notificações ou revogue a permissão no Windows.
- **Área de transferência:** limpe o histórico pela aba Cópias ou apague `clips.json` e a pasta `clips`.
- **Letras, agenda, bateria de dispositivos, estatísticas e envio ao celular:** cada recurso tem um interruptor nas configurações da Ilha.

## Crianças

A Ilha não coleta dados pessoais, de ninguém, incluindo crianças.

## Mudanças nesta política

Se a Ilha passar a tratar dados de outra forma, esta página será atualizada antes e a data acima mudará.

## Contato

Dúvidas sobre privacidade: use o contato de suporte na página do IlhaNotch na Microsoft Store.
