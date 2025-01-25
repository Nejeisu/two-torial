# Taiko no Tatsujin Nijiiro
<img src="https://github.com/Nejeisu/two-torial/blob/master/docs/img/taikonijiiro/taikonijiiro.png?raw=true">

🚨 Tenha certeza de que você baixou os arquivos de uma fonte confiável.<br>Esse guia é incapaz de resolver problemas relacionados à má gestão de gerenciamento dos arquivos.

---
### Primeiros passos

 

⚠️ Taiko é geralmente distribuído em uma única pasta. Na versão Nijiro o conteúdo deve estar nomeado como `SBWY 39.06`. O jogo deve conter as seguintes pastas `AMCUS`, `Data` e `Executable`.

<img src="https://github.com/Nejeisu/two-torial/blob/master/docs/img/taikonijiiro/setup/1%20PT-BR.PNG?raw=true">

🚨 A versão Nijiro de Taiko é rolling release e é altamente aconselhável verificar a versão do jogo abrindo o arquivo  `AMCUS\AMConfig.ini` e verificando se está descrito `cacfg-game_ver=39.06`"

ℹ️ "O jogo também é distribuído em arquivos `.VHDX` and `.VHD`. Esses arquivos são úteis para fins de arquivamento e preservação, mas não é obrigatório para rodar o jogo. Sempre baixe o arquivo descompactado para uso individual."

---
### instalando o TaikoArcadeLoader (TAL)

