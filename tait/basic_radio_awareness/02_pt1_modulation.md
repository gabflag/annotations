A discursão desse tópico será a modulação e os blocos de construção da rádio. Como é que a sua voz é convertida em ondas que podem ser transmitidas e recebidas por aparelhos de rádio?

  - Como funciona a modulação?


Como funciona a modulação?

A frequência de um canal de RF (Radio Frequencia) é melhor compreendida como a frequência de uma onda transportadora (Carrier). Uma onda transportadora é uma onda pura de frequência constante, semelhante a uma onda senoidal. Por si só, não carrega muitas informações com as quais podemos nos relacionar (como fala ou dados).

Para incluir informações de fala ou informações de dados, outra onda precisa ser imposta, chamada de sinal de entrada (Input signal), no topo da onda portadora. Este processo de impor um sinal de entrada em uma onda transportadora é chamado de modulação. Em outras palavras, a modulação altera a forma de uma onda transportadora para de alguma forma codificar a fala ou as informações de dados que estávamos interessados em transportar. A modulação é como esconder um código dentro da onda portadora.

![Image-23-300x168](https://user-images.githubusercontent.com/95552879/179827681-201cf969-432d-491d-9647-214dc538d863.png)

Lembre-se de que qualquer onda tem três propriedades básicas:

  1) Amplitude – a altura da onda
  2) Frequência – um número de ondas passando em um determinado segundo
  3) Fase – onde a fase está em um determinado momento.

Existem diferentes estratégias para modular a onda transportadora.

Primeiro, um usuário pode ajustar a altura da onda transportadora. Se a altura de um sinal de entrada variar com o volume da voz de um usuário e, em seguida, adicionar isso à transportadora, a amplitude da transportadora mudará de acordo com o sinal de entrada que foi alimentado nele.
Isso é chamado de modulação de amplitude ou AM.

![am](https://user-images.githubusercontent.com/95552879/179829156-9138f132-e114-4a86-8399-35b2f9bb5f3f.png)

Não custa ressaltar que nesse caso a frequencia não é alterada.

A frequência de um sinal de entrada também pode ser alterada, isso é chamado de modulação de frequência ou FM. Se este sinal de entrada for adicionado à onda transportadora pura, ele irá alterar a frequência da onda transportadora. Dessa forma, os usuários podem usar mudanças de frequência para transportar informações de fala. 

![fm](https://user-images.githubusercontent.com/95552879/179829686-2f396935-465f-4830-8b95-921adea17855.png)



Essas duas estratégias podem ser combinadas para criar um terceiro esquema. De fato, qualquer estratégia que combine um sinal de entrada (Input signal) com uma onda portadora para codificar a fala ou outras informações úteis é chamada de esquema de modulação.

Os esquemas de modulação podem ser analógicos ou digitais. Um esquema de modulação analógica tem uma onda de entrada que varia continuamente como uma onda senoidal. No esquema de modulação digital, é um pouco mais complicado. A voz é amostrada em alguma taxa e depois comprimida e transformada em um fluxo de bits – um fluxo de zeros e uns – e isso, por sua vez, é criado em um tipo particular de onda que é então sobreposto à portadora. Abaixo terá uma imagem o exemplo deste Input e outras ondas:

![digital](https://user-images.githubusercontent.com/95552879/179830577-fdbd752d-90e5-4074-9eca-5d274dc670b1.png)


A grande questão é: por que as ondas transportadoras estão em modulação? Por que não simplesmente usar o sinal de entrada diretamente? Afinal, ele carrega todas as informações que nos interessam e ocupa apenas alguns kilohertz e largura de banda. Então, por que não usá-lo diretamente? Por que as portadoras e a modulação são necessárias?

Curiosamente, os sinais de entrada podem ser transportados (sem uma onda portadora) por ondas eletromagnéticas de frequência muito baixa. O problema, no entanto, é que isso precisará de um pouco de amplificação para transmitir essas frequências muito baixas. Os próprios sinais de entrada não têm muita potência e precisam de uma antena bastante grande para transmitir as informações. Para manter a comunicação barata e conveniente e exigir menos energia para transportar o máximo de informações possível, são usados sistemas de ondas transportadoras com ondas transportadoras moduladas.






