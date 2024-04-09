```mermaid
sequenceDiagram
    participant browser
    participant server

    Note right of browser: Browser sends form data: note: test

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    server-->>browser: Status: 302 Found
    deactivate server

    Note right of browser: After submitting the form, the page reloads

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document, Status: 304 Not Modified
    deactivate server

    Note right of browser: The browser finds a link to CSS in the HTML markup and sends a GET request to retrieve the styles.

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: CSS file, Status: 304 Not Modified
    deactivate server

    Note right of browser: The browser finds a link to JS in the HTML markup and sends a GET request to retrieve the code.

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: JS file, Status: 304 Not Modified
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "new note again", "date": "2024-04-07T21:33:19.657Z" }, ... ], status: 200 OK
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes
```