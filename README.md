# Brincando com Django REST Framework

## Seguindo passo a passo os tutoriais do site oficial: https://www.django-rest-framework.org/

Instalação das dependências.

Ubuntu
´´´sh
python3 -m virtualenv venv
source venv/bin/activate
pip install -r requirements.txt
´´´

Windows
'''sh
python -m virtualenv venv
./venv/Scripts/activate
pip install -r requirements.txt
'''

Execução de projetos.
'''sh
cd tutorial

python manage.py makemigrations
python manage.py migrate
'''

inserção de dados de teste.
'''sh
python manage.py shell
>>> from snippets.models import Snippet
>>> from snippets.serializers import SnippetSerializer
>>> from rest_framework.renderers import JSONRenderer
>>> from rest_framework.parsers import JSONParser
>>> snippet = Snippet(code='foo = "bar"\n')
>>> snippet.save()
>>> snippet = Snippet(code='print("hello, world")\n')
>>> snippet.save()
'''

Consultando dados:
'''sh
http http://127.0.0.1:8000/snippets/
'''

Resultado:
'''json
HTTP/1.1 200 OK
Content-Length: 234
Content-Type: application/json      
Date: Mon, 13 Apr 2020 15:47:23 GMT 
Server: WSGIServer/0.2 CPython/3.7.7
X-Content-Type-Options: nosniff     
X-Frame-Options: DENY

[
    {
        "code": "foo - \"bar\"\n",  
        "id": 1,
        "language": "python",
        "linenos": false,
        "style": "friendly",
        "title": ""
    },
    {
        "code": "print(\"hello world!\")\n",
        "id": 2,
        "language": "python",
        "linenos": false,
        "style": "friendly",
        "title": ""
    }
]
'''

Consultando um registro.
'''sh
http http://127.0.0.1:8000/snippets/2
'''

Resultado:
'''json
HTTP/1.1 200 OK
Content-Length: 120
Content-Type: application/json
Date: Mon, 13 Apr 2020 15:49:14 GMT
Server: WSGIServer/0.2 CPython/3.7.7
X-Content-Type-Options: nosniff
X-Frame-Options: DENY

{
    "code": "print(\"hello world!\")\n",
    "id": 2,
    "language": "python",
    "linenos": false,
    "style": "friendly",
    "title": ""
}
'''