# TALLER1
TALLER 1 DE ARQUITECTURA DE COMPUTADORES UTP
TALLER1 JULIAN ANDRES CASTANEDA. Cod:10012497
ARQUITECTURA DE COMPUTADORES

Este taller consiste en mejorar las habilidades de los conceptos aprendidos en clase.

1. Implemente en VHDL un FlipFlop de 1bit, con entradas D, Reset, CLK, y una salida Dout.
         __________ 
D-------|          |    
        |          |    
RST-----|          |_______Dout    
        |          |
CLK-----|>         |
        |__________|

2. Escriba los 4 principios de diseÃ±o de hardware aprendidos en clase.

. La simplicidad favorece la regularidad
. Entre mas pequeno mas rapido
. Un buen diseno demanda compromisos
. Hacer comun el caso rapido


3. Convertir a instrucciones de bajo nivel.

int x=0; 
int y =8; 
int z = 1; 

y=x+3;
z=z+3;
x=(x-z)+(3+y);

0XOOOO    add %g0 , 0   ,   &L1
0XOOO4    add %g0 , 8   ,   &L2
0XOOO8    add %g0 , 1   ,   &L3
0XOOOC    add %L1 , 3   ,   &L4
0XOO1O    add %L3 , 3   ,   &L5
0XOO14    add %L1 , %L3 ,   &L6
0XOO18    add %L2 , 3   ,   &L7
0XOO1C    add %L6 , %L7 ,   %g1


4. Usar el ld, y st.
a[4]= a[2]+x;

ld  (%L1 ,(2X2)) , %L2
add  %L2 , %L3   , %L4
st   %L4 , %L2   ,  16


y[0] = y[40]+13;

ld  (%L1 ,(40X4)), %L2
add  %L2 ,  13   , %g1
st   %g1 ,  %l1  ,  0




5. Convertir a lenguaje de mÃ¡quina.
a.
int main(){
    
    int i =3; p=2;
    return i+3;
}

       Lenguaje de bajo nivel:
0XOOOO    add %g0 , 3, &L0        |1
0XOOO4    add %g0 , 2, &L1        |2
0XOOO8    add %L0 , 3, &L2        |3

       Lenguaje de maquina:
   op       rd        op3      rs1     i     zero       rs2  
  | 10 |  |10000|  |000000|  |00000| | 1| |00000000|  |00011|

  | 10 |  |10001|  |000000|  |00000| | 1| |00000000|  |00010|
   
  | 10 |  |10010|  |000000|  |10000| | 1| |00000000|  |00011|


b.
int main(){
    int p=3; x=1; z=4;
    int w=0; 
    w=(p+40)+(x-z);
    return 0; 
}

          Lenguaje de bajo nivel:
0XOOOO    add %g0 , 3    , &L1        |1
0XOOO4    add %g0 , 1    , &L2        |2
0XOOO8    add %g0 , 4    , &L3        |3
0XOOOC    add %g0 , 0    , &L4        |4
0XOO1O    add %L1 , 40   , &L5        |5
0XOO14    add %L2 , %L3  , &L6        |6
0XOO18    add %L5 , &L6  , &g1        |7
0XOO1C    add %g0 , 0    , %O0        |8

          Lenguaje de maquina:
    op      rd        op3      rs1    i      zero       rs2  
  | 10 |  |10001|  |000000|  |00000| | 1| |00000000|  |00011|
  
  | 10 |  |10010|  |000000|  |00000| | 1| |00000000|  |00001|
    
  | 10 |  |10011|  |000000|  |00000| | 1| |00000000|  |01000|
    
  | 10 |  |10100|  |000000|  |00000| | 1| |00000000|  |00000|

    
  | 10 |  |10101|  |000000|  |10001| | 1| |00000001|  |01000|
    
  | 10 |  |10110|  |000000|  |10010| | 0| |00000000|  |10011|
    
  | 10 |  |00001|  |000000|  |10101| | 0| |00000000|  |10110|
    
  | 10 |  |01000|  |000000|  |00000| | 1| |00000000|  |00000|

6. Inicializar las siguientes variables negativas usando OR.
n=-12,
a=-11,
b=-14

0XOOOO    or  %g0 , -12 , &L0            
0XOOO4    or  %g0 , -11 , &L1            
0XOOO8    or  %g0 , -14 , &L2            

