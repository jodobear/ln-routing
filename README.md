# Exploring Lightning Network

## Data

1 hour data of Channels and Nodes taken from timestamp: `2020_03_04_02_36_56`.
[source](https://www.kaggle.com/dataset/f83ba8b53821f154bf3e642c8e484338b008f574760d7e0a7d6f67e4154a6bc2)

## Preliminary analysis

1. I was able to find some weakly connected components. This is interesting since
this can serve as a good way to identify better nodes to connect to for
routing.

2. While using the following code to find shortest pah, I would get `No path found error`. Makes sense, but then how do i ignore those and continue with the algo. Should do `try...except`, but then `Networkx` had `all_pairs_shortest_path`:

```py
import random

sh_path = dict()
def find_sh_path(G, s=list(G)[random.randrange(1000)], \
                    t=list(G)[random.randrange(1000)]):
    return s, t, nx.shortest_path(G, source=s, target=t, method='dijkstra')

i = 1000
while i > 0:
    s, t, path = find_sh_path(G)
    sh_path[(s, t)] = path
    i -= 1
```

