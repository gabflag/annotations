<h3>Com o propósito de esclarecer algumas configurações possíveis de VMs no VirtualBox, abaixo estará contido algumas informações básicas para o melhor entendimento dos tipos de redes que podem ser criadas no virtualizador.</h1>

Definições que auxiliaram a leitura do documento:

   - Guest: Se refere a maquina virtual;
   - Host: Computador onde a VM está rodando;
   - External: Rede externa, ou para ficar ainda mais claro se refere a Internet.

<p>Tendo fixado preliminarmente essas definições paratiremos agora para os tipos de conexão que podemos estabelecer para o Guest. Vamos lá!<p>


-------------------------------------------------------------------
<h4>1° Not Attached</h4>

   Not Attached: Na tradução literal Não anexado, podemos entender como não conectado.Como sugere, o Guest não terá qualquer tipo de conexão de rede.
   

-------------------------------------------------------------------
<h4>2° NAT</h4>

   <p>NAT (Network Address Translation): Na tradução literal Tradução de Endereço de Rede, ela permite que o Guest acesse a internet, entretanto, não da acesso a rede interna, ou seja, o Host e está em um rede e o Guest será colocado em uma sub-rede separada. Essa escolha geralmente é utilizada para os Guests que precisam apenas acessar a internet.<p>
   <p>Para maiores informações: https://www.cisco.com/c/pt_br/support/docs/ip/network-address-translation-nat/26704-nat-faq-00.html<p>


-------------------------------------------------------------------
<h4>3° NAT Network</h4>

   <p>NAT (Network Address Translation Network): Na tradução literal Rede de Tradução de Endereço de Rede, ela é muito similar ao que acontece no modo NAT, entretanto, para além de permitir acesso a internet está opção possibilita a configuração de um serviço DHCP local para permitir que o Guest tenha um IP interno. Isso possibilita, alem do acesso a redes externas, que outros Guests que estão na mesma rede se conectem a esta maquina (Se o serviço de Dynamic Host Configuration Protocol estiver configurado).<p>
   
    
-------------------------------------------------------------------
<h4>4° Bridged Adapter</h4>

   <p>Bridged Adapter: Na tradução literal Adaptador em Ponte, é a opção mais abrangente no que se refere a configuração de adaptadores nas VMs. Quando selecionada, o VirtualBox utiliza os drivers de rede do Host e fazem um ‘net filter (filtro de rede)’, interceptando e injetando dados na rede locaL, ou seja, ele usa a interface física do Host (placa de rede) como passagem de dados. O Guest que possui este modo selecionado, aparece para o Host como se fosse uma maquina física conectada na rede.<p>
  <p>Em linhas gerais, esta máquina consegue acessar a internet e também pertence a rede interna do Host, permitindo uma conexão SSH (Secure Shell) ou usar ferramentas como o SCP (Secure Copy).<p>
   <p>Isso é para necessidades de rede mais avançadas, como simulações de rede e servidores em execução em um Guest.<p>
   

-------------------------------------------------------------------   
<h4>5° Internal Network</h4>

   <p>Internal Network: Na tradução literal Rede Interna, permite que as VMs (Guests) consigam se visualizar, conversar entre si, mas as mesmas não são visiveis pela rede do Host. Ao contráriio do que ocorre no modo Bridged, que faz com que os dados passem por uma interface física, no modo Internal Network, todos os pacotes ficam ‘escondidos’ na rede interna criada pelo VirtualBox. Este comportamento oferece um nível a mais de segurança, pois sniffers de pacotes na rede do Host (Analisador de pacotes - Exemplo de farejador: Wireshark) não será capaz de capturar os dados transferidos entre as VMs que estão neste modo.<p>
   <p>Para maiores informações: https://www.virtualbox.org/manual/ch06.html#network_internal<p>


-------------------------------------------------------------------   
<h4>6° Host-Only</h4>

   <p>Host-Only: Na tradução literal Somente o Hospedeiro, assim como no Bridged Adapter, as máquinas virtuais podem conversar entre si e com o host como se estivessem conectadas através de um interruptor Ethernet físico. E tambem como na Internal Network, uma interface de rede física não precisa estar presente, e as máquinas virtuais não podem falar com o mundo fora do host, pois não estão conectadas a uma interface de rede física.<p>
   <p>Para clarificar, enquanto com a rede conectada uma interface física existente (placa de rede) é usada para anexar máquinas virtuais (Bridged), com a rede somente de host (Host-Only) uma nova interface de LOOPBACK é criada no host. E não menos importante, o que diferencia a rede interna (Internal Network) onde o tráfego entre as máquinas virtuais não pode ser visto, o tráfego na interface loopback no host pode ser interceptado.<p>
   <p>Para maiores informações: https://www.virtualbox.org/manual/ch06.html#network_hostonly<p>
      
 
-------------------------------------------------------------------   
<h4>7° Generic Driver</h4>

   <p>Generic Driver: Na tradução literal Drive Genérico, permite que o usuário selecione qual driver de rede será incluído na VM. No momento, existem dois sub-modos disponíveis para o Generic Driver:
   </p>- UDP Tunnel: Utilizado para conectar VMs que estão rodando em hosts diferentes, de forma fácil e transparente, sobre uma infraestrutura de rede existente;
   </p>- VDE (Virtual Distributed Ethernet) networking: Pode ser utilizado para habilitar conexão com um switch “Virtual Distributed Ethernet” em um ambiente Linux ou FreeBSD.
   </p>Para maiores informações:
      </p>https://www.virtualbox.org/manual/ch06.html#network_udp_tunnel
      </p>https://www.virtualbox.org/manual/ch06.html#network_vde<p>

-------------------------------------------------------------------   
<h4>Tabela de comparativo entre os modos de rede</h4>

![Screenshot_1](https://user-images.githubusercontent.com/95552879/169851560-1f298249-c236-4408-8278-6c70d123150f.png)

<p>Legenda:
      </p>  '+' significa 'sim, esta direção de iniciação de conexão é possível;
      </p>  '-' significa 'não', não é possível iniciar conexões na direção indicada no título da coluna;
      </p>  'Port Foward' significa 'encaminhamento de portas', isso significa que o VM VirtualBox ouve certas portas no host e reencaminha todos os pacotes que chegam lá ao Guest interessado, na mesma ou em uma porta diferente. Essa é uma configuração manual.


-------------------------------------------------------------------
<p><h3>Para consultar a respeito de melhoria de desempenho da rede</h3></p>
<p>Os modos Internal Network, Bridged Adapter e Host-Only possuem praticamente a mesma performance. Sendo que o modo Internal Network é um pouco mais rápido e usa menos ciclos do CPU, já que os pacotes nunca chegam na pilha da rede do host. O modo Nat é o mais lento deles, mas também é o mais seguro. Entretanto a recomendação dada pelo site oficial da VMBob é usar o modo Bridged ao invés do NAT.</p>
<p/>Link para a consulta:https://www.virtualbox.org/manual/ch06.html#network_performance</p>

      
<p>.</p>.</p>.</p><h4>Site para aprofundamento do conteúdo acima disposto:</h4>
</p>https://wltech.com.br/tipos-de-conexao-de-rede-no-virtualbox/#page-content
</p>https://www.virtualbox.org/manual/ch06.html
</p>https://www.cisco.com/c/pt_br/support/docs/ip/network-address-translation-nat/26704-nat-faq-00.html<p>
