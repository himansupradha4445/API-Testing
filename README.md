# API-Testing
## 1. Common HTTP Status Codes

### 2xx – Success
- **200 OK** – Request succeeded
- **201 Created** – Resource successfully created
- **204 No Content** – Success, no response body

### 3xx – Redirection
- **301 Moved Permanently** – Resource moved to a new URL
- **302 Found** – Temporary redirect
- **304 Not Modified** – Cached version still valid

### 4xx – Client Errors
- **400 Bad Request** – Invalid request syntax
- **401 Unauthorized** – Authentication required
- **403 Forbidden** – Client not allowed
- **404 Not Found** – Resource not found
- **409 Conflict** – Resource conflict
- **422 Unprocessable Entity** – Validation failed

### 400 – Bad Request
**Why it happens:**  
The server cannot process the request because the client sent invalid or malformed data.  
Common causes:
- Missing required fields  
- Wrong data types  
- Invalid JSON  
- Query parameters formatted incorrectly  

**How to fix:**  
- Validate input before sending the request  
- Ensure JSON is valid  
- Check the API documentation for required fields  
- Use correct data formats  

---

### 401 – Unauthorized
**Why it happens:**  
Authentication is required, but the client did not provide credentials or provided invalid/expired credentials.  

**How to fix:**  
- Include a valid API key, token, or login credentials  
- Refresh the token if expired  
- Ensure the Authorization header is correct  
  Example:  
  `Authorization: Bearer <token>`

---

### 403 – Forbidden
**Why it happens:**  
The server understood the request, but the client does not have permission to access the resource.  
This is **authorization**, not authentication.  

**How to fix:**  
- Check user roles or permissions  
- Ensure your API key has sufficient access rights  
- Contact the API owner if you need additional access  

---

### 404 – Not Found
**Why it happens:**  
The server cannot find the requested resource.  
Common causes:
- Wrong URL path  
- Resource ID does not exist  
- The endpoint was removed or renamed  

**How to fix:**  
- Verify URL and endpoints  
- Check that the resource ID exists  
- Confirm the endpoint is still supported in the API  

---

### 409 – Conflict
**Why it happens:**  
There is a conflict with the current state of the server.  
Common examples:
- Trying to create a user that already exists  
- Updating a resource that has been modified by someone else  

**How to fix:**  
- Check if the resource already exists before creating  
- Refresh the data and try again  
- Handle version conflicts if the API uses versioning or ETags  

---

### 422 – Unprocessable Entity
**Why it happens:**  
The server understands the request, but the data is logically invalid.  
Very common in REST APIs for validation errors.  
Examples:
- Password too short  
- Email format invalid  
- Required fields contain invalid values  

**How to fix:**  
- Follow validation rules defined in the API  
- Correct invalid fields  
- Read the server’s error message (usually includes exact validation errors)  


### 5xx – Server Errors
- **500 Internal Server Error** – Generic server error
- **501 Not Implemented** – Endpoint/method not supported
- **502 Bad Gateway** – Invalid response from upstream service
- **503 Service Unavailable** – Server overloaded or down

## 📘 API Methods Summary Table

| Method   | Purpose              | Description (Short)                           |
|----------|----------------------|-----------------------------------------------|
| GET      | Retrieve data        | Fetches information without changing anything |
| POST     | Create data          | Adds a new resource using request body        |
| PUT      | Full update          | Replaces the entire existing resource         |
| PATCH    | Partial update       | Updates only specific fields                  |
| DELETE   | Delete data          | Removes an existing resource                  |
| HEAD     | Headers only         | Same as GET but returns no body               |
| OPTIONS  | Allowed methods      | Shows supported methods for the endpoint      |
| TRACE    | Diagnostic           | Returns request for debugging (rare)          |
| CONNECT  | Tunnel               | Creates a network tunnel via proxy            |

## 📘 SELECTOR SUMMARY  TABLE

| Selector Type        | Syntax Example                               | Usage                             |
|----------------------|-----------------------------------------------|-----------------------------------|
| ID                   | By.id("username")                             | Fastest & most preferred          |
| Name                 | By.name("email")                              | When ID not available             |
| Class Name           | By.className("btn-primary")                   | For elements with class attribute |
| Tag Name             | By.tagName("button")                          | Useful for generic HTML tags      |
| Link Text            | By.linkText("Login")                          | For exact link text <a>           |
| Partial Link Text    | By.partialLinkText("Log")                     | For partial match of <a>          |
| CSS Selector         | By.cssSelector("input[type='text']")          | Powerful & flexible selector      |
| XPath                | By.xpath("//input[@id='user']")               | Most powerful, handles complex    |

## 📘 XPATH Summary Table

| XPath Type                  | Example                                             | Use Case |
|-----------------------------|-----------------------------------------------------|----------|
| Basic attribute             | //input[@id='name']                                 | Simple locator |
| OR / AND                    | //input[@a='1' or @b='2']                           | Multiple match conditions |
| contains()                  | //*[contains(@class,'btn')]                         | Partial match |
| starts-with()               | //input[starts-with(@id,'user')]                   | Dynamic attributes |
| text()                      | //*[text()='Login']                                 | Exact visible text |
| contains(text())            | //*[contains(text(),'Log')]                         | Partial text |
| Index / position            | (//input)[2]                                        | When multiple matches |
| parent                      | //div/parent::section                                | Navigate upward |
| child                       | //div/child::input                                  | Direct children |
| following                   | //label/following::input[1]                         | Search downward |
| following-sibling           | //label/following-sibling::input                    | Same-level elements |
| preceding                   | //input/preceding::label                            | Backward search |
| preceding-sibling           | //input/preceding-sibling::label                    | Previous siblings |
| ancestor                    | //input/ancestor::form                              | Parent structure |
| descendant                  | //div/descendant::input                             | Nested elements |
| last()                      | (//input)[last()]                                   | Last element |
| Relative XPath              | //input[@type='text']                               | Best practice |
| Absolute XPath              | /html/body/...                                      | Avoid use |

## 📘 CSS Summary Table

| Predicate Type         | Example                                 | Meaning |
|------------------------|-------------------------------------------|---------|
| Attribute              | //input[@id='name']                       | Match specific attribute |
| Multiple attributes    | //input[@type='text' and @name='user']    | Both conditions true |
| OR condition           | //button[@id='a' or @name='b']            | Either condition true |
| contains()             | //div[contains(@class,'active')]          | Partial match |
| starts-with()          | //input[starts-with(@id,'user')]          | Beginning match |
| text()                 | //*[text()='Login']                       | Exact text |
| contains(text())       | //*[contains(text(),'Log')]               | Partial text |
| Index                  | (//input)[2]                              | 2nd matched element |
| last()                 | (//button)[last()]                        | Last matched element |

## AUTHENTICATION(Verifies identity)
- Authentication is the process of verifying the identity of a user or system before giving access to an API.
  Examples:
- Logging in with username and password
-  Verifying an access token
-  Using an API key
## AUTHORIZATION (Verifies permissions)
- Authorisation is the process of checking what an authenticated user is allowed to do.
  Examples:
- Admin can delete users
-  User can view only their own data


