# 1. Define the id of next variables:
int_a = 55
print(id(int_a))
# 11169376
str_b = 'cursor'
print(id(str_b))
# 140463443209840
set_c = {1, 2, 3}
print(id(set_c))
# 139857085883648
lst_d = [1, 2, 3,]
print(id(lst_d))
# 139857085883648
dict_e = {'a': 1, 'b': 2, 'c': 3}
print(id(dict_e))
# 140463443697904

# 2. Append 4 and 5 to the lst_d and define the id one more time.
lst_d = [1, 2, 3, 4, 5]
print(id(lst_d))
# 139857086766208

# 3. Define the type of each object from step 1.
print(type(int_a))
# <class 'int'>
print(type(str_b))
# <class 'str'>
print(type(set_c))
# <class 'set'>
print(type(lst_d))
# <class 'list'>
print(type(dict_e))
# <class 'dict'>

# 4*. Check the type of the objects by using isinstance.
print(isinstance(int_a, int))
# True
print(isinstance(str_b, str))
# True
print(isinstance(set_c, set))
# True
print(isinstance(lst_d, list))
# True
print(isinstance(dict_e, dict))
# True

# String formatting:
# Replace the placeholders with a value:
# 5. With .format and curly braces {}
print("Anna has {} apples and {} peaches".format(5, 5))
# Anna has 5 apples and 5 peaches
# 6. By passing index numbers into the curly braces.
print("Anna has {0} apples and {1} peaches".format(5, 6))
# Anna has 5 apples and 6 peaches
# 7. By using keyword arguments into the curly braces.
print("Anna has {apples} apples and {peaches} peaches".format(apples=5, peaches=6))
# Anna has 5 apples and 6 peaches
# 8*. With indicators of field size (5 chars for the first and 3 for the second)


# 9. With f-strings and variables
fruit1 = 5
fruit2 = 3
fruit_info = f"Anna has {fruit1} apples and {fruit2} peaches"
print(fruit_info)
# Anna has 5 apples and 3 peaches

# 10. With % operator
y = ("5", "3")
x = "Anna has %s apples and %s peaches"
print(x % y)
# Anna has 5 apples and 3 peaches

# 11*. With variable substitutions by name (hint: by using dict)
class Fruit(object):
    def __init__(self, x, y):
        self.x = 5
        self.y = 3

    def __str__(self):
        return 'Anna has {x} apples and {y} peaches'.format(**self.__dict__)
fruit = Fruit('5', '3')
print(fruit)
# Anna has 5 apples and 3 peaches

# Comprehensions:
# (1)
lst = []
for num in range(10):
    if num % 2 == 1:
        lst.append(num ** 2)
    else:
        lst.append(num ** 4)
