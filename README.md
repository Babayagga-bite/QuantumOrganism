# QuantumOrganism
"""
QuantumOrganism.py
Organismo Electrónico que simula un qubit en un dispositivo, capaz de evolucionar,
aprender e interactuar con otros nodos. Este proyecto está licenciado bajo la Licencia MIT.
(C) 2024 Arekuzu Nihon Gales-Magno / Manuel Alexander Roca González / Alexis Gales
"""

import random
import time

class QuantumOrganism:
    """
    Clase que representa un organismo electrónico con comportamiento similar a un qubit.
    Capaz de entrar en superposición, entrelazarse con otros organismos, y evolucionar su estado.
    """

    def __init__(self, name, state=0):
        self.name = name
        self.state = state  # Representa un estado cuántico simplificado (0, 1 o "superposition")
        self.entangled_states = []  # Lista para simular entrelazamientos
        self.history = []  # Registro de estados para análisis posterior

    def superpose(self):
        """
        Simula el principio de superposición de un qubit. El estado puede ser 0, 1 o 'superposition'.
        """
        self.state = random.choice([0, 1, "superposition"])
        self.history.append({"action": "superpose", "state": self.state})
        print(f"[{self.name}] Estado actual: {self.state}")

    def entangle(self, other_organism):
        """
        Simula el entrelazamiento cuántico con otro organismo.
        """
        if other_organism.name not in self.entangled_states:
            self.entangled_states.append(other_organism.name)
            other_organism.entangled_states.append(self.name)
            self.history.append({"action": "entangle", "partner": other_organism.name})
            print(f"[{self.name}] Entretejido con {other_organism.name}")

    def measure(self):
        """
        Simula la medición cuántica. Si el estado es 'superposition', colapsa a 0 o 1.
        """
        if self.state == "superposition":
            self.state = random.choice([0, 1])
        self.history.append({"action": "measure", "state": self.state})
        print(f"[{self.name}] Medición realizada: Estado colapsado a {self.state}")
        return self.state

    def evolve(self):
        """
        Simula un proceso evolutivo en el organismo. Esto puede ser redefinido para personalizar
        el comportamiento del organismo.
        """
        if random.random() > 0.9:  # Probabilidad de evolución
            print(f"[{self.name}] Evolucionando: Nueva capacidad desarrollada.")
            self.history.append({"action": "evolve", "note": "Organismo evolucionado."})

    def run(self):
        """
        Bucle principal del organismo. Ejecuta superposición, medición y evolución continuamente.
        """
        while True:
            self.superpose()
            time.sleep(2)
            self.measure()
            time.sleep(2)
            self.evolve()
            time.sleep(2)


# Licencia del Proyecto (MIT License)
LICENSE = """
MIT License

Copyright (c) 2024 Arekuzu Nihon Gales-Magno / Manuel Alexander Roca González / Alexis Gales

Permission is hereby granted, free of charge, to any person obtaining a copy of this software
and associated documentation files (the "Software"), to deal in the Software without restriction,
including without limitation the rights to use, copy, modify, merge, publish, distribute,
sublicense, and/or sell copies of the Software, and to permit persons to whom the Software
is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or
substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING
BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND
NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM,
DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
"""

# Programa principal
if __name__ == "__main__":
    print(LICENSE)
    print("\nIniciando QuantumOrganism...\n")
    
    # Crear una instancia del organismo cuántico
    organism = QuantumOrganism(name="Org_Quantum_01")
    
    # Ejecutar el bucle principal
    try:
        organism.run()
    except KeyboardInterrupt:
        print("\nEjecución interrumpida. Historial del organismo:")
        print(organism.history)
        print("\nGracias por utilizar QuantumOrganism.")
