# Dicionário para armazenar alunos e suas presenças
alunos_cadastrados = {}
presenca = {}

def registrar_aluno(nome, matricula):
    """
    Função para registrar um novo aluno no sistema.
    Verifica se o aluno já está cadastrado usando o número de matrícula.
    """
    if matricula in alunos_cadastrados:
        print(f"Aluno já cadastrado: {alunos_cadastrados[matricula]}.")
    else:
        alunos_cadastrados[matricula] = nome
        presenca[matricula] = False  # Define como 'não presente'
        print(f"Aluno {nome} cadastrado com sucesso.")

def registrar_presenca(matricula):
    """
    Função para registrar a presença do aluno.
    """
    if matricula in alunos_cadastrados:
        if not presenca[matricula]:  # Verifica se a presença já foi registrada
            presenca[matricula] = True
            print(f"Presença registrada para {alunos_cadastrados[matricula]}.")
        else:
            print(f"Presença já registrada para {alunos_cadastrados[matricula]}.")
    else:
        print("Matrícula não encontrada. Por favor, cadastre o aluno antes.")

# Exemplo de uso
registrar_aluno("Mariana Camões", "12345")
registrar_aluno("Stheffanny Mayara", "67890")
registrar_aluno("Beatriz Soares", "12345")  # Tentativa de cadastro duplicado

registrar_presenca("12345")  # Registra presença para Mariana
registrar_presenca("12345")  # Tentativa de presença duplicada
registrar_presenca("67890")  # Registra presença para Stheffanny
registrar_presenca("11111")  # Tentativa com matrícula não cadastrada

import sqlite3

# Função para conectar ao banco de dados
def connect_to_db(db_name):
