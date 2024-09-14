#🧮 Calculadora com Armazenamento de Resultados

Este projeto é uma calculadora simples desenvolvida em Python, que suporta variáveis, operações matemáticas básicas e armazena os resultados de cálculos anteriores para reutilização. Além disso, oferece um histórico interativo para consultar os resultados passados. 🔥

#📜 Funcionalidades
Suporta operações aritméticas: adição (+), subtração (-), multiplicação (*), divisão (/).
Aceita números reais (com ou sem ponto decimal).
Usa variáveis pré-definidas como x e y.
Armazena o histórico dos cálculos passados.
Permite reutilizar os resultados anteriores nas expressões futuras.
Possibilidade de visualizar o histórico de resultados digitando o comando historico.

#🚀 Como Funciona
Entrada de Expressões:

Você pode digitar expressões como x + y * 2, onde x e y são variáveis.
A calculadora processa a expressão e exibe o resultado.
Armazenamento de Resultados:

Cada cálculo é automaticamente salvo em um histórico interno.
O resultado é armazenado em uma chave do tipo "resultado_X", onde X é o número da expressão (ex: resultado_1, resultado_2).
Reutilização de Resultados:

Você pode reutilizar os resultados anteriores nas novas expressões. Por exemplo, se resultado_1 = 50, você pode usar resultado_1 + 10 em expressões futuras.
Comando de Histórico:

Para ver o histórico completo dos resultados calculados, basta digitar historico durante a execução.

#📚 Exemplo de Uso
bash
Copiar código
Digite uma expressão (ou 'sair' para terminar, 'historico' para ver resultados passados): x + y * 2
Resultado: 50.0

Digite uma expressão (ou 'sair' para terminar, 'historico' para ver resultados passados): resultado_1 - 10
Resultado: 40.0

Digite uma expressão (ou 'sair' para terminar, 'historico' para ver resultados passados): historico

Histórico de Resultados:
resultado_1: 50.0
resultado_2: 40.0
📦 Estrutura do Projeto
calculadora.py: Arquivo principal que contém o código da calculadora com o histórico de resultados.
README.md: Documentação do projeto (este arquivo).
