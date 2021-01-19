# Term 4 Workbook - T4A1 Developer Workbook



## Question 13



```python
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

<b>Lines 1 - 8</b>

```python
import random

class Car:
    def __init__(self, brand):
        self.car_name = brand
        
	def present(self):
    	return 'I have a ' + self.car_name
```


**Line 1** - The import statement tells Python to search for the module named ```random```. The `random` module uses pseudo-random number generators for its various distributions. The module is found by the interpreter and a module object  called `random` is initialised. This module contains the function `randint` which will be used later in the code snippet for randomly selecting a make and model of a car.

**References**

https://docs.python.org/3/tutorial/modules.html



**Line 3** - This line creates a new class called `Car`. This is a blueprint for a new type of object and it enables objects of that type to be created.  No instances of `Car` can be initialised before defining the `Car` class so it is unsurprising that it is at the top of the file. Furthermore, classes usually have attributes and methods to give it functionality. The lines to follow give the `Car` class its functionality.

**References**

https://docs.python.org/3/tutorial/classes.html

https://realpython.com/python-main-function/



**Lines 4 and 5** - The `Car` class has the reserved`__init__` method. The `__init__` method is known as a constructor and when a new instance of the `Car` class is created, the `__init__` method is called so that the statements within the `__init__` method are executed. The `__init__` method is used to initialise the attributes of an object. In this case, the value of one instance variable is set in the `__init__` method. The instance variable is`car_name`and its value is set for just that particular instance by using `self`. 

The first parameter of a method is named `self` by convention. `self` is used to represent that particular instance of the class. Therefore by using `self.car_name`, the instance variable `car_name` is set for just that particular instance. The new car object has it's `car_name` attribute set equal to the value of the `brand` argument.

**References**

https://www.tutorialspoint.com/What-is-difference-between-self-and-init-methods-in-python-Class

https://www.geeksforgeeks.org/self-in-python-class/

https://www.journaldev.com/18397/python-class-init

https://micropyramid.com/blog/understand-self-and-__init__-method-in-python-class/

https://www.edureka.co/blog/self-in-python/



**Lines 7 and 8** - These lines define a method called `present`. The method is available to all instances of the `Car` class and classes derived from it. When called on a particular `Car` object, it concatenates 'I am a '  and the object's car name. It can get access to the object's `car_name` attribute by using the first argument of the method which is named `self`. After the strings 'I am a ' and `self.car_name` are concatenated, the resulting string is returned. In our case, if the car name was 'Holden', it would concatenate the two strings 'I am a ' and 'Holden', before returning the one string 'I am a Holden'. 

**References**

https://docs.python.org/3/tutorial/classes.html

https://www.geeksforgeeks.org/python-string-concatenation/



<b>Lines 10 - 16</b>

```python
class Model(Car):
    def __init__(self, brand, mod):
        super().__init__(brand)
        self.model = mod

    def show(self):
        return self.present() + ', it was made in ' + str(self.model)
```



**Line 10** - The lines define another class called `Model`. The `model` class is defined to inherit from the base class called `Car` which has previously been defined. Inheritance in Python means that attributes and methods in the base class are inherited into the derived class. In this example, the base class is `Car` and the derived class is `Model`, therefore the `Car`'s attributes and methods are available to be accessed by the `Model` class. Specially, the `Car`'s attribute `car_name` and method `present` are accessible to the `Model` class.



**Line 11** - The line has the method that initialises the `Model` object. The first parameter is `self` and refers to the particular instance of the model class that is being instantiated. There are two other parameters named brand and mod. 

**Line 12** - The super() function returns a temporary, proxy superclass object. In this case, the temporary object is of type `Car` and therefore gives the `Model` class access to the `Car` methods. The init method is then called on the `Car` object. This initialises the attributes of `Car`. The value of the `brand` attribute is passed to the`Car` class and is assigned to the `car_name` attribute. Since we inherit attributes from the base class `Car`, we can then access the `car_name` attribute from the `Model` class

**References**

https://realpython.com/python-super/

https://appdividend.com/2019/01/22/python-super-function-example-super-method-tutorial/



**Line 13** - The value of the `mod` argument is assigned to the `model` attribute within the `Model` class. This is done using the first argument of the `init` method which is called `self` by convention.  The first argument `self` represents an instance of the `Model` class. It allows us to assign the value of `mod` to the `model` attribute of this particular instance.

**Lines 15 and 16** - Here we have the `show` method. Since the `Model` class inherits from the `Car` class, we can call the `Car`'s `present` method, even though we are in the `Model` class. We access the `present` method by calling it on the first argument `self`. The present method, as mentioned in the Line 7 explanation, concatenates 'I am a '  and the object's car name before returning it as one string. Furthermore, the string concatenates with '', it was made in " and the string version of the `model` attribute. After being concatenated, the new concatenated string is returned. Eg. if the car name was Ford and the model was 1980, the show method would return 'I have a Ford, it was made in 1980'.



<b>Lines 18 - 24</b>

```python
makes = ["Ford", "Holden", "Toyota"]
models = []
for i in range(40):
    models.append(i+1980)

def random_int_from_interval(min,max):
    return random.randint(min, max)
```



**Line 18** - The `makes` variable is assigned a list of strings. It holds 3 strings that can be indexed by 0, 1 and 2 respectively. Each string represents a different kind of make and will be randomly chosen later in the code snippet.

**Line 19** - An empty list is assigned to the `models` variable. In the next two lines, the list will be populated with the integers 1980, 1981, 1982, ..., 2019.

**Line 20 and 21** - The `range` object can accept a start, stop and step value. However, in this case, only the stop value of 40 is provided, therefore, the start value defaults to 0 and the step value defaults to 1 because they were not specified. The `range()`object returns an iterator of integers which will be used to generate the integers from the start value, up to but not including the stop value. The start value is 0, the stop value is 40, and the step value is 1 so each integer from 0 to 39 will be generated one at a time. 

The `for loop` iterates through each integer generated by the iterator and assigns it to the `i` variable. Each time `i` is assigned a new integer, the statement within the `for loop` is executed. The sum of `i` and 1980 is appended to the end of the models list. Once again, the value of `i` is incremented and the sum of `i` and 1980 is appended to the end of the models list. This process repeats until the value of `i` reaches 39, then for the last time, the sum of `i` and 1980 is appended to the end of the models list.

**Line 23 and 24** - The `random_int_from_interval` function takes two arguments, the min and max. Both arguments must be numbers. The function will return a random integer between those two numbers, inclusive. 

In our case `random_int_from_interval(0,2)` will return either a 0, 1 or 2. The probability of returning each integer is the same. There are 3 different integers, therefore each integer has a 1/3 or 33.3% chance of being returned. 

Likewise, `random_int_from_interval(0,39)` will return either a 0, 1, 2, 3, ..., or 39. In this case, each integer has a 1/40 or 2.5% chance of being returned.

**References**

https://docs.python.org/3/reference/compound_stmts.html

https://www.geeksforgeeks.org/python-range-does-not-return-an-iterator/

https://docs.python.org/3/library/random.html



<b>Lines 26 - 30</b>

```python
for model in models:
    make = makes[random_int_from_interval(0, len(makes)-1)]
    model = models[random_int_from_interval(0, len(models)-1)]
    my_car = Model(make, model)
    print(my_car.show())
```



**Line 26** - The `for loop` iterates through each item in the `models` list and assigns the value to the `model` variable. The `models` list is populated with integers from 1980 to 2019. Therefore, the `mode`l variable will be assigned the value of 1980 during the first iteration of the loop, 1981 for the second iteration of the loop, and so on until it is assigned the value of 2019 for the final iteration of the loop.

**Line 27** - The `len(makes)` function returns the number of items in the `makes` list. There are 3 items so it returns 3. Therefore the `make` variable is going to be randomly assigned one of the strings in the `makes` list. It will be assigned to either "Ford", "Holden" or "Toyota". 

**Line 28** - The `len(model)` function returns the number of items in the `models` list. There are 40 items so it returns 40. Therefore the `models` variable is going to be randomly assigned one of the integers in the `models` list. It will be assigned to one of the integers between 0 and 39 inclusive.

**Line 29** - The `Model` class takes two arguments in order to instantiate an object. Those two arguments are `make` and `model`. Once the `model` object is instantiated, it's reference is assigned to the `my_car` variable. 

**Line 30** - The `show()` method is called upon the `my_car` object. The functionality of the show method is covered in the explanation of lines 16 and 17. Essentially, Those two arguments are `make` and `model`. Once the `model` object is instantiated, it's reference is assigned to the `my_car` variable.





## Question 12



**JSON** stands for **JavaScript Object Notation** and represents data in an unordered collection of key-value pairs, similar to a dictionary in python.

JSON can be **manipulated** by converting a JSON string into a python object  It can be done in a python file by using the `loads` method from the `json` module. 



### json.loads()  method

Here is an example of a **JSON string** being converted into a **python object** using the `json.loads()` method

```python
import json

sporting_interests = '{"name": "Michael", "sports": ["AFL", "Soccer"]}' # JSON string
sporting_interests_dict = json.loads(person) # Convert to python object

# Output: {"name": "Michael", 'sports": ["AFL", "Soccer"]} # Python object
print(sporting_interests_dict) 

# The python object is a dictionary 
# Output: ["AFL", "Soccer"]
print(sporting_interests_dict["sports"])
```



We can change the contents of the python object and then convert the **python object** back into a **JSON string**.

 It can be done in a python file by using the `dumps` method from the `json` module. 



### json.dumps()  method

Here is an example of a **python object** being changed and then converted into a **JSON string** using the `json.dumps()` method

```python
# continued from the previous python code

# change the contents of the python object
sporting_interests_dict["sports"] = ["Badminton", "Basketball"]

# Output: {"name": "Michael", 'sports": ["Badminton", "Basketball"]} # Python object
print(sporting_interests_dict) 

sporting_interests = json.dumps(sporting_interests_dict) # Convert to JSON string

# Output: {"name": "Michael", 'sports": ["Badminton", "Basketball"]} # JSON string
print(sporting_interests)

```



Let's convert it back again to a **python object**

```python
# continued from the previous python code

# change the JSON string to python object
sporting_interests = json.loads(sporting_interests_dict)

```



We can write the new sporting interests to a file as **JSON**. 

### json.dump()  method

Below the `json.dump()` convert the python object to a **JSON** **string** and then writes it to a file called `new_file.txt`

```python
# continued from the previous python code

with open('new_file.txt', 'w') as json_file:
  json.dump(sporting_interests, json_file)

```



The JSON string is now located in the file called `new_file.txt`. We can exit our python program and the JSON string will still be left in the `new_file.txt` file. 

Our file contains a **JSON string** and looks like this

```json
{"name": "Michael", 
"languages": ["Badminton", "Basketball"]
}
```



We can create a new program and run it to retrieve our **JSON string** from the file.



We can read it in to our python file by using the `json.load()` method.

Here is an example of reading the **JSON string** from the file

### json.load()  method

Here is an example of reading the **JSON string** from the file using the `json.load()` method.

```python
import json

with open('path_to_file/new_file.txt') as f:
  data = json.load(f)

# Output: {'name': 'Michael', 'sports': ['Badminton', 'Basketball']}
print(data)
```





### Serialising python objects into a json format



Above the **load, loads, dump and dumps** methods were used to convert from **JSON string** to **Python** and **Python** to **JSON string**. They all dealt with primitive Python types that have a direct JSON equivalent. Sadly, the JSON encoder is limited in that it can only serialize those basic data types such as lists, strings and numbers. 

A Python Class cannot be so simply encoded into JSON string. Likewise a JSON string cannot be so easily decoded into a python object. 



**References**

https://realpython.com/python-json/

https://pynative.com/python-json/

https://www.programiz.com/python-programming/json