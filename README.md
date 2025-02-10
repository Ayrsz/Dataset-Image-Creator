<style>
grey { color: Grey }
red { color: LightCoral }
blue { color: RoyalBLue }
yellow { color: Yellow}
green { color: LightGreen}
</style>




# References and Methods


# Propose


# Functions


## <grey>Blurs</grey>

### <grey>Gaussian blur</grey>
~~~ python
0: generate_gaussian_blur(image, sigma, kernel_size)
~~~

Apply a gaussian filter in the image, smoothing high frequencies making a blur effect. Simple function who use opencv gaussian blur

Parameters:
- **sigma**: sigmaX/sigmaY from the kernel of the gaussian filter [**FLOAT**]
- **kernel_size**: size of the kernel [**INT**]

---
### <grey>Motion blur<grey>
~~~python
1: generate_motion_blur(image, kernel_size)
~~~ 




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

--- 


### <blue>Color saturation HSV</blue>
~~~python
10 generate_color_saturation_hsv(image)
~~~

---



### <blue>Color saturation L.A.B</blue>
~~~python
11 generate_color_saturation_lab(image)
~~~


## <yellow> JPEG'S compressions </yellow>

### <yellow>JPEG compression</yellow>
~~~python
12 generate_compression_jpeg(image)
~~~
---

### <yellow>JPEG2000 compression</yellow>

~~~python 
13 generate_compression_jpeg2000(image)
~~~

---


## <green>Warpping<green>


### Invert
~~~python
14 generate_invert_warp(image)
~~~

### Shearing warp

~~~python
15 generate_shearing_warp(image, sx, sy)
~~~

### Elastic warp

~~~python
16 generate_elastic_warp(image, alpha)
~~~

### Bilinear interpolation

~~~python  
17 generate_bilinear_interpolation(image, scale)
~~~

### Rotations

~~~python  
18 generate_rotations(image)
~~~

---  


## Sharpness and Contrast

### Unsharp mask
~~~python
19 generate_unsharp_mask(image, intensity)
~~~

--- 

### Changin contrast
~~~python
20 generate_mult_contrast(image, intensity)
~~~



## Brigthness

### Global brigthness
~~~python
21 generate_global_brigthness(image, intensity)
~~~
---

### Gamma brigthness 
~~~python
22 generate_gamma_correction(image, gama)
~~~
---  

### Random local brigthness
~~~python
23 generate_random_local_brigthness(image, n, sigma_range_x, sigma_range_y)
~~~
Dada uma imagem de tamanho **(L x H)**, a imagem de feixe de luz "F" é criada partindo de uma matriz gaussiana bivariada **(L x H)**, com sigma_x/sigma_y presente dentro do range específicado no parâmetro. 

