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

Min (C1.GT1 + C2.GT2 + CDef.def + 0.01.Vv)

s.t. 
    > Balanço Hídrico: Vf = Vi (Volume Inicial no mês) + Afl (Afluência) - Vt (Volume Turbina) - Vv (Volume Vertido)
    > Atendimento da Demanda: P.Vt + GT1 + GT2 + Def  = Carga
    > Restrições de Canalização: Limites inferiores e superiores das variáveis de decisão:
        > Vf: [20, 100]
        > Vt: [0, 60]
        > Vv: [0, infinito]    

        > GT1: [0, 15]
        > GT2: [0, 25]

        > Def: [0, infinito]
        
### Vale lembrar que devemos inserir futuramente a  *função de custo*  futuro que é o "$\alpha$ a mais na função". 

### Portanto, temos a função:

$ Min \hspace{0.5cm} C_1 \cdot GT_1 + C_2 \cdot GT_2 + CDef \cdot def + 0.01 \cdot Vvet $

![equacao 1](https://latex.codecogs.com/gif.latex?Min%20%5Chspace%7B0.5cm%7D%20C_1%20%5Ccdot%20GT_1%20&plus;%20C_2%20%5Ccdot%20GT_2%20&plus;%20CDef%20%5Ccdot%20def%20&plus;%200.01%20%5Ccdot%20Vvet)

sujeito a:

$ \hspace{2cm}  V_f = VI + AFL - Vtur - Vvert $ (Equação de Balanço Hídrico)
![equacao balanço hidrico](https://latex.codecogs.com/gif.latex?%5Chspace%7B2cm%7D%20V_f%20%3D%20VI%20&plus;%20AFL%20-%20Vtur%20-%20Vvert) (Equação de Balanço Hídrico)

$ \hspace{2cm}  Carga = \rho \cdot Vtur + GT_1 + GT_2 + def $ (Equação de Demanda)
![equacao de Demanda](https://latex.codecogs.com/gif.latex?%5Chspace%7B2cm%7D%20Carga%20%3D%20%5Crho%20%5Ccdot%20Vtur%20&plus;%20GT_1%20&plus;%20GT_2%20&plus;%20def) (Equação de Demanda)

$ \hspace{3cm} 20 \le V_f \le 100 $
![restricao 1](https://latex.codecogs.com/gif.latex?%5Chspace%7B3cm%7D%2020%20%5Cle%20V_f%20%5Cle%20100)

$ \hspace{3cm} 0 \le Vtur \le \infty $
![restricao 2](https://latex.codecogs.com/gif.latex?%5Chspace%7B3cm%7D%200%20%5Cle%20Vtur%20%5Cle%20%5Cinfty)

$ \hspace{3cm} 0 \le Vvert \le \infty $
![restricao 3](https://latex.codecogs.com/gif.latex?%5Chspace%7B3cm%7D%200%20%5Cle%20Vvert%20%5Cle%20%5Cinfty)

$ \hspace{3cm} 0 \le GT_1 \le 15 $
![restricao 4](https://latex.codecogs.com/gif.latex?%5Chspace%7B3cm%7D%200%20%5Cle%20GT_1%20%5Cle%2015)

$ \hspace{3cm} 0 \le GT_2 \le 10 $
![restricao 4](https://latex.codecogs.com/gif.latex?%5Chspace%7B3cm%7D%200%20%5Cle%20GT_2%20%5Cle%2010)

$ \hspace{3cm} 0 \le def \le \infty $
![restricao 5](https://latex.codecogs.com/gif.latex?%5Chspace%7B3cm%7D%200%20%5Cle%20def%20%5Cle%20%5Cinfty)



