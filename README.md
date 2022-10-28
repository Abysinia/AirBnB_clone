# AIRBNB project

<img src="./image/hbnb.png" width="100%" style="max-width: 300px; background: #fff;"/>
## Background Context

## Welcome to the AirBnB clone project!

## First step: Write a command interpreter to manage your AirBnB objects.

### This is the first step towards building your first full web application: the AirBnB clone. This first step is very important because you will use what you build during this project with all other following projects: HTML/CSS templating, database storage, API, front-end integration..

### Each task is linked and will help you to:
- put in place a parent class (called BaseModel) to take care of the initialization, serialization and deserialization of your future instances
- create a simple flow of serialization/deserialization: Instance <-> Dictionary <-> JSON string <-> file
- create all classes used for AirBnB (User, State, City, Place…) that inherit from BaseModel
- create the first abstracted storage engine of the project: File storage.
- create all unittests to validate all our classes and storage engine

## What's a command interpreter?

### Do you remember the Shell? It’s exactly the same but limited to a specific use-case. In our case, we want to be able to manage the objects of our project:

- Create a new object (ex: a new User or a new Place)
- Retrieve an object from a file, a database etc.
- Do operations on objects (count, compute stats, etc...)
- Update attributes of an object
- Destroy an object

### Learning Objectives

#### At the end of this project, you are expected to be able to explain to anyone, without the help of Google:

## General
- How to create a Python package
- ow to create a command interpreter in Python using the cmd module
- What is Unit testing and how to implement it in a large project
- How to serialize and deserialize a Class
- How to write and read a JSON file
- How to manage datetime
- What is an UUID
- What is *args and how to use it
- What is **kwargs and how to use i
- How to handle named arguments in a function

## usage
- ./console.py to run 
- quit to ext the shell

### Console Commands

The HolbertonBnB console supports the following commands:

* **create**
  * Usage: `create <class>`

Creates a new instance of a given class. The class' ID is printed and 
the instance is saved to the file `file.json`.

```
$ ./console.py
(hbnb) create BaseModel
efcc8fb6-e10c-4543-a7ac-1c047dca37a7
(hbnb) quit
$ cat file.json ; echo ""
{"BaseModel.efcc8fb6-e10c-4543-a7ac-1c047dca37a7": {"updated_at": "2022-10-27T20:56:08.691287", "created_at": "2022-10-27T20:56:08.691287", "__class__": "Base
Model", "id": "efcc8fb6-e10c-4543-a7ac-1c047dca37a7"}}
```

* **show**
  * Usage: `show <class> <id>` or `<class>.show(<id>)`

Prints the string representation of a class instance based on a given id.

```
$ ./console.py
(hbnb) create User
8d5d54fd-70d3-4d10-9d01-d1d43ed3a66a
(hbnb)
(hbnb) show User 8d5d54fd-70d3-4d10-9d01-d1d43ed3a66a
[User] (8d5d54fd-70d3-4d10-9d01-d1d43ed3a66a) {'id': '8d5d54fd-70d3-4d10-9d01-d1d43ed3a66a', 'created_at': datetime.datetime(2022-10-27T21:09:59.202247), 
'updated_at': datetime.datetime(2022-10-27T21:09:59.202247)}
(hbnb) 
(hbnb) User.show(8d5d54fd-70d3-4d10-9d01-d1d43ed3a66a)
[User] (8d5d54fd-70d3-4d10-9d01-d1d43ed3a66a) {'id': '8d5d54fd-70d3-4d10-9d01-d1d43ed3a66a', 'created_at': datetime.datetime(2022-10-27T21:09:59.202247), 
'updated_at': datetime.datetime(2022-10-27T21:09:59.202247)}
(hbnb) 
```
* **destroy**
  * Usage: `destroy <class> <id>` or `<class>.destroy(<id>)`

Deletes a class instance based on a given id. The storage file `file.json` 
is updated accordingly.

```
$ ./console.py
(hbnb) create State
efcc8fb6-e10c-4543-a7ac-1c047dca37a7
(hbnb) create Place
85f3ca3e-6dcd-4f4b-bc2a-6cac7a73b9a5
(hbnb)
(hbnb) destroy State efcc8fb6-e10c-4543-a7ac-1c047dca37a7
(hbnb) Place.destroy(85f3ca3e-6dcd-4f4b-bc2a-6cac7a73b9a5)
(hbnb) quit
$ cat file.json ; echo ""
{}
```

* **all**
  * Usage: `all` or `all <class>` or `<class>.all()`

