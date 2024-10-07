# Manual de Utilização da Urna Eletrônica
Manual referente à utilização do projeto urna eletrônica arduino, com projeto e detalhamento disponível no [github](https://github.com/alguemla/urna-arduino)

## Considerações Iniciais
O projeto da urna eletrônica foi feito tendo em mente a simplicidade da utilização e simplificação das funções utilizadas, a favor de oferecer um projeto de qualidade e robusto, de forma que erros possam ser minimizados.Neste projeto usufruímos do uso de 1x Arduino (módulo programável de computação), 1x Teclado numérico (como forma de injetar informações na urna) 1x Tela LCD (como forma de retorno visual das ações tomadas na urna). Garantindo a integridade destes módulos, a urna não necessita de mais módulos do que os mencionados acima para conduzir uma votação simples.

## Funcionamento da urna
A urna eletrônica funciona como um contador aprimorado, de forma que um contador é atribuído a um número, exemplo:
| Valor	| Contagem |
| ----- | -------- |
| 01 | 06 |
| 02 | 03 |
| 05 | 12 |

Neste exemplo o “valor” seria o partido e a “contagem” seria o numero de votos recebidos pelo partido. Neste programa o “valor” ou partido só e contado caso ele receba algum voto, assim o partido sem votos não aparecerá na apuração final

## Dispositivos necessários para conduzir uma votação
Para conduzir uma votação simples a principio somente é necessário a urna eletrônica, mas para uma apuração mais detalhada e mais completa se faz necessário o uso de um computador com entrada usb 2.0+ e um cabo serial → usb e o programa [coolterm](https://freeware.the-meiers.org) para realizar a leitura das informações da urna.

## Limites de operação
Os limites da urna são 300 partidos com números até 65535 por votação, nos quais 250 deles podem ser salvos entre votações, cada partido pode receber até 65535 votos.

## Como operar a urna
A urna opera com comandos em forma de senhas, sendo elas
| Senha	| Função |
| ----- | -------- |
| 1879582644 | Mostrar os votos pelo monitor de serial |
| 879582644 | Apagar os votos pelo monitor de serial |
| 1879582654 | Armazenar*¹ os votos pelo monitor de serial |
| 187958265 | Mostrar os votos armazenados pelo monitor de serial |
| 1879582659 | Somar*² os votos armazenados com os atuais pelo monitor de serial |
| 9162420 | Somar os votos armazenados com os atuais pelo teclado da urna |
| 5162420 | Armazenar os votos pelo teclado da urna |

1. Armazenar significa guardar os votos para que mesmo caso a urna tenha sido desligada da energia os votos ainda vão estar salvos.

2. O comando somar soma os votos armazenados com os atuais.

As senhas 5162420 e 9162420 tem que ser guardadas, ja que é possível ser colocada pelo teclado.

## Comandos do usuário
Comandos que o usuário pode colocar no teclado da urna
| Comando | Função |
| ----- | -------- |
| * | Corrigir o voto |
| # | Confirmar o voto |
| 0 | Voto branco*¹ |
| >65535 | Não vai contabilizar o voto como segurança para evitar números grandes |

Depois do voto ser confirmado ele não pode ser corrigido.

1. O voto branco vai ser considerado no partido mais votado.

Qualquer voto que não seja de um partido presente deve ser considerado um voto nulo.

## Utilização do coolterm
### Instalação
A instalação pode ser realizada pelo site do [coolterm](https://freeware.the-meiers.org) na opção intel64bit

![image](https://i.ibb.co/qnvr1dL/image.png)

Depois é só extrair o arquivo que a instalação vai estar concluida.
### Operação
Para a urna ser operada adequadamente e sem perda de dados deve mudar algumas configurações.

A primeira e mais importante é ativar o DTR

![image](https://i.ibb.co/2nyQX31/image.png)

A segunda é mudar para a porta de comunicação que a urna se encontra, que é sinalizada pelo texto arduino uno ou serial.

![image](https://i.ibb.co/J2vr27p/image.png)

A terceira é na sessão terminal ativar o line mode

![image](https://i.ibb.co/BjQjgzR/image.png)

A quarta e ultima é ainda no terminal trocar de CR + LF para CR

![image](https://i.ibb.co/Jy0FmRR/image.png)

Para conectar a urna é simplesmente pressionar connect

![image](https://i.ibb.co/rm2kYKk/image.png)

Se tudo tiver sido configurado corretamente agora é simplesmente digitar o comando
