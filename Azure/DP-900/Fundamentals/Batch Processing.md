---
title: "Batch Processing"
---
# Batch Processing
## Common Scenarios
When accessing the data after a specific amount of time, or after a specific amount of events.

Examples:
- Data for a product catalog will be loaded every 12 hours to a data warehouse.
- Updates to inventory data will be loaded to a data warehouse every 1 million transactions.

## Benefits
When using batch processing, you can output data to:
- a file store
- a relational database
- a NoSQL database

## Downsides
When using batch processing, latency is expected.