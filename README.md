# Plotter-Retrofit
Contém um resumo do projeto de retrofit para a plotter de corte e desenho do CITeBauru.

## CNC
De acordo com o [dicionário Collins](https://www.collinsdictionary.com/dictionary/english/cnc) CNC, em tradução livre, é "Controle Numérico Computacional" que é um meio de controlar como máquinas operam, utilizando um computador ou um microcontrolador(MCU). Então, impressoras, plotters, impressoras 3D, cortadoras laser, são todas máquinas que utilizam CNC para transformar arquivos gerados pelos usuários em um resultado físico.

Pra isso, geralmente é associado uma [MCU](https://www2.decom.ufop.br/imobilis/iot-cpu-vs-mcu-vs-soc-vs-fpga/) com, geralmente, interfaces de potências para controlar os [atuadores](https://www.feis.unesp.br/Home/departamentos/engenhariaeletrica/aula-5---sensor-25-04-2013b.pdf) que vão gerar alguma coisa no mundo material, como um motor que gera algum movimento ou que acionam a lâmina, com no caso da plotter cortadora.

## Problemas de equipamentos antigos
Com o passar do tempo, os fornecedores de equipamentos deixam de atualizar os softwares/drivers. Isso faz com que seja perdida a possibilidade de uso dos mesmos, pois não temos mais como utilizar as funcionalidades dele.

## Retrofit
Como solução para essa obsolecência programada que acontece quando os equipamentos ficam sem suporte por parte do fabricante, sem ter a necessidade de obter um equipamento novo que surge o [retrofit](https://industrial4-0.com.br/retrofit-de-equipamentos-industriais/). Para esse processo, geralmente substituimos a MCU original por uma que podemos programar e, se os controladores dos atuadores utilizarem um protocolo conhecido, podemos jumpear o nosso MCU por cima do antigo, já utilizando a interface existente e assim barateando ainda mais  o processo. 
Com a MCU nova, nossa, rodando geralmente um software de CNC open source, podemos voltar a utilizar o equipamento com softwares mais modernos e, quando necessário, podemos atualizar e inclusive fazer  as alterações que forem necessárias, dado que com a MCU rodando o que quisermos, temos total controle sobre o equipamento.

O Primeiro contato que tive com projetos do gênero foi [com um perfil do instagram](https://www.instagram.com/eringer_retrofit/) que realiza retrofit de equipamentos industriais, como CNC 5 eixos, com projetos um pouco diferentes do que faremos com a plotter, dado a maior complexidade desses outros projetos. Esses projetos servem de base para entendermos o potencial do processo de retrofit e, uma vez que, acompanhado de conhecimentos de eletrônica e computação/programação e suas associações, como tenho, podemos modificar os elementos envolvidos, mas sempre com a mesma ideia de controle próprio, com ferramentas open source, para "reviver" equipamentos que utilizam CNC.

## O projeto
Para revivermos a plotter do CITeBauru, podemos utilizar o projeto de [retrofit de impressora comum para plotter de corte](https://www.youtube.com/watch?v=StF1HVZoEus&ab_channel=LoopLinks) como base, dado que podemos utilizar todos os programas e plugins existentes na referência para nosso projeto.

![Unidade cortadora do projeto da impressora como plotter](static%2Fatuador_cortadora_plotter.png)

Como podemos ver, o projeto se encaixa bem com o nosso projeto, dado que a estrutura de ambos é igual: 2 motores, um para movimento do rolo e outro que movimenta a unidade cortadora da plotter e a unidade cortadora que utiliza um atuador linear eletrônico acionado por uma interface de potência, no caso do projeto referência utiliza um relê, mas acredito que com MOSFET consigamos um resultado ainda mais parecido com a plotter original com controle de força de corte, por exemplo.

![Esquema eletrônico do projeto de referência](static%2Fesquema_eletrônico_componentes_básicos.png)

No projeto de referência, como a base é uma impressora comum, ele precisa inferfacear o Arduino com drivers pros motores de passo e o relê para acionamento da unidade de corte, mas, no caso do retrofit da plotter, eu acredito que, num bom cenário, podemos utilizar os drivers e interfaces já existentes, precisando apenas desligar a MCU original e jumpear o Arduino ali. No pior dos casos, vamos precisar comprar os drivers e fazer uma placa parecida, mas que ainda assim é tranquilo de ser feito.

![Esquemático montado do projeto](static%2Fesquematico_drawio.png)

Então, para o projeto, fiz esse esquemático simplificado no qual, o controlador de motor de passo e o mosfet eu acredito que seja possível utilizar o existente, como dito, apenas jumpeando o Arduino para que ele os controle.

Para a realização do projeto, contando o tempo e esforço que vou precisar investir, acredito que consigo fazer por 80R$H e, apesar de já ter alguma experiência na área, como nunca fiz um retrofit desses e como nunca desmontei a plotter, não sei dizer quanto tempo seria necessário, mas acredito que pelo menos umas 20H investidas que, com umas 2 à 6H semanais investidas, daria para terminar o projeto em uns 2~4 meses, sem contar imprevistos que aconteçam no meio do caminho.

### Lista de materiais

Para a lista de materiais, irei listar inclusive os componentes que pode ser que nem precisaremos, mas os listarei para registro:
- 2x [Placa de prototipagem](https://www.eletrogate.com/placa-circuito-impresso-ilhada-3x7cm-dupla-face)¹
- 1x [Arduino nano](https://www.eletrogate.com/nano-v3-0-cabo-usb-para-arduino)
- 2x [Driver para motor de passo](https://www.eletrogate.com/driver-motor-de-passo-a4988-c-dissipador-de-calor)²
- 1x [Mosfet para controle da ponta de corte](https://www.eletrogate.com/transistor-mosfet-irf3205)²
- Xx [Fios](https://www.eletrogate.com/fio-wire-wrap-250m-30awg)¹

¹ Quantidades podem variar a depender da necessidade do projeto

² Pode ser que não seja necessário, mas só será possível saber após analisar o hardware existente na plotter
    
## Referências
- 1: https://www.instagram.com/eringer_retrofit/
- 2: https://www.youtube.com/watch?v=StF1HVZoEus&ab_channel=LoopLinks
- 3: https://www.youtube.com/watch?v=1Qary7jwNQc
- 4: https://www.collinsdictionary.com/dictionary/english/cnc
- 5: https://www2.decom.ufop.br/imobilis/iot-cpu-vs-mcu-vs-soc-vs-fpga/
- 6: https://www.feis.unesp.br/Home/departamentos/engenhariaeletrica/aula-5---sensor-25-04-2013b.pdf
- 7: https://industrial4-0.com.br/retrofit-de-equipamentos-industriais/
- 8: https://www.eletrogate.com/placa-circuito-impresso-ilhada-3x7cm-dupla-face
- 9: https://www.eletrogate.com/nano-v3-0-cabo-usb-para-arduino
- 10: https://www.eletrogate.com/driver-motor-de-passo-a4988-c-dissipador-de-calor
- 11: https://www.eletrogate.com/transistor-mosfet-irf3205
- 12: https://www.eletrogate.com/fio-wire-wrap-250m-30awg
