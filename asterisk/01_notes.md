O presente artigo trata-ra de algumas informações básicas de instalação e configuração do asterisk. Ao fim da leitura o indiviudo será capaz
de realizar uma chamada telefonica através do computador. Ressalto também que não tenho grandes conhecimentos a respeito do funcionamento/comportamento
do asterisk, mas espero que esse conteúdo seja de certa forma proveitoso.

Instalando

Para instalar podemos optar por duas maneiras, uma um pouco mais complexa e manual, e a outra, usando a o recurso dos sistemas Linux 'apt-get'. No shell do
Linux com a permissão de administrador ativada digitar os seguintes comandos:

1° apt-get update
2° apt-get upgrade
3° apt-get install asterisk

Joia. Asterisk Instalando.

Antes de começarmos a configurar o Asterisk, vale-se reforçar que iremos trabalhar sempre via linha de comando. Para um maior entendimento nesse primeiro momneto,
vou clarificar 3 pastas de suma importância para nós:

1° /etc/asterisk/pjsip.conf : Local de configuração de ramais (Usuários do sistena);
2° /etc/asterisk/extensions.conf : Local de configuração de comportamento no recebimento de chamadas (É aqui onde ficam os contextos - veremos mais adiante);
3° /var/log/asterisk/sounds/en : Local padrão do asterisk para buscar/utilizar áudios;

Abaixo comento e listo as configurações:

PJSIP.CONF:

Preliminarmente, deixemos claro que o pjsip.conf é um arquivo de texto plano composto de seções como a maioria dos arquivos de configuração usados com Asterisk. 
Cada seção define a configuração de um objeto de configuração dentro de res_pjsip ou um módulo associado. Para ficar um pouco mais claro ao visualizar o arquivo entenda
como sessão aquilo delimitado por [], exemplo: [404], [rh], entenda isso como ramais/usuário. E quanto ao módulo por hora não se preocupe muito, só entenda que é possível
atualiza-lo sem precisar reninicar todo o asterisk com o comando:

1° rasterisk ('entrando' no asterisk)
2° module reload res_pjsip.conf.

Não menos importante, o arquivo padrão do pjsip vem com muita informação e pré configurações, meu conselho é que você faça uma copia dele e inicie um arquivo
totalmente do zero. Só não precisaremos de fato da primeira informação padrão que é a que define o protocolo de comunicação que estaremos usando. Não se preocupe,
logo abaixo vou mostrar como deve ficar.

Configurações no pjsip.conf:

Como descrito anteriormente, o arquivo é composto de diversas seções, desta maneira, abaixo demonstro e comento qual o obetivo de cada uma, vamos lá:


Delimitando como o dados serão transportados:

[transporte] ;Nome da sessão

type=transport    ; Tipo da sessão
protocol=udp      ; Protocolo usado
bind=0.0.0.0      ; Vai se vincular a interface de IP X. Usei 0.0.0.0 porque é a mais genérica, mas não faça isso por questões de segurança.
                  ; Minha sugestão é configurar com IP da máquina que está rodando o asterisk, desta forma ele só vai aceitar chamadas
                  ; de máquinas da pertencentes a infraesturtura dele. 

Documentação oficial: https://wiki.asterisk.org/wiki/display/AST/PJSIP+Configuration+Sections+and+Relationships

