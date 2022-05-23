Site de pesquisa: https://wltech.com.br/tipos-de-conexao-de-rede-no-virtualbox/#page-content


Conforme o próprio artigo sugere é interessante deixar claro definições básicas para melhor entendimento ao decorrer da explicação, segue:
    
    Guest: Se refere a maquina virtual;
    Host: Computador onde a VM está rodando;
    External: Rede externa, ou para ficar ainda mais claro se refere a Internet.
   
Tendo fixado preliminarmente essas definições paratiremos agora para os tipos de conexão que podemos estabelecer para o Guest, vamos lá!

1° Not Attached

   Not Attached: Na tradução literal Não anexado, podemos entender como não conectado.Como sugere, o Guest não terá qualquer tipo de conexão de rede.
   
 
2° NAT

   NAT (Network Address Translation): Na tradução literal Tradução de Endereço de Rede, ela permite que o Guest acesse a internet, entretanto, não da acesso a rede interena. Essa escolha geralmente é utilizada para os Guests que precisam apenas acessar a internet.
   

3° NAT Network

   NAT (Network Address Translation Network): Na tradução literal Rede de Tradução de Endereço de Rede, ela é muito similar ao que acontece no modo NAT, entretanto, para além de permitir acesso a internet está opção possibilita a configuração de um serviço DHCP local para permitir que o Guest tenha um IP interno. Isso possibilita, alem do acesso a redes externas, que outros Guests que estão na mesma rede se conectem a esta maquina.
   
    
4° Bridged Adapter

   Bridged Adapter: Na tradução literal Adaptador em Ponte, é a opção mais abrangente no que se refere a configuração de adaptadores nas VMs. Quando selecionada, o VirtualBox utiliza os drivers de rede do Host e fazem um ‘net filter (filtro de rede)’, interceptando e injetando dados na rede locaL. O Guest que possui este modo selecionado, aparece para o Host como se fosse uma maquina física conectada na rede.
   Em linhas gerais, esta máquina consegue acessar a internet e também pertence a rede interna do Host, permitindo uma conexão SSH (Secure Shell) ou usar ferramentas como o SCP (Secure Copy).
   
   
5° Internal Network
 
