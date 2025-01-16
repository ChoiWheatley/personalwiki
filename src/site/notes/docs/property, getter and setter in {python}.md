---
{"dg-publish":true,"permalink":"/docs/property, getter and setter in {python}/","title":"property, getter and setter in {python}"}
---

<https://realpython.com/python-property/>


```python
# circle.py
class Circle:
    def __init__(self, radius):
        self._radius = radius

    @property
    def radius(self):
        """The radius property."""
        print("Get radius")
        return self._radius

    @radius.setter
    def radius(self, value):
        print("Set radius")
        self._radius = value

    @radius.deleter
    def radius(self):
        print("Delete radius")
        del self._radius
```
