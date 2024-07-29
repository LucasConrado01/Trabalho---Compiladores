import re  # Importa a biblioteca re para usar expressões regulares

class SimpleCalculator:
    def __init__(self):
        # Inicializa o dicionário de variáveis e o conjunto de operadores válidos
        self.variables = {}
        self.valid_operators = set('+-*/()')

    def is_valid_expression(self, expression):
        # Verifica se a expressão contém apenas caracteres válidos (variáveis, números, operadores e parênteses)
        valid_pattern = re.compile(r'^[a-zA-Z0-9_+\-*/().\s]*$')
        return valid_pattern.match(expression) is not None

    def is_valid_assignment(self, assignment):
        # Verifica se a atribuição é válida (uma variável sendo atribuída a uma expressão válida)
        valid_pattern = re.compile(r'^[a-zA-Z_][a-zA-Z0-9_]*\s*=\s*[\d\w+\-*/().\s]+$')
        return valid_pattern.match(assignment) is not None

    def evaluate_expression(self, expression):
        try:
            # Verifica se a expressão contém apenas caracteres válidos
            if not self.is_valid_expression(expression):
                raise ValueError("Invalid characters in expression.")
            
            # Substitui variáveis pelos seus valores na expressão
            for var in self.variables:
                expression = expression.replace(var, str(self.variables[var]))
            
            # Avalia a expressão e retorna o resultado
            result = eval(expression)
            return result
        except Exception as e:
            # Retorna uma mensagem de erro em caso de exceção
            return f"Error: {str(e)}"

    def assign_variable(self, assignment):
        try:
            # Verifica se a atribuição é válida
            if not self.is_valid_assignment(assignment):
                raise ValueError("Invalid assignment statement.")
            
            # Divide a atribuição em variável e expressão
            var, expr = assignment.split('=', 1)
            var = var.strip()
            expr = expr.strip()
            
            # Avalia a expressão parte da atribuição
            value = self.evaluate_expression(expr)
            if isinstance(value, str) and value.startswith("Error"):
                return value
            else:
                # Armazena o valor da variável no dicionário
                self.variables[var] = value
                return f"{var} = {value}"
        except Exception as e:
            # Retorna uma mensagem de erro em caso de exceção
            return f"Error: {str(e)}"

    def run(self):
        # Loop principal que lê a entrada do usuário, executa atribuições ou avalia expressões, e imprime o resultado
        while True:
            user_input = input("Enter expression or assignment (or 'exit' to quit): ")
            if user_input.lower() == 'exit':
                break
            if '=' in user_input:
                print(self.assign_variable(user_input))
            else:
                print(self.evaluate_expression(user_input))

if __name__ == "__main__":
    # Cria uma instância da calculadora e inicia o loop principal
    calc = SimpleCalculator()
    calc.run()
