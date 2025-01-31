## Join Optimization Techniques in Spark  
Joins in Apache Spark are expensive operations because they involve data movement across the cluster. If not optimized, joins can cause:

❌ Slow Performance – Due to expensive shuffles across nodes.

❌ High Memory Usage – Large joins can cause OutOfMemory (OOM) errors.

❌ Network Bottlenecks – Large data transfers slow down execution.

Thus, join optimization is crucial to ensure efficient and scalable Spark performance.

## Join Optimizations in Spark

### 1️⃣ Broadcast Join (Avoids Shuffle)

👉 Best for: Small vs. Large Dataset
- Broadcasts the smaller dataset to all nodes
- Eliminates shuffling, making the join super fast 🚀

```python
# Using Broadcast Join
broadcast_df = large_df.join(broadcast(small_df), "country_code")
broadcast_df.explain(True)  # See how Spark optimizes the query

# Action to trigger execution
broadcast_df.count()
```
✅ Fast execution (no shuffle)

✅ Reduces memory & network overhead