print(lst)
#[0, 1, 16, 9, 256, 25, 1296, 49, 4096, 81]
# 12. Convert (1) to list comprehension
lst_comp = [num **2 if num % 2 == 1 else num ** 4 for num in range(10)]
print(lst_comp)
#[0, 1, 16, 9, 256, 25, 1296, 49, 4096, 81]
# (2)
list_comprehension = [num // 2 if num % 2 == 0 else num * 10 for num in range(10)]
print(list_comprehension)
# [0, 1, 16, 9, 256, 25, 1296, 49, 4096, 81]
# 13. Convert (2) to regular for with if-else
list = []
for num in range(10):
    if num % 2 == 0:
        list.append(num // 2)
    else:
        list.append(num * 10)
print(list)
# [0, 10, 1, 30, 2, 50, 3, 70, 4, 90]

# (3)
d = {}
for num in range(1, 11):
    if num % 2 == 1:
        d[num] = num ** 2
print(d)
# {1: 1, 3: 9, 5: 25, 7: 49, 9: 81}
# 14. Convert (3) to dict comprehension.
d_comp = {num: num **2 for num in range(1, 11) if num % 2 == 1}
print(d_comp)
# {1: 1, 3: 9, 5: 25, 7: 49, 9: 81}

# (4)
d = {}
for num in range(1, 11):
    if num % 2 == 1:
        d[num] = num ** 2
    else:
        d[num] = num // 0.5
print(d)
# {1: 1, 2: 4.0, 3: 9, 4: 8.0, 5: 25, 6: 12.0, 7: 49, 8: 16.0, 9: 81, 10: 20.0}
# 15*. Convert (4) to dict comprehension.
d_comp_1 = {num: num **2 if num % 2 ==1 else num // 0.5 for num in range(1, 11)}
print(d_comp_1)
# {1: 1, 2: 4.0, 3: 9, 4: 8.0, 5: 25, 6: 12.0, 7: 49, 8: 16.0, 9: 81, 10: 20.0}

# (5)
dict_comprehension = {x: x**3 for x in range(10) if x**3 % 4 == 0}
print(dict_comprehension)
# {0: 0, 2: 8, 4: 64, 6: 216, 8: 512}
# 16. Convert (5) to regular for with if.
d = {}
for x in range(10):
    if x**3 % 4 == 0:
        d[x] = x ** 3
print(d)
# {0: 0, 2: 8, 4: 64, 6: 216, 8: 512}

# (6)
dict_comprehension = {x: x**3 if x**3 % 4 == 0 else x for x in range(10)}
print(dict_comprehension)
# {0: 0, 1: 1, 2: 8, 3: 3, 4: 64, 5: 5, 6: 216, 7: 7, 8: 512, 9: 9}
# 17*. Convert (6) to regular for with if-else.
d = {}
for x in range(10):
    if x**3 % 4 == 0:
        d[x] = x ** 3
    else:
        d[x] = x
print(d)
# {0: 0, 1: 1, 2: 8, 3: 3, 4: 64, 5: 5, 6: 216, 7: 7, 8: 512, 9: 9}

# Lambda:

# (7)
def foo(x, y):
    if x < y:
        return x
    else:
        return y
print(foo(1, 3))
# 1
# 18. Convert (7) to lambda function
foo_1 = lambda x, y: x if x < y else y
print(foo_1(1, 3))
# 1

# (8)
foo = lambda x, y, z: z if y < x and x > z else y
print(foo(1, 2, 3))
# 2
# 19*. Convert (8) to regular function
def foo_1(x, y, z):
    if y < x and x > z:
        return z
    else:
        return y
print(foo_1(1, 2, 3))
# 2

lst_to_sort = [5, 18, 1, 24, 33, 15, 13, 55]

# 20. Sort lst_to_sort from min to max
print(sorted(lst_to_sort))
# [1, 5, 13, 15, 18, 24, 33, 55]

# 21. Sort lst_to_sort from max to min
print(sorted(lst_to_sort, reverse=True))
# [55, 33, 24, 18, 15, 13, 5, 1]

# 22. Use map and lambda to update the lst_to_sort by multiply each element by 2
lst_to_sort_1 = list(map(lambda x: x*2, lst_to_sort))
print(lst_to_sort_1)
# [10, 36, 2, 48, 66, 30, 26, 110]

# 23*. Raise each list number to the corresponding number on another list:
list_A = [2, 3, 4]
list_B = [5, 6, 7]
lst = list(map(lambda x, y: x ** y, list_A ,list_B))
print(lst)
# [32, 729, 16384]

# 24. Use reduce and lambda to compute the numbers of a lst_to_sort.
from functools import reduce
sum = reduce(lambda a, b: a + b, lst_to_sort)
print(sum)
# 164

# 25. Use filter and lambda to filter the number of a lst_to_sort with elem % 2 == 1.
list_1 = list(filter(lambda x: (x % 2 == 1), lst_to_sort))

print(list_1)
# [5, 1, 33, 15, 13, 55]

# 26. Considering the range of values: b = range(-10, 10), use the function filter to return only negative numbers.
lst_comp1 = [x for x in range(-10, 10) if x < 0]
print(lst_comp1)


# 27*. Using the filter function, find the values that are common to the two lists:
list_1 = [1, 2, 3, 5, 7, 9]
list_2 = [2, 3, 5, 6, 7, 8]

lst = list(filter(lambda x: x in list_1,list_2))
print(lst)

