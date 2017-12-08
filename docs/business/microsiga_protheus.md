# Microsiga Protheus

O [Microsiga Protheus](http://tdn.totvs.com/display/framework/Microsiga+Protheus) é um sistema integrado de gestão empresarial (ERP/CRM/HCM/SCM) , criado e desenvolvido pela TOTVS S/A, para atender a todo mercado corporativo.
 
O sistema contempla todos os principais processos de empresa, através de seus módulos, onde cada módulo corresponde a uma área especifica de gestão, como por exemplo, o módulo FAT (Vendas e Faturamento) que contempla a área de Vendas, fazendo a integração das informações com as demais áreas da empresa. Cada módulo é responsável por dezenas de processos de negócios, baseado em práticas do dia a dia de diversos segmentos de negócio.

O Rung por meio de integração WebService REST ou SOAP permite extrair de forma inteligente excepcionalidades a serem apresentadas em forma de alertas no dashboard dos usuários. Para que isso seja possível será necessário cumprir com alguns pré requisitos e configurações listadas abaixo.

***

## Pré requisitos

* Protheus com versão igual ou superior a 12.1.14
* Binário superior a `Build 7.00.131227A - Mar 31 2016 - 13:24:20`
* Patch dos _WebService_ REST e SOAP *RUNG*
* Configuração Web Service REST ou SOAP no ambiente Protheus
* Liberação de IP e porta do _web service_

***
## Patch

> EM BREVE 

***

## Configuração Webservice

### SOAP

O _web service_ em AdvPL utiliza-se de working threads para atender as solicitações de processamento através do protocolo HTTP.

Para isso, existem duas maneiras de habilitar um _web service_:

1. Através da criação da seção `[WebServices]`, no arquivo de configuração (appserver.ini), do TOTVS | Application Server.
2. Configuração manual de um ambiente working threads extended (_WEBEX_), no arquivo de configuração (_appserver.ini_), do TOTVS | Application Server.
A diferença entre ambas é que a segunda opção permite especificar mais detalhes do ambiente de execução do serviço, configurar os serviços de Web Sites simultaneamente e o atendimento diferenciado do processamento para mais de um host e diretórios virtuais.

!!! info
    A Totvs recomenda a utilização do assistente de configuração do servidor Microsiga Protheus - [ApWebWizard](http://tdn.totvs.com/display/framework/Como+iniciar+um+servidor+de+Webservices+no+Protheus), para instalar e configurar o ambiente de Web Services.


A seguir, observe um exemplo de como configurar o servidor TOTVS | Application Server para _web services_, utilizando a seção `[WebServices]`.

``` sh
[WebServices]
Enable=1 ;(Obrigatório) - Indica se o service está habilitado (1) ou não (0).
Environment=EnvTeste  ;(Obrigatório) - Indica qual environment do Server que irá atender as requisições.
Conout=0  ;(Opcional) - Permite a exibição de informações dos status internos do serviço (padrão=0:desabilitado). Utilizado APENAS para depuração, em casos específicos, pois prejudica significativamente a performance do(s) serviço(s).
Trace=0  ;(Opcional) - Habilita a gravação de um arquivo de log (wsstrace.log), contendo as informações sobre todas as chamadas e status do Web Service (padrão=0).
PrepareIn=01,01  ;(Obrigatório) - Permite especificar qual a empresa e filial do ERP serão utilizados para a montagem do ambiente de processamento das requisições.
NameSpace=http://localhost  ;(Opcional) - Permite especificar o nome do namespace 'padrão', utilizado pelo(s) serviço(s) compilado(s) sem a definição de 'NameSpace'. (Padrão=host atualmente utilizado).
URLLocation=http://localhost  ;(Opcional) - Permite especificar a URL responsável pelo atendimento às solicitações de processamento do(s) serviço(s) (padrão=host atualmente utilizado).
```

!!! attention
    Esta configuração exige que a seção `[HTTP]` não esteja configurada no TOTVS | Application Server. Pois, essa configuração irá internamente habilitar o serviço de HTTP e configurar o processo de resposta para o _web services_.

No entanto, é possível configurar o _web service_ manualmente. Para isso, deve-se inicialmente habilitar o serviço de HTTP, do servidor Microsiga Protheus, configurar um processo WEBEX apontando para funções internas de processamento dos _web services_ e configurar um host através do qual as requisições de processamento serão atendidas.

``` sh
[HTTP]  ;Configuração do protocolo HTTP
Enable=1
Port=80
Path=c:\P10\Http

[Localhost]  ;Configuração do host da estação local
Defaultpage=wsindex.apw
ResponseJob=WSTeste

[WSTeste]  ;Configuração do job para atender aos Web Services.
Type=WEBEX  ;(Obrigatório) - Tipo do job para Web Services deve ser WEBEX.
OnStart=__WSSTART  ;(Obrigatório) - Configuração fixa para Web Services.
OnConnect=__WSCONNECT  ;(Obrigatório) - Configuração fixa para Web Services.
Environment=ENVTeste  ;Especifique qual ambiente (environment) do servidor Microsiga Protheus que irá atender aos Web Services.
Instances=2.5  ;(Obrigatório) - Indica qual a quantidade mínima (padrão) e máxima de processos (Threads) que serão colocados na memória para atender às solicitações de processamento do(s) serviço(s) publicado(s).
Conout=0  ;(Opcional) - Permite a exibição de informações dos status internos do serviço (padrão=0:desabilitado). Utilizado APENAS para depuração, em casos específicos, pois prejudica significativamente a performance do(s) serviço(s).
Trace=1  ;(Opcional) - Habilita a gravação de um arquivo de log (wsstrace.log), contendo as informações sobre todas as chamadas e status do Web Services (padrão=0).
PrepareIn=01,01  ;(Obrigatório) - Permite especificar qual empresa e filial, do ERP, serão utilizados para a montagem do ambiente de processamento das requisições.
NameSpace=http://localhost/  ;(Opcional) - Permite especificar o nome do namespace 'padrão', utilizado pelo(s) serviço(s) compilado(s) sem a definição de 'NameSpace'. (padrão=host atualmente utilizado).
URLLocation=http://localhost/  ;(Opcional) - Permite especificar a URL responsável pelo atendimento às solicitações de processamento do(s) serviço(s) (padrão=host atualmente utilizado).
```

!!! info 
    Para maiores informações de como configurar o _web service_ SOAP, acessar documentação oficial no [TDN](http://tdn.totvs.com/pages/viewpage.action?pageId=6064937)

### REST

O _web service_ REST do AdvPL não utiliza as seções `[HTTP]` e `[WebServices]` utilizadas para o configurar o modelo _SOAP_. Apesar disso o REST também utiliza _working threads_ para atender as requisições recebidas também pelo protocolo HTTP.

A função HTTP_START que prepara o Application Server como HTTP para REST, devendo ser configurada na seção ONSTART. Segue abaixo exemplo básico de configuração.

``` sh
[GENERAL]
MAXSTRINGSIZE=10
 
[HTTPV11]
Enable=1
Sockets=HTTPREST

[HTTPREST]
Port=8080
URIs=HTTPURI
SECURITY=2

[HTTPURI]
URL=/rest
PrepareIn=All
Instances=1,2

[ONSTART]
jobs=HTTPJOB
RefreshRate=30

[HTTPJOB]
MAIN=HTTP_START
ENVIRONMENT=environment
```

!!! info 
    Para maiores informações de como configurar o _web service_ REST, acessar documentação oficial no [TDN](http://tdn.totvs.com/pages/viewpage.action?pageId=185747842)

***

## Liberação IP : Porta

> EM BREVE 

!!! info
    É possível liberar em seu firewall a comunicação do seu _web service_ apenas para IP ou DNS do Rung

***

## Configuração no Rung

O próximo passo após realizar todas as configurações listadas acima é vincular o IP e porta publica para que o Rung consiga realizar a comunicação das integrações com o Microsiga Protheus. Para isso você precisará realizar poucos passos, conforme descrito abaixo:

!!! info
    O usuário logado na conta Rung deverá ter permissão de administrador para poder visualizar as opções de configuração e servidores.

 1. Acesse sua conta Rung e clique sobre a opção "Configuração".
![Opção de configuração](https://i.imgur.com/iK86i7D.png)
 2. Clique sobre a opção "Servidores" e adicione um servidor clicando sobre o botão "+" no canto inferior direito.
![Opção de servidores](https://i.imgur.com/yAAJw2B.png)
3. Informe o nome do servidor, o tipo (REST ou SOAP) e o IP:Porta pública.
![Inclusão de servidor](https://i.imgur.com/iJ8Tj38.png)
4. Ao confirmar a tela, deverá ser feita a autenticação com um login e senha válida do Microsiga Protheus.
![Autenticação com o Microsiga Protheus](https://i.imgur.com/StZO2Ze.png)
5. Visualize seu servidor com status de online
![Resgitro de servidor online](https://i.imgur.com/HLlaEfh.png)
6. No [Rung Store](https://app.rung.com.br/store/) ao ativar uma integração do Protheus será possível visualizar na lista de "Servidor Protheus" o servidor incluído.
![Visualização do servidor na instalação da integração de Documentos Vencidos](https://i.imgur.com/5Zm7i0Z.png)