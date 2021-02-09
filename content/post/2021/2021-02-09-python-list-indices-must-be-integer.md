---
title: "2021 02 09 Python List Indices Must Be Integer"
date: 2021-02-09T00:30:12-08:00
draft: false
keywords: []
description: ""
tags: ["Python"]
categories: 
    - "个人笔记"
---

We can solve the error “typeerror: list indices must be integers or slices, not str” by making sure that we  access items in a list using index numbers, not strings.

The problem in our code is that we’re trying to access “level” in our list of lods:
```lods['level']```

```python

# Python typeerror: list indices must be integers or slices, not str Solution

# Get the scale by the level of LOD
#

lods = [
	 {
        "level": 16,
        "resolution": 2.38865713397468,
        "scale": 9027.9774109999998
    },
    {
        "level": 17,
        "resolution": 1.1943285668550501,
        "scale": 4513.9887049999998
    }
]

def getScaleByLod(lod):
	  # for lod in lods  
    #   if lods['level'] == lod:
	  # TypeError: list indices must be integers or slices, not str 
    for  i in range(len(lods)):
        if lods[i]["level"] == lod:
            scale = lods[i]['scale']
            # print(scale)
            print("The scale of LOD {} is {}.".format(lods[i]["level"], scale))
            return scale
  
  
```

