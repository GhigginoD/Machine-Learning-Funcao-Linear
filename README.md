
# LearnLinear

Aprendendo como criar uma IA para prever o resultado de uma função Linear de uma função de 1°grau.

**f(x) = 2x+1**



## Stack utilizada

HTML, TensorFlow




## Setup Inicial

Para ensinar a IA deste projeto, foram utilizados os seguintes valores de teste.

``` 
f(-1) = -1

f(0) = 1 

f(1) = 3

f(2) = 5

f(3) = 7

f(4) = 9
``` 

## Uso/Exemplos

```javascript
async function learnLinear(){
      // Saidas de uma camada, são as entradas de uma proxima
      // Preparação do modelo
      const model = tf.sequential();
      model.add(tf.layers.dense({units: 1, inputShape: [1]}));

      model.compile({
        loss: "meanSquaredError", // Modelo de perda
        optimizer: "sgd"          // Modelo de treinamento de optimização
      });
      // 1° parametro => valores passados
      // 2° parametro => quantidade de linhas e quantidade de colunas
      const xs = tf.tensor2d([-1, 0, 1, 2, 3, 4], [6, 1]); 
      const yx = tf.tensor2d([-1, 1, 3, 5, 7, 9], [6, 1]);

      // treinando o modelo a partir dos valores de x e y 250 vezes 
      await model.fit(xs,ys, {epochs: 250});

      // prevendo o valor de Y quando o valor de X é igual a 20
      document.getElementById('outputResult').innerText = model.predict(tf.tensor2d([20], [1, 1]));

    }
```

