# Gerenciamento-de-Invent-rio
Gerenciamento de Inventário de Estoque

import mysql.connector

conn = mysql.connector.connect(
    host="localhost",
    user="root",
    password="sua_senha",
    database="estoque"
)

cursor = conn.cursor()

cursor.execute('''CREATE TABLE fornecedores (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(255) NOT NULL
)''')

cursor.execute('''CREATE TABLE categorias (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(255) NOT NULL
)''')

cursor.execute('''CREATE TABLE produtos (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(255) NOT NULL,
    categoria_id INT,
    fornecedor_id INT,
    estoque INT,
    FOREIGN KEY (categoria_id) REFERENCES categorias(id),
    FOREIGN KEY (fornecedor_id) REFERENCES fornecedores(id)
)''')

conn.commit()
conn.close()
