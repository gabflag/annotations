


Conforme o próprio artigo sugere é interessante deixar claro definições básicas para melhor entendimento ao decorrer da explicação, segue:

   - Guest: Se refere a maquina virtual;
   - Host: Computador onde a VM está rodando;
   - External: Rede externa, ou para ficar ainda mais claro se refere a Internet.

<p>Tendo fixado preliminarmente essas definições paratiremos agora para os tipos de conexão que podemos estabelecer para o Guest, vamos lá!<p>


-------------------------------------------------------------------
1° Not Attached

   Not Attached: Na tradução literal Não anexado, podemos entender como não conectado.Como sugere, o Guest não terá qualquer tipo de conexão de rede.
   

-------------------------------------------------------------------
2° NAT

   <p>NAT (Network Address Translation): Na tradução literal Tradução de Endereço de Rede, ela permite que o Guest acesse a internet, entretanto, não da acesso a rede interna, ou seja, o Host e está em um rede e o Guest será colocado em uma sub-rede separada. Essa escolha geralmente é utilizada para os Guests que precisam apenas acessar a internet.<p>
   <p>Para maiores informações: https://www.cisco.com/c/pt_br/support/docs/ip/network-address-translation-nat/26704-nat-faq-00.html<p>


-------------------------------------------------------------------
3° NAT Network

   <p>NAT (Network Address Translation Network): Na tradução literal Rede de Tradução de Endereço de Rede, ela é muito similar ao que acontece no modo NAT, entretanto, para além de permitir acesso a internet está opção possibilita a configuração de um serviço DHCP local para permitir que o Guest tenha um IP interno. Isso possibilita, alem do acesso a redes externas, que outros Guests que estão na mesma rede se conectem a esta maquina (Se o serviço de Dynamic Host Configuration Protocol estiver configurado).<p>
   
    
-------------------------------------------------------------------
4° Bridged Adapter

   <p>Bridged Adapter: Na tradução literal Adaptador em Ponte, é a opção mais abrangente no que se refere a configuração de adaptadores nas VMs. Quando selecionada, o VirtualBox utiliza os drivers de rede do Host e fazem um ‘net filter (filtro de rede)’, interceptando e injetando dados na rede locaL, ou seja, ele usa a interface física do Host (placa de rede) como passagem de dados. O Guest que possui este modo selecionado, aparece para o Host como se fosse uma maquina física conectada na rede.<p>
  <p>Em linhas gerais, esta máquina consegue acessar a internet e também pertence a rede interna do Host, permitindo uma conexão SSH (Secure Shell) ou usar ferramentas como o SCP (Secure Copy).<p>
   <p>Isso é para necessidades de rede mais avançadas, como simulações de rede e servidores em execução em um Guest.<p>
   

-------------------------------------------------------------------   
5° Internal Network

   <p>Internal Network: Na tradução literal Rede Interna, permite que as VMs (Guests) consigam se visualizar, conversar entre si, mas as mesmas não são visiveis pela rede do Host. Ao contráriio do que ocorre no modo Bridged, que faz com que os dados passem por uma interface física, no modo Internal Network, todos os pacotes ficam ‘escondidos’ na rede interna criada pelo VirtualBox. Este comportamento oferece um nível a mais de segurança, pois sniffers de pacotes na rede do Host (Analisador de pacotes - Exemplo de farejador: Wireshark) não será capaz de capturar os dados transferidos entre as VMs que estão neste modo.<p>
   <p>Para maiores informações: https://www.virtualbox.org/manual/ch06.html#network_internal<p>


-------------------------------------------------------------------   
6° Host-Only

   <p>Host-Only: Na tradução literal Somente o Hospedeiro, assim como no Bridged Adapter, as máquinas virtuais podem conversar entre si e com o host como se estivessem conectadas através de um interruptor Ethernet físico. E tambem como na Internal Network, uma interface de rede física não precisa estar presente, e as máquinas virtuais não podem falar com o mundo fora do host, pois não estão conectadas a uma interface de rede física.<p>
   <p>Para clarificar, enquanto com a rede conectada uma interface física existente (placa de rede) é usada para anexar máquinas virtuais (Bridged), com a rede somente de host (Host-Only) uma nova interface de LOOPBACK é criada no host. E não menos importante, o que diferencia a rede interna (Internal Network) onde o tráfego entre as máquinas virtuais não pode ser visto, o tráfego na interface loopback no host pode ser interceptado.<p>
   <p>Para maiores informações: https://www.virtualbox.org/manual/ch06.html#network_hostonly<p>
      
 
-------------------------------------------------------------------   
7° Generic Driver

   <p>Generic Driver: Na tradução literal Drive Genérico, permite que o usuário selecione qual driver de rede será incluído na VM. No momento, existem dois sub-modos disponíveis para o Generic Driver:
   </p>- UDP Tunnel: Utilizado para conectar VMs que estão rodando em hosts diferentes, de forma fácil e transparente, sobre uma infraestrutura de rede existente;
   </p>- VDE (Virtual Distributed Ethernet) networking: Pode ser utilizado para habilitar conexão com um switch “Virtual Distributed Ethernet” em um ambiente Linux ou FreeBSD.
   </p>Para maiores informações:
      </p>https://www.virtualbox.org/manual/ch06.html#network_udp_tunnel
      </p>https://www.virtualbox.org/manual/ch06.html#network_vde
      

<p>Site para aprofundamento do conteúdo acima disposto:
https://wltech.com.br/tipos-de-conexao-de-rede-no-virtualbox/#page-content
https://www.virtualbox.org/manual/ch06.html
https://www.cisco.com/c/pt_br/support/docs/ip/network-address-translation-nat/26704-nat-faq-00.html<p>
