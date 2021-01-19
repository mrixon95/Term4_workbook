# Term 4 Workbook - T4A1 Developer Workbook

### Question 13



```
import random

class Car:
    def __init__(self, brand):
        self.car_name = brand

    def present(self):
        return 'I have a ' + self.car_name

class Model(Car):
    def __init__(self, brand, mod):
        super().__init__(brand)
        self.model = mod

    def show(self):
        return self.present() + ', it was made in ' + str(self.model)

makes = ["Ford", "Holden", "Toyota"]
models = []
for i in range(40):
    models.append(i+1980)

def random_int_from_interval(min,max):
    return random.randint(min, max)

for model in models:
    make = makes[random_int_from_interval(0, len(makes)-1)]
    model = models[random_int_from_interval(0, len(makes)-1)]
    my_car = Model(make, model)
    print(my_car.show())
```



### Comments on what the code snippets does on each line.

<b>Lines 1 - 7</b>

    import random
    
    class Car:
        def __init__(self, brand):
            self.car_name = brand
    	def present(self):
        	return 'I have a ' + self.car_name


**Line 1** - The import statement tells Python to search for the module named ```random```. The `random` module uses pseudo-random number generators for its various distributions. The module is found by the interpreter and a module object  called `random` is initialised. This module contains the function `randint` which will be used later in the code snippet for randomly selecting a make and model of a car.

**References**

https://docs.python.org/3/tutorial/modules.html



**Line 3** - This line creates a new class called `Car`. This is a blueprint for a new type of object and it "allows new instances of that type to be created". No instances of `Car` can be initialised before defining the `Car` class so it is unsurprising that it is at the top of the file. Furthermore, classes usually have attributes and methods to give it functionality. The lines to follow give the `Car` class its functionality.

**References**

https://docs.python.org/3/tutorial/classes.html

https://realpython.com/python-main-function/



**Line 4** - The `Car` class has the reserved`__init__` method. The `__init__` method is known as a constructor and when a new instance of the `Car` class is created, the `__init__` method is called so that the statements within the `__init__` method are executed. The `__init__` method is used to initialise the attributes of an object. In this case, the value of one instance variable is set in the `__init__` method. The instance variable is`car_name`and its value is set for just that particular instance by using `self`. 

The first parameter of a method is named `self` by convention. `self` is used to represent that particular instance of the class. Therefore by using `self.car_name`, the instance variable `car_name` is set for just that particular instance. The new car object has it's `car_name` attribute set equal to the value of the `brand` argument.

**References**

https://www.tutorialspoint.com/What-is-difference-between-self-and-init-methods-in-python-Class

https://www.geeksforgeeks.org/self-in-python-class/

https://www.journaldev.com/18397/python-class-init

https://micropyramid.com/blog/understand-self-and-__init__-method-in-python-class/

https://www.edureka.co/blog/self-in-python/



**Line 7** - This line defines a method called `present`. The method is available to all instances of the `Car` class and classes derived from it. When called on a particular `Car` object, it concatenates 'I am a '  and the object's car name before returning the result as one string. If the car name was 'Holden', it would concatenate the two strings 'I am a ' and 'Holden', before returning the one string 'I am a Holden'. 

**References**

https://docs.python.org/3/tutorial/classes.html

https://www.geeksforgeeks.org/python-string-concatenation/



<b>Lines 10 - 16</b>

```
class Model(Car):
    def __init__(self, brand, mod):
        super().__init__(brand)
        self.model = mod

    def show(self):
        return self.present() + ', it was made in ' + str(self.model)
```



**Line 10** - The lines defines another class called `Model`. The `model` class is defined to inherit from the base class called `Car` which has previously been executed. Inheritance in Python means that attributes and methods in the base class are inherited into the derived class. In this example, the base class is `Car` and the derived class is `Model` . The `Car`'s attributes and methods are available to be accessed by `Model` . Specially, the attribute `car_name` and method `present` are accessible to the `Model` class.



Line 11. The line has the method that initialises the `Model` object. The first parameter is `self` and refers to the particular instance of the model class that is being instantiated. There are two other parameters named brand and mod. 

Line 12. The super() function returns a temporary, proxy superclass object. In this case, the temporary object is of type `Car` and therefore gives the `Model` class access to the `Car` methods. The init method is then called on the `Car` object. This initialises the attributes of `Car`. The value of the`brand` attribute is passed to the`Car` class and is assigned to the `car_name` attribute. Since we inherit attributes from the base class `Car`, we can then access the `car_name` attribute from the `Model` class

https://realpython.com/python-super/

https://appdividend.com/2019/01/22/python-super-function-example-super-method-tutorial/

Line 13. The value of the `mod` argument is assigned to the `model` attribute within the `Model` class. This is done using the first argument of the `init` method which is called `self` by convention.  

Line 16. Here we have the `show` method. Since the `Model` class inherits from the `Car` class, we can call the `Car`'s `present` method, even though we are in the `Model` class. We access the `present` method by calling it on the first argument `self`. The present method, as mentioned in the Line 7 explanation, concatenates 'I am a '  and the object's car name before returning it as one string. Furthermore, the string concatenates with '', it was made in " and the string version of the `model` attribute. After being concatenated, the new concatenated string is returned. Eg. if the car name was Ford and the model was 1980, the show method would return 'I have a Ford, it was made in 1980'.