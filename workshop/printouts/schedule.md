# Schedule and Material

## Schedule

| Code Smell                                                                           | Exercise                                | Exercise          | Hints                                                           |
|--------------------------------------------------------------------------------------|-----------------------------------------|-------------------|-----------------------------------------------------------------|
| Introduction slides                                                                  | Good / Bad Code, Code Smells            | On whiteboard     |                                                                 |
| ?Magic Number / String, Redundant Comment                                            | find on paper                           | On paper          | no refactoring                                                  |
| Complicated Conditional Expression                                                   | Circle::contains                        | branch: main      | Make it better to read. Extract method, extract variable        |
| Deeply-Nested Control Flow & Long method                                             | Circle::countContainedPoints            | branch: exercise2 | invert if, merge if, remove redundant else, composed method     |
| Refactoring slides                                                                   | Refactoring                             |                   |                                                                 |
| Side effect & temporary field, Duplicate & Reduce                                    | Circle::countContainedPoints / contains | branch: exercise3 | Duplicate and Reduce                                            |
| Primitive Obsession, Data Clump, Long Parameter List, Parallel Change, Narrow Change | Circle: x, y, r                         | branch: exercise4 | Parallel Change, Point, Radius, Discussion Value Objects        |
| Data Class, Feature Envy                                                             | Radius validation, Circle::format()     | branch: exercise5 |                                                                 |   
| Loop Split                                                                           | Circle::countContainedPoints            | branch: exercise6 | Maybe do these two                                              |
| Emerging Software Design                                                             | Circle::countContainedPoints            | branch: exercise7 |                                                                 |
| Flag Parameter                                                                       | Circle::format()                        | branch: exercise8 | Extract Method for subbranches, Elvis Operator trick            |
| Bad Name                                                                             | Naming Exercise (ppt)                   |                   |                                                                 |
| Speculative Generality & Lazy Class                                                  | Circle extends Shape                    | branch: exercise9 | Only shown by trainer                                           |
| Inconsistent Solution, Dead Code                                                     | Color                                   |                   | Find in code (e.g. String concat, errorMessage), no refactoring |    
| Outro                                                                                | -                                       | -                 | slides                                                          |

## Printouts

- Code on paper
- ? Refactoring shortcuts
- ? 1 pager code smells

## Materials

- set of sticky notes
- red & green sticky notes (for 'done w/ exercise')
- pin-up posters
- whiteboard markers

## Repositories

- [Java](https://github.com/ozihler/software-design-workshop-java)
- [Python](https://github.com/ozihler/software-design-workshop-python)

## Solution Videos

- [Java](https://youtu.be/hFx1AiLb7dc)
- [Python](https://www.youtube.com/watch?v=URPIL-Vyu60)

## TODOs

- split ifs with same exception into multiple ifs to show "merge if"
- switch Complicated Cond w/ Deeply-Nested Control Flow and Long Method