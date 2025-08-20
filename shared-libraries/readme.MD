# Shared libraries:

As Pipeline is adopted for more and more projects in an organization, common patterns are likely to emerge. Oftentimes it is useful to share parts of Pipelines between various projects to reduce redundancies and keep code "DRY"

## Directory Structure:

``` groovy 
(root)
+- src                     # Groovy source files
|   +- org
|       +- foo
|           +- Bar.groovy  # for org.foo.Bar class
+- vars
|   +- foo.groovy          # for global 'foo' variable
|   +- foo.txt             # help for 'foo' variable
+- resources               # resource files (external libraries only)
|   +- org
|       +- foo
|           +- bar.json    # static helper data for org.foo.Bar
```



## configure:

- Manage jenkins --> configure system --> global pipeline libraries --> library_name, branch_name, retrival_method --> modern SCM --> Git repo etc --> save


## Ways to use Shared libraries: 

``` groovy
@Library('my-shared-library') _
/* Using a version specifier, such as branch, tag, etc */
@Library('my-shared-library@1.0') _
/* Accessing multiple libraries with one statement */
@Library(['my-shared-library', 'otherlib@abc1234']) _
```

- The annotation can be anywhere in the script where an annotation is permitted by Groovy. When referring to class libraries (with src/ directories), conventionally the annotation goes on an import statement:

``` groovy 
@Library('somelib')
import com.mycorp.pipeline.somelib.UsefulClass
```

## Advantages:
- Code maintenanace
- Reduce errors in the code
- Reduce duplication of code