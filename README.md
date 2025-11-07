Goodbye Things
==============

I use the code in this project to **reduce the time it takes to post an eBay listing** for the things I no longer want or need.

The name is a hat tip to the book [Goodbye, Things] by Fumio Sasaki.

[Goodbye, Things]: https://www.penguin.co.uk/books/305840/goodbye-things-by-sasaki-fumio/9780141986388

## Getting setup

You run Goodbye Things by running the `./gbt` script, which lives in the project's directory. If you haven't already done so, clone the project to your computer:

    git clone https://github.com/gma/goodbye-things
    cd goodbye-things

`gbt` uses some software called Playwright to control a web browser, filling in eBay's forms for creating a listing. In short, `gbt` will:

- read a text file (that you created) describing your item, how much it costs, etc
- login to your eBay account
- use the information in the text file to fill out the "Create listing" pages on eBay's site

You'll need to install Playwright first. Start by creating a virtual environment:

```sh
python3 -m venv .venv
source .venv/bin/activate
```

Now we can install Playwright's Python code, and a browser that Playwright will use to navigate eBay's site:

```sh
pip install pip-tools
pip-sync requirements.txt
playwright install firefox
```

## Run the tests locally

You need to get everything installed, then the tests should pass. Start by creating a virtual environment:

```sh
python3 -m venv .venv
source .venv/bin/activate
```

Now we can install our development tools:

```sh
pip install --upgrade pip
pip install pip-tools
pip-sync dev-requirements.txt
```

The dev tools included in the template are sufficient to be able to run the linter, type checker, and tests. They're all run by this script:

```sh
./test
```

## Adding dependencies

Once you've got non-development dependencies you can specify them in `requirements.in`, running these commands to install them alongside your development dependencies:

```sh
pip-compile requirements.in
pip-sync requirements.txt dev-requirements.txt
```

If you want to add more development tools, add them to `dev-requirements.in` and run:

```sh
pip-compile dev-requirements.in
pip-sync requirements.txt dev-requirements.txt
```
