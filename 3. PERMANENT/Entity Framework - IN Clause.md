---
type: evidence
topic: dotnet
---

- Topic : #dotnet 
- Tags : #entityframework

# Idea


Equivalent of `WHERE col IN (10,14)`

```javascript
albumIds = {1,2,13,25,277,567};
var query = context.Albums.Where(x=> albumIds.Contains(x.ID));
```

# Links

Sources : [asp.net - Equivalent IN operator in entity framework - Stack Overflow](https://stackoverflow.com/questions/31318405/equivalent-in-operator-in-entity-framework)

## West : Similar

## East : Opposite

## North : Theme / Question

- [[How to optimise Entity Framework requests]]


## South : What does it lead to

