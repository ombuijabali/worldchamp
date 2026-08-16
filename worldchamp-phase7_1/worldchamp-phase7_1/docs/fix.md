# Phase 7.1 compiler fix

Original failing lines:

```pine
array.swap(levels, i, best)
array.swap(names, i, best)
```

Replacement:

```pine
float levelAtI = array.get(levels, i)
float levelAtBest = array.get(levels, best)
string nameAtI = array.get(names, i)
string nameAtBest = array.get(names, best)
array.set(levels, i, levelAtBest)
array.set(levels, best, levelAtI)
array.set(names, i, nameAtBest)
array.set(names, best, nameAtI)
```
