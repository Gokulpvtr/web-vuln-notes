# SQL Injection

## What it is
User input is inserted into a SQL query without safe handling, so an attacker can change the query's meaning and read or modify database data.

## Where to look
Login forms, search boxes, filters, sort parameters, IDs in URLs, cookies and headers used in queries.

## How to test
1. Add a single quote `'` and watch for errors or behaviour changes.
2. Try boolean conditions: `' AND 1=1--` vs `' AND 1=2--` and compare responses.
3. Try time-based payloads when there is no visible difference.
4. Use `UNION SELECT` after finding the column count and types.

## Example payloads
```
' OR 1=1--
administrator'--
' ORDER BY 3--
' UNION SELECT NULL,NULL--
```

## Bypasses
- Different comment styles (`--`, `#`, `/* */`) depending on the database
- Encoding and case variations against simple filters

## Impact
Authentication bypass, data theft, data modification, and sometimes command execution.

## Prevention
- Parameterized queries / prepared statements
- Least-privilege database accounts
- Input validation as defense in depth

## Related labs
Link your PortSwigger SQLi write-ups here.

## References
- PortSwigger Web Security Academy: SQL injection
- OWASP: SQL Injection Prevention Cheat Sheet
