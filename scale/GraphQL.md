## [Our learnings from adopting GraphQL](https://medium.com/netflix-techblog/our-learnings-from-adopting-graphql-f099de39ae5f)

### Background
- Many UI needs many data.
- Provides denormalized data makes network bandwidth bottleneck.
- Instead of making cusom endpoints for each UI, use GraphQL.

### Benefit
- (Redistributing load and payload optimization)
  - GraphQL <-> API ... No change but it's ok because high spec network.
  - GraphQL <-> UI ... dramatically improved.
- (Reusable abstractions)
  - just define how to map / join data.
- (Chaining type systems)
  - auto code gen, GraphQL -> TypeScript, for example.
- (DI/DX — Simplifying development)
  - UI app does not need to impl complicated codes to call GraphQL from each component.
- (Other benefits)
  - failover is implemented in GraphQL, test easy

### Pains
- (Selfish resolvers)
  - Resolver will work independently -> Makes similar requests to APIs -> It's waste of resource.
  - Solved by making in-mem cache layer not to make similar requests by 1 request.
- (What a tangled web we weave)
  - debug mode is implemented. if request has flag, response contains all logs.
- (Breaking down typing)
  - OOP broken. Method can't run on partial data which requires full data.


## [How Netflix Scales its API with GraphQL Federation (Part 1)](https://netflixtechblog.com/how-netflix-scales-its-api-with-graphql-federation-part-1-ae3557c187e2)

### Issue
When one team handles several domains managed by other teams, it had negative impacts (GraphQL team does not know much about each domain, resolvers are implemented manually, etc..).

### Solution
- Developed GraphQL federation.
Each domain team can define schema independently.
- Resolver will plan how to run query?
- etc..