# Exercise 0.4 - New Note Diagram

```mermaid
sequenceDiagram
    participant user
    participant browser
    participant server

    user->>browser: User input: "Hello Helsinki!" in the form element.
    user->>browser: Submit Notes Form clicking the Save Button

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    server-->>browser: HTTP 302 Found / Location address: https://studies.cs.helsinki.fi/exampleapp/notes
    deactivate server

    Note right of browser: The browser reloads the Notes page.

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "Hello Helsinki!", "date": "2026-06-22T15:57:02.977Z" }, ... ]
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes, adding the new note.