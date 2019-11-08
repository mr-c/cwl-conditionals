# CWL conditionals test bed

## Useful links

1. [Design decision document](https://github.com/common-workflow-language/common-workflow-language/blob/kaushik-work-patch-1/design-decisions/conditionals-2019.md)
1. [Proposal](https://github.com/common-workflow-language/common-workflow-language/issues/854)
1. [Collected list of use cases](https://github.com/common-workflow-language/common-workflow-language/issues/725)
1. [List of proposals for conditionals](https://github.com/common-workflow-language/common-workflow-language/issues?utf8=%E2%9C%93&q=label%3Aconditionals+)


## Steps for getting up an running

Also see [setup.sh](setup.sh)

- Create a new virtual environment for testing
- Install Toil from `kaushik-work/toil`  `kaushik/conditionals/when` branch
- Install CWL tool `pa/conditionals` branch
- Checkout the test scripts and test files
- Run them with `toil-cwl-runner` 


Due to the vagaries of python's setup infrastructure, you have to do the following state dependent steps

```
git clone https://github.com/kaushik-work/toil.git
cd toil
git checkout kaushik/conditionals/when
pip install -e .[cwl]
cd ..

toil-cwl-runner --version  # should read 3.21.0a1

# cwltool has to be installed from a clone. Not clear to me why
# has something to do with the schema not being properly installed I think
git clone https://github.com/common-workflow-language/cwltool.git
cd cwltool
git checkout pa/conditionals
pip install -e .
cd ..

git clone https://github.com/kaushik-work/cwl-conditionals.git
cd cwl-conditionals

chmod +x run-examples.sh
./run-examples.sh
```  

## Running Toil in macOS

You may need to do the following before running a task that uses Docker
`export TMPDIR=/tmp/docker_tmp` from Toil
