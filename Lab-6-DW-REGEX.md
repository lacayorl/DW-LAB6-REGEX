Lab 6 DW REGEX
================
Roberto Lacayo
4/10/2021

## 1. Genere una expresión regular que sea capaz de detectar las placas de un vehículo particular guatemalteco.

``` r
placas <- c('P365GRL','P452BQQ','P043JVB','M543DDF','P238HJÑ', 'P078AGR','PDFR786','P3424GH')

str_detect(placas, '^[P]{1}[0-9]{3}(?![AEIOUÑ])[A-Z]{3}$')
```

    ## [1]  TRUE  TRUE  TRUE FALSE FALSE FALSE FALSE FALSE

Con la expresión regular anterior podemos validar placas de carros
particulares de Guatemala, en donde deben iniciar con la letra P,
seguida por una serie de tres números incuildo el 0 a la izquierda y
terminando con una seria de tres letras sin incluir vocales ni la Ñ

## 2. Genere una expresión regular que valide si un archivo es de tipo .pdf o jpg.

Ejemplo1.pdf, prueba2.PDF, respuestas\_del\_examen.jpg, amor.JPG

``` r
archivos <- c('Ejemplo1.pdf', 'prueba2.PDF', 'respuestas_del_examen.jpg', 'amor.JPG', 'Este_No.doc')
str_extract(archivos,'[.](jpg|JPG|pdf|PDF)$')
```

    ## [1] ".pdf" ".PDF" ".jpg" ".JPG" NA

Esta expresión regular valida que los archivos sean tipo jpg o pdf,
tambien en mayuscula y podemos ver como no aplica para el ultimo archivo
que es un doc.

## 3. Genere una expresión regular para validar contraseñas de correo.

Una contraseña de correo debe contener por lo menos 8 caracteres, una
letra mayúscula y un carácter especial

``` r
contraseñas <- c('Guli1299$','chechA!!!','dAnIelArturO?','yoyopo7654$','Duyh87')
str_detect(contraseñas, '^(?=.*[a-z])(?=.*[A-Z])(?=.*[@$!%*?&])[A-Za-z\\d@$!%*?&]{8,}$')
```

    ## [1]  TRUE  TRUE  TRUE FALSE FALSE

## 5. Cree una expresión regular que encuentre todas las palabras de la primera línea, pero ninguna de la segunda.

-   pit, spot, spate, slap two, respite
-   pt, Pot, peat, part

``` r
palabras <- c('pit', 'spot', 'spate', 'slap two', 'respite', 'pt', 'Pot', 'peat', 'part')

str_extract(palabras,'.*p.t.*')
```

    ## [1] "pit"      "spot"     "spate"    "slap two" "respite"  NA         NA        
    ## [8] NA         NA

## 7. Genere una expresión regular que sea capaz de obtener correos de la UFM.

La sigueinte expresión regular obtiene correos unicamente de la ufm, es
decir que contienen extensión institucional educativa y el nombre de la
ufm como dirección

``` r
correos <- c('robertolacayo@ufm.edu', 'robertolacayo@gmail.com', 'daniellopez@ufm.edu', 'guliovale@ufm.edu')
str_extract(correos, '[A-Za-z]+@[ufm]+.(edu)$')
```

    ## [1] "robertolacayo@ufm.edu" NA                      "daniellopez@ufm.edu"  
    ## [4] "guliovale@ufm.edu"

## 8. En el mundo distópico de Eurasia, Big Brother le asigna un identificador único a cada ciudadano. Genere una expresión regular que valide las identificaciones. Composición del id:

-   El id inicia con 0 a 3 letras minúsculas (puede tener 0 letras
    minúsculas hasta tres letras minúsculas)
-   Luego es seguido por una cadena de dígitos que puede ser de 2 a 9
    dígitos respectivamente.
-   Inmediatamente después de la cadena de dígitos, se encuentra por lo
    menos tres letras mayúsculas.
-   Ej: abc012333ABCDEEEE

``` r
id_eurasia <- c('abc012333ABCDEEEE', 'df095777DRTE', '45768GHJK', 'abcd567444YUTR')
str_detect(id_eurasia,'^[a-z]{0,3}[0-9]{2,9}[A-Z]{2,}$')
```

    ## [1]  TRUE  TRUE  TRUE FALSE
