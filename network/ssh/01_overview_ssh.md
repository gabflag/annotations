- Tópico: SSH e seu funcionamento
- Nota pessoal: Talvez esse seja um dos artigos mais longos que vou escrever aqui no Github, entretanto, é um tópico bem interessante.

<h2>Overview a respeito para estabelecer conexão SSH.</h2>

SHH (Secure Shell) é um protocolo para realizar conexões remotas na rede de forma segura em uma rede insegura, o que faz essa conexão segura é a 
criptografia utilizada para estabelecer comunicação entre cliente (máquina que faz a conexão) e servidor (máquina, site, servidor) no qual se é conectado.

Para garantir a transmissão de informações de maneira segura, o SSH emprega vários tipos diferentes de técnicas de manipulação de dados em vários pontos
da transação. Isso inclui formas de criptografia simétrica, criptografia assimétrica e hashing. Logo voltamos a falar delas.


<h4> => Caracteristicas do seu funcionamento: </h4>

- O componente do servidor escuta em uma porta designada para conexões, setada automaticamente na porta 22. Ele é responsável por negociar a conexão segura, autenticar a parte conectada e gerar o ambiente correto se as credenciais forem aceitas.

- O cliente é responsável por iniciar o handshake (1 Troca de versao - 2 Troca de chaves - 3 Inicialização Diffie-Hellman da Curva Elíptica - 4 Resposta
Diffie-Hellman da curva elíptica SSH - 5 Novas Chaves) inicial do protocolo de controle de transmissão (TCP) com o servidor, negociar a 
conexão segura, verificar se a identidade do servidor corresponde às informações gravadas anteriormente e fornecer credenciais para autenticação.

- Para ficar claro sessão SSH é estabelecida em dois estágios separado, a primeira é concordar e estabelecer a criptografia para proteger comunicações futuras. A segunda etapa é autenticar o usuário e descobrir se o acesso ao servidor deve ser concedido.

<h4> => Tipos de criptografia utilizadas: </h4>

<h5>Symmetrical Encryption:</h5>Tipo de criptografia em que uma chave pode ser usada para criptografar mensagens para a parte oposta e também para 
descriptografar as mensagens recebidas do outro participante. Isso significa que qualquer pessoa que possua a chave pode criptografar e descriptografar 
mensagens para qualquer outra pessoa que possua a chave.

As chaves simétricas são usadas pelo SSH para criptografar toda a conexão. Ao contrário do que alguns usuários supõem, os pares de chaves assimétricas
públicas/privadas que podem ser criados são usados apenas para autenticação, não criptografando a conexão. A criptografia simétrica permite que até 
mesmo a autenticação de senha seja protegida contra espionagem.

Esse tipo de esquema de criptografia é frequentemente chamado de criptografia de “segredo compartilhado - shared secret” ou criptografia de 
“chave secreta - secret key”. Normalmente, há apenas uma única chave que é usada para todas as operações, ou, um par de chaves 
em que o relacionamento é detectável e é comum originar-se a chave oposta.

Essa troca segredo compartilhado faz parte do handshake do ssh, que em linhas gerais escolhe o método (criptografia) compartilhando as listas criptograficas suportadas para gerar seguranca no ato da troca de senhas.

O SSH pode ser configurado para usar uma variedade de diferentes sistemas de cifra simétrica, incluindo Advanced Encryption Standard (AES), Blowfish, 
3DES, CAST128 e Arcfour. O servidor e o cliente podem decidir sobre uma lista de suas criptografias suportadas, ordenadas por preferência. A primeira 
opção da lista do cliente que está disponível no servidor é usada como algoritmo de cifra em ambas as direções.

No Ubuntu 20.04 por exemplo, tanto o cliente quanto o servidor são padronizados como as seguintes cifras:

- chacha20-poly1305@openssh.com
- aes128-ctr
- aes192-ctr

Isso significa que, se duas máquinas Ubuntu 20.04 estiverem se conectando (sem substituir as cifras padrão por meio das opções de configuração), elas
sempre usarão a chacha20-poly1305@openssh.com como cifra como padrão para criptografar sua conexão.

