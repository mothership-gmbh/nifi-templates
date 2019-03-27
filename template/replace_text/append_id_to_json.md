# Abstract

I want to be able to append a NiFi-attribute to an existing JSON.

Before: 

```
{
  "a": "i do exist"
}
```

Expected After:

```
{
  "a": "i do exist",
  "b": "i am new"
}
```

# Strategy

Use the Replace-Text Processor and a combination of regex, replacement and NiFi-Expression-Language to solve this problem.

# Settings

Required Processor: ReplaceText 1.8.0

| Variables        |      Values        |
|------------------|:------------------:|
| Search Value     |    (?s:(^.*)}$)    |
| Replaement Value | $1,"_id":"${sku}"} |


