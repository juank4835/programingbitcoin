class FieldElement:

    # Definimos los atributos num y prime de la clase FieldElement:
    # num = elemento del campo/cuerpo finito
    # prime = el orden/tamaño del campo/cuerpo finito. El orden del campo debe ser primo si fuera un número compuesto,
    # multiplicar el conjunto por uno de los divisores daría como resultado un conjunto más pequeño. Lo cual afectaría
    # el pequeño teorema de Fermat el cual logra definir la division a través del inverso múltiplicativo solo
    # para campos finitos primos.
    def __init__(self, num, prime):

        # Verificamos que el elemento num esté entre el campo finito. De lo contrario, generamos un ValueError
        # que indique que el elemento esta fuera del campo. Asignamos valores para inicializar el objeto.
        if num >= prime or num < 0:
            raise ValueError(f"Num {num} not in the field range 0 to {prime - 1}")
        self.num = num
        self.prime = prime

    # Definimos la manera como queremos imprimir una instancia de FieldElement
    def __repr__(self):
        return f"FieldElement_{self.prime} ({self.num})"

    # Comprobamos si dos objetos de la clase FieldElement son iguales (==).
    def __eq__(self, other):
        # Si other es el un número en el infinito no cumple la igualdad.Se retorna False
        if other is None:
            return False
        # Solo se cumple cuando tanto el elemento del campo y el campo son el mismo.
        return self.num == other.num and self.prime == other.prime

    #Comprobamos si dos objetos FieldElement no son iguales (!=).
    def __ne__(self, other):
        return not (self == other)

    def __add__(self, other):
        # Nos aseguramos que los elementos se encuentren en el mismo campo
        if self.prime != other.prime:
            raise TypeError("Cannot add two numbers in different Fields")
        # Definimos la suma de un campo finito con el modulo para que cumpla la propiedad cerrada.
        num = (self.num + other.num) % self.prime
        return self.__class__(num, self.prime)

    def __sub__(self, other):
        if self.prime != other.prime:
            raise TypeError("Cannot subtract two numbers in different Fields")
        num = (self.num - other.num) % self.prime
        return self.__class__(num, self.prime)

    def __mul__(self, other):
        if self.prime != other.prime:
            raise TypeError("Cannot multiply two numbers in different Fields")
        num = (self.num * other.num) % self.prime
        return self.__class__(num, self.prime)

    def __truediv__(self, other):
        if self.prime != other.prime:
            raise TypeError("Cannot divide two numbers in different Fields")
        num = self.num * pow(other.num, self.prime - 2, self.prime) % self.prime
        return self.__class__(num, self.prime)

    def __pow__(self, exponent):
        n = exponent % (self.prime - 1)
        num = pow(self.num, n, self.prime)
        return self.__class__(num, self.prime)

    def __rmul__(self, coefficient):
        num = (self.num * coefficient) % self.prime
        return self.__class__(num=num, prime=self.prime)