Para ficar um pouco mais claro na linha de comando, utilize os seguintes comandos para verificar as criptografias disponiveis no seu computador para realizar o handshake:

          
          searching ...


<h5>Asymmetrical Encryption:</h5> A criptografia assimétrica é diferente da criptografia simétrica pelo motivo de, para enviar dados em uma única direção, são necessárias duas chaves associadas. Uma dessas chaves é conhecida como chave privada (private key), enquanto a outra é chamada de chave pública (public key).

A chave pública pode ser compartilhada livremente com qualquer parte. Ela está associada à sua chave pareada (da privada no caso), mas a chave privada não pode ser derivada da chave pública. A relação matemática entre a chave pública e a chave privada permite que a chave pública criptografe mensagens que só podem ser decriptografadas pela chave privada. Essa é uma habilidade unidirecional, o que significa que a chave pública não tem capacidade de descriptografar as mensagens que escreve, nem pode descriptografar nada que a chave privada possa enviar.

A chave privada deve ser mantida totalmente em segredo e nunca deve ser compartilhada com outra parte (Cliente). Este é um requisito fundamental para que o paradigma de chave pública funcione com eficácia. A chave privada é o único componente capaz de descriptografar mensagens que foram criptografadas usando a chave pública associada. Em virtude desse fato, qualquer entidade capaz de descriptografar essas mensagens demonstrou que está no controle da chave privada.

O SSH usa criptografia assimétrica em alguns lugares diferentes. Durante o processo inicial de troca de chaves usado para configurar a criptografia simétrica (usada para criptografar a sessão), a criptografia assimétrica é usada. Nesse estágio, ambas as partes produzem pares de chaves temporários e trocam a chave pública para produzir o segredo compartilhado que será usado para criptografia simétrica.

O uso mais discutido da criptografia assimétrica com SSH vem da autenticação baseada em chave SSH. Os pares de chaves SSH podem ser usados para autenticar um cliente em um servidor. O cliente cria um par de chaves e então carrega a chave pública para qualquer servidor remoto que deseja acessar. Isso é colocado em um arquivo chamado authorized_keys dentro do ~/.ssh diretório no diretório inicial da conta do usuário no servidor remoto.

Depois que a criptografia simétrica é estabelecida para proteger as comunicações entre o servidor e o cliente, o cliente deve se autenticar para ter acesso permitido. O servidor pode usar a chave pública neste arquivo para criptografar uma mensagem de desafio para o cliente. Se o cliente puder provar que conseguiu descriptografar esta mensagem, ele demonstrou que possui a chave privada associada.

<h5>Cryptographic hash:</5h>As funções de hash criptográfico são métodos de criação de uma “assinatura”,  sendo que elas nunca devem ser revertidas e são virtualmente impossíveis de influenciar de forma previsível, e não menos importante, são praticamente únicos.

Usar a mesma função de hash e mensagem deve produzir o mesmo hash. Modificar qualquer parte dos dados deve produzir um hash totalmente diferente. Um usuário não deve ser capaz de produzir a mensagem original a partir de um determinado hash, mas deve ser capaz de dizer se uma determinada mensagem produziu um determinado hash.

Passada essa introdução, os hashes são usados ​​principalmente para fins de integridade de dados e para verificar a autenticidade da comunicação. O principal uso em SSH é com HMAC , ou códigos de autenticação de mensagem baseados em hash (hash message authentication code). Eles são usados ​​para garantir que o texto da mensagem recebida esteja intacto e não modificado (tipo um checksum da vida).

Similar ao que acontece na criptografia simétrica, o hash usa a primeira cifra de encriptação suportada pelo servidor será para realizar sua operação.

Cada mensagem enviada após a negociação da criptografia deve conter um MAC para que a outra parte possa verificar a integridade do pacote. O MAC é calculado a partir do segredo compartilhado simétrico, do número de sequência do pacote da mensagem e do conteúdo real da mensagem.



O protocolo SSH para encaminhar portas para um servidor com acesso externo para web, chamamos isso de SSH Tunnel.







Boa parte do material daqui por diante retirei deste site: https://www.digitalocean.com/community/tutorials/understanding-the-ssh-encryption-and-connection-process , recommend a leitura.

