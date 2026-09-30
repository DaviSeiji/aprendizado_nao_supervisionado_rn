# Projeto 2 — Quantização de Cores com SOM e GNG

## Objetivo

O objetivo deste projeto é compreender o funcionamento do **aprendizado competitivo** e da **preservação topológica** por meio da redução da paleta de cores de imagens utilizando:

- Self-Organizing Maps (SOM);
- Growing Neural Gas (GNG).

A imagem digital deverá ser tratada como um conjunto de dados tridimensional, no qual cada pixel representa uma amostra com três características:

- Red (R);
- Green (G);
- Blue (B).

## Etapas do Projeto

### 1. Extração dos dados

O sistema deve carregar uma imagem colorida e extrair todos os seus pixels.

Os valores RGB devem ser normalizados para o intervalo `[0, 1]`.

### 2. Treinamento

Devem ser avaliadas as seguintes configurações:

#### SOM

Utilizar grids:

- 4 × 4;
- 8 × 8;
- 16 × 16.

#### GNG

Utilizar redes com:

- 16 neurônios;
- 64 neurônios;
- 256 neurônios.

Durante o treinamento, devem ser realizados ajustes nos hiperparâmetros das redes.

As redes geradas devem ser avaliadas utilizando:

- erro de quantização;
- erro topológico.

### 3. Inferência

Para cada pixel da imagem original, deve ser encontrado o **neurônio vencedor (BMU)** da rede treinada.

A cor original do pixel deve ser substituída pela cor correspondente aos pesos do neurônio vencedor.

### 4. Reconstrução

Após a quantização, a matriz da imagem deve ser reconstruída utilizando as novas cores e exibida para comparação com a imagem original.

## Experimentos Complementares

### K-Means

Deve ser utilizado o **K-Means** como baseline sem topologia, considerando:

- K = 16;
- K = 64;
- K = 256.

### Conjunto de Imagens

Devem ser utilizadas pelo menos **5 imagens com perfis distintos**, incluindo características como:

- poucas cores dominantes;
- gradientes suaves;
- alta saturação;
- objetos pequenos com cores raras.

### Repetições

Cada configuração deve ser executada utilizando pelo menos **5 sementes diferentes**.

Os resultados devem ser reportados utilizando:

**média ± desvio padrão**

## Avaliações Quantitativas

Devem ser avaliados os seguintes aspectos:

### Qualidade da Imagem

- diferença entre a imagem original e a imagem quantizada;
- histograma das diferenças.

### Uso dos Neurônios

- histograma de vitórias;
- número de neurônios não ativados.

### Custo Computacional

- tempo de treinamento;
- tempo de inferência;
- custo da busca pela BMU.

## Avaliações Qualitativas

Devem ser realizadas análises visuais dos resultados obtidos.

### Reconstruções

As imagens reconstruídas devem ser comparadas lado a lado, com atenção especial para:

- gradientes suaves;
- bordas;
- objetos pequenos com cores raras.

### Mapas de Erro

Deve ser calculado o erro `ΔE` por pixel e apresentado utilizando um **heatmap**.

### Espaço de Cor

Os pixels devem ser visualizados no espaço de cores juntamente com os protótipos aprendidos.

Para a SOM, deve ser apresentada a malha da rede.

Para a GNG, deve ser apresentado o grafo gerado pela rede.

## Questões para Discussão

Ao final do projeto, os resultados devem permitir discutir as seguintes questões:

1. O erro topológico se correlaciona com a qualidade visual da reconstrução?

2. Por que a SOM com vizinhança final não nula tende a apresentar erro de quantização maior do que o K-Means com o mesmo valor de K?

3. Em que tipos de imagem uma rede supera a outra, e por quê?

4. As métricas numéricas concordam com a percepção visual? Em quais situações elas divergem?