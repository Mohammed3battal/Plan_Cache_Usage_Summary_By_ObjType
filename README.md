## Script: Analyze SQL Server Plan Cache Usage by Object Type

**Description**:
This script provides an overview of the SQL Server plan cache, grouped by object type (`Proc`, `Prepared`, `Adhoc`, etc.). It calculates the total number of cached plans, their total memory usage (in MB), average use count, and average age in minutes based on plan creation time.

**What It Shows**:
- `CacheType`: Type of cached object (`Adhoc`, `Proc`, `Prepared`, etc.)
- `Total Plans`: Number of cached plans per type
- `Total MBs`: Total memory used by those plans
- `Avg Use Count`: How often each plan is reused
- `Avg Age in Minutes`: How old the plans are on average

**Use Case**:
- Identify excessive ad-hoc plan caching (plan cache bloat)
- Troubleshoot memory pressure in the plan cache
- Detect underused or old cached plans
- Optimize plan reuse via parameterization or forced plans

**Requirements**:
- SQL Server 2005 or later
- `VIEW SERVER STATE` permission

**Tips**:
- High `Total MBs` in `Adhoc` cache type may indicate parameterization issues.
- Use with `DBCC FREESYSTEMCACHE('SQL Plans')` cautiously in dev/test environments to clear cache and test effects.
