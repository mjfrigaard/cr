# Code Reviews

> Below is a compilation of code reviewing resources I've compiled from various books, websites, white-papers, etc. These items are intended to be used à la carte.   
> 

## Google Engineers (code review)

[What reviewers look for (from Google Code Review Developer Guide, eng-practices)](https://google.github.io/eng-practices/review/#look_for)

### __Design__

Is the code well-designed and appropriate for your system?

### __Functionality__

Does the code behave as the author likely intended? Is the way the code behaves good for its users?

### __Complexity__

Could the code be made simpler? Would another developer be able to easily understand and use this code when they come across it in the future?

### __Tests__

Does the code have correct and well-designed automated tests?

### __Naming__

Did the developer choose clear names for variables, classes, methods, etc.?

### __Comments__

Are the comments clear and useful?

### __Style__

Does the code follow our style guides?

### __Documentation__

Did the developer also update relevant documentation?

## [YAML (Azure Pipelines) Code Review Checklist](https://microsoft.github.io/code-with-engineering-playbook/code-reviews/recipes/azure-pipelines-yaml/#code-review-checklist)

### Pipeline Structure

- [ ] The steps are well understood and components are easily identifiable. Ensure that there is a proper description `displayName`: for every step in the pipeline  

- [ ] Steps/stages of the pipeline are checked in Azure Pipelines to have more understanding of components  

- [ ] In case you have complex nested `YAML` files, The pipeline in Azure Pipelines is edited to find trigger root file  

- [ ] All the template file references are visited to ensure a small change does not cause breaking changes, changing one file may affect multiple pipelines  

- [ ] Long inline scripts in `YAML` file are moved into script files  

### YAML Structure

- [ ] Re-usable components are split into separate YAML templates
  
- [ ] Variables are separated per environment stored in templates or variable groups  

- [ ] Variable value changes in `Queue Time`, `Compile Time` and `Runtime` are considered

- [ ] Variable syntax values used with `Macro Syntax`, `Template Expression Syntax` and `Runtime Expression Syntax` are considered

- [ ] Variables can change during the pipeline, Parameters cannot

- [ ] Unused variables/parameters are removed in pipeline

- [ ] Does the pipeline meet with stage/job `Conditions` criteria?


## [Implementing Effective Code Reviews](https://www.oreilly.com/library/view/implementing-effective-code/9781484261620/)

> This text is a "_a comprehensive guide across all the main aspects to look at during code reviews._" It covers a wide range of topics (and has multiple checklists and definitions). 

### APIs


1. Does the actual implementation reflect the architecture?  
    > - *This is in reference to the implementation of the documented architecture.*
    > - *For APIs, these items focus on general structure (and are language agnostic)*

2. Is the code easy to understand?  
    > - *Similar to the complexity dimension from the Google Engineers' review items above*

3. Is the code too long?
    > - *Long is relative, but following the principle from the Zen of Python: 'Simple is better than complex.'*

4. Is cohesion in place?
    > - _`cohesion` is_ "__how focused a portion of code is on a unified purpose__" - [source](https://anh.cs.luc.edu/170/mynotes/cohesion.html#:~:text=Cohesion)

5. Is the code modular?
    > - _`modular` code_: 
        - "__`Modular` code consists of well-separated components. In such case, modifying one component would have minimal impact on others.__"

6. Are components cohesive?
    > - `cohesive` if defined below.

7. Is the code loosely coupled?
    > - _the previous four items come from the following definitions:_
        - "__`Modularity` is a basic principle of software systems. It means that components in a software system should be `cohesive` and `loosely coupled`. A `cohesive` component has a clearly defined function. Multiple components are `loosely coupled` if the dependencies between each other are minimal."__

8. Is the code reusable?
    > - _reusable code is code that is is logically `cohesive` (i.e., "__a cohesive method is easy to reuse in combination with other cohesive methods__" - [source](https://anh.cs.luc.edu/170/mynotes/cohesion.html#:~:text=Cohesion))_

9. Is the code readable?
    > - _readability is directly influenced by `modularity`. `Modular` code is logically separated (and easier to [mentally chunk](https://dictionary.apa.org/chunking))._

10. Is the code easy to maintain and test?
    > - The definition for _Testability refers to how easy it is to ensure correctness of code by means of writing tests for it._

11. Are premature optimizations in place?

12. Is composition preferred?

13. Is inheritance properly used?

### Data structures

1. Are data structures appropriately used?

2. Is the data structure appropriate based on the data size the code is dealing with?

3. Are potential changes to data size considered and handled?

4. Is the data structured forced to do operations not natively supported?

5. Does the data structure support growth (i.e., scalability)?

6. Does the data structure reflect the need for relationships between elements?

7. Does the data structure optimally support the operations you need to perform on it?

8. Is the choice of a specific data structure overcomplicating the code?

9. Is the data structure chosen based on most frequent operations to be performed on data?

10. Are you using stacks for problems that do not require FIFO?

