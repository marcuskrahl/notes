# Tracking architecture fitnesse


## Fitnesse function

Architectural goals, especially quality measures, may be combined into a "fitnesse function" of the architecture to provide a high level view on how fit the architecture is to fulfil its purpose.

A high level fitnesse function may be composed of smaller specialized fitnesse functions for specific goals. Typical examples might be cyclomatic complexity or unit test coverage.

However it might be difficult to quantify certain goals.

Source: https://www.youtube.com/watch?v=ttL7MiF8VZw 

## Find pain points with git

The following command will list files which change most frequently in a git project

```
git log --format=format: --name-only | egrep -v '^$' | sort | uniq -c | sort -rg | head -10
```

## Tools

- Sonarqube
- [Codescene](https://codescene.com/)
    - paid service 
