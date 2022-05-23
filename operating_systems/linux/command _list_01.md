1 - Para descobrir qual o IP da interface ethO:
    
    COMANDO: ifconfig
    255.255.255.0
    IP retornado vai variar conforme a classe dele.

2 - Qual o Kernel de uma máquina Ubuntu:
    
    COMANDO: uname -r
    0.0.0-0-generic
    Retorna algo semelhante a isso;
    
3 - Tamanho das partições Ubuntu:
    
    COMANDO: df -h
    lista todas as partições.

4 - Cron - listar as tarefas:
    
    COMANDO: contrab -l

5 - Cron - editar/adicionar tarefas:
    
    COMANDO: contrab -e
    
6 - Listando os processos e filtrando por tipo (optei por processos em python):
 
    COMANDO: top
    Depois clicar na letra "o" e escrever "COMANDO=python3" para filtra pela coluna COMANDO.
    
7 - Descobrindo se a máquina possui alguma regra de iptables ativa:
 
    COMANDO: iptables -nvL INPUT --line-numbers 
 
8 - Colocando uma regra no iptables para acessar algum site:
 
    COMANDO: host facebook.com 
    vai retornar o endereço do facebook, agora é só descrever a regra e salvar para não perder no próximo boot:
    COMANDO: iptables -A OUTPUT -p tcp -d 157.240.226.35 -j DROP
    service iptables save
    
9 - Bloquear todas tentativas de conexões da rede 10.1.1.0/24, e DESBLOQUEAR:

    COMANDO: iptables -A INPUT -d 10.1.1.0/24  -j DROP
    service iptables save
   
    COMANDO: iptables -A INPUT -d 10.1.1.0/24  -j DROP
    OU excluir a regra
    COMANDO: iptables -L INPUT --line-numbers CONFERIR O N° DA REGRA E iptables -D INPUT

10 - Bloquear todas tentativas de conexões no range de portas de 5000 a 6000 tcp:    
    
    COMANDO: iptables -A INPUT -p tcp --dport 5000:6000 -j DROP
    service iptables save
    
 11 - Fazendo um checksum de integridade com o algoritimo MD5:
     
    COMANDO: md5sum ARQUIVO_EXEMPLO.zip
    produz um valor de hash de 128 bits expresso em 32 caracteres.
    
 12 - Fazendo um checksum de integridade com o algoritimo SHA256:
     
    COMANDO: sha256sum ARQUIVO_EXEMPLO.zip
 
