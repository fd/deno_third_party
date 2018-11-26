# 0.3.4

* Another potentially weak ordering discovered (with even less practical effect
  than the previous).

# 0.3.3

* Increased potentially weak ordering (probably without any practical effect).

# 0.3.2

* Documentation link fix.

# 0.3.1

* Few convenience constructors.
* More tests (some randomized property testing).

# 0.3.0

* `compare_and_swap` no longer takes `&Guard` as current as that is a sure way
  to create a deadlock.
* Introduced `Lease` for temporary storage, which doesn't suffer from contention
  like `load`, but doesn't block writes like `Guard`. The downside is it slows
  down with number of held by the current thread.
* `compare_and_swap` and `rcu` uses leases.
* Made the `ArcSwap` as small as the pointer itself, by making the
  shards/counters and generation ID global. This comes at a theoretical cost of
  more contention when different threads use different instances.

# 0.2.0

* Added an `ArcSwapOption`, which allows storing NULL values (as None) as well
  as a valid pointer.
* `compare_and_swap` accepts borrowed `Arc` as `current` and doesn't consume one
  ref count.
* Sharding internal counters, to improve performance on read-mostly contented
  scenarios.
* Providing `peek_signal_safe` as the only async signal safe method to use
  inside signal handlers. This removes the footgun with dropping the `Arc`
  returned from `load` inside a signal handler.

# 0.1.4

* The `peek` method to use the `Arc` inside without incrementing the reference
  count.
* Some more (and hopefully better) benchmarks.

# 0.1.3

* Documentation fix (swap is *not* lock-free in current implementation).

# 0.1.2

* More freedom in the `rcu` and `rcu_unwrap` return types.

# 0.1.1

* `rcu` support.
* `compare_and_swap` support.
* Added some primitive benchmarks.

# 0.1.0

* Initial implementation.