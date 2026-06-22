# Exercise 0.6 - New Note in Single page app diagram

```mermaid
sequenceDiagram
    participant user
    participant browser
    participant server

    user->>browser: User types "Hello SPA!"
    user->>browser: Click Save Button

    browser->>browser: Create note object
    browser->>browser: Add the note to local array
    browser->>browser: Re-render the DOM

    browser->>server: POST /new_note_spa
    activate server
    server-->>browser: HTTP 201 Created
    deactivate server

    Note right of browser: The browser doesn't redirect or reload the page