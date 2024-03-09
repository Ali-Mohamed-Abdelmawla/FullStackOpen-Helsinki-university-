::: mermaid
sequenceDiagram
    participant browser
    participant server



    browser->>browser:     var note = {content: e.target.elements[0].value, date: new Date()}
    Note right of browser: creating the new note

    browser->>browser:     notes.push(note)
        Note right of browser: pushing the new note into an empty array


    browser->>browser:      redrawNotes()
            Note right of browser: This function is to show the nodes on the page (the previous ones that were fetched from the server, and then the new added ones)


    browser->>browser:         sendToServer(note)
            Note right of browser: This function is to send the added note to the server


    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
        Note right of browser: sending the note to the server
    deactivate server

        Note right of server: The idea here is to take the new input and rerender the list using only javascript then <br> after this we send the data to the server <br> (considering to prevent the default behaviour of submitting the form) <br> and this is how it was added without needing to refresh the page.<br>Also the next time the user refreshes he will find the same data <br> because at the end we sent to the server


:::
