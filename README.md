# PythonToKnow
On peut en chaine des comparaions
```python
>> 1 < 2 < 3
True
>> 1 < 3 < 2
False
```
L'affectation d'une liste est une copy de reference pas de valeur
```python
>> a = [1, 2, 3, 4]
>> b = a #copy de reference
>> b
[1, 2, 3, 4]
>> a
[1, 2, 3, 4]
>> b[0] = 9
>> b
[9, 2, 3, 4]
>> a #a prends la meme valeur
[9, 2, 3, 4]
```

Utiliser is pour la comparation avec ```None``` et == pour le reste
```python
>> a = None
>> b = [1, 3, 4]
>> a is None
True
>> b == [1, 3, 4]
True
```

La selection d'une liste peut s'effectuer de deux maniere et on peut preciser un pas de selection
```python
>> a = [1, 2, 3, 4, 6, 7]
>> a[0:4] # equivaut a a[:4]
[1, 2, 3, 4]
>> a[-4:-1] # de -4 a -1 (-1 exclut)
[3, 4, 6]
>> a[1:7:2] # par pas de 2: a[debut:fin-1:pas]
[2, 4, 7]
>> a[:] #selection de toute la liste (du debut a la fin)
[1, 2, 3, 4, 6, 7]
```

pour une copie de liste avec des references differente: faites
```python
>> a = [1, 2, 3, 4]
>> b = a[:] #copy de surface ou shallow copy
>> b
[1, 2, 3, 4]
>> a
[1, 2, 3, 4]
>> b[0] = 9
>> b
[9, 2, 3, 4]
>> a #a ne change pas
[1, 2, 3, 4]
>> a = [1, 2, [3, 4]] #pour une list de list
>> import copy
>> b = copy.deepcopy(a) #deep copy ou copy profonde
>> b
[1, 2, [3, 4]]
>> a
[1, 2, [3, 4]]
>> b[2][0] = 90
>> b
[1, 2, [90, 4]]
>> a #a ne change pas
[1, 2, [3, 4]]
```
Pour declarer un tuple d'un element
```python
>> a = (1,) #ou 1,
>> a
(1,)
>> type(a)
<class 'tuple'>
>> a = (1) # donner un int
>> type(a)
<class 'int'>
```

Unpacking tuple
```python
>> a, *b = 1, 2, 3
>> a
1
>> b
[2,3]
```

Les cles de disctionnaire doit etre immuable
```python
>> mydict = {[1,2,3]:'a', 'b': 1}
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unhashable type: 'list'
>> mydict = {(1,2,3):'a', 'b': 1} #ok immuable type: int - float - string - tuple
>> mydict
{(1, 2, 3): 'a', 'b': 1}
```

Avec in on peut verifier la presence d'une cle dans un dictionnaire
```python
>> mydict = {'a':1, 'b':2, 'c':3}
>> 'a' in mydict
True
>> mydict.get('z', False) #'z' not existing
False
```

On peut faire une insertion si une cle exist dans un dictionnaire
```python
>> mydict = {'a':1, 'b':2, 'c':3}
>> mydict.setdefault('z', 100)
100
>> mydict
{'a': 1, 'b': 2, 'c': 3, 'z': 100}
>> mydict.setdefault('a', 100) # si la cle existe pas d'insertion
1
>> mydict
{'a': 1, 'b': 2, 'c': 3}
>>
```
L'element d'un set doit etre immuable
```python
>> myset = {[1], 1}
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unhashable type: 'list'
>> myset = {(1,), 1} #ok
>> myset
{1, (1,)}
```

On peut ajouter un element dans un set avec `add`
```python
>> myset = {1,2,5}
>> myset.add(8)
>> myset
{1,2,5, 8}
```

lamda peut prends plusieurs paramettre
```python
>> (lambda x,y:x*2+y*2)(2,3)
10
```

une condition peut se tenir sur une ligne
```python
>> if True: print('yes')
...
'yes'
>> if False: print('yes')
>> else: print('no')
...
'no'
```

On peut enchener plusieurs instructions
```python
>> if True: print('yes 1'); print('yes 2')
...
'yes 1'
'yes 2'
```
NB : Mais il ne faut pas en abuser, plus de 3 utiliser la condition claissque

Ternaire en python
```python
>> raining = False
>> 'beach' if not raining else 'library'
'beach'
>> age = 12
>> s = 'minor' if age < 21 else 'adult'
>> s
'minor'
```

En python on a un for...else et while...else
```python
>> for i in range(10):
...   if i == 5: break
...   print(f'item .. {i}')
...else: #no-break
...   print('for no break...')
...
item.. 0
item.. 1
item.. 2
item.. 3
item.. 4
>> for i in range(10):
...   if i == 100: break
...   print(f'item .. {i}')
...else: #no-break
...   print('for no break...')
...
item.. 0
item.. 1
item.. 2
item.. 3
item.. 4
item.. 5
item.. 6
item.. 7
item.. 8
item.. 9
for no break...
```

A savoir, la reference d'une liste passer en paramettre est global
```python
>> def add_food(food, menu=[]):
...   menu.append(food)
...   return menu
...
>> add_food('spam')
['spam']
>> add_food('egg') #python utilise la meme reference
['spam', 'egg']
```
NB : consequence: les paramettres d'une fonction sont creer (une seul fois) lors de la declaration de la fonction pas lors du l'appel.


# Credit
Harouna Diallo

