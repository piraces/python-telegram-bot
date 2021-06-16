# Simple Python Telegram bot template

This repository contains all you may need to bootstrap your new Telegram bot in Python.
It makes use of the awesome [`python-telegram-bot`](https://github.com/python-telegram-bot/python-telegram-bot) library, 
and a [basic example](https://github.com/python-telegram-bot/python-telegram-bot/blob/master/examples/echobot.py) 
from the official repository.

# Getting started

Just tap on the **"Use this template"** button in the top toolbar of the repository and introduce the details of the project
you want to create.

After that, you only need to clone your own repository and make all the modifications you need.

# What is included?

Just the essentials.

## A fully functional example bot

This template includes an example in the directory `/src` containing the [`echobot.py` example from the official 
repository](https://github.com/python-telegram-bot/python-telegram-bot/blob/master/example).
This bot will simply reply to each text message with a message that contains the same text.

## A Dockerfile

A simple `Dockerfile` is provided for creating a container for the bot.
This `Dockerfile` only builds a simple container using the 
[official `python` base image](https://hub.docker.com/_/python) and a few commands to install the requirements for the 
bot project, copy the source files and establish the bot token as an 
[environment variable](https://en.wikipedia.org/wiki/Environment_variable).

🛑 **Note**: this `Dockerfile` uses as base the **latest** version of the Python docker image, which will change 
in the future. In order to make your container more stable, change the tag to a specific version, which will ensure no 
possible breaking changes.
For example, if you want to stick with `Python 3.9`:
```dockerfile
# set base image (host OS)
FROM python:3.9

# Rest of the file...
```

## A `requirements.txt` file

This file contains all dependencies for the bot project.
For the template and the basic behaviour of the bot, only the package `python-telegram-bot` is needed.

You can just run this command in order to get dependencies installed:
```shell
pip install -r requirements.txt
```

🛑 **Note**: the version number for the package **is not being set**. This will cause downloading always the latest version 
of the package. If you don't want this behaviour, please modify the `requirements.txt` file to set it.
For example:
```text
python-telegram-bot==13.6
```

# Configuring your new bot

The only thing you need to get started with bots in Telegram is an account and to talk to 
[BotFather](https://t.me/BotFather). This bot will provide you instructions to create a new bot, and at the end will
provide you **a token**.

You will need this token and keep it secret (**don't ever commit it to GitHub or make it public in any way**).
Once you have this token, you can set it to the bot via an 
[environment variable](https://en.wikipedia.org/wiki/Environment_variable) or directly in code.

## Setting the token as an environment variable

If using the `Dockerfile` substitute the line `ENV TOKEN=""` with your token inside the double quotes.
For example:
```dockerfile
# ... previous file content

# set the token for the telegram bot
ENV TOKEN="mysupersecrettoken"

# Rest of the file...
```

If running your code directly from the terminal, declare the environment variable `TOKEN` with your token as its 
value.
For example, in Linux or macOS:
```shell
export TOKEN="mysupersecrettoken"
```

Or in Windows (Powershell):
```powershell
$env:Token = 'mysupersecrettoken'
```

## Setting the token inside the code

Search in the `main.py` file for the `PUT_YOUR_TOKEN_HERE` word (it is in the `main` method).
As you can see, the program will attempt to load the token from an environment variable named `TOKEN`.
Nevertheless, if this environment variable does not exist, the second parameter will be used by default.

If you change that second parameter, the bot will get the correct token directly from the code 
(just ensure the is no environment variable named `TOKEN` created).

🛑 **Note**: if using the provided `Dockerfile`, comment out the line starting with `ENV` since it will set the 
environment variable to an empty string, which will cause your bot to fail starting.
