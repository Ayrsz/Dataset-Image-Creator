<style>
grey { color: Grey }
red { color: LightCoral }
blue { color: DeepSkyBlue }
yellow { color: Yellow}
green { color: LightGreen}
pink { color: DeepPink}
snow { color: Snow}
</style>




# References and Methods


# Propose


# Functions


## <grey>Blurs</grey>

### <grey>Gaussian blur</grey>
~~~ python
0: generate_gaussian_blur(image, sigma, kernel_size)
~~~
#### Parâmetros:
- **image** (*numpy.ndarray*): Imagem de entrada em formato NumPy, com 3 canais de cor (BGR).
- **sigma** (*float*): Desvio padrão da distribuição Gaussiana.
- **kernel_size** (*int*): Tamanho do kernel quadrado aplicado ao filtro Gaussiano (deve ser ímpar).

#### Retorno:
- **numpy.ndarray**: Imagem com o efeito de desfoque Gaussiano aplicado.

#### Funcionamento:
1. Um kernel Gaussiano de tamanho `kernel_size x kernel_size` é gerado.
2. A função `cv.GaussianBlur` é aplicada à imagem usando o desvio padrão `sigma`.
3. O resultado é uma imagem suavizada, reduzindo ruídos e detalhes pequenos.
---

### <grey>Motion blur</grey>
~~~python
1: generate_motion_blur(image, kernel_size)
~~~
#### Parâmetros:
- **image** (*numpy.ndarray*): Imagem de entrada em formato NumPy, com 3 canais de cor (BGR).
- **kernel_size** (*int*): Tamanho do kernel usado para simular o desfoque de movimento (deve ser ímpar).

#### Retorno:
- **tupla[numpy.ndarray, numpy.ndarray, numpy.ndarray]**: Três imagens com desfoque de movimento aplicado nas direções **horizontal**, **vertical** e **diagonal**.

#### Funcionamento:
1. Três kernels diferentes são criados para aplicar o efeito de desfoque de movimento:
   - **Horizontal**: Cria um kernel com valores diferentes na linha central.
   - **Vertical**: Cria um kernel com valores diferentes na coluna central.
   - **Diagonal**: Cria um kernel com valores ao longo da diagonal.
2. Cada kernel é convolvido com a imagem original usando `cv.filter2D`, resultando em três versões desfocadas.
3. As imagens resultantes representam o efeito de desfoque em diferentes direções.



## <red>Noises</red>

### <red> Gaussian noise </red>

~~~python
2: generate_gaussian_noise(image)
~~~

Add gaussian noise in the image: each pixel of the image is added by a number obtained through normal distribution. The library random was used for this function

Parameters:
- **mean**: mean of the distribution [**FLOAT**]
- **variance**: The variance of the normal distribution [**FLOAT**]



### <red>Uniform noise</red>

~~~python
3: generate_uniform_noise(image)
~~~
--- 

Add an uniform noise: each pixel of the image is added by a random number between 0 and an integer "limit". The library random was used for this function

Parameters:
- **limit**: the top value of the range of numbers to be chosen randomly[**INT**]



### <red>Speckle noise</red>
~~~python
4 generate_speckle_noise(image)
~~~
--- 

Add speckle noise to the image: each pixel is added by his own value multiplied by a number from a normal distribution. The library random was used for this function

Parameters:
c
- **variance**: The variance of the normal distribution [**FLOAT**]



### <red>Poisson noise</red>
~~~python
5 generate_poisson_noise(image)
~~~

Apply shot (poisson) noise to simulate systems in which the noise is proportional to the signal intensity. A bias is used to scale the values of each pixel. The quantity of noise will be bigger if the bias is close to 1

Parameters:
- **bias**: constant to scale the value of each pixel [**FLOAT**]


### <red>Salt and pepper</red>
~~~python
6 generate_sep_noise(image)
~~~

## <blue>Colors</blue>

### <blue>Color diffusion</blue>
~~~python
7 generate_color_diffusion(image)
~~~
--- 


### <blue>Color shift</blue>
~~~python
8 generate_color_shift(image)
~~~

---  


### <blue>Color quantization</blue>
~~~python
9 generate_color_quantization(image)
~~~



### <blue>Color saturation HSV</blue>
~~~python
10 generate_color_saturation_hsv(image)
~~~





### <blue>Color saturation L.A.B</blue>
~~~python
11 generate_color_saturation_lab(image)
~~~


## <yellow> JPEG'S compressions </yellow>

### <yellow>JPEG compression</yellow>
~~~python
12 generate_compression_jpeg(image)
~~~


### <yellow>JPEG2000 compression</yellow>

~~~python 
13 generate_compression_jpeg2000(image)
~~~




## <green>Warpping<green>

### <green>Invert</green>
~~~python
14 generate_invert_warp(image)
~~~



#### Parâmetros:
- **image (*numpy.ndarray*)**: Imagem de entrada a ser invertida.

#### Retorno:

- **numpy.ndarray**: Imagem com a inversão aplicada.

#### Funcionamento:
1. Definem-se os pontos iniciais e finais para a transformação da perspectiva.
2. Aplica-se a transformação de perspectiva usando `cv.getPerspectiveTransform`.
3. A imagem é invertida com a função `cv.warpPerspective` e retornada.


### <green>Shearing warp</green>

~~~python
15 generate_shearing_warp(image, sx, sy)
~~~

#### Parâmetros:
- **image** (*numpy.ndarray*): Imagem de entrada em formato NumPy, com 3 canais de cor (BGR)Imagem de entrada.
- **sx** (*float*): Valor de cisalhamento no eixo X, normalizado em ([0, 1])
- **sy** (*float*): Valor de cisalhamento no eixo Y, normalizado em ([0, 1]).

#### Retorno:
- **numpy.ndarray**: Imagem resultante do cisalhamento aplicado.

#### Funcionamento:
1. Aplica-se o cisalhamento à imagem utilizando uma matriz de transformação de cisalhamento.
2. Retorna a imagem resultante.

### <green>Elastic warp</green>

~~~python
16 generate_elastic_warp(image, alpha)
~~~

#### Parâmetros:
- **image** (*numpy.ndarray*): Imagem de entrada.
- **alpha** (*float*): Controlar a intensidade da deformação, normalizado em ([0, 1]), sendo o valor máximo de range de shift como 0.5% de `max(L, H)` sendo L largura e H altura.

#### Retorno:
- **numpy.ndarray**: Imagem deformada elasticamente.

#### Funcionamento:
1. Dado o valor de `alpha`, deslocamentos aleatórios são aplicados nas coordenadas da imagem.
2. Aplica-se o desfoque Gaussiano nas distorções.
3. Realiza-se a deformação na imagem usando as coordenadas distorcidas.
4. Retorna a imagem deformada.

### <green>Bilinear interpolation</green>

~~~python  
17 generate_bilinear_interpolation(image, scale)
~~~

#### Parâmetros:
- **image** (*numpy.ndarray*): Imagem de entrada em formato NumPy, com 3 canais de cor (BGR).
- **scale** (*float*): Escala para redimensionamento, normalizado entre ([0, 1]) sendo 1 a escala original.

#### Retorno:
- **numpy.ndarray**: Imagem redimensionada utilizando interpolação bilinear.

#### Funcionamento:
1. A imagem é redimensionada para um novo tamanho usando interpolação bilinear.
2. Em seguida, a imagem redimensionada é ajustada de volta ao tamanho original.
3. Retorna a imagem redimensionada.

### <green>Rotations</green>

~~~python  
18 generate_rotations(image)
~~~

#### Parâmetros:
- **image** (*numpy.ndarray*): Imagem de entrada em formato NumPy, com 3 canais de cor (BGR).

#### Retorno:
- **numpy.ndarray**: Imagem rotacionada.

#### Funcionamento:
1. A imagem é rotacionada em 90°, 180° e 270°.
2. Retorna vetor com essas rotações (O.B.S: SSIM não é calculado para 90° e 270°)


## <pink>Sharpness and Contrast</pink>

### <pink>Unsharp mask</pink>
~~~python
19 generate_unsharp_mask(image, intensity)
~~~
#### Parâmetros:
- **image** (*numpy.ndarray*): Imagem de entrada em formato NumPy, com 3 canais de cor (BGR).
- **intensity** (*float*): Intensidade do efeito de nitidez.

#### Retorno:
- **numpy.ndarray**: Imagem com o efeito de nitidez aplicado.

#### Funcionamento:
1. A imagem é suavizada utilizando um desfoque Gaussiano.
2. A diferença entre a imagem original e a suavizada é calculada.
3. A imagem é ajustada adicionando um peso à diferença, criando o efeito de nitidez.
4. Retorna a imagem resultante.

### <pink>Changin contrast</pink>
~~~python
20 generate_mult_contrast(image, intensity)
~~~

#### Parâmetros:
- **image** (*numpy.ndarray*): Imagem de entrada em formato NumPy, com 3 canais de cor (BGR).
- **intensity** (*float*): Intensidade do contraste (valores > 1 aumentam o contraste e valores < 1 diminuem).

#### Retorno:
- **numpy.ndarray**: Imagem com o ajuste de contraste aplicado.

#### Funcionamento:
1. O contraste da imagem é ajustado multiplicando os valores dos pixels por um fator de intensidade.
2. Retorna a imagem ajustada.



## <snow>Brigthness</snow>

### <snow>Global brigthness</snow>
~~~python
21 generate_global_brigthness(image, intensity)
~~~
#### Parâmetros:
- **image** (*numpy.ndarray*): Imagem de entrada em formato NumPy, com 3 canais de cor (BGR).
- **intensity** (*float*): Intensidade da adição, sendo 1 o valor médio de brilho, valores negativos diminuem a intensidade. 

#### Retorno:
- **numpy.ndarray:** Imagem com adição/subtração de uma fração do valor médio de intensidade
#### Funcionamento:
- Calculo da média de luminância da imagem de entrada.
- Multiplica essa média por `intensity`.



### <snow>Gamma brigthness</snow> 
~~~python
22 generate_gamma_correction(image, gama)
~~~
#### Parâmetros:
- **image** (*numpy.ndarray*): Imagem de entrada em formato NumPy, com 3 canais de cor (BGR).
- **gama** (*float*): Taxa de ajuste/diminuição da iluminação, para gama em ((0, 1)), diminui a iluminação e para gama maior que 1, aumenta a iluminação.

#### Retorno:
- **numpy.ndarray:** Imagem "corrijida" com o fato gama

#### Funcionamento
1. Normaliza todos os valores da imagem (Nos três canais) dividindo por 255.
2. Eleva todas esses valores por `gamma` e multiplica por 255.
3. Retorna imagem ajustada.

### <snow>Random local brigthness</snow>
~~~python
23 generate_random_local_brigthness(image, n, sigma_range_x, sigma_range_y, intensity)
~~~

#### Parâmetros:
- **image** (*numpy.ndarray*): Imagem de entrada em formato NumPy, com 3 canais de cor (BGR).
- **sigma_range_x** (*float*): Intervalo normalizado \([0, 1]\) para o desvio padrão da Gaussiana no eixo X.
- **sigma_range_y** (*float*): Intervalo normalizado \([0, 1]\) para o desvio padrão da Gaussiana no eixo Y.
- **intensity** (*float*): Intensidade da modificação do brilho.

#### Retorno:
- **numpy.ndarray**: Imagem com variação local de brilho aplicada.

#### Funcionamento:
#### 1. Criação de uma matriz gaussiana bivariada de mesmo shape da imagem, possui três canais de cores com mesmo valor.

#### 2. Normaliza os valores da gaussiana e clipa ele a 8 bits (255 tons).
<div align = "center">
    <img src="images/gaussian_bivariate_center.png"  />
</div>

#### 3. Definição de deslocamento aleatório da Gaussiana dentro da imagem.
<div align = "center">
    <img src="images/gaussian_bivariate_shifted.png" />
</div>

#### 4. Adicionar essa máscara à imagem original, criando um efeito de "borramento" de luz.
