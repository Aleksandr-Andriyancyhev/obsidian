---
fast api: 2024-04-16
---
##### Hello world fast api

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
async def root():
    return {"message": "Hello world"}
```

Сохраните файл и запустите приложение с помощью `uvicorn` (в консоли):
`uvicorn main:app --reload` 

Откройте `http://localhost:8000`в вашем веб-браузере, и вы должны увидеть сообщение "Hello World"

Если создать такое приложение:
```python
from fastapi import FastAPI 

my_awesome_api = FastAPI() 

@my_awesome_api.get("/") 
async def root(): 
	return {"message": "Hello World"}
```

То его вызов будет таким: `uvicorn main:my_awesome_api --reload`