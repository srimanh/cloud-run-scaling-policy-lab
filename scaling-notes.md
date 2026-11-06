# Scaling policy evidence

## Task 1: idle reservation
Minimum 3 reserved three idle slots despite accepted cold-start delay. Set minimum 0; task1 now passes, other two failures remain. Best-effort warm minimum can restart; bursts and rollouts can cold-start. Zero minimum permits scale-to-zero, not zero total bill or instant shutdown.

## Task 2: downstream bound
Pool 4 and connection budget 8 imply max <= 2. Changed max8 to max2: 32 toy connections become 8. Task2 now passes; max2/c1 takes six waves, so task3 remains red. Actual Cloud Run maximum can briefly be exceeded; revisions, pool size, fan-out, retries and other clients also matter. Maximum is risk control, not spend cap or downstream guarantee. Ordinary alerts-only budgets notify and can lag, not stop spend. Separate supported spend-cap features have coverage/eligibility limits; not our lab safety boundary.

## Task 3: packing within memory
32 + 32*c <= 160 implies c <= 4. First-wave admission >= 8 requires max*c >= 8. With max <= 2, c >= 4. Combined with memory c <= 4 this forces max2/c4: 8 admitted, 4 deferred, two waves. max2/c1 used six waves. max2/c4 uses 160/160 MiB assumed memory; concurrency is simultaneous requests, not RPS. c5 uses 192 and must fail memory check. Restore c4 afterward.

## Limits and evidence
No measured RAM, cloud scaling, autoscaler timing, latency or billing forecast. Identical assumed burst slots before/after do not prove equal real throughput or monetary savings. Request-based and instance-based billing treat idle time differently; no currency computed. All runs local Docker, no cloud load test or resources. Original baseline, intermediate, final and c5 output captured during authoring. Public PR will carry evidence; mentor walkthrough script is not a recorded learner submission video.
