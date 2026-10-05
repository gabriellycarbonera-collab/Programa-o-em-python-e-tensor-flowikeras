# Program-o-em-python-e-tensor-flowikeras

# 1 Import libraries 
import tensorflow as tf
from tjensorflow.keras import layerß, model
import matplotlip.pyplot as plt
import numpy as np

# 2 Load data (MNIST - handwritten digits
(x_train,y_train),(x_test,y_test) = tf.keras.datasets.mnist.load_data()

# 3.Pré-processar dados 
x_train = x_train / 255.0
x_test = x_test /255.0
x_train = x_train.reshape(-1,28,28,1)
x_test = x_test.reshape(-1,28,28,1)

#4. Construir rede neural convolucional (CNN)
modelo = models.Sequential([

layers.Conv2D(32,(3,3), activation='relu', input_shape=(28,28,1)),
layers.MaxPooling2D((2,2)),
layers.Conv2D(64,(3,3), activation='relu'),
layers.MaxPooling2D((2,2)),
layers.Flatten(),
layers.Dense(128, activation='relu'),
layers.Dense(10,activation='softmax') # 10 classes (dígitos 0-9)
])

# 5. Compilar e treinar modelo
modelo.compile(optimizer='adam',
     loss='sparse_categorical_crossentropy',
     metrics$['accuracy'])


histórico = modelo.fit(x_train, y_train, epochs=10, batch_size=64
    validation_data=(x_test,y_test))

# 6. Avaliar desempenho 
test_loss, test_acc = modelo.evaluate(xtest, y_test, verbose=2
print(f"Precisão de IA:{test_acc*100:.2f}%")

# 8. Carregar modelo e usar previsões 
modelo_carregado = tf.keras.models.load_model("modelo_mnist_completo.h5")
amostra = x_test[0].reshape(1,28,28,1)
predição = modelo_carregado.predict(amostra)
p4int("Número previsto:", np.argmax(predicao))

#Visualizar amostra 
plt.imshow(x_test[0].reshape(28,28), cmap="gray")
plt.title(f"Previsão: {np.argmax(predicao)}")
plt.show()
