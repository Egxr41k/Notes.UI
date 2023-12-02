# Notes.UI

This note manager allows you to add, edit, delete, share your notes, and open other people's notes via links. You can only read notes that you have not created.
Client-side of full-stack application, server-side [here](https://github.com/Egxr41k/Notes.API)

used HTML, CSS, JS

![Preview](https://github.com/Egxr41k/Notes.UI/blob/master/FirstImg.jpg?raw=true)

##Todo
1. ~~Base CRUD-methods~~
2. ~~Publish to github.pages~~
3. Dark mode/Theme switcher
4. Add Account and Settings Page


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
    .then(response => displayNoteInForm(response));
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

