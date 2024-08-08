# Welcome to No Devs

For full documentation visit [mkdocs.org](https://www.mkdocs.org).

## code Annotation Examples
## codeblocks
Some `code` goes here 
## plain codeblock
A plain codeblock:
```
some code here
from fastapi import FastAPI,Path
from typing import Optional
from pydantic import BaseModel
app = FastAPI()
students ={
    1:{ "name":"surya",
        "age":19,
        "calss":"Y22"
      }
}

class Student(BaseModel):
    name:str
    age:int
    year:str

class UpdateStudent(BaseModel):
    name: Optional[str]=None
    age: Optional[int]=None
    year:Optional[str]=None

@app.get("/")
def index():
    return {"name": "First Data"}

#path parameter
@app.get("/get-students/{student_id}")
def get_students(student_id:int = Path(...,description="Enter Student ID",gt=0, )):
    return students[student_id]
#Query Parameter
@app.get("/get-by-name/{student_id}")
def get_student(*,student_id:int,name: Optional[str] = None):
    for student_id in students:
        if students[student_id]["name"] == name:
            return students[student_id]
    return {"Data":"Not found"}
@app.post("/create-student/{student_id}")
def create_student(student_id: int, student: Student):
    if student_id in students:
        return {"Error":"Student exists"}
    students[student_id]=student
    return students[student_id]


@app.put("/update-student/{student_id}")
def update_student(student_id: int, student:UpdateStudent):
    if student_id not in students:
        return {"error":"Does not exist"}
    if student.name !=None:
        students[student_id].name=student.name
    if student.age !=None:
        students[student_id].age=student.age
    if student.year !=None:
        students[student_id].year=student.year
    return students[student_id]

@app.delete("/delete-student/{student_id}")
def delete_student(student_id: int):
    if student_id not in students:
        return {"Error":"Student does not exist"}
    
    del students[student_id]
    return {"Message":"Student deleted Sucessfully"}

```
### code for a specific language
Some more code with the `py` at the starts:
```py
import pandas sa pd
```
#### With a title
``` py title="hello.py"
def hello():
    print("hello")
```

#### linenums
``` py title="hello.py" linenums="1"
def hello():
    print("hello")
```
#### highlighting line
``` py title="hello.py" linenums="1" hl_lines="2 3"
def hello():
    print("hello")
```

## Icons and Emojs
:smile:

:fontawesome-regular-face-laugh-wink:
:fontawesome-brands-twitter:{ .twitter }