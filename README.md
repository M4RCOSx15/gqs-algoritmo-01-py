#  Verificador de Palíndromos (gqs-algoritmo-01-py)

![Python Version](https://img.shields.io/badge/python-3.14%2B-blue)
![Status](https://img.shields.io/badge/status-concluído-success)
![License](https://img.shields.io/badge/license-MIT-green)

Este repositório contém a resolução da **Missão README**, parte da disciplina de Garantia e Qualidade de Software. O projeto consiste em um algoritmo que testa se determinadas frases são palíndromos.

---

## 1: O Básico da Investigação

### O que o código faz?
O código possui como propósito principal validar se uma frase é um **palíndromo** (ou seja, se lida da esquerda para a direita é idêntica à leitura da direita para a esquerda). 
Para garantir que a verificação seja imune a formatações, a função principal realiza uma "limpeza" na string antes de testá-la:
1. Converte todas as letras para minúsculas.
2. Remove tudo o que não for letra ou número (ignorando espaços, vírgulas, hifens, etc.).
3. Compara a frase limpa com a sua versão invertida.
4. Retorna um valor booleano (`True` se for palíndromo, `False` caso contrário).

###  Como executar?
**Ferramentas mínimas:** Python 3.14 e um terminal (CMD ou VS Code).

1. Clone o repositório para a sua máquina:
   ```bash
   git clone [https://github.com/danhpaiva/gqs-algoritmo-01-py.git](https://github.com/danhpaiva/gqs-algoritmo-01-py.git)
   cd gqs-algoritmo-01-py

```

2. Crie e ative um ambiente virtual (Recomendado):
```bash
# Criação do ambiente
python -m venv venv

# Ativação no Windows:
venv\Scripts\activate

# Ativação no Linux/Mac:
source venv/bin/activate

```


3. Instale as dependências (caso exista o arquivo `requirements.txt`):
```bash
pip install -r requirements.txt

```


4. Execute o programa:
```bash
python algoritmo.py

```

### Exemplo de Saída

Ao executar o programa, o console exibirá os seguintes resultados para as frases testadas:

```text
Teste 1: False
Teste 2: True

```

---

## 2: Engenharia Reversa e Análise de Comportamento

### Desvendando os métodos

#### O Papel do bloco Principal (`main`)

O bloco principal funciona como o ponto de entrada da aplicação. Ele é responsável por orquestrar a execução: declara as variáveis contendo as duas frases de teste, invoca a função de verificação para cada uma delas e imprime o resultado final no console.

#### A Lógica da Função `analisar(entrada)`

Abaixo está a análise passo a passo de como o texto é processado (fazendo um paralelo com a lógica descrita na tarefa original):

* **Conversão para minúsculas:** O algoritmo utiliza funções nativas de string (como `.lower()` em Python) para padronizar o texto.
* **Expressão Regular / Remoção:** Substitui a função do `replaceAll()` do Java. O código remove os caracteres indesejados (como o espaço e o hífen) para garantir que apenas texto limpo seja comparado.
* **Inversão da String:** Diferente do Java que utilizaria a classe `StringBuilder` e seu método `.reverse()`, no ecossistema Python essa inversão ocorre de forma muito mais enxuta através do fatiamento (slicing) de strings, utilizando `[::-1]`.

Por que o Teste 1 falhou e o Teste 2 passou? A explicação é puramente estrutural:

| Teste | Frase Original | Resultado Limpo | Inversão | Retorno |
| --- | --- | --- | --- | --- |
| **1** | `"A sacada da casa de cadasa"` | `asacadadacasadecadasa` | `asadacedasacadadacasa` | ❌ **False** |
| **2** | `"Socorram-me, subi no ônibus em Marrocos"` | `socorrammesubinoonibusemmarrocos` | `socorrammesubinoonibusemmarrocos` | ✅ **True** |

* **Análise Técnica do Teste 1:** A string começa com o conhecido palíndromo "A sacada da casa", mas a inserção do sufixo " de cadasa" quebra totalmente a simetria da palavra. Quando limpa e invertida, as letras deixam de coincidir perfeitamente.
* **Análise Técnica do Teste 2:** É um palíndromo perfeito. Ao remover a vírgula, o hífen de "Socorram-me" e os espaços, a massa de texto restante mantém exatamente a mesma sequência de caracteres lida de ambos os lados.

---

## 3

Toda a formatação deste documento foi desenvolvida utilizando Markdown avançado, englobando a separação por títulos de hierarquia (`##`), blocos de código com *syntax highlighting*, formatação de dados estruturados em tabela e badges indicativos de tecnologia e status.

###  Sobre o Autor

**Desenvolvido por:** Marcos

**Instituição:** UNA - Ciência da Computação

> *Trabalho submetido para a disciplina de Gestão e Qualidade de Software, ministrada pelo Prof. Daniel Henrique Matos de Paiva.*

```

```
