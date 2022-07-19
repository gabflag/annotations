# A diferença entre FDMA e TDMA

Um canal de RF (Radio Frequencia) ocupa uma certa quantidade de espectro de rádio. Qual é o uso mais eficiente desse pequeno pedaço de espectro de rádio que compõe nosso canal?

Existem 3 tipos de tecnologias digitais para o aproveitamento de frequencias: FDMA (Frequency Division Multiple Access), TDMA (Time Division Multiple Access), e CDMA (Code Division Multiple Access).


Apesar das siglas soarem intimidadoras, você pode ter uma ótima noção de como elas funcionam separando o nome de cada uma em partes. A primeira palavra explica o método de acesso. A segunda, Division (divisão em português), mostra que as chamadas são divididas nesse método de acesso:

FDMA —Frequency— coloca cada chamada em uma frequência separada.

TDMA —Time— separa para cada chamada, uma porção de tempo em uma determinada freqüência.

CDMA —Code— dá a cada chamada um código único que se espalha por todas as frequências disponíveis no sistema.

A última parte do nome —Multiple Access— apenas mostra que mais de um usuário pode utilizar o sistema ao mesmo tempo.



- FDMA:

A primeira técnica é chamada de acesso múltiplo por divisão de frequência (FDMA).

Esse método separa os canais por frequência, portanto, se os usuários quiserem ter dois canais, eles terão duas frequências separadas. Se uma conversa atravessa um canal, ela ocupa exclusivamente todo o canal. Há apenas uma conversa e um usuário de cada vez por canal de rádio. Mais canais de rádio requerem mais frequências.

![Image-16](https://user-images.githubusercontent.com/95552879/179842414-c91692c5-0c84-4d85-a2a2-44c68c93226c.png)


- TDMA

O TDMA é o protocolo de canalização no qual a largura de banda do canal é dividida em várias estações com base no tempo.
 
O TDMA ocupa um canal mas permite que dois usuários ocupem o mesmo canal no que lhes parece ser o mesmo tempo. Uma analogia poderia ser as taxas de quadros paradas no cinema, onde em cerca de 30 quadros por segundo dá a ilusão de movimento contínuo, mas na verdade é um exercício de transporte de tempo.

Com um sistema TDMA de 2 slots de tempo, dois usuários podem compartilhar a mesma frequência da seguinte maneira: O usuário 1 pode usar a frequência por um período de tempo fixo muito curto, talvez 50 milissegundos. Em seguida, o canal reverte para o usuário 2 que recebe 50 milissegundos. Em seguida, ele volta para o usuário que recebe mais 50 milissegundos, e assim por diante.

Esse processo é tão rápido que cada usuário pensa que tem uso exclusivo do canal de frequência. Com TDMA de 2 slots de tempo, para ter mais de duas conversas ao mesmo tempo, é necessário outro canal de rádio. Se for outro canal TDMA de 2 slots de tempo, então duas frequências podem suportar simultaneamente quatro conversas; ou aparentemente simultaneamente, por causa desse exercício de vaivém.

![Image-25](https://user-images.githubusercontent.com/95552879/179843351-b6ce7c3d-a6b8-487f-ab00-12d3c60364a4.png)


- CDMA

Em CDMA, todas as estações podem transmitir dados simultaneamente. Ele permite que cada estação transmita dados por toda a frequência o tempo todo. Múltiplas transmissões simultâneas são separadas por uma sequência de código exclusiva. Cada usuário recebe uma sequência de código exclusiva.

Tabela demonstrando diferenças entre FDMA, TDMA e CDMA:

![Screen Shot 2022-07-19 at 17 25 42](https://user-images.githubusercontent.com/95552879/179841994-09be08ab-635e-436c-97d0-8ccf8d078b16.png)
