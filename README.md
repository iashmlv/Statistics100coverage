### Instructions (C0 Coverage)
The smallest unit JaCoCo counts are single Java byte code instructions. Instruction coverage provides information about the amount of code that has been executed or missed. This metric is completely independent from source formatting and always available, even in absence of debug information in the class files.

### Branches (C1 Coverage)
JaCoCo also calculates branch coverage for all if and switch statements. This metric counts the total number of such branches in a method and determines the number of executed or missed branches. Branch coverage is always available, even in absence of debug information in the class files. Note that exception handling is not considered as branches in the context of this counter definition.

If the class files haven been compiled with debug information decision points can be mapped to source lines and highlighted accordingly:

No coverage: No branches in the line has been executed (red diamond)
Partial coverage: Only a part of the branches in the line have been executed (yellow diamond)
Full coverage: All branches in the line have been executed (green diamond)

### Lines
For all class files that have been compiled with debug information, coverage information for individual lines can be calculated. A source line is considered executed when at least one instruction that is assigned to this line has been executed.

Due to the fact that a single line typically compiles to multiple byte code instructions the source code highlighting shows three different status for each line containing source code:

No coverage: No instruction in the line has been executed (red background)
Partial coverage: Only a part of the instruction in the line have been executed (yellow background)
Full coverage: All instructions in the line have been executed (green background)
Depending on source formatting a single line of a source code may refer to multiple methods or multiple classes. Therefore the line count of methods cannot be simply added to obtain the total number for the containing class. The same holds true for the lines of multiple classes within a single source file. JaCoCo calculates line coverage for classes and source file based on the actual source lines covered.

### Cyclomatic Complexity
JaCoCo also calculates cyclomatic complexity for each non-abstract method and summarizes complexity for classes, packages and groups. According to its definition by McCabe1996 cyclomatic complexity is the minimum number of paths that can, in (linear) combination, generate all possible paths through a method. Thus the complexity value can serve as an indication for the number of unit test cases to fully cover a certain piece of software. Complexity figures can always be calculated, even in absence of debug information in the class files.

The formal definition of the cyclomatic complexity v(G) is based on the representation of a method's control flow graph as a directed graph:

v(G) = E - N + 2

Where E is the number of edges and N the number of nodes. JaCoCo calculates cyclomatic complexity of a method with the following equivalent equation based on the number of branches (B) and the number of decision points (D):

v(G) = B - D + 1

Based on the coverage status of each branch JaCoCo also calculates covered and missed complexity for each method. Missed complexity again is an indication for the number of test cases missing to fully cover a module. Note that as JaCoCo does not consider exception handling as branches try/catch blocks will also not increase complexity.