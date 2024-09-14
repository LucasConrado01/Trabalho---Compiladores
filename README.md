Passos para que o código funcione:
📥 Instalação do ANTLR4 e Configuração do Ambiente:

🔧 Você deve instalar o ANTLR4 e configurar o ambiente corretamente.
Faça o download do arquivo antlr-4.8-complete.jar e configure o CLASSPATH no seu ambiente. Execute os seguintes comandos:

      cd /usr/local/lib
      sudo curl -O https://www.antlr.org/download/antlr-4.8-complete.jar
      export CLASSPATH=".:/usr/local/lib/antlr-4.8-complete.jar:$CLASSPATH"
      alias antlr4='java -jar /usr/local/lib/antlr-4.8-complete.jar'
      alias grun='java org.antlr.v4.gui.TestRig'
      
Isso permite que você use o comando antlr4 para gerar os arquivos lexer e parser.

🐍 Instalação do runtime Python para ANTLR:

🛠️ Para que o código Python funcione com ANTLR, instale o pacote antlr4-python3-runtime com o seguinte comando:

      pip3 install antlr4-python3-runtime

📄 Geração do Lexer e Parser:
📜 Depois de configurar o ANTLR, use o arquivo de gramática Calculantlr.g4 para gerar os arquivos necessários para o lexer e parser:
      antlr4 -Dlanguage=Python3 Calculantlr.g4 -visitor -o dist

O comando acima gera os arquivos CalculantlrLexer.py, CalculantlrParser.py e CalculantlrVisitor.py dentro da pasta dist. Certifique-se de que a gramática está correta!

💻 Execução do Código:
Agora, você pode executar o código com o Python normalmente. O código lê uma expressão matemática, realiza o "lexing" e "parsing", e então avalia a expressão com o visitor personalizado:
      python3 main.py
