# Como funciona um Trasmissor FM?

O processo é relativamente simples:

1) O microfone capta a voz.
2) Este sinal de voz entra em um processador de áudio para criar um sinal de entrada.
3) O sinal de entrada é combinado com uma frequência transportadora que é gerada pelo oscilador controlado por tensão (VCO - Voltage Controlled Oscillator).
4) O resultado é um sinal que carrega nossas informações, mas não suficientemente poderoso para ser transmitido através de uma antena. O sinal é amplificado através de dois estágios diferentes:
5) O estágio excitador amplifica a potência do sinal em um nível de saída.
6) O amplificador de potência eleva-o para outro nível de saída de potência, agora suficiente para a antena do transmissor.

O diagrama abaixo exemplifica o funcionamento:

![FM_Transmitter](https://user-images.githubusercontent.com/95552879/179834793-2f350e0b-292e-4d10-abcd-cf8ddee4e565.jpeg)


O processo de recebimento é muito semelhante:

1) A transmissão é capturada pela antena do receptor e é alimentada em um seletor de frequência RF (Radio Frequencia).
2) A transmissão vai para um mixer onde é combinada com transportadora gerada por um VCO local (VCO - Voltage Controlled Oscillator)
3) O resultado é então alimentado em um amplificador de sinal IF (Intermediate Frequency). Ele reduz a frequência por meio de um processo de filtragem necessário para remover a transportadora mais facilmente.
4) O sinal é demodulado.
5) O resultado é alimentado em uma seção de áudio que amplifica os resultados para que possa ser alimentado em um alto-falante e ouvido pelo usuário.

O segredo para entender o recebimento é pensar na desmodularização do sinal. Temos a frequencia que ambos estão conversando, agora é necessário extrair os dados extras existentes na onda transportadora. O resultado será o dado inserido no input do rementente do sinal.

O diagrama abaixo exemplifica o funcionamento:

![FM_Receiver](https://user-images.githubusercontent.com/95552879/179836721-800a048d-5f61-4eb0-98a2-2fb0f2d6bdb5.jpeg)


O rádio é essencialmente um receptor e transmissor combinados, com controle de frequência, microprocessador, memória, e uma interface de utilizador (teclado). A depender do rádio, pode-se tanto receber como transmitir, mas não ambos ao mesmo tempo.

A frequência VCO é controlada e estabilizada por um sintetizador, este é instruído a operar de acordo com os comandos de saída digital do microprocessador. O microprocessador é instruído a funcionar de acordo com os comandos do usuário, através do teclado de controle do rádio. A informação da frequência dos canais apropriados é armazenada na memória.

O VCO compartilhada entre a recepção e a transmissão de funções geradoras de frequência. O VCO é modulado em frequência na transmissão, mas não na Recepção. A antena também tem funções de compartilhamento, através do interruptor de troca de antena.

![Screen Shot 2022-07-19 at 17 07 34](https://user-images.githubusercontent.com/95552879/179838994-7e772b82-fe8d-40f2-9a17-dff0e0c3855d.png)
