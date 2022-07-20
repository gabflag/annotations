Suponha que um sistema tenha vários repetidores diferentes em locais diferentes. Todos estão transmitindo o mesmo áudio, mas os usuários geralmente estão em movimento. Embora possam começar com uma excelente recepção no primeiro local, eventualmente terão uma recepção melhor no segundo local do que no primeiro local original.

A imagem abaixo demostra bem a situação: 

![Image-18](https://user-images.githubusercontent.com/95552879/180037298-bad8c048-b5e6-4561-b14b-0198fd9cbdb0.png)

Existe o processo chamado de VOTAÇÃO que garante, geralmente, que o usuário de rádio obtenha a melhor recepção possível. A votação pode ocorrer nas unidades de assinantes (votação de downlink) ou na rede (votação de uplink) ou em uma combinação de ambos.

  - Votação de downlink:
  
    Ocorre na unidade do assinante (Rádio móvel), permite que o rádio selecione automaticamente o canal de melhor qualidade de um grupo de canais que estão transmitindo o mesmo áudio.
    
    Isso ocorre em três etapas:
    
    Etapa 1. O rádio procura atividade no canal em um processo semelhante à varredura.
    Etapa 2. A unidade do assinante mede a qualidade do sinal de todos os canais.
    Etapa 3. A unidade do assinante vai para o canal com a melhor intensidade de sinal e ativa o som do receptor.
    
    Em segundo plano, o processo de digitalização continua a ocorrer.
    
    Segue uma figura elucidando o funcionamento prático:
    
    
    ![Image-28](https://user-images.githubusercontent.com/95552879/180038951-f51a5835-b485-4108-b277-bd12eca6b0d7.png)

   - Votação do uplink:
   
   Está ocorre na rede. Geralmente envolve uma rede que possui repetidores recebendo na mesma frequência, mas transmitindo em frequências diferentes.
   
   Na prática, a rede seleciona o melhor sinal para repetir por toda parte. Uma unidade de assinante transmite (rádio móvel) e a votação ocorre na rede. Uma caixa especial, como um votante, seleciona o melhor áudio possível entre os sinais recebidos porque todos os repetidores estão recebendo essa transmissão do SEU. Essa rede é chamada de rede de votação (voting network).
   
   Isso ocorre em três etapas:
   
   Etapa 1. O rádio móvel transmite
   Etapa 2. A votação ocorre na rede
   Etapa 3. O votante seleciona o repetidor com o melhor sinal.  

![Image-81](https://user-images.githubusercontent.com/95552879/180039919-136fb7d9-c05b-457e-9934-5a9b2abfa1c7.png)



  - Outro tipo de rede de votação é chamado de rede de transmissão simultânea. 

  Esta envolve a transmissão do mesmo áudio usando a mesma modulação na mesma frequência com vários transmissores, todos transmitindo exatamente ao mesmo tempo. Uma rede simulcast é projetada para que todos os repetidores sincronizem suas transmissões, fazendo com que pareçam um super repetidor único extremamente grande com uma área de cobertura super grande. Essa coordenação de transmissão é bastante desafiadora, mas para usuários que operam uma rede simulcast ela produz um ótimo resultado.
  Os rádios podem se mover de um local para outro sem que o usuário toque no rádio ou modifique suas configurações ou mude de canal, pois operam em uma única frequência. Os rádios funcionam em todos os lugares.
  
  ![Image-9](https://user-images.githubusercontent.com/95552879/180046563-efbaf363-5d2b-4268-8098-7991fbac5cf4.png)


