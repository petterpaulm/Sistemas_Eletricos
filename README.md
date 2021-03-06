# Planejamento de Sistemas Eletricos

![github](https://media.giphy.com/media/2surg4h1puFna/giphy-downsized.gif)

A intenção deste projeto é apresentar um simples modelo de otimização entre usinas hidreletricas ("UHE") e termeletricas ("UTE"), considerando o "dilema do oeprador do sistema elétrico".

A Técnica de Programação Dinâmica Estocástica "Adaptada" pelo Python é utilizada.

## Um pouco de teoria e explicação do problema abordado

### Temos 3 variáveis para avaliar no caso das usinas UHEs:

        > Vf: Volume Final (quanto que a usina chegará de voluma no final do mês operativo)

        > Vt: volume turbina

        > Vv: volume vertido (quando no final do mês houver mais volume do que a capacidade)

### Temos 2 variáveis associadas às UTEs:

        > GT1: Geração Termica da Usina 1

        > GT2: Geração Termica da Usina 2

E, por fim, gostaríamos de saber o déficit.

Vamos escever a função objetivo:

        > Min (C1.GT1 + C2.GT2 + CDef.def + 0.01.Vv)

        > s.t.

        > Balanço Hídrico: Vf = Vi (Volume Inicial no mês) + Afl (Afluência) - Vt (Volume Turbina) - Vv (Volume Vertido)

        > Atendimento da Demanda: P.Vt + GT1 + GT2 + Def  = Carga

Restrições de Canalização: Limites inferiores e superiores das variáveis de decisão:

        > Vf: [20, 100]
        > Vt: [0, 60]
        > Vv: [0, infinito]    
        > GT1: [0, 15]
        > GT2: [0, 25]
        > Def: [0, infinito]
        
Vale lembrar que devemos inserir futuramente a  *função de custo*  futuro que é o "$\alpha$ a mais na função". 

Portanto, temos a função:

![equacao 1](.pictures/funcao_objetivo_print.png)

#### Alguns exemplos de evolução do Multiplicador de Lagrange (CMO - Custo Marginal de Operação):

![grafico 1](./pictures/grafico_estagio_1.png)

![grafico 2](./pictures/grafico_estagio_2.png)

## Contribuições / Comentários / Críticas
Pull requests são muito bem-vindos. 
Para maiores alterações, por favor envie um issue especificando os detalhes.
