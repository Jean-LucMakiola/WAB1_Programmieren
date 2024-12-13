
### Comparing the Performance and Package Management Capabilities of Python Virtual Environments: An evaluation on *venv*, *conda/miniconda*, *Pipenv*, and *Virtualenv* for efficient *Pytest* pipelines

Python environments are essential for creating isolated environments that bundle an independently managed Python instance with its own dependencies and versions, independent of the systems Python installation. In modern software development  requires constant testing and continuous integration (CI) workflows. The right tool for the creation and management of a virtual environment is crucial due to its direct impact on a developers efficiency and the applications security. Later is in the form of version control, especially of dependencies, making sure to minimize the chance of possible security loop holes and following breaches. The study aims to compare these tools on the following criteria: 
* *Test execution speed*: How efficiently can each tools created environment run a fixed suite of tests?
* *Package management:* How well does the tool manage dependencies, by keeping the up to date and resolving conflicting dependencies, with minimal human workload?
##### Relevance for the business
The business has a variety of different python projects in use and development. The use of  Python virtual environments can often be located in *CI Pipelines* and in the developer's personal testing suite. For both time saving and efficiency are key in assuring waiting and downtimes for developers and services are kept at a minimum, maintaining a fast feedback loop for developers. Slow setup or excessive test execution time can lead to bottlenecks, delaying the release cycle and negatively affecting developer productivity. Thus, evaluating the performance of each virtual environment tool in these contexts is of significant practical relevance.
Furthermore maintaining project dependencies is essential for secure, reproducible and consistent software. It has to be evaluates weather the overhead introduced by more robust and feature rich solutions like *Pipenv* and *conda* outweighs the resulting time saver due to improved and automated dependency management.

From a theoretical perspective, this research contributes to the understanding of **best practices** in virtual environment management and its relationship with software development performance. The comparison of *venv*, *conda*, *Pipenv*, and *virtualenv* also adds to the body of knowledge on dependency management in Python programming, particularly in the context of testing and *CI/CD pipelines*.
### 1. Speed of environment setup and *pytest* execution

#### Hypothesis:
"The use of *venv* or *virtualenv* will result in the fastest environment creation, as well as *pytest* run time. In contrast both *Pipenv* and *conda/miniconda* will invoke an increased run time due to their dependency management features."
#### Rational
* *venv* and *virtualenv* are simple, handling just Python dependencies, which should make them faster in both environment creation and run time
* *conda/miniconda* adds overhead with it extended dependency management capabilities
* *Pipenv* introduces overhead as well due to its additional features like dependency resolution and *Pipfile.lock* 

### 2. Package Management and Security (Up-to-date Dependencies)
#### Hypothesis
"*Conda/miniconda* and *Pipenv* will better manage package versions and ensure dependencies are up to date, reducing security vulnerabilities, while *venv* and *virtualenv* will require more manual intervention to keep packages secure and up-to-date."

#### Rationale:
- *conda/miniconda* not only manages Python dependencies but also system-level libraries, which can lead to better overall security and package resolution
- *Pipenv* automatically locks dependencies with *Pipfile.lock*, making it easier to track and update dependencies, ensuring a more secure and reproducible environment
- *venv and virtualenv* are more basic, requiring manual management of dependencies and updates. Keeping everything secure and up to date is more time-consuming without the automation features offered by *pipenv* and *conda*



We use *LeanIX* to manage software artifacts (microservices (ms)) and the *LeanIX Connector* that checks for different and configurations in the ms is written in Python and testes using *Pytest* running in *venv*, which can take quite some time, just to see weather a small change one implemented work as it is meant to.      
## Methodology
**Data Collection:**
To compare the performance and package management capabilities of the four virtual environment tools (*venv*, *conda/miniconda*, *pipenv*, and *virtualenv*), data will be collected through a series of  tests:

1. **Test Execution Performance**:
    - A consistent set of test cases, including unit and integration tests using *pytest*, will be executed within each environment.
    - The time taken to run these tests will be measured, and resource utilization (such as CPU and memory) will be monitored using profiling tools.
2. **Package Management and Dependency Handling**:
    - Each tool will be tested for its ability to manage and resolve package dependencies.
    - The tools will be evaluated by introducing dependency conflicts (e.g., different versions of the same package) and assessing how the tools handle these conflicts, including their ability to update dependencies to secure, stable versions.

**Tools for Data Collection:**

- **Time Measurement**: Standard Python libraries such as *time* or *timeit* will be used to measure the time taken for *pytest* execution.
- **Profiling Tools**: Profiling tools like *cProfile* and *psutil* will be used to monitor resource utilization (e.g., CPU and memory consumption) during the test execution phase.
- **Security Scans**: Tools like *safety* (for checking for insecure dependencies) will be used to evaluate each tool’s ability to keep dependencies up-to-date and secure.

The prementioned data will be analyzed and evaluated using the following methods:
1. Some test provide hard data that can be statistically analyzed, including mean, median and standard deviation for run time and resource consumption
2. Other like the test on dependency resolution and security evaluation are interpretate by the tools ability to handle mismatches in version and updates to packages. Furthermore the security will be tested by checking for outdated or vulnerable packages, based on security scans using the *safety* tool
## Related works
This topic does not have any papers on the difference of between any tools rather just on that it is a good practice to use them. Still the documentations of the different tools as well as their wikis provide a starting point to evaluate their capabilities.

Bhanot, Karan. 2019. “Comparing Python Virtual Environment Tools.” Medium. February 1, 2019. [https://towardsdatascience.com/comparing-python-virtual-environment-tools-9a6543643a44](https://towardsdatascience.com/comparing-python-virtual-environment-tools-9a6543643a44).

“Conda Documentation — Conda 24.11.1 Documentation.” n.d. Accessed December 11, 2024. [https://docs.conda.io/projects/conda/en/stable/](https://docs.conda.io/projects/conda/en/stable/).

David, Henrique Miguel Castilho. 2020. “Development of a Machine Learning Platform.” Universidade Nova de Lisboa. [https://run.unl.pt/bitstream/10362/160388/1/David_2021.pdf](https://run.unl.pt/bitstream/10362/160388/1/David_2021.pdf).

Gonzalez-Rivas, Garrett, Zhihui Du, and David A Bader. n.d. “A Deployment Tool for Large Scale Graph Analytics Framework Arachne,” 7.

“Managing Environments — Conda 24.11.1 Documentation.” n.d. Accessed December 11, 2024. [https://docs.conda.io/projects/conda/en/stable/user-guide/tasks/manage-environments.html](https://docs.conda.io/projects/conda/en/stable/user-guide/tasks/manage-environments.html).

“Miniconda — Anaconda Documentation.” n.d. Accessed December 12, 2024. [https://docs.anaconda.com/miniconda/](https://docs.anaconda.com/miniconda/).

“Pipenv: Python Dev Workflow for Humans — Pipenv 2024.4.0 Documentation.” n.d. Accessed December 11, 2024. [https://pipenv.pypa.io/en/latest/](https://pipenv.pypa.io/en/latest/).

“Terms of Services Info.” n.d. Anaconda. Accessed December 12, 2024. [https://www.anaconda.com/pricing/terms-of-service-faqs](https://www.anaconda.com/pricing/terms-of-service-faqs).

“Venv — Creation of Virtual Environments.” n.d. Python Documentation. Accessed December 11, 2024. [https://docs.python.org/3/library/venv.html](https://docs.python.org/3/library/venv.html).

Wilkes, Matthew. 2020. “Prototyping and Environments.” In _Advanced Python Development: Using Powerful Language Features in Real-World Applications_, edited by Matthew Wilkes, 1–49. Berkeley, CA: Apress. [https://doi.org/10.1007/978-1-4842-5793-7_1](https://doi.org/10.1007/978-1-4842-5793-7_1).

## Outline draft

## 1. Introduction
- Introduction to Python virtual environments and the tools (*venv*, *conda/miniconda*, *pipenv*, *virtualenv*).
- Research aim: Compare the performance and package management in automated testing with *pytest*.
## 2. Literature Review
- Overview of virtual environments, their role in dependency management, and testing efficiency.
- Review of each tool's features and previous research on performance and package management.
## 3. Methodology
- **Data Collection**: Test execution with *pytest*, resource consumption, and security scans using tools like *time*, *psutil*, and *safety*.
- **Evaluation**: Statistical analysis of performance, dependency management, and security.
## 4. Results and Analysis
- Comparison of test execution times, resource usage, dependency management, and security.
## 5. Discussion
- Interpretation of results and recommendations for the best tool based on performance and package management needs in CI/CD pipelines.
## 6. Conclusion
- Summary of findings and final recommendations for choosing the right tool.
## 7. References
- List of all references used.



