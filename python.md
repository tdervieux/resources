
# Create a virtual environment

1. cd to $VIRTUAL_ENV_ROOT
2. virtualenv my_env_name #(otio)
3. source my_env_name/bin/activate.csh
4. pip install -U pip
5. pip install -U setuptools
6. cd ~/otio_dir
7. pip install -e .
8. pip install PySide2==5.11.0
9. pip install -e .\[dev] #linter, mock library 
10. rehash; which otioview #should be pointing at your dir```

11.to turn it off: `deactivate`

# Serialization and Deserialization of Python Objects
[Serialization and Deserialization of Python Objects](https://code.tutsplus.com/tutorials/serialization-and-deserialization-of-python-objects-part-1--cms-26183)

```python
from datetime import datetime

class A(object):
 
    def __init__(self, simple):
        self.simple = simple        
 
    def __eq__(self, other):
        if not hasattr(other, 'simple'):
            return False
        return self.simple == other.simple
 
    def __ne__(self, other):
        if not hasattr(other, 'simple'):
            return True
        return self.simple != other.simple
  
complex = dict(a=A(simple), when=datetime(2016, 3, 7))
```

## JSON encode with CustomEncoder

```python
from datetime import datetime
 
import json
 
class CustomEncoder(json.JSONEncoder): 
     def default(self, o):
         if isinstance(o, datetime):
             return {'__datetime__': o.replace(microsecond=0).isoformat()}
         return {'__{}__'.format(o.__class__.__name__): o.__dict__}
         
serialized = json.dumps(complex, indent=4, cls=CustomEncoder)
```

## JSON decode with a decode_object

```python
def decode_object(o):
 
    if '__A__' in o:
        a = A()
        a.__dict__.update(o['__A__']) 
        return a

    elif '__datetime__' in o:
        return datetime.strptime(o['__datetime__'], '%Y-%m-%dT%H:%M:%S')        
    return o

deserialized = json.loads(serialized, object_hook=decode_object)
```    


# List manipulation

## functools.reduce
```python
l = [ [1,2,3,10],[4,5,6,10],[7,8,9,10]]
functools.reduce(lambda a,b : set(a).intersection(set(b)),l)
([10])
```
## flatten a list with itertools.chain
```python
l = [ [1,2,3,10],[4,5,6,10],[7,8,9,10]]
list(itertools.chain(*l))
[1, 2, 3, 10, 4, 5, 6, 10, 7, 8, 9, 10]
```

## collections.Counter to counter occurences
```python
>>> str = "this is just a test of grouping letters"
>>> collections.Counter(str)
Counter({' ': 7, 't': 6, 's': 5, 'e': 3, 'i': 3, 'g': 2, 'o': 2, 'r': 2, 'u': 2, 'a': 1, 'f': 1, 'h': 1, 'j': 1, 'l': 1, 'n': 1, 'p': 1})
```

## itertools.groupby group element by value
```python
>>> str = "this is just a test of grouping letters"
>>> collections.Counter(str)
Counter({' ': 7, 't': 6, 's': 5, 'e': 3, 'i': 3, 'g': 2, 'o': 2, 'r': 2, 'u': 2, 'a': 1, 'f': 1, 'h': 1, 'j': 1, 'l': 1, 'n': 1, 'p': 1})

occTags = collections.Counter(str)
>>> tagGrouped = [list(g[1]) for g in itertools.groupby( occTags.most_common(), key=lambda x:x[1])]
>>> tagGrouped
[[(' ', 7)], [('t', 6)], [('s', 5)], [('e', 3), ('i', 3)], [('g', 2), ('o', 2), ('r', 2), ('u', 2)], [('a', 1), ('f', 1), ('h', 1), ('j', 1), ('l', 1), ('n', 1), ('p', 1)]]
```


