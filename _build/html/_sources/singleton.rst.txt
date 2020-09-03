Singleton
---------

.. code:: python

    """
    >>> singleton_1 = Singleton()
    >>> singleton_1.attr = 10
    >>> singleton_2 = Singleton()
    >>> singleton_2 is singleton_1
    True
    singleton_2.attr = 10
    """
    
    
    class SingletonPlain:
        _instance = None
        
        def __new__(cls, *args, **kwargs):
            if cls._instance is None:
                cls._instance = super().__new__(cls, *args, **kwargs)
            return cls
        
        def __init__(self, *args, **kwargs):
            self.__dict__ = self._instance.__dict__
    
    
    class SingletonMetaclass(type):
        _instance = None
        
        def __call__(cls, *args, **kwargs):
            if cls._instance is None:
                cls._instance = super().__call__(*args, **kwargs)
            return cls._instance
    
    
    class SingletonViaMetaclass(metaclass=SingletonMetaclass):  
        def __init__(self):
            pass
