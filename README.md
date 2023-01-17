# CI Workshop Repository 

Respository used during the Byte-Sized RSE workshop on Continuous Integration (CI). 

## Useful links:
* https://github.com/UNIVERSE-HPC/ci-example - example GitHub repository we'll use for the activity
* [Our first workflow](https://gist.github.com/steve-crouch/eef5f0e14513e86871d09312c1c1760c) - the first workflow we will write, as a reference
* [Our workflow containing a matrix](https://gist.github.com/steve-crouch/0170f3bba058610fba4bbabb67975cff) - the second workflow, containing a build matrix that will run our unit tests over multiple operating system and Python languages

## Additional Resources
* [Automating Unit Testing with Continuous Integration](https://software.ac.uk/blog/2022-05-23-automating-unit-testing-continuous-integration) - a tutorial that demonstrates how to use GitHub Actions to automated some unit tests written using Pytest, as well as how to scale your platform testing using build matrices
* [GitHub's introduction to YAML](https://learnxinyminutes.com/docs/yaml/) - a comprehensive introduction to YAML for the purposes of using it to define GitHub Actions workflows
* [GitHub Actions documentation](https://docs.github.com/en/actions)
* [GitHub Actions Marketplace](https://github.com/marketplace?type=actions) - a directory which contains many "actions" you can use in your workflows, including many third-party ones

## Notes
* GitHub Actions workflows need to be located within a particular directory in the repository: .github/workflows/

### 1. Create a virtual environment in your ci-example directory:

python -m venv env  (create a virtual environment within your ci-example directory)
source ./env/bin/activate   (activate the virtual environment - you should see the prompt change to show (env) at the start…
Once you’ve activated the environment, Steve showed that you can check that it’s an empty environment with hardly any packages installed using the “pip list” command.
Then we installed “pytest” to be able to run the tests:
pip install pytest
After running pip install pytest, if it completes successfully, the command pytest will be be available and you can then run the tests…
python -m pytest -v tests/test_factorial.py

### 2. Set up the Workflow
Within GitHub, we’re now creating a new file to setup our CI workflow  (we also checked in Settings -> Actions -> General that “Allow all actions and reusable workflows” is enabled)

We create a file called main.yml in ci-example/.github/workflows    (in the front page of the ci-example github repository, click “Add file” and the “Create new file”. For the file name, type .github/workflows/main.yml

### 3. File content:

```
name: run-unit-tests

on: push

jobs:

    build:

        runs-on: ubuntu-latest

        steps:
        
        -name: Checkout repository
         uses: actions/checkout@v3

        -name: Set up python 3.10
         uses: actions/setup-python@v4
         with:
             python-version: “3.10”

        -name: Install Python dependencies
         run: |
             python3 -m pip install –upgrade pip
             pip3 install -r requirements.txt

        -name: Test with pytest
         run: |
             python3 -m pytest -v tests/test_factorial.py
```


Now we commit this file into our repository:
At the bottom of the page, add a description - e.g.  “workflow configuration for CI” then with commit directly to main branch selected, you can commit the file.

If the contents of your file is correct, GitHub will detect the file and should run the CI pipeline straight away
