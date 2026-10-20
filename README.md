# Web Application Security Assessment & SQL Injection Testing

A hands-on web application security assessment using **Damn Vulnerable Web Application (DVWA)** in an authorized lab environment.

## Project Overview

This project explores SQL injection vulnerabilities through manual testing, Boolean-based blind SQL injection, parameter analysis, and automated testing with SQLMap.

## Lab Environment

- **Application:** DVWA
- **Platform:** Kali Linux
- **Target:** Private, intentionally vulnerable lab
- **Security level during manual testing:** Low

## Tests Performed

- Baseline input testing
- SQL syntax-error observation
- Boolean-based SQL injection testing
- Boolean-based blind SQL injection comparison
- GET parameter identification
- Initial SQLMap assessment

## Key Observations

- Input `1` returned the `admin` record.
- Input `1'` triggered a MySQL syntax error.
- Input `1' OR '1'='1` returned multiple records.
- In the blind SQL injection module, true and false conditions produced different visible responses.
- The initial SQLMap scan was redirected to the login page and did not confirm injection. This automated result is inconclusive because the authenticated session was not supplied.

## Security Recommendations

- Use parameterized queries and prepared statements.
- Avoid concatenating untrusted input into SQL queries.
- Apply least-privilege database permissions.
- Return generic error messages to users.
- Keep detailed errors in protected server logs.
- Validate inputs and perform security regression testing.

## Project Status

**In progress.** Authentication-bypass testing, POST parameter testing, time-based blind testing, and further authenticated automated testing still require verification.

## Ethical Scope

All testing described in this project is limited to an intentionally vulnerable DVWA lab. No production-system vulnerability claims are made.

## Tools

- Kali Linux
- DVWA
- SQLMap
- Web browser developer tools

