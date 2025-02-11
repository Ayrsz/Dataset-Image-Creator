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




### <red>Uniform noise</red>

~~~python
3: generate_uniform_noise(image)
~~~
--- 



### <red>Speckle noise</red>
~~~python
4 generate_speckle_noise(image)
~~~
--- 


### <red>Poisson noise</red>
~~~python
5 generate_poisson_noise(image)
~~~




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

#### Retorno:

#### Funcionamento:

### <green>Shearing warp</green>

~~~python
15 generate_shearing_warp(image, sx, sy)
~~~

#### Parâmetros:

#### Retorno:

#### Funcionamento:

### <green>Elastic warp</green>

~~~python
16 generate_elastic_warp(image, alpha)
~~~
#### Parâmetros:

#### Retorno:

#### Funcionamento:


### <green>Bilinear interpolation</green>

~~~python  
17 generate_bilinear_interpolation(image, scale)
~~~

#### Parâmetros:

#### Retorno:

#### Funcionamento:

### <green>Rotations</green>

~~~python  
18 generate_rotations(image)
~~~

#### Parâmetros:

#### Retorno:

#### Funcionamento:


## <pink>Sharpness and Contrast</pink>

### <pink>Unsharp mask</pink>
~~~python
19 generate_unsharp_mask(image, intensity)
~~~
#### Parâmetros:

#### Retorno:

#### Funcionamento:

### <pink>Changin contrast</pink>
~~~python
20 generate_mult_contrast(image, intensity)
~~~

#### Parâmetros:

#### Retorno:

#### Funcionamento:


## <snow>Brigthness</snow>

### <snow>Global brigthness</snow>
~~~python
21 generate_global_brigthness(image, intensity)
~~~

#### Parâmetros:

#### Retorno:

#### Funcionamento:



### <snow>Gamma brigthness</snow> 
~~~python
22 generate_gamma_correction(image, gama)
~~~
#### Parâmetros:
- **image** (*numpy.ndarray*): Imagem de entrada em formato NumPy, com 3 canais de cor (BGR).
- **gama** (*float*): Taxa de ajuste/diminuição da iluminação, para gama em ((0, 1)), diminui a iluminação e para gama maior que 1, aumenta a iluminação.

#### Retorno:

#### Funcionamento

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
