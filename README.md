[11/3 06:42] Fabio Empresa Wch Tech: import pandas as pd
import numpy as np
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestRegressor
from sklearn.metrics import mean_absolute_error

# Carregar dados (exemplo fictício)
dados = pd.DataFrame({
    'temperatura': [25, 30, 22, 27, 26, 31, 29, 28, 24, 32],
    'chuva': [100, 50, 200, 150, 80, 60, 90, 70, 110, 40],
    'safra_passada': [500, 400, 600, 550, 480, 450, 470, 460, 490, 420],
    'demanda_real': [520, 390, 610, 560, 470, 430, 460, 450, 500, 410]  # O que queremos prever
})

# Separar variáveis de entrada e saída
X = dados[['temperatura', 'chuva', 'safra_passada']]
y = dados['demanda_real']

# Dividir dados em treino e teste
X_treino, X_teste, y_treino, y_teste = train_test_split(X, y, test_size=0.2, random_state=42)

# Criar e treinar o modelo
modelo = RandomForestRegressor(n_estimators=100, random_state=42)
modelo.fit(X_treino, y_treino)

# Fazer previsões
y_pred = modelo.predict(X_teste)

# Avaliar modelo
erro = mean_absolute_error(y_teste, y_pred)
print(f'Erro médio absoluto: {erro:.2f}')

# Exemplo de previsão com novos dados
novos_dados = np.array([[27, 120, 510]])  # Exemplo com nova temperatura, chuva e safra anterior
previsao = modelo.predict(novos_dados)
print(f'Previsão de demanda: {previsao[0]:.2f}')
[11/3 06:42] Cleyson Empresa Wch Tech: CREATE DATABASE agro_vendas;

CREATE TABLE vendas (
    id SERIAL PRIMARY KEY,
    produto VARCHAR(100),
    quantidade INT,
    preco DECIMAL(10,2),
    data_venda DATE
);

CREATE TABLE clima (
    id SERIAL PRIMARY KEY,
    data_clima DATE,
    temperatura DECIMAL(5,2),
    chuva DECIMAL(5,2)
);

CREATE TABLE previsoes (
    id SERIAL PRIMARY KEY,
    data_prevista DATE,
    produto VARCHAR(100),
    demanda_prevista INT
);
[11/3 06:43] Cleyson Empresa Wch Tech: CREATE DATABASE agro_vendas;

CREATE TABLE vendas (
    id SERIAL PRIMARY KEY,
    produto VARCHAR(100),
    quantidade INT,
    preco DECIMAL(10,2),
    data_venda DATE
);

CREATE TABLE clima (
    id SERIAL PRIMARY KEY,
    data_clima DATE,
    temperatura DECIMAL(5,2),
    chuva DECIMAL(5,2)
);

CREATE TABLE previsoes (
    id SERIAL PRIMARY KEY,
    data_prevista DATE,
    produto VARCHAR(100),
    demanda_prevista INT
);
