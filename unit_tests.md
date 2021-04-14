This notebook was prepared by [Donne Martin](http://donnemartin.com). Source and license info is on [GitHub](https://github.com/donnemartin/data-science-ipython-notebooks).

# Nose Unit Tests with IPython Notebook

## Nose

Testing is a vital part of software development.  Nose extends unittest to make testing easier.

## Install Nose

Run the following command line:


```python
!pip install nose
```

## Create the Code

Save your code to a file with the %%file magic:


```python
%%file type_util.py
class TypeUtil:

    @classmethod
    def is_iterable(cls, obj):
        """Determines if obj is iterable.

        Useful when writing functions that can accept multiple types of
        input (list, tuple, ndarray, iterator).  Pairs well with
        convert_to_list.
        """
        try:
            iter(obj)
            return True
        except TypeError:
            return False

    @classmethod
    def convert_to_list(cls, obj):
        """Converts obj to a list if it is not a list and it is iterable, 
        else returns the original obj.
        """
        if not isinstance(obj, list) and cls.is_iterable(obj):
            obj = list(obj)
        return obj

```

    Overwriting type_util.py
    

## Create the Nose Tests

Save your test to a file with the %%file magic:


```python
%%file tests/test_type_util.py
from nose.tools import assert_equal
from ..type_util import TypeUtil


class TestUtil():

    def test_is_iterable(self):
        assert_equal(TypeUtil.is_iterable('foo'), True)
        assert_equal(TypeUtil.is_iterable(7), False)

    def test_convert_to_list(self):
        assert_equal(isinstance(TypeUtil.convert_to_list('foo'), list), True)
        assert_equal(isinstance(TypeUtil.convert_to_list(7), list), False)
```

    Overwriting tests/test_type_util.py
    

## Run the Nose Tests

Run the following command line:


```python
!nosetests tests/test_type_util.py -v
```

    core.tests.test_type_util.TestUtil.test_convert_to_list ... ok
    core.tests.test_type_util.TestUtil.test_is_iterable ... ok
    
    ----------------------------------------------------------------------
    Ran 2 tests in 0.001s
    
    OK

