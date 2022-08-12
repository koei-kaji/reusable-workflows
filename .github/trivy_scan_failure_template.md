---
title: Trivy scan failure
labels: vulnerability
---
Trivy scan was failured !!!  
Here's who did it: @{{ env.ACTOR }}.  
commit hash: {{ env.SHA }}  
actions: {{ env.ACTIONS_URL }}

<details><summary>Show Trivy Results</summary>

```
{{ env.TRIVY_RESULTS }}
```

</details>