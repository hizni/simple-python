# simple-python

This aim of this simple Python example, is to implement Python code that includes simple unit tests. And then roll in CI support using Travis.

### Basic unit test support

#### Unit test module used
The unit testing module that is made use of is called: *unittest* (it is sometimes called *pyunit*).

[Example implementation can be found here](https://cgoldberg.github.io/python-unittest-tutorial/), but in essence:

Tests, as defined by unittest, have two parts: 
* code to manage test "fixtures", and 
* the test itself. 

#### Implementation

Individual tests are created by subclassing TestCase and overriding or adding appropriate methods. 

For example,

```python
import unittest

class SimplisticTest(unittest.TestCase):

    def test(self):
        self.assertTrue(True)
```
In this case, the SimplisticTest has a single test() method, which would fail if True is ever False.

The simplest way to allow the unit tests is to be run is to include the following code at the bottom of the script file:

```python
if __name__ == '__main__':
    unittest.main()
```
#### Executing test
To run the tests, the Python script can be run from the command line, as so:

```commandline
python test_simple.py
```

### Possible outcomes

Test Outcomes
Tests have 3 possible outcomes:
* OK    -  The test passes.
* FAIL  -  The test does not pass, and raises an AssertionError exception.
* ERROR -  The test raises an exception other than AssertionError.


### Continuous Integration support

#### Background
As the above code is worked on by developers and checked into the Git repo, we can ensure that the builds all pass successfully
automatically using the Travis CI framework.

Travis monitors the selected repo and makes use of the settings in the *.travis.yml* file to understand how to execute the 
tests once code is pushed to the repo.
 
The build process would be as follows:
* a developer adds the features that script files they are working on to their branch of the project. 
* They would then write their unit tests and use them to ensure their implementation works successfully.
* Commit the code
* the developer would add the name of their script files to the *.travis.yml* file in the *script* section.
* Commit the modification
* Push to remote repo. Doing this will automatically cause the build to run all the tests named in the *.travis.yml* file
* The build will pass or fail.

#### .travis.yml file

The *.travis.yml* file will look as follows:

```commandline
language: python

python:
  - "2.7"

script:
  - python test_simple.py
  - python test_notequal.py
```




 
