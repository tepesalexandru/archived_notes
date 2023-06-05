---
title: "Durable Functions"
---
Durable Functions is an extension of [[Azure Functions]] that lets you write stateful functions in a serverless compute environment.

The `durable functions` extension lets you defined `stateful` workflows by writing `orchestrator functions` and stateful entities by writing `entity functions` using the Azure Functions programming model.

Behind the scenes, the extension manages state, checkpoints, and restarts for you, allowing you to focus on your business logic.

Durable Functions offer support for a multitude of languages, such as C#, Javascript, Python, F# and PowerShell.

### Patterns
The primary use case for Durable Functions is simplifying complex, stateful coordination requirements in serverless applications. 5 important patterns have came out over the years, which are the following:
- Function chaining
- Fan-out/Fan-in
- Async HTTP APIs
- Monitor
- Human Interaction