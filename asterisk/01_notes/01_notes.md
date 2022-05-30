O presente artigo tratará de algumas informações básicas de instalação e configuração do asterisk. Ao fim da leitura o indiviudo será capaz de realizar uma chamada telefônica através do computador. Ressalto também que não tenho grandes conhecimentos a respeito do funcionamento/comportamento do asterisk, mas espero que esse conteúdo seja de certa forma proveitoso. 

Os arquivos de configuração estarão dispostos no respectivo diretório.

Instalando 

Para instalar podemos optar por duas maneiras, uma um pouco mais complexa e manual, e a outra, usando a o recurso dos sistemas Linux 'apt-get'. No shell do Linux com a permissão de administrador ativada digitar os seguintes comandos: 

    1° apt-get update 
    2° apt-get upgrade 
    3° apt-get install asterisk 

Joia. Asterisk Instalando. Para verificar se o serviço está rodando digitar o seguinte comando:
    
    systemctl list-unit-files --type service -all | grep asterisk
    Ou
    service asterisk status

Antes de começarmos a configurar o Asterisk, vale-se reforçar que iremos trabalhar sempre via linha de comando. Para um maior entendimento nesse primeiro momneto,  vou clarificar 3 pastas de suma importância para nós: 

    1° /etc/asterisk/pjsip.conf : Local de configuração de ramais (Usuários do sistena); 
    2° /etc/asterisk/extensions.conf : Local de configuração de comportamento no recebimento de chamadas (É aqui onde ficam os contextos - veremos mais adiante); 
    3° /usr/share/asterisk/sounds/en : Local padrão do asterisk para buscar/utilizar áudios; 

Abaixo comento e listo as configurações: 

PJSIP.CONF: 

Preliminarmente, deixemos claro que o pjsip.conf é um arquivo de texto plano composto de seções como a maioria dos arquivos de configuração usados com Asterisk. Cada seção define a configuração de um objeto de configuração dentro de res_pjsip ou um módulo associado. Para ficar um pouco mais claro ao visualizar o arquivo entenda como sessão aquilo delimitado por [], exemplo: [404], [rh], entenda isso como ramais/usuário. E quanto ao módulo por hora não se preocupe muito, só entenda que é possível atualizá-lo sem precisar renicar todo o asterisk com o comando: 

    1° rasterisk ('entrando' no asterisk) 
    2° module reload res_pjsip.conf (Reniciando o módulo)
    
Uma forma um pouco mais bruta é diretamente no shell digitar o comando:
        
       service asterisk restart

Não menos importante, o arquivo padrão do pjsip vem com muita informação e pré configurações, meu conselho é que você faça uma cópia dele e inicie um arquivo totalmente do zero. Só não precisaremos de fato da primeira informação padrão que é a que define o protocolo de comunicação que estaremos usando. Não se preocupe, logo abaixo vou mostrar como deve ficar.

Documentação oficial: https://wiki.asterisk.org/wiki/display/AST/PJSIP+Configuration+Sections+and+Relationships 


Configurações no pjsip.conf: 

Como descrito anteriormente, o arquivo é composto de diversas seções, desta maneira, abaixo demonstro e comento qual o obetivo de cada uma, vamos lá: 

Delimitando como o dados serão transportados

    [transporte]      ; Nome da sessão 
    type=transport    ; Tipo da sessão 
    protocol=udp      ; Protocolo usado 
    bind=0.0.0.0      ; Vai se vincular a interface de IP X. Usei 0.0.0.0 porque é a mais genérica, mas não faça isso por questões de segurança. 
                      ; Minha sugestão é configurar com IP da máquina que está rodando o asterisk, desta forma ele só vai aceitar chamadas 
                      ; de máquinas da pertencentes a infraestrutura dele.
                      
    [100]             ; Nome do ramal/sessão/usuário 100
    
    type=endpoint     ; O tipo endpoint fornece inúmeras opções relacionadas à funcionalidade principal do SIP e ligações com outras seções como auth ou aor. 
    context=home      ; O contexto que ele irá se relacionar no arquivo extensions (Seleciona o método que a chamada será tratada)
    disallow=all      ; Método de compressão do áudio
    allow=ulaw        ; Método de compressão do áudio
    aors=100          ; Indicando a sessão com o número máximo de usuário para o ramal 100
    auth=auth100     ; Indicando a sessão com que define senha de acesso
    
    [100]
    
    type=aor          ; Tipo desta sessão AOR (Address of Record - Endereço de Registro).
    max_contacts=1    ; Em linhas gerais, o aor define onde um ponto final (endpoint) pode ser contatado. Sem uma seção AOR associada, um ponto final não pode ser.                             contatado. Aqui estou definindo que o endpoint pode ter no máximo 1 usuário a ser contatado.
    
    [100]
    
    type=auth           ; Indicando o tipo da sessão de autenticação
    auth_type=userpass  ; Indicando que a autenticação será realizado via senha, entranto, podemos usar com autenticação MD5
    password=123entrei  ; Senha
    username=100        ; Usuário
    
    
    
    [escritorio]       
    type=endpoint    
    context=trabalho  
    disallow=all      
    allow=ulaw        
    aors=escritorio          
    auth=authescritorio         
    
    [escritorio]
    type=aor          
    max_contacts=1    
    
    [authescritorio]
    type=auth           
    auth_type=userpass  
    password=entrei321
    username=escritorio     


Joia. Essa são as configurações básicas no para você conseguir fazer sua primeira ligação, na verdade, até duas. Temos duas sessões cadastradas, a 100 e a escritório. A 100 vai usar o contexto 'home' e a escritório vai usar o contexto 'trabalho'. Uma dica legal, para conferir se de fato os endpoints (ramais) foram cadastrados digite o seguinte comando no seu shell:

     pjsip show endpoints
     
Irá retornar a quantidade e quais são os endpoints. Por hora terminamos com esse arquivo, vamos para o próximo.

EXTENSIONS.CONF

Alguns exemplos de configuracao:


Delimitando Range de numeros:

        [range2000]
        exten => _2xxx, 1, Ringing
        exten => _2xxx, n, Wait(4)
        exten => _2xxx, n, Answer()
        exten => _2xxx, n, Wait(3)
        exten => _2xxx, n, Playback(welcome)
        exten => _2xxx, n, Playback(gabrielcode)
        exten => _2xxx, n, Hangup()Ligacao entre ramais:  
  
  
  
Tomada de acao diferente a depender do ramal de origem:


        exten => _0954, 1,GotoIf($[${CALLERID(num)} = 3000]?C20,0954,teste)
            same => n,Wait(4)
            same => n,Answer()
            same => n,Wait(1)
            same => n,Playback(hello-world)
            same => n,Hangup()
            same => n(teste),Playback(tt-monkeys)
            same => n,Hangup()
            
            
Observacao: Nesse caso se o número de origem for igual a 3000 que tiver digitado o ramal 0954 ele irá pular para a linha teste,
            se o ramal for qualquer outro ele poderá escultar hello-world
            

Chamada entre ramais internos:

        [interna]
        exten =>_xx,1,NoOp(Ligacao entre ramais)
            same =>n,Set(Chamada feita por =${CALLERID(num)})
            same =>n,Dial(PJSIP/${EXTEN},20,Tt) ;Tt permite a conversacao e transferencia
            same =>n,HangUp(Causa do desligamento =${HANDUPCAUSE}
    
Observacao: Apenas para deixar claro, aqui é interessante trabalhar com um arquivo diaplan exclusivo para ele. Para fazer isso basta digitar no arquivo extensions.conf a seguinte linha: #include extensions_interno.conf (Não esqueca de criar esse arquivo dentro da pasta do asterisk)
