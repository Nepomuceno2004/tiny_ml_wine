# TinyML – Classificação do Dataset Wine no Raspberry Pi Pico W

## Prática com Rede Neural Artificial (RNA) para Microcontroladores

Este projeto implementa uma **Rede Neural Artificial do tipo Perceptron Multicamadas (MLP)** embarcada no **Raspberry Pi Pico W**, utilizando a biblioteca **TensorFlow Lite Micro (TFLM)** para executar **inferência diretamente no microcontrolador**, caracterizando uma aplicação típica de **TinyML**.

O projeto demonstra o **fluxo completo de desenvolvimento em TinyML**, desde o pré-processamento e treinamento do modelo em ambiente de alto nível até o **deploy e execução em hardware com recursos extremamente limitados**.

---

## 📌 Objetivos

- Demonstrar o fluxo completo de TinyML:  
  **Criação → Treinamento → Conversão → Deploy → Inferência embarcada**
- Utilizar o **dataset Wine**, com 13 características e 3 classes.
- Realizar o **balanceamento do dataset** por *undersampling*.
- Aplicar **normalização padrão (StandardScaler)** de forma idêntica no treinamento e no ambiente embarcado.
- Treinar uma **Rede Neural MLP** para classificação multiclasse.
- Converter o modelo para **TensorFlow Lite (.tflite)**.
- Gerar o modelo no formato **array C (.h)** para uso com TFLite Micro.
- Executar inferência embarcada utilizando **TensorFlow Lite Micro (TFLM)**.
- Construir e exibir a **matriz de confusão 3×3**.
- Calcular a **acurácia final** diretamente no microcontrolador.
- Integrar código **C/C++** ao TensorFlow Lite Micro via *wrapper*.

---

## 🧠 Visão Geral do Projeto

A aplicação realiza as seguintes etapas:

- Carregamento do **dataset Wine**.
- Balanceamento das classes para garantir igualdade no número de amostras.
- Divisão dos dados em **treino e teste** mantendo a proporção das classes.
- Normalização dos dados com **StandardScaler**.
- Treinamento de uma rede neural MLP com:
  - Duas camadas ocultas (16 e 8 neurônios)
  - Função de ativação **ReLU**
  - Camada de saída **Softmax** (3 classes)
- Avaliação do modelo com:
  - Acurácia
  - Matriz de confusão
  - Relatório de classificação
- Exportação do modelo para os formatos:
  - `.keras`
  - `.h5`
  - `.tflite`
- Conversão do modelo `.tflite` para **array C (.h)**.
- Inferência amostra por amostra em ambiente embarcado.
- Reconstrução e validação do modelo TFLite a partir do arquivo `.h`.

---

## 🧪 Dataset Utilizado

**Wine Dataset (scikit-learn)**

- Classes: 3 tipos de vinho
- Atributos: 13 características físico-químicas
- Total original: 178 amostras
- Dataset balanceado para **48 amostras por classe**
- Total após balanceamento: **144 amostras**

O balanceamento evita viés no treinamento e melhora a confiabilidade dos resultados, especialmente em aplicações de TinyML.

---

## 📊 Resultados

- O modelo apresentou **boa acurácia** mesmo após a conversão para TensorFlow Lite.
- A matriz de confusão confirma a capacidade de separação entre as três classes.
- O projeto comprova que **modelos de Machine Learning podem ser executados em microcontroladores**, desde que o fluxo de TinyML seja corretamente aplicado.

---

## 👥 Autores

- Aulo César  
- Leonardo Romão  
- Marcus Vinícius  
- Matheus Nepomuceno

**Mentor:** Auerê Veras  
**Data:** 17/12/2025
