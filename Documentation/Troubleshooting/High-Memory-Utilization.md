Business Problem: Windows Server VM reported 96% memory utilization.
Investigation: Used Task Manager, **Get-Process**, and **Get-CimInstance** to identify memory usage and system capacity.
Root Cause: VM had approximately 1 GB of RAM, which was insufficient for the installed services and interactive administration.
Resolution: Determined that no individual process was leaking memory. Recommended reducing unnecessary workloads or resizing the VM rather than restarting it.
Lessons Learned: High memory utilization alone is not enough to diagnose a problem. Always gather evidence, identify the root cause, and choose a corrective action that addresses the underlying issue.

