# barilochetrekking
Proyecto Coder house 
import unittest

from hormiguero import Hormiguero, Hormiga, Alimento

class TestHormiguero(unittest.TestCase):

    def test_crear_hormiguero_vacio(self):
        hormiguero = Hormiguero()
        self.assertEqual(hormiguero.obtener_cantidad_hormigas(), 0)

    def test_crear_hormiga(self):
        hormiguero = Hormiguero()
        hormiguero.crear_hormiga()
        self.assertEqual(hormiguero.obtener_cantidad_hormigas(), 1)

    def test_hormiga_ir_a_posicion(self):
        hormiguero = Hormiguero()
        hormiga = hormiguero.crear_hormiga()
        hormiga.ir_a_posicion(3, 4)
        self.assertEqual(hormiga.obtener_posicion(), (3, 4))

    def test_hormiga_recolectar_alimento(self):
        hormiguero = Hormiguero()
        hormiga = hormiguero.crear_hormiga()
        alimento = Alimento('hojitas', 5)
        hormiga.recolectar_alimento(alimento)
        self.assertEqual(hormiga.obtener_carga_alimento(), 5)
        self.assertEqual(alimento.obtener_cantidad(), 0)

    def test_hormiga_entregar_alimento(self):
        hormiguero = Hormiguero()
        hormiga = hormiguero.crear_hormiga()
        alimento = Alimento('hojitas', 5)
        hormiga.recolectar_alimento(alimento)
        hormiga.entregar_alimento()
        self.assertEqual(hormiga.obtener_carga_alimento(), 0)
        self.assertEqual(hormiguero.obtener_cantidad_alimento(), 5)

    def test_cantidad_total_alimento_recolectado(self):
        hormiguero = Hormiguero()
        hormiga1 = hormiguero.crear_hormiga()
        hormiga2 = hormiguero.crear_hormiga()
        alimento1 = Alimento('hojitas', 5)
        alimento2 = Alimento('migajas de pan', 10)
        hormiga1.recolectar_alimento(alimento1)
        hormiga2.recolectar_alimento(alimento2)
        self.assertEqual(hormiguero.obtener_cantidad_alimento(), 15)


if __name__ == '__main__':
    unittest.main()
class Hormiguero:
    def __init__(self):
        self.hormigas = []
        self.alimento_recolectado = 0

    def crear_hormiga(self):
        hormiga = Hormiga(self)
        self.hormigas.append(hormiga)
        return hormiga

    def obtener_cantidad_hormigas(self):
        return len(self.hormigas)

    def obtener_cantidad_alimento(self):
        return self.alimento_recolectado

    def agregar_alimento(self, cantidad):
        self.alimento_reco
