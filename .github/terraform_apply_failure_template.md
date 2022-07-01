---
title: Terraform apply failure
labels: bug
---
Terraform apply was failured !!!  
Here's who did it: @{{ env.ACTOR }}.  
commit hash: {{ env.SHA }}  
actions: {{ env.ACTIONS_URL }}

<details><summary>Show Apply Error</summary>

```
{{ env.APPLY_STDERR }}
```

</details>