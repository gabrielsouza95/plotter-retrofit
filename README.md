# plotter-retrofit
Contém um resumo do projeto de retrofit para a plotter de corte e desenho do CITeBauru.

## CNC
De acordo com o [dicionário Collins](https://www.collinsdictionary.com/dictionary/english/cnc) CNC, em tradução livre, é "Controle Numérico Computacional" que é um meio de controlar como máquinas operam, utilizando um computador. Então, impressoras, plotters, impressoras 3D, cortadoras laser, são todas máquinas que utilizam CNC para transformar arquivos gerados pelos usuários em um resultado físico.

Pra isso, geralmente é associado uma [MCU](https://www2.decom.ufop.br/imobilis/iot-cpu-vs-mcu-vs-soc-vs-fpga/) com, geralmente, interfaces de potências para controlar os [atuadores](https://www.feis.unesp.br/Home/departamentos/engenhariaeletrica/aula-5---sensor-25-04-2013b.pdf) que vão gerar alguma coisa no mundo material, como um motor que gera algum movimento ou que acionam a lâmina, com no caso da plotter cortadora.

## Problemas de equipamentos antigos
Com o passar do tempo, os fornecedores de equipamentos deixam de atualizar os softwares/drivers. Isso faz com que seja perdida a possibilidade de uso dos mesmos, pois não temos mais como utilizar as funcionalidades dele.

## Retrofit
Como solução para essa obsolecência programada que acontece quando os equipamentos ficam sem suporte por parte do fabricante, sem ter a necessidade de obter um equipamento novo que surge o [retrofit](https://industrial4-0.com.br/retrofit-de-equipamentos-industriais/). Para esse processo, geralmente substituimos a MCU original por uma que podemos programar e, se os controladores dos atuadores utilizarem um protocolo conhecido, podemos jumpear o nosso MCU por cima do antigo, já utilizando a interface existente e assim barateando ainda mais  o processo. 
Com a MCU nova, nossa, rodando geralmente um software de CNC open source, podemos voltar a utilizar o equipamento com softwares mais modernos e, quando necessário, podemos atualizar e inclusive fazer  as alterações que forem necessárias, dado que com a MCU rodando o que quisermos, temos total controle sobre o equipamento.

O Primeiro contato que tive com projetos do gênero foi [com um perfil do instagram](https://www.instagram.com/eringer_retrofit/) que realiza retrofit de equipamentos industriais, como CNC 5 eixos, com projetos um pouco diferentes do que faremos com a plotter, dado a maior complexidade desses outros projetos. Esses projetos servem de base para entendermos o potencial do processo de retrofit e, uma vez que, acompanhado de conhecimentos de eletrônica e computação/programação e suas associações, como tenho, podemos modificar os elementos envolvidos, mas sempre com a mesma ideia de controle próprio, com ferramentas open source, para "reviver" equipamentos que utilizam CNC.

## O projeto
Para revivermos a plotter do CITeBauru, podemos utilizar o projeto de [retrofit de impressora comum para plotter de corte](https://www.youtube.com/watch?v=StF1HVZoEus&ab_channel=LoopLinks) como base, dado que podemos utilizar todos os programas e plugins existentes na referência para nosso projeto.

## Referências
- 1: https://www.instagram.com/eringer_retrofit/
- 2: https://www.youtube.com/watch?v=StF1HVZoEus&ab_channel=LoopLinks
- 3: https://www.youtube.com/watch?v=1Qary7jwNQc
- 4: https://www.collinsdictionary.com/dictionary/english/cnc
- 5: https://www2.decom.ufop.br/imobilis/iot-cpu-vs-mcu-vs-soc-vs-fpga/
- 6: https://www.feis.unesp.br/Home/departamentos/engenhariaeletrica/aula-5---sensor-25-04-2013b.pdf
- 7: https://industrial4-0.com.br/retrofit-de-equipamentos-industriais/
