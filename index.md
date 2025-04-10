<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>IDOR Allows Unauthorized Access to Files</title>
</head>
<body>
    <h1>IDOR Allows Unauthorized Access to Files</h1>
    <p><strong>URL:</strong> https://test.com?file=123</p>
    <p><strong>Severity:</strong> Medium/High (depending on data)</p>
    <p><strong>Description:</strong> The endpoint https://test.com?file=123 is vulnerable to IDOR. By manipulating the <code>file</code> parameter, an authenticated user can access files belonging to other users without authorization.</p>
    
    <h2>Steps to Reproduce:</h2>
    <ol>
        <li>Log in as User A (e.g., ID: 100).</li>
        <li>Visit <a href="https://test.com?file=123">https://test.com?file=123</a> — observe access to a file.</li>
        <li>Change the parameter to <code>file=124</code> (or another valid ID).</li>
        <li>Successfully access a file not assigned to User A.</li>
    </ol>
    
    <p><strong>Impact:</strong> Unauthorized access to sensitive files (e.g., user data, documents). Potential for data leakage or privilege escalation.</p>
    
    <p><strong>Evidence:</strong></p>
    <pre>
Request: GET /?file=124 HTTP/1.1
Response: [Contents of file 124]
    </pre>
    <p>(Attach screenshot if possible)</p>
    
    <p><strong>Recommendation:</strong> Implement proper access controls. Validate the <code>file</code> parameter against the user’s permissions before serving content.</p>
</body>
</html>
