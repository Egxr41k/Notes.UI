# Notes

Client side of full stack application, server side [here](https://github.com/Egxr41k/Notes.API)

used only html, css, js

![Preview](https://github.com/Egxr41k/Notes.UI/blob/master/FirstImg.jpg?raw=true)

### CRUD operation realization

Create:

```js
function addNote(title, description) {
    const body = {
        title: title,
        description: description,
        isVisible: true
    }

    fetch('https://egxr41k-notesapi.azurewebsites.net/api/Notes', {
        method: 'POST',
        body: JSON.stringify(body),
        headers: {
            "content-type": "application/json"
        }
    })
    .then(data => data.json())
    .then(() => {
        clearForm();
        getAllNotes();
    });
}
```
Read:

```js
function getNoteById(id){
    fetch(`https://egxr41k-notesapi.azurewebsites.net/api/Notes/${id}`)
    .then(data => data.json())
    .then(responce => displayNoteInForm(responce));
}
```
Update:

```js
function updateNote(id, title, description){
    const body = {
        title: title,
        description: description,
        isVisible: true
    }


    fetch(`https://egxr41k-notesapi.azurewebsites.net/api/Notes/${id}`, {
        method: 'PUT',
        body: JSON.stringify(body),
        headers: {
            "content-type": "application/json"
        }
    })
    .then(data => data.json())
    .then(() => {
        clearForm();
        getAllNotes();
    });
}
```
Delete:

```js
function deleteNote(id) {
    fetch(`https://egxr41k-notesapi.azurewebsites.net/api/Notes/${id}`, {
        method: 'DELETE',
        headers: {
            "content-type": "application/json"
        }
    })
    .then(() => {
        clearForm();
        getAllNotes();
    });
}
```

###@Egxr41k 2023

