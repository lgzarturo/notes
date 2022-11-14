# python-tips

Remplazar datos None con cadenas vacías en un diccionario de python.

```python
import json

employee = {
    'name': None,
    'address': {'country': None, 'city': 'Hamburg'},
    'age': 30,
}

def none_to_empty_str(items):
    return {k: v if v is not None else '' for k, v in items}


json_str = json.dumps(employee)

employee = json.loads(json_str, object_pairs_hook=none_to_empty_str)

# 👇️ {'name': '', 'address': {'country': '', 'city': 'Hamburg'}, 'age': 30}
print(employee)
```
