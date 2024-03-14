# Exercises: Part 0
## 0.4: New note diagram
```mermaid
sequenceDiagram
    participant User
    participant Browser
    participant Server
    User->>Browser: types text in the input box of the form
    User->>Browser: submits the form
    Note right of Browser: browser binds the user's input to the name "note"
    Browser->>Server: sends a POST request with the user's input formatted in the URL Encoding standard
    Note right of Server: the server creates a note in its data repository from the user's input
    Server->>Browser: redirects back to the "/notes" page
    Note right of Browser: loads the "/notes" page all over again, which is omitted, since it's not part of this exercise
```

## 0.5: Single page app diagram
```mermaid
sequenceDiagram
  participant Browser
  participant Server
  Browser->>Server: sends a GET request for the HTML page
  Server->>Browser: returns the HTML server
  Note right of Browser: loading the HTML page causes requests for main.css and spa.js
  Browser->>Server: sends a GET request for main.css
  Browser->>Server: sends a GET request for spa.js
  Server->>Browser: returns main.css
  Server->>Browser: returns spa.js
  Note right of Browser: loading spa.js causes a request for data.json
  Browser->>Server: sends a GET request for data.json
  Server->>Browser: returns data.json
  Note right of Browser: spa.js inserts the notes into the HTML document
```

## 0.6: New note in Single page app diagram
```mermaid
sequenceDiagram
    participant User
    participant Browser
    participant Server
    User->>Browser: types text in the input box of the form
    User->>Browser: submits the form
    Note right of Browser: browser binds the user's input to the name "note"
    Browser->>Server: spa.js sends a POST request with the user's input and a timestamp
    Server->>Browser: returns a 201 and a json response, indicating that the note was created succesfully
    Note right of Server: the server creates a note in its data repository from the user's input
    Note right of Browser: spa.js redraws the notes, including the newly created one
```
