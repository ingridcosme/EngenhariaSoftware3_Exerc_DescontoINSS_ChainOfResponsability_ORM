# Exerc�cio pertencente a disciplina de Engenharia de Software III

## Design Patterns

### Chain of Responsability

Implementar em Java, com camada model completa e camada de persist�ncia para a solu��o do seguinte problema:

Um sistema de pagamento de funcion�rios que precisa cadastrar os funcion�rios por um ID �nico (INT), nome (VARCHAR(60)), sal�rio (FLOAT). O sistema deve permitir o CRUD Completo dessa entidade e um Select ALL.
Al�m disso, o sistema deve ter, na camada de controle, uma forma de calcular, para posterior exibi��o, o desconto INSS do funcion�rio, que segue o seguinte padr�o:

- At� R&dollar; 1.212,00 (sal�rio-m�nimo) � 7,5% do sal�rio
- Entre R\$ 1. 212,00 e R\$ 2.427,35 � 9% da diferen�a
- Entre R\$ 2.427,36 e R\$ 3.641,03 � 12% da diferen�a
- Entre R\$ 3.641,03 e R\$ 7.087,22� 14% da diferen�a

**Exemplo 1:**

Se um trabalhador ganha R\$ 1.500,00, o desconto do INSS ser� de 7,5% sobre R$ 1.212,00 (R\$ 90,90) + a al�quota de 9% sobre a quantia que est� na faixa seguinte (1.500,00 � 1.212,00 = R\$ 288). O valor ser� de R\$ 25,92.

C�lculo final: R\$ 90,90+ R$ 25,92 = R\$ 116,82

Para calcular a al�quota efetiva, divida o valor efetivo pelo sal�rio do trabalhador (116,82� 1.500,00), o que resultar� em 7,88% do seu sal�rio.

**Exemplo 2:**

Se um trabalhador ganha R\$ 3.000,00, ele se encontra na terceira faixa (R\$ 2.427,36 e R\$ 3.641,03). Ser� necess�rio calcular o valor da al�quota para cada faixa:

1� faixa salarial: 1.212,00 x 7,5% = 90,90

2� faixa salarial: [2.427,35 � 1.212,00] x 9% = 1.215,35 x 9% = 109,38

Faixa que atinge o sal�rio: [3.000,00 � 2.427,35] x 12% = 572,65 x 12% = 68,71

Total a recolher: 90,90 + 109,38 + 68,71 = 268,99

O desconto do INSS tem um teto de contribui��o, que � de R\$ 7.087,22. Al�m disso, � importante destacar que os ajustes tamb�m valem para empregados dom�sticos e trabalhadores avulsos.
