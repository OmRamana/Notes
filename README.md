# Notes
Making queries to django models

(venv) C:\Users\keanu\django\filter\fil>python manage.py shell
Python 3.10.2 (tags/v3.10.2:a58ebcc, Jan 17 2022, 14:12:15) [MSC v.1929 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
(InteractiveConsole)
>>> from filter.models import Book
>>> from filter.models import Author
>>> Author.objects.all()
<QuerySet [<Author: Author object (1)>, <Author: Author object (2)>, <Author: Author object (3)>]>
>>> Author.objects.all()[0]
<Author: Author object (1)>
>>> Author.objects.all()[0].name
'om'
>>> for a in Author.objects.all():
... print(a.name)
  File "<console>", line 2
    print(a.name)
    ^^^^^
IndentationError: expected an indented block after 'for' statement on line 1
>>> for a in Author.objects.all():
...   print(a.name)
...
om
brad
tom
>>>
  
  
