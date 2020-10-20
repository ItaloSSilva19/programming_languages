# Tavern vs Schemathesis
### Python testing comparison

**Tavern** testing is designed to be as simple as possible, only **write the tests on a YAML file** and they will take care of the rest, but **Schemathesis generate the test automatically** based on the OpenAPI (former Swagger). Two options that look like be stuning tools. Write simple or auto generate, which of then is the best testing tool for Python test?  
Let's see more about each. 

## Tavern

It's designed for **Integrations Test**, wich means that it make a *request* to the API and *compare* the results with some expected behaviour.

As it self says on it [GitHub](https://github.com/taverntesting/tavern) description: "Tavern is a command-line tool, Python library and Pytest plugin for automated testing of **RESTful APIs**, with a simple, concise and flexible **YAML-based syntax**."

**For more informartions**:
[https://taverntesting.github.io](https://taverntesting.github.io)
[https://github.com/taverntesting/tavern](https://github.com/taverntesting/tavern)

##### Community
It GitHub repo today (Oct 20, 2020) has near 700 stars, 135 forks, 40 issues, 34 contributors and used by near 200 other peoples, with the last update 11 days ago. Look like it have some community, is not soo big and active, but still active and used. Currenctly is maintanined by @michaelboulton.

##### How to install:
To install, make sure Python is installed and pip upgraded, and then  run this command on terminal: 
>  pip install tavern[pytest]

The test, as said before, is writen on an YAML file and is recommended that all test file start with "***test_***".

##### Lets see an example from [Tavern site](https://taverntesting.github.io):
File named **test_minimal.tavern.yaml**:

    test_name: Get some fake data from the JSON placeholder API

    stages:
    - name: Make sure we have the right ID
        request:
          url: https://jsonplaceholder.typicode.com/posts/1
          method: GET
        response:
          status_code: 200
          json:
            id: 1





**This can then be run like so in the terminal:**

    $ py.test test_minimal.tavern.yaml  -v
    =================================== test session starts ===================================
    platform linux -- Python 3.5.2, pytest-3.4.2, py-1.5.2, pluggy-0.6.0 -- /home/taverntester/.virtualenvs/tavernexample/bin/python3
    cachedir: .pytest_cache
    rootdir: /home/taverntester/myproject, inifile:
    plugins: tavern-0.7.2
    collected 1 item

    test_minimal.tavern.yaml::Get some fake data from the JSON placeholder API PASSED   [100%]

    ================================ 1 passed in 0.14 seconds =================================
    
#### Problems with Tavern

Tavern idea for testing is amazing, even not being the unique to do tests this kind. But by making test write simple, it have some limitation. 
When writing this article the example from it site look outdated, not working, and try to fix it was a hard work as a sum of problems going to YAML and JSON formating and Tavern assert, being hard to update the string to have line breaks like from the Fake Placeholder API. 
Also, adding complex json is hard, but some what possible.

It had a documentation and inside some tricks to make things work, witch means that to more complex work, must learn in deep how to use Tavern.

Maybe all that problems can being fixed, and also maybe there some option to enable more advanced testing.

#### When use Tavern

If you have every simple API and want to **write** *Integration Tests* faster, maybe it will be very useful, but if you have more advanced API it is not soo recommended, something is possible but must read a lot the documentation to understand better how to use it.

## Schemathesis

