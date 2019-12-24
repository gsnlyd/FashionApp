# FashionApp

A demo outfit-building application which uses outputs from a deep neural network to recommend compatible items.

### Setup

This application uses items from the Polyvore dataset, a popular outfit dataset. It also uses masked embeddings generated via the FashionEmbed repository.

The following files/directories are expected by the application:

- `/static/images` - Images from the Polyvore dataset.
- `/data/categories.csv` - Categories from the Polyvore dataset.
- `/data/item_metadata.json` - Item metadata from the Polyvore dataset.
- `/data/embeddings/` - A directory containing masked embeddings as output by the savemasks.py script from FashionEmbed. Four sets of masked embeddings, as well as the full embeddings, are expected.
- `config.json` - A config file containing database login information and a secret key. An empty config will be generated when the application is run for the first time.

A MySQL or MySQL-compatible database is also required.

### Usage

First, run the application as a script. This will create database tables, load the items into the database, and build indexes for nearest neighbor search. This will take a few minutes.

If you have not supplied a `config.json`, an empty one will be generated automatically. Fill it out and run the script again.

```
python app.py
```

Then start the application as a Flask app.

```
export FLASK_APP=app.py
flask run
```
