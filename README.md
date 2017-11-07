# Python Pyrus API client

The Pyrus API provides a python 3 implementation of core API methods. 

To get started, you must do the following:

## Getting Started

* instal pyrus-api library using pip:

````
$ pip install pyrusAPI
````

* Import packages into your project:

```python   
from pyrus import client
import pyrus.models
```
* Create API client:

```python
pyrus_client = client.PyrusAPI(login='login@pyrus.com', security_key='sadf2R5Wrdkn..')
```

* Perform authorization:

```python
auth_response = pyrus_client.auth()
```

## Forms

* Get all form templates:

```python
forms_response = pyrus_client.forms()
forms = forms_response.forms
```

* Get tasks list by form template:

```python
request = pyrus.models.requests.FormRegisterRequest(
        include_archive=True,
        steps=[1,2],
        filters=[pyrus.models.entities.EqualsFilter(1, "hello world")])
form_register_response = pyrus_client.get_registry(forms[0].id, request)
tasks = form_register_response.tasks
```

## Tasks

* Get task with all comments:

```python
task = pyrus_client.get_task(tasks[0].id).task
```

* Add task comment:

```python
request = pyrus.models.requests.TaskCommentRequest(text="hello", action="finished")
task = pyrus_client.comment_task(tasks[0].id, request).task
```

* Create a task:

```python
request = CreateTaskRequest(
        text="Task from python client", 
        participants=['colleague@email.com', 10196]
        attachments = ['BEFCE22E-AEFF-4771-83D4-2A4B78FB05C6'])
task = pyrus_client.create_task(request).task
```

## Files

* Upload a file:

```python
response = myclient.upload_file('C:\\path\\to\\file.txt').guid
```

## Catalogs

* Get catalog with all items:
    
```python
catalog_id = 1525
catalog_response = pyrus_client.get_catalog(catalog_id)
items = catalog_response.items
```

## Contacts

* Get all available contacts:

```python    
contacts = pyrus_client.get_contacts()
```

## Support

If you have any questions or comments please send an email to support@pyrus.com
