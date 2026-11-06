# Scaling policy evidence

## Task 1: idle reservation
Minimum 3 reserved three idle slots despite accepted cold-start delay. Set minimum 0; task1 now passes, other two failures remain. Best-effort warm minimum can restart; bursts and rollouts can cold-start. Zero minimum permits scale-to-zero, not zero total bill or instant shutdown.

## Task 2: downstream bound
Pool 4 and connection budget 8 imply max <= 2. Changed max8 to max2: 32 toy connections become 8. Task2 now passes; max2/c1 takes six waves, so task3 remains red. Actual Cloud Run maximum can briefly be exceeded; revisions, pool size, fan-out, retries and other clients also matter. Maximum is risk control, not spend cap or downstream guarantee. Ordinary alerts-only budgets notify and can lag, not stop spend. Separate supported spend-cap features have coverage/eligibility limits; not our lab safety boundary.
