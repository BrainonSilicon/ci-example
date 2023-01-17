# CI Example Repository 

Respository used during the Byte-Sized RSE workshop on Continuous Integration (CI). 


### Useful links:
* https://github.com/UNIVERSE-HPC/ci-example - example GitHub repository we'll use for the activity
* [Our first workflow](https://gist.github.com/steve-crouch/eef5f0e14513e86871d09312c1c1760c) - the first workflow we will write, as a reference
* [Our workflow containing a matrix](https://gist.github.com/steve-crouch/0170f3bba058610fba4bbabb67975cff) - the second workflow, containing a build matrix that will run our unit tests over multiple operating system and Python languages


### Notes
* GitHub Actions workflows need to be located within a particular directory in the repository: .github/workflows/

### Additional Resources
* [Automating Unit Testing with Continuous Integration](https://software.ac.uk/blog/2022-05-23-automating-unit-testing-continuous-integration) - a tutorial that demonstrates how to use GitHub Actions to automated some unit tests written using Pytest, as well as how to scale your platform testing using build matrices
* [GitHub's introduction to YAML](https://learnxinyminutes.com/docs/yaml/) - a comprehensive introduction to YAML for the purposes of using it to define GitHub Actions workflows
* [GitHub Actions documentation](https://docs.github.com/en/actions)
* [GitHub Actions Marketplace](https://github.com/marketplace?type=actions) - a directory which contains many "actions" you can use in your workflows, including many third-party ones
