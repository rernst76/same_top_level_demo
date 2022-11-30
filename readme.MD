This call to pytest is successful:
pytest test_func1_top_level.py
Fails:
C:\Users\bsnahrwold79\python\same_top_level>pytest test_func1_top_level.py
===================================== test session starts ======================================
platform win32 -- Python 3.9.15, pytest-7.1.2, pluggy-1.0.0
rootdir: C:\Users\bsnahrwold79\python\same_top_level
plugins: anyio-3.5.0
collected 1 item

test_func1_top_level.py .                                                                 [100%] 

====================================== 1 passed in 0.02s ======================================= 

Calling the test in the test directory fails
I get the same error whether I use 
the windows style   \tests
or the Linux style: /tests

C:\Users\bsnahrwold79\python\same_top_level>pytest \tests\test_func1_in_tests.py  
===================================== test session starts ======================================
platform win32 -- Python 3.9.15, pytest-7.1.2, pluggy-1.0.0
rootdir: C:\Users\bsnahrwold79\python\same_top_level
plugins: anyio-3.5.0
collected 0 items

==================================== no tests ran in 0.01s ===================================== 
ERROR: file or directory not found: \tests\test_func1_in_tests.py


QUESTION:
How do I construct a pytest project using the  standard directory structure:
/src
/tests