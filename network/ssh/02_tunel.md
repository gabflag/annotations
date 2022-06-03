<h3>Tunel SSH</h3>


Em resumo, o tunel SSH é um método para transportar fluxos de dados adicionais em uma sessão SSH existente, sem a necessidade de se expor fora
desta conexão. 


Quando você se conecta a um servidor usando SSH, obtém o shell de um servidor (linha de comando), pode ser um linux por exemplo. Este é o comportamento padrão de uma conexão SSH, ao contrário do que acontece no RDP (Remote Desktop Protocol) aonde temos uma interface gráfica. Sob o capô, seu cliente SSH (máquina que faz conexão) cria uma sessão criptografada entre seu cliente SSH e o servidor SSH. Mas os dados transportados na sessão SSH podem ser de qualquer tipo. Portanto, o tunelamento SSH é apenas uma maneira de transportar dados arbitrários com um fluxo de dados dedicado (túnel) dentro de uma sessão SSH existente.
Isso pode ser feito com encaminhamento de porta local, encaminhamento de porta remoto, encaminhamento de porta dinâmico ou criando um túnel TUN/TAP.


- Ele pode ser usado como proxy (Acessar como se estivesse em outro lugar)
- Acessar um servico remoto que nao tenha criptografia, ao usar o tunel ssh ele trás consigo a criptografia.




<h4>Encaminhamento de porta local</h4>

Quando o encaminhamento de porta local é usado, o OpenSSH cria um túnel separado dentro da conexão SSH que encaminha o tráfego de rede da porta local
para a porta do servidor remoto. No OpenSSH, esse recurso de encapsulamento pode ser usado fornecendo -Lsinalizador. Internamente, o SSH aloca um ouvinte
de soquete no cliente na porta especificada. Quando uma conexão é feita a esta porta, a conexão é encaminhada pelo canal SSH existente para a porta do 
servidor remoto.

O encaminhamento de porta local é uma das maneiras de proteger um protocolo inseguro ou fazer com que um serviço remoto pareça local.



O nossoTunel proxy

ssh -D porta servidor