Prints the string representations of all instances of a given class. If no 
class name is provided, the command prints all instances of every class.

```
$ ./console.py
(hbnb) create BaseModel
5aeb1b4b-029f-498d-8813-3c5298f6ffe6
(hbnb) create BaseModel
138430f6-3d8c-45cd-b65b-233d3be90043
(hbnb) create User
672f59a7-a256-44b6-abf8-c21236fcd4cc
(hbnb) create User
e4caab94-7c30-41f2-a888-7e79654555ae
(hbnb)
(hbnb) all BaseModel
["[BaseModel] (5aeb1b4b-029f-498d-8813-3c5298f6ffe6) {'id': '5aeb1b4b-029f-498d-8813-3c5298f6ffe6', 'created_at': datetime.datetime(2022, 10, 27, 21, 13, 47, 1277), 'updated_at': datetime.datetime(2022, 10, 27, 21, 13, 47, 1277)}", "[BaseModel] (138430f6-3d8c-45cd-b65b-233d3be90043) {'id': '138430f6-3d8c-45cd-b65b-233d3be90043', 'created_at': datetime.datetime(2022, 10, 27, 21, 14, 4, 590996), 'updated_at': datetime.datetime(2022, 
10, 27, 21, 14, 4, 590996)}"]
(hbnb)
(hbnb) User.all()
["[User] (8d5d54fd-70d3-4d10-9d01-d1d43ed3a66a) {'id': '8d5d54fd-70d3-4d10-9d01-d1d43ed3a66a', 'created_at': datetime.datetime(2022, 10, 27, 21, 
9, 59, 202247), 'updated_at': datetime.datetime(2022, 10, 27, 21, 9, 59, 202247)}", "[User] (672f59a7-a256-44b6-abf8-c21236fcd4cc) {'id': '672f59a7-a256-44b6-abf8-c21236fcd4cc', 'created_at': datetime.datetime(2022, 10, 27, 21, 14, 19, 358356), 'updated_at': datetime.datetime(2022, 10, 27, 21, 14, 19, 358356)}", "[User] (e4caab94-7c30-41f2-a888-7e79654555ae) {'id': 'e4caab94-7c30-41f2-a888-7e79654555ae', 'created_at': datetime.datetime(2022, 10, 27, 21, 14, 32, 166378), 'updated_at': datetime.datetime(2022, 10, 27, 21, 14, 32, 166378)}"]
(hbnb) 
(hbnb) all
["[State] (f93d7ff3-1435-4682-ad8e-abe66db77b9e) {'id': 'f93d7ff3-1435-4682-ad8e-abe66db77b9e', 'created_at': datetime.datetime(2022, 10, 27, 20, 56, 3, 571019), 'updated_at': datetime.datetime(2022, 10, 27, 20, 56, 3, 571019)}", "[State] (57dc2f3f-bec6-4aca-bdc6-b50eefdc6c0e) {'id': '57dc2f3f-bec6-4aca-bdc6-b50eefdc6c0e', 'created_at': datetime.datetime(2022, 10, 27, 20, 56, 8, 691287), 'updated_at': datetime.datetime(2022, 10, 27, 20, 56, 8, 691287)}", "[State] (efcc8fb6-e10c-4543-a7ac-1c047dca37a7) {'id': 'efcc8fb6-e10c-4543-a7ac-1c047dca37a7', 'created_at': datetime.datetime(2022, 10, 27, 20, 59, 32, 48275), 'updated_at': datetime.datetime(2022, 10, 27, 20, 59, 32, 48275), 'Test': '1234'}", "[User] (8d5d54fd-70d3-4d10-9d01-d1d43ed3a66a) {'id': '8d5d54fd-70d3-4d10-9d01-d1d43ed3a66a', 'created_at': datetime.datetime(2022, 10, 27, 21, 9, 59, 202247), 'updated_at': datetime.datetime(2022, 10, 27, 21, 9, 59, 202247)}", "[Place] (85f3ca3e-6dcd-4f4b-bc2a-6cac7a73b9a5) {'id': '85f3ca3e-6dcd-4f4b-bc2a-6cac7a73b9a5', 'created_at': datetime.datetime(2022, 10, 27, 21, 13, 13, 540361), 'updated_at': datetime.datetime(2022, 10, 27, 21, 13, 13, 540361)}", "[BaseModel] (5aeb1b4b-029f-498d-8813-3c5298f6ffe6) {'id': '5aeb1b4b-029f-498d-8813-3c5298f6ffe6', 'created_at': datetime.datetime(2022, 10, 27, 21, 13, 47, 1277), 'updated_at': datetime.datetime(2022, 10, 27, 21, 13, 47, 1277)}", "[BaseModel] (138430f6-3d8c-45cd-b65b-233d3be90043) {'id': '138430f6-3d8c-45cd-b65b-233d3be90043', 'created_at': datetime.datetime(2022, 10, 27, 21, 14, 4, 590996), 'updated_at': datetime.datetime(2022, 10, 27, 21, 14, 4, 590996)}", "[User] (672f59a7-a256-44b6-abf8-c21236fcd4cc) {'id': '672f59a7-a256-44b6-abf8-c21236fcd4cc', 'created_at': datetime.datetime(2022, 10, 27, 21, 14, 19, 358356), 'updated_at': datetime.datetime(2022, 10, 27, 21, 14, 19, 358356)}", "[User] (e4caab94-7c30-41f2-a888-7e79654555ae) {'id': 'e4caab94-7c30-41f2-a888-7e79654555ae', 'created_at': datetime.datetime(2022, 10, 27, 21, 14, 32, 166378), 'updated_at': datetime.datetime(2022, 10, 27, 21, 14, 32, 166378)}"]
(hbnb) 
```

