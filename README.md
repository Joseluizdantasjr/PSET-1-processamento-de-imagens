# PSET-1-processamento-de-imagens
### Aluno: José Luiz Dantas Júnior
### Disciplina: Linguagens de Programação
### Professor Abrantes
Tarefa em python para realiza funções de processamento de imagens. Segue abaixo respostas das questões determinadas.
## Questão 1:
O output esperado dos pixels seria [226, 166, 119, 55]. Para obtê-lo, basta subtrair os valores de cada um dos pixels originais ([29, 89, 136, 200]) de 255. Ou seja, 255 - 29 = 226, 

255 - 89 = 166, 

255 - 136 = 119, 

255 - 55 = 200

## Questão 2:
Para obter a imagm, rodei:
i = Imagem.carregar('test_images/bluegill.png')
a = i.invertida()
a.salvar("bluegill_invertida.png")

### Imagem invertida:

![bluegill_invertida](https://github.com/Joseluizdantasjr/PSET-1-processamento-de-imagens/blob/main/imagens_questoes/bluegill_invertida.png)

## Questão 3:
Para calcular o valor do pixel, basta multiplicar o valor de cada pixel do array 3x3 em sua volta pelo valor na posição correspondente no kernel, e fazer a soma de todos.
Assim:

(0 * 80) + (0,07 * 53) + (0 * 99) + (-0,45 + 129) + (1,20 * 127) + (-0,25 * 148) + (0 * 175) + (-0,12 * 174) + (0 * 193)

= (0,07 * 53) + (-0,45 + 129) + (1,20 * 127) + (-0,25 * 148) + (-0,12 * 174)

= (-3,71) + (-58,05) + 152,4 + (-37) + (-20,88)

= 32,76

## Questão 4:
Para criar o kernel rodei:

kernel = [

    [0, 0, 0, 0, 0, 0, 0, 0, 0],
    
    [0, 0, 0, 0, 0, 0, 0, 0, 0],
    
    [1, 0, 0, 0, 0, 0, 0, 0, 0],
    
    [0, 0, 0, 0, 0, 0, 0, 0, 0],
    
    [0, 0, 0, 0, 0, 0, 0, 0, 0],
    
    [0, 0, 0, 0, 0, 0, 0, 0, 0],
    
    [0, 0, 0, 0, 0, 0, 0, 0, 0],
    
    [0, 0, 0, 0, 0, 0, 0, 0, 0],
    
    [0, 0, 0, 0, 0, 0, 0, 0, 0]
    
]
E apartir dele para obter a imagem, rodei:

i = Imagem.carregar('test_images/pigbird.png')

a = i.correlacao(kernel)

a.salvar('pigbirg_kernel.png')

### Imagem passada pelo kernel:

![pigbird_kernel.png](https://github.com/Joseluizdantasjr/PSET-1-processamento-de-imagens/blob/main/imagens_questoes/pigbirg_kernel.png)

## Questão 5:
Ao pegar uma imagem I podemos representar o kernel como:

I(x-1, y-1), I(x, y-1), I(x+1, y-1)

I(x-1, y),   I(x, y),   I(x+1, y+1)

I(x-1, y+1), I(x, y+1), I(x+1, y+1)

Para Calcular 2I, basta multiplicar cada valor por 2:

2(I(x-1, y-1)), 2(I(x, y-1)), 2(I(x+1, y-1))

2(I(x-1, y)),   2(I(x, y)),   2(I(x+1, y+1))

2(I(x-1, y+1)), 2(I(x, y+1)), 2(I(x+1, y+1))

O kernel de desfoque de caixa 3x3 possuim 9 valores de 1/9:

1/9 1/9 1/9

1/9 1/9 1/9

1/9 1/9 1/9

Assim, para calcular o valor da imagem borrada B, basta multiplicar os valores de I pelos valores do kernel de desfoque de caixa:

1/9(I(x-1, y-1)), 1/9(I(x, y-1)), 1/9(I(x+1, y-1))

1/9(I(x-1, y)),   1/9(I(x, y)),   1/9(I(x+1, y+1))

1/9(I(x-1, y+1)), 1/9(I(x, y+1)), 1/9(I(x+1, y+1))

Com isso, 2I - B representa:

(2-1/9)(I(x-1, y-1)), (2-1/9)(I(x, y-1)), (2-1/9)(I(x+1, y-1))

(2-1/9)(I(x-1, y)),   (2-1/9)(I(x, y)),   (2-1/9)(I(x+1, y+1))

(2-1/9)(I(x-1, y+1)), (2-1/9)(I(x, y+1)), (2-1/9)(I(x+1, y+1))


Dividindo pelos valores de 1, obtemos o kernel que, ao multiplicar os valores I por ele e arrendondar, obtém-se os valores de S, sendo este kernel:

(2-1/9) (2-1/9) (2-1/9)

(2-1/9) (2-1/9) (2-1/9)

(2-1/9) (2-1/9) (2-1/9)

Para criar a imagem, rodei:

i = Imagem.carregar('test_images/python.png')

a = i.focada(11)
    
a.salvar('python_focada.png')

### Imagem focada:

![python_focada](https://github.com/Joseluizdantasjr/PSET-1-processamento-de-imagens/blob/main/imagens_questoes/python_focada.png)

## Questão 6:

Enquanto o kernel Kx é utilizado para detectar as bordas horizontais do objeto, o kernel Ky é responsável por detectar as bordas verticais.
Assim, o primeiro é utilizado para criar uma imagem com as bordas horizxontais destacadas e o outro das verticais. Ao juntar os valores com a aplicação da fórmula, obtem-se a imagem com todas as bordas detectadas. 

i = Imagem.carregar('test_images/construct.png')

a = i.bordas()
    
a.salvar('construct_bordas.png')

### Imagem com bordas detectadas:

![construct_bordas](https://github.com/Joseluizdantasjr/PSET-1-processamento-de-imagens/blob/main/imagens_questoes/construct_bordas.png)
