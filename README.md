# Eliza chatbot in Python

Loosely based on Charles Hayden's version in Java, at http://chayden.net/eliza/Eliza.html.

I feel that it is fairly complete. However there are some holes, as the library was written immediately prior to my discovery of Joseph Weizenbaum's own description of the original program, which is quite detailed, along with the original "doctor" script. Oh well. A copy of that article is provided in the repo as a reference to the correct behavior.

## Usage

Before running the chatbot, you need to download the spaCy language model:

```
$ python -m spacy download en_core_web_sm
```

You should also create a Python virtual environment and install the dependencies using `requirements.txt`:

```
$ python -m venv venv
$ source venv/bin/activate  # On Windows use `venv\Scripts\activate`
$ pip install -r requirements.txt
```

Can be run interactively:

```
$ python elizaNew.py

or

$ python elizaOG.py

How do you do.  Please tell me your problem.
> I would like to have a chat bot.
You say you would like to have a chat bot ?
> bye
Goodbye.  Thank you for talking to me.
```

...or imported and used as a library:

```python
import eliza

eliza = eliza.Eliza()
eliza.load('doctorNew.txt') # for improved Eliza ('doctorOG.txt' otherwise)

print(eliza.initial())
while True:
    said = input('> ')
    response = eliza.respond(said)
    if response is None:
        break
    print(response)
print(eliza.final())
```
