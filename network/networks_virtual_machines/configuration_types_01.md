


Conforme o próprio artigo sugere é interessante deixar claro definições básicas para melhor entendimento ao decorrer da explicação, segue:

   - Guest: Se refere a maquina virtual;
   - Host: Computador onde a VM está rodando;
   - External: Rede externa, ou para ficar ainda mais claro se refere a Internet.

Tendo fixado preliminarmente essas definições paratiremos agora para os tipos de conexão que podemos estabelecer para o Guest, vamos lá!


-------------------------------------------------------------------
1° Not Attached

   Not Attached: Na tradução literal Não anexado, podemos entender como não conectado.Como sugere, o Guest não terá qualquer tipo de conexão de rede.
   

-------------------------------------------------------------------
2° NAT

   NAT (Network Address Translation): Na tradução literal Tradução de Endereço de Rede, ela permite que o Guest acesse a internet, entretanto, não da acesso a rede interna, ou seja, o Host e está em um rede e o Guest será colocado em uma sub-rede separada. Essa escolha geralmente é utilizada para os Guests que precisam apenas acessar a internet.
   Para maiores informações: https://www.cisco.com/c/pt_br/support/docs/ip/network-address-translation-nat/26704-nat-faq-00.html


-------------------------------------------------------------------
3° NAT Network

   NAT (Network Address Translation Network): Na tradução literal Rede de Tradução de Endereço de Rede, ela é muito similar ao que acontece no modo NAT, entretanto, para além de permitir acesso a internet está opção possibilita a configuração de um serviço DHCP local para permitir que o Guest tenha um IP interno. Isso possibilita, alem do acesso a redes externas, que outros Guests que estão na mesma rede se conectem a esta maquina (Se o serviço de Dynamic Host Configuration Protocol estiver configurado).
   
    
-------------------------------------------------------------------
4° Bridged Adapter

   <p>Bridged Adapter: Na tradução literal Adaptador em Ponte, é a opção mais abrangente no que se refere a configuração de adaptadores nas VMs. Quando selecionada, o VirtualBox utiliza os drivers de rede do Host e fazem um ‘net filter (filtro de rede)’, interceptando e injetando dados na rede locaL, ou seja, ele usa a interface física do Host (placa de rede) como passagem de dados. O Guest que possui este modo selecionado, aparece para o Host como se fosse uma maquina física conectada na rede.
   Em linhas gerais, esta máquina consegue acessar a internet e também pertence a rede interna do Host, permitindo uma conexão SSH (Secure Shell) ou usar ferramentas como o SCP (Secure Copy).
   Isso é para necessidades de rede mais avançadas, como simulações de rede e servidores em execução em um Guest.<p>
   

-------------------------------------------------------------------   
5° Internal Network

   Internal Network: Na tradução literal Rede Interna, permite que as VMs (Guests) consigam se visualizar, conversar entre si, mas as mesmas não são visiveis pela rede do Host. Ao contráriio do que ocorre no modo Bridged, que faz com que os dados passem por uma interface física, no modo Internal Network, todos os pacotes ficam ‘escondidos’ na rede interna criada pelo VirtualBox. Este comportamento oferece um nível a mais de segurança, pois sniffers de pacotes na rede do Host (Analisador de pacotes - Exemplo de farejador: Wireshark) não será capaz de capturar os dados transferidos entre as VMs que estão neste modo.
   Para maiores informações: https://www.virtualbox.org/manual/ch06.html#network_internal









Site de pesquisa:
https://wltech.com.br/tipos-de-conexao-de-rede-no-virtualbox/#page-content
https://www.virtualbox.org/manual/ch06.html
https://www.cisco.com/c/pt_br/support/docs/ip/network-address-translation-nat/26704-nat-faq-00.html
                    
