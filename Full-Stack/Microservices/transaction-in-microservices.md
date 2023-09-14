# Transaction in microservices

## 2-phase commit, SAGA

### 2-phase commit

`2-phase commit` is a widely used pattern to implement distributed transaction management.

<img src = "../../photo/Full-Stack/Microservices/2-phase-commit.png">

    It has two phases:

    1. Prepare phase: The coordinator asks the participating nodes whether they are ready to commit.

    2. Commit phase: If all participating nodes are ready, the coordinator will ask them to commit their changes, or roll back if at least one node failed
