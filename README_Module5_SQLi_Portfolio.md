# Web Application Security Assessment and SQL Injection Testing

**Module:** 5 Assignment  
**Lab:** Damn Vulnerable Web Application (DVWA)  
**Environment:** Authorized private lab (`http://172.20.10.5/dvwa/`)  
**Status:** Partial assessment; only observed results are claimed.

## Objective
Assess SQL injection behavior in an intentionally vulnerable training app, document manual observations and automated-tool limitations, and recommend secure coding controls.

## Scope and ethics
Testing was limited to the DVWA instance in the private lab. Do not use these tests against systems without explicit authorization. Do not publish passwords, session cookies, or other secrets in screenshots.

## Observed results
- Baseline input `1` returned the `admin` record.
- Input `1'` produced a visible MySQL syntax error.
- Input `1' OR '1'='1` returned five records.
- In the blind module, `1' AND '1'='1` returned `admin`; `1' AND '1'='2` returned no visible record.
- The URL `?id=1&Submit=Submit` indicates GET query parameters.
- Initial SQLMap run was redirected to `/dvwa/login.php`; it did not confirm injection. Because no authenticated browser session was supplied, the result is inconclusive for the vulnerable endpoint.

## Findings
1. SQL injection behavior in DVWA Low: a Boolean expression returned multiple records.
2. Boolean-based blind behavior: true and false conditions produced different visible results.
3. Database error disclosure: malformed input produced a MySQL syntax error.

These are findings in a deliberately vulnerable lab, not claims about a production website.

## Remediation
- Use parameterized queries/prepared statements.
- Avoid concatenating untrusted input into SQL.
- Apply least-privilege database accounts.
- Return generic user-facing errors and keep detailed exceptions in protected logs.
- Validate inputs server-side and add regression tests.

## Remaining work
- Complete and document a dedicated authentication-bypass test.
- Test POST parameters if supported.
- Complete a time-based blind test if required.
- Repeat SQLMap only after confirming the authenticated request reaches the intended endpoint.
- Attach actual screenshots in `evidence/` and update this README with final results.

## Suggested repository structure
```text
module5-sqli-assessment/
├── README.md
├── report/
│   └── Module5_SQLi_Assessment_Report.pdf
└── evidence/
    ├── evidence-01-baseline.png
    ├── evidence-02-syntax-error.png
    ├── evidence-03-boolean-sqli.png
    ├── evidence-04-blind-true.png
    ├── evidence-05-blind-false.png
    ├── evidence-06-get-parameters.png
    └── evidence-07-sqlmap-initial.png
```

Do not mark the project fully complete until remaining tests and evidence are completed.
