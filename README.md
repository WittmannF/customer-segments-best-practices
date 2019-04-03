# Melhores práticas para o projeto Customer Segments
- Também podemos visualizar as amostras mais relevantes a partir deste *heatmap*:
```
import matplotlib.pyplot as plt
import seaborn as sns # instale via terminal: 'pip install seaborn'
%matplotlib inline 
fig, ax = plt.subplots(figsize=(10,30))
sns.heatmap(data[:150], annot=True, ax=ax)
```
![Screen Shot 2018-01-14 at 03.12.11.png](https://udacity-reviews-uploads.s3.us-west-2.amazonaws.com/_attachments/38140/1515895965/Screen_Shot_2018-01-14_at_03.12.11.png)

- Visualização das correlações

```
import seaborn as sns
sns.heatmap(data.corr(), annot=True);
```
![download.png](https://udacity-reviews-uploads.s3.amazonaws.com/_attachments/38140/1508794850/download.png)

- Distribuição dos atributos antes da aplicação da transformação logarítimica
![download.png](https://udacity-reviews-uploads.s3.us-west-2.amazonaws.com/_attachments/38140/1554310842/download.png)


- Distribuição dos atributos após a transformação logarítmica:

[![download (18).png](https://udacity-reviews-uploads.s3.us-west-2.amazonaws.com/_attachments/38140/1535106345/download__18_.png)](https://udacity-reviews-uploads.s3.us-west-2.amazonaws.com/_attachments/38140/1535106345/download__18_.png)

- Distribuição dos atributos após a remoção de outliers:  
[![download (17).png](https://udacity-reviews-uploads.s3.us-west-2.amazonaws.com/_attachments/38140/1535106281/download__17_.png)](https://udacity-reviews-uploads.s3.us-west-2.amazonaws.com/_attachments/38140/1535106281/download__17_.png)

- Revisão sobre PCA
    - Disponível gratuitamente no curso [Intro to Machine Learning](https://classroom.udacity.com/courses/ud120/lessons/2962298545/concepts/30765685820923)
    - Principais vídeos:
        - https://www.youtube.com/watch?time_continue=62&v=nDuo5ECT1G4
        - https://www.youtube.com/watch?time_continue=4&v=Kst3mlrqJnQ
        - https://www.youtube.com/watch?time_continue=2&v=i6zv8vyZBk0
        - https://www.youtube.com/watch?v=cTjBlM2ATLQ
        - https://www.youtube.com/watch?time_continue=1&v=PRjmvj6Vubs
        - https://www.youtube.com/watch?time_continue=3&v=th34aboBOO0    
        ![Screen Shot 2019-04-03 at 14 12 53](https://user-images.githubusercontent.com/5733246/55513466-9aeef200-561a-11e9-86df-912862b3e2e4.png)

### Questão 5
A transformação de cada componente faz uso do produto desses pesos com a diferença entre os valores de cada categoria e a sua média:


    Transformação PCA = Pesos x (Valores dos Atributos - Média dos Atributos)

Pesos positivos para um dado atributo fazem com que qualquer valor deste atributo que seja _acima da média_ também assuma valores positivos na transformação. Valores abaixo da média são traduzidos em valores negativos na transformação. Reciprocamente, pesos negativos com alta amplitude fazem com que valores acima da média assumam valores negativos na transformação e valores abaixo da média assumam valores positivos na transformação. Portanto, o sinal do peso sempre sempre refletirá nos atributos que estão acima da média.

Uma visualização gráfica talvez seja mais fácil. O seguinte biplot permite comparar algumas amostras transformadas em 2D com a amostra original com 6 dimensões (a ordem de categorias para os valores originais é `['Fresh', 'Milk', 'Grocery', 'Frozen', 'Detergents_Paper', 'Delicatessen']`) :

[![download (2).png](https://udacity-reviews-uploads.s3.us-west-2.amazonaws.com/_attachments/38140/1529150497/download__2_.png)](https://udacity-reviews-uploads.s3.us-west-2.amazonaws.com/_attachments/38140/1529150497/download__2_.png)

Como os pesos de Milk, Grocery e Detergents_Paper estão do lado esquerdo (eixo negativo), isto significa que clientes com altos gastos nestas três categorias também ficam do lado esquerdo enquanto que clientes que gastaram pouco nestas três categorias ficarão do lado direito.

- Este slide resume bem a diferença entre ambos GMM e k-means:  
[![slide_6.jpg](http://images.slideplayer.com/17/5305656/slides/slide_6.jpg)](http://images.slideplayer.com/17/5305656/slides/slide_6.jpg)

- Este GIF ilustra como GMM funciona:

[![Animation1.gif](https://udacity-reviews-uploads.s3.us-west-2.amazonaws.com/_attachments/38140/1529162571/Animation1.gif)](https://udacity-reviews-uploads.s3.us-west-2.amazonaws.com/_attachments/38140/1529162571/Animation1.gif)

- E este, como K-Means funciona:

[![K-means_convergence.gif](https://udacity-reviews-uploads.s3.us-west-2.amazonaws.com/_attachments/38140/1529162788/K-means_convergence.gif)](https://udacity-reviews-uploads.s3.us-west-2.amazonaws.com/_attachments/38140/1529162788/K-means_convergence.gif)

- Podemos claramente ver que o GMM é um caso generalizado de k-means: o GMM executa uma atribuição suave enquanto o k-means executa uma atribuição dura.

