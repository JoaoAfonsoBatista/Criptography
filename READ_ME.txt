Projeto de Criptografia e Protocolos de Segurança 2020

João Afonso Batista 89629
Óscar Ribeiro 89635



Implementação de Honest-but-Curious set intersection.

Este é o paper que seguimos: https://people.eecs.berkeley.edu/~dawnsong/papers/set-int-full.pdf



É preciso escolher um "additively homomorphic public-key cryptosystem" e como recomendado pelos autores do paper, escolher o criptosistema de Paillier.
O funcionamento do criptosistema pode ser visto aqui: https://en.wikipedia.org/wiki/Paillier_cryptosystem

Este criptosistema tem as propriedades homomórficas para a soma de mensagens encriptadas, como pedido, e que se manifestam da seguinte maneira:
 1. dec( enc(m1,r1) * enc(m2,r2) mod n^2) = m1 + m2 mod n;
 2. dec( enc(m1,r1) * g^(m2) mod n^2) = m1 + m2 mod n;
 
 3. dec( enc(m1,r1)^(m2) mod n^2) = m1 * m2 mod n;
 4. dec( enc(m2,r2)^(m1) mod n^2) = m1 * m2 mod n;
 5. dec( enc(m1,r1)^k mod n^2) = k * m1 mod n;


Queremos também explicitar uma restrição do protocolo: As listas dos participantes têm de ter todas o mesmo tamanho.


Nós achamos que há um erro no paper, na págica 9, quando eles explicitam como fazer o produto de um polinómio encriptado com outro nao encriptado.
Eles dizem que i vai desde 0 até à soma dos graus dos dois polinómios, mas depois chamam "f_2[i]", ou seja, 
o coeficiente de grau i do segundo polinomio, mas isso não existe para i maior que o grau de f_2.
No nosso projeto fizemos a forma correta de realizar o produto de dois polinómios.