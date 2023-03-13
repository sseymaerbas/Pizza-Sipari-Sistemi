# Pizza-Sipari-Sistemi

import csv
import datetime
with open("Menu.txt", "w") as menu:
    menu.write("* Lütfen Bir Pizza Tabanı Seçiniz:\n")
    menu.write("1: Klasik\n")
    menu.write("2: Margarita\n")
    menu.write("3: TürkPizza\n")
    menu.write("4: Sade Pizza\n")
    menu.write("* ve seçeceğiniz sos:\n")
    menu.write("11: Zeytin\n")
    menu.write("12: Mantarlar\n")
    menu.write("13: Keçi Peyniri\n")
    menu.write("14: Et\n")
    menu.write("15: Soğan\n")
    menu.write("16: Mısır\n")
    menu.write("* Teşekkür ederiz!")
class Pizza:
    def __init__(self, description, cost):
        self.description = description
        self.cost = cost
        
    def get_description(self):
        return self.description
        
    def get_cost(self):
        return self.cost
class KlasikPizza(Pizza):
    def __init__(self):
        super().__init__("Klasik pizza", 15)
        
class MargaritaPizza(Pizza):
    def __init__(self):
        super().__init__("Margarita pizza", 20)

class TurkPizza(Pizza):
    def __init__(self):
        super().__init__("Türk pizzası", 25)
        
class SadePizza(Pizza):
    def __init__(self):
        super().__init__("Sade pizza", 10)
class Decorator(Pizza):
    def __init__(self, component):
        self.component = component
        
    def get_cost(self):
        return self.component.get_cost() + Pizza.get_cost(self)

    def get_description(self):
        return self.component.get_description() + ' ' + Pizza.get_description(self)
class ZeytinSosu(Decorator):
    def __init__(self, component):
        super().__init__(component)
        self.description = "z"
