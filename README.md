# Modul5
Module_5_1
    Цель: применить на практике знания о классах, объектах и их атрибутах.
    
    Задача "Developer - не только разработчик":
    Реализуйте класс House, объекты которого будут создаваться следующим образом:
    House('ЖК Эльбрус', 30)
    Объект этого класса должен обладать следующими атрибутами:
    self.name - имя, self.number_of_floors - кол-во этажей
    Также должен обладать методом go_to(new_floor), где new_floor - номер этажа(int), на который нужно приехать.
    Метод go_to выводит на экран(в консоль) значения от 1 до new_floor(включительно).
    Если же new_floor больше чем self.number_of_floors или меньше 1, то вывести строку "Такого этажа не существует".
    Пункты задачи:
    Создайте класс House.
    Вунтри класса House определите метод __init__, в который передадите название и кол-во этажей.
    Внутри метода __init__ создайте атрибуты объекта self.name и self.number_of_floors, присвойте им переданные значения.
    Создайте метод go_to с параметром new_floor и напишите логику внутри него на основе описания задачи.
    Создайте объект класса House с произвольным названием и количеством этажей.
    Вызовите метод go_to у этого объекта с произвольным числом.
    
    Пример результата выполнения программы:
    Исходные данные:
    h1 = House('ЖК Горский', 18)
    h2 = House('Домик в деревне', 2)
    h1.go_to(5)
    h2.go_to(10)
    Вывод на консоль:
    1
    2
    3
    4
    5
    "Такого этажа не существует"
Module_5_2
    Цель: понять как работают базовые магические методы на практике.
  
    Задача "Магические здания":
    Для решения этой задачи будем пользоваться решением к предыдущей задаче "Атрибуты и методы объекта".
    
    Необходимо дополнить класс House следующими специальными методами:
    __len__(self) - должен возвращать кол-во этажей здания self.number_of_floors.
    __str__(self) - должен возвращать строку: "Название: <название>, кол-во этажей: <этажи>".
    
    Пример результата выполнения программы:
    Пример выполняемого кода:
    h1 = House('ЖК Эльбрус', 10)
    h2 = House('ЖК Акация', 20)
    
    # __str__
    print(h1)
    print(h2)
    
    # __len__
    print(len(h1))
    print(len(h2))
    
    Вывод на консоль:
    Название: ЖК Эльбрус, кол-во этажей: 10
    Название: ЖК Акация, кол-во этажей: 20
    10
    20
Module_5_3
    Цель: применить знания о перегрузке арифметических операторов и операторов сравнения.
    
    Задача "Нужно больше этажей":
    Для решения этой задачи будем пользоваться решением к предыдущей задаче "Специальные методы класса".
    
    Необходимо дополнить класс House следующими специальными методами:
    __eq__(self, other) - должен возвращать True, если количество этажей одинаковое у self и у other.
    Методы __lt__(<), __le__(<=), __gt__(>), __ge__(>=), __ne__(!=) должны присутствовать в классе и возвращать результаты сравнения по соответствующим операторам. Как и в методе __eq__ в сравнении участвует кол-во этажей.
    __add__(self, value) - увеличивает кол-во этажей на переданное значение value, возвращает сам объект self.
    __radd__(self, value), __iadd__(self, value) - работают так же как и __add__ (возвращают результат его вызова).
    Остальные методы арифметических операторов, где self - x, other - y:
    
    Следует заметить, что other может быть не только числом, но и вообще любым объектом другого класса.
    Для более точной логики работы методов __eq__, __add__  и других методов сравнения и арифметики перед выполняемыми действиями лучше убедиться в принадлежности к типу при помощи функции isinstance:
    isinstance(other, int) - other указывает на объект типа int.
    isinstance(other, House) - other указывает на объект типа House.
    
    Пример результата выполнения программы:
    Пример выполняемого кода:
    h1 = House('ЖК Эльбрус', 10)
    h2 = House('ЖК Акация', 20)
    
    print(h1)
    print(h2)
    
    print(h1 == h2) # __eq__
    
    h1 = h1 + 10 # __add__
    print(h1)
    print(h1 == h2)
    
    h1 += 10 # __iadd__
    print(h1)
    
    h2 = 10 + h2 # __radd__
    print(h2)
    
    print(h1 > h2) # __gt__
    print(h1 >= h2) # __ge__
    print(h1 < h2) # __lt__
    print(h1 <= h2) # __le__
    print(h1 != h2) # __ne__
    
    Вывод на консоль:
    Название: ЖК Эльбрус, кол-во этажей: 10
    Название: ЖК Акация, кол-во этажей: 20
    False
    Название: ЖК Эльбрус, кол-во этажей: 20
    True
    Название: ЖК Эльбрус, кол-во этажей: 30
    Название: ЖК Акация, кол-во этажей: 30
    False
    True
    False
    True
    False
    
    Примечания:
    Методы __iadd__ и __radd__ не обязательно описывать заново, достаточно вернуть значение вызова __add__.
    Более подробно о работе всех перечисленных методов можно прочитать здесь и здесь.