ℹ️ `TaikoArcadeLoader` é um loader e emulador do hardware do arcade do Nijiro. Ele permite você abrir o jogo, configurar controles e o servidor de rede. Mais informações podem ser encontrado [na pagina do github do TAL](https://github.com/esuo1198/TaikoArcadeLoader).


- Baixe a última versão do TAL [na aba actions](https://github.com/esuo1198/TaikoArcadeLoader/actions) Na pagina do TAL. O arquivo deve estar nomeado como `TaikoArcadeLoader`. é obrigatório estar logado no github para baixar este arquivo.

	- Se caso o link do github não estiver funcionando no momento ou esteja quebrado, você poderá baixar o arquivo no nosso servidor do [Discord](https://discord.gg/cZRUmEPK78) no canal de texto `Taiko > Resources`

	- Copie os arquivos do `TaikoArcadeLoader.zip` para dentrdo do diretório `Executable/Release`. Caso o sistema pergunte, escolha a opção `Substituir o arquivo no destino` substituindo os arquivos existentes com os novos.  

 <img src="https://github.com/Nejeisu/two-torial/blob/master/docs/img/taikonijiiro/setup/2%20PT-BR.PNG?raw=true">

### Configurando TaikoArcadeLoader



⚠️ O parâmetro de configuração do TaikoArcadeLoader está na pasta como `config.toml`.

Abra o arquivo `config.toml` com um editor de sua preferência. Estaremos usando o [Notepadfis](https://notepad-plus-plus.org/).  

ℹ️ O `config.toml` é separado pelas abas, com as opções descritas em `[colchetes]`"
 	Mais informações podem ser encontradas [na página do github do TAL](https://github.com/esuo1198/TaikoArcadeLoader).
	

ℹ️ A Aba `[amauth]` contém configurações relacionadas a rede

	- `server =` Mantenha ess opção se caso jogar em um servidor local ou offline, mas é recomendado jogar em uma [Rede online](#Tipos de rede).                                 
	- `port =` Não mude caso não saiba o que está fazendo.                                                                           
	- `chassis_id =` Não mude caso não saiba o que está fazendo.    
	- `shop_id =` Meramente visual. Altere se caso desejar.                            
	- `game_ver =` Meramente visual. Altere se caso desejar.                                                               
	- `country_code =` Não mude caso não saiba o que está fazendo.                                                           

	```toml
	[amauth]
	server = "127.0.0.1"
	port = "54430"
	chassis_id = "284111080000"
	shop_id = "TWO-TORIAL"
	game_ver = "39.06"
	country_code = "JPN"
	```

ℹ️ A aba `[graphics]` contém configurações relacionadas a patches de mudança de resolução do jogo 

	- `res =` Altera a resolução do game.
	- `windowed =` Coloque como `true` se caso desejar rodar o game em modo janela.
	- `cursor =` Meramente visual. Altere se caso desejar.
    - `vsync =` Coloque como `true` se caso o seu monitor tenha a taxa de 120hz e esteja configurado com essa taxa de atualização.                                        
	- `fpslimit =` Não mude caso não saiba o que está fazendo.  
	- `model_res_rate =` Não mude caso não saiba o que está fazendo.  

	```toml
	[graphics]
	res = { x = 1920, y = 1080 }
	windowed = false
	cursor = true
	vsync = false
	# fpslimit = 0
	model_res_rate = 1.0
	```

ℹ️ A aba `[keyboard]` contém configurações relacionadas ao teclado"

	- `auto_ime =` Se colocar como `true`, altera o leiaute do teclado até o jogo ser fechado.
	- `jp_layout =` Deve ser colocado como `true` caso você use teclado japonês **moderno**.

	```toml
	[keyboard]
	auto_ime = false
	jp_layout = false
	```

### Configurando controles

ℹ️ Dependendo do tipo de controle que você vai jogar, a configuração dele pode ter alugumas diferenças. Abaixo você verá os tipos de controle disponíveis.

ℹ️ Teclado
Teclado é o principal método de controle. 

O leiaute padrão usa:
- `D F J K` Para o controle "tambor" do Jogador 1
	
- `Z X C V` Para o controle "tambor" do Jogador 2

- `P` Para `Insert Card (inserir o cartão)`
	
- `F2` Para `SERVICE`
	
- `Enter` Para "add coins" (inserir ficha)
 
Se você desejar mudar o leiaute padrão, você pode alterar abrindo o arquivo `keyconfig.toml` com o editor de texto de sua preferência. 

ℹ️ Controles
A configuração do controle "tambor" e o controle convencional é o mesmo processo.
- Abrindo o arquivo `config.toml` coloque `wait_period =` para `0`           
    - Se você estiver usando um controle que não use os botões como as teclas do teclado, voce deve configurar as teclas em SDL editando o arquivo `keyconfig.toml`
    - Se caso usar os analógicos para o mapeamento dos botões do controle "tambor" `analog_input = false` to `true` in `config.toml`
  
Mapeamento SDL válidos está descrito no arquivo  `keyconfig.toml`

Se caso você usar 2 controles, use o [JoyToKey](https://joytokey.net/en/) e remova  o mapeamento SDL no arquivo `keyconfig.toml`




## ⚠️ Leitores de cartões fisicos

Você pode inserir o cartão usando o leitor físico. Se você possuí um, você pode usar ele para o Taiko no Tatsujin Nijiiro.
 
### ℹ️ AIC Pico
	
- Editando o arquivo `config.toml` coloque `card_reader =` para `false`.
- Atualize para a última versão do [firmware](https://github.com/whowechina/aic_pico)
- Edite os parâmetros `AMFWConfig.ini` e mude o "COM4" para o controle do seu AIC Pico  

### ℹ️ ACR122U
- Edite o arquivo `config.toml` e coloque `card_reader =` para `true`.
- Use o AkaiiKitsune [O plugin leitor de cartão TAL](https://gitea.farewell.dev/AkaiiKitsune/tal-cardreader)

ℹ️ Nota: Se você não possuir um leitor de cartão físico, você pode pular para a parte da rede online  na seção Tipos de rede.

---
## Tipos de rede

⚠️Por favor use uma das alternativas, não ambas.

#### ℹ️ Servidores hospedados (Recomendado)

Existe alguns servidores que suportam o Taiko Nijiiro, Porém a maioria deles é apenas por convite. Pergunte aos seus amigos onde eles jogam, e talvez ele irá te convidar!

**Elara Global Taiko Server**

[EGTS](https://egts.ca/guide) É o unico servidor do Taiko Nijiro que também vem com a versão Omnimix que incluí músicas personalizadas e de outros jogos da franquia Taiko. 

#### ℹ️ Servidor local (Método Complexo)

Se desejar rodar o jogo localmente, mas com a capacidade de criar e salvar um perfil, você pode rodar um servidor local no mesmo computador em que está jogando. Este servidor deve estar rodando antes de você iniciar o jogo, mas pode ser desligado quando você não estiver mais jogando.

Qualquer guia para configurá-los deve ficar obsoleto rapidamente. 

   Consulte as instruções de como configurá-los na página de seus respectivos projetos.

- [TLS](https://github.com/asesidaa/TaikoLocalServer/tree/Refactor) - Uma aplicação pra emular o serviço online do Taiko Nijiro. A configuração pode ser um pouco trabalhoso para ser feito e é obrigatório compilar usando o código fonte usando o [VisualStudio](https://visualstudio.microsoft.com/) e com os arquivos `.sln`.

---
### Requisitos de pré inicialização

⚠️ É obrigatório seguir esses passos, senão o jogo não vai abrir.

#### VCRedist & DirectX

ℹ️- Baixe e instale a última versão do [VCRedist](https://github.com/abbodi1406/vcredist/releases/latest) (`VisualCppRedist_AIO_x86_x64.exe`)

ℹ️- Baixe e instale o [DirectX End-User Runtimes](https://www.microsoft.com/en-us/download/details.aspx?id=8109)

---
### Primeira inicialização

Abra o arquivo `Taiko.exe` para iniciar o jogo.

Entre na opção I/O na tela de "DIP Switches" pressionando a tecla `F1` na tela de opções usando as `setinhas` do teclado e apertando a tecla `Enter`, vá na opção `I/O TEST` -> `TAIKO TEST`. Ajuste essas configurações do jeito que você prefira, pois a configuração varia por tipo de controle. Caso não tenha certeza sobre o que alterar, deixe as opções padrão do jeito que estão.
<img src="https://github.com/Nejeisu/two-torial/blob/master/docs/img/taikonijiiro/setup/io.png?raw=true">
Se você desejar abrir o test menu (DIP Switches) pressioando a tecla `F1` na tela de opções usando as `setinhas` e aperte a tecla `Enter`, indo para a opção `MOD MANAGER`.
<img src="https://github.com/Nejeisu/two-torial/blob/master/docs/img/taikonijiiro/setup/mod.png?raw=true">

⚠️ Está tudo pronto! O jogo deverá iniciar corretamente.

---
### Troubleshooting

🚨"Eu tenho algum problema?"
Consulte a pagina [Troubleshooting](troubleshooting.md).