* **count**
  * Usage: `count <class>` or `<class>.count()`

Retrieves the number of instances of a given class.

```
$ ./console.py
(hbnb) create Place
5e6889ba-afa1-45e6-819e-34029bbc7202
(hbnb) create Place
b551af95-3607-4b3d-afc4-ac529ebb8251
(hbnb) create City
e2b35055-63f0-41c9-8801-4847b31cd556
(hbnb) 
(hbnb) count Place
3
(hbnb) city.count()
1
(hbnb) 
```

* **update**
  * Usage: `update <class> <id> <attribute name> "<attribute value>"` or
`<class>.update(<id>, <attribute name>, <attribute value>)` or `<class>.update(
<id>, <attribute dictionary>)`.

Updates a class instance based on a given id with a given key/value attribute 
pair or dictionary of attribute pairs. If `update` is called with a single 
key/value attribute pair, only "simple" attributes can be updated (ie. not 
`id`, `created_at`, and `updated_at`). However, any attribute can be updated by 
providing a dictionary.

```
$ ./console.py
(hbnb) create User
913a0b69-b324-4d5c-a405-ec17e9baa557
(hbnb)
(hbnb) update User 913a0b69-b324-4d5c-a405-ec17e9baa557 name "Alx AirBnB project"
(hbnb) show User 913a0b69-b324-4d5c-a405-ec17e9baa557
[User] (913a0b69-b324-4d5c-a405-ec17e9baa557) {'id': '913a0b69-b324-4d5c-a405-ec17e9baa557', 'created_at': datetime.datetime(2022, 10, 27, 21, 17, 48, 657947), 'updated_at': datetime.datetime(2022, 10, 27, 21, 17, 48, 657947), 'name': 'Alx AirBnB project'}
(hbnb)
(hbnb) User.update(913a0b69-b324-4d5c-a405-ec17e9baa557, team, "Yilkal Desta and Bright Uzosike")
(hbnb) User.show(913a0b69-b324-4d5c-a405-ec17e9baa557)
[User] (913a0b69-b324-4d5c-a405-ec17e9baa557) {'id': '913a0b69-b324-4d5c-a405-ec17e9baa557', 'created_at': datetime.datetime(2022, 10, 27, 21, 17, 48, 657947), 'updated_at': datetime.datetime(2022, 10, 27, 21, 17, 48, 657947), 'name': 'Alx AirBnB project', 'team': 'Yilkal Desta and Bright Uzosike'}
(hbnb)
(hbnb) User.update(913a0b69-b324-4d5c-a405-ec17e9baa557, {'email': 'holberton@h
olberton.com', 'last_name': 'School'})
[User] (913a0b69-b324-4d5c-a405-ec17e9baa557) {'id': '913a0b69-b324-4d5c-a405-ec17e9baa557', 'created_at': datetime.datetime(2022, 10, 27, 21, 17, 48, 657947), 'updated_at': datetime.datetime(2022, 10, 27, 21, 17, 48, 657947), 'name': 'Alx AirBnB project', 'team': 'Yilkal Desta and Bright Uzosike', 'start_date': 'Oct 23, 2022', 'end_date': 'Oct 30, 2022'}
(hbnb) 
```

## Authors
- Yilkal Desta
- Bright Uzosike
