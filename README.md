# animalgessinggame
#  Learn AI — Animal Guessing Game

Une application web interactive, **dockerisée** et développée avec **Flask**, combinant **intelligence artificielle** et **jeux éducatifs** autour de la classification et de la génération d’images.

Ce projet a été réalisé dans le cadre du **projet TDLOG** par  
**Max Castres Saint-Martin, Maxime Muhlethaler et Titouan Pottier**.  

---

##  Objectifs

L’objectif initial était d’explorer les **modèles génératifs et de classification d’images** afin de créer un ensemble de **jeux éducatifs basés sur l’IA** :

- Générer des images (ex. animaux, chiffres) avec un **Variational Autoencoder (VAE)**.  
- Classifier ces images parmi **plus de 90 classes** à l’aide d’un modèle fine-tuné sur ImageNet.  
- Intégrer ces fonctionnalités dans une **application web interactive**, fluide et esthétique, pensée pour l’apprentissage ludique.

---

##  Fonctionnalités principales

###  1. Animal Guessing Game
- Une image d’animal est affichée.  
- Le joueur doit deviner l’espèce.  
- Le **classifieur ResNet18 fine-tuné** vérifie la réponse parmi **90 animaux**.  
- Trois modes de jeu :  
  - *Classique* (10 animaux)  
  - *Étendu* (90 animaux)  
  - *Contre-la-montre* (deviner un maximum d’animaux en 1 minute).

###  2. Number Guessing Game
- Utilise la base **MNIST** (écriture manuscrite de chiffres).  
- Le joueur doit écrire le nombre affiché (en lettres, en français ou en anglais).  
- Les chiffres sont soit **réels (MNIST)**, soit **générés par un VAE entraîné**.

###  3. IA ou pas IA
- Le joueur doit déterminer si une image est **humaine** ou **générée par IA**.  
- Deux variantes :  
  - Images de chiffres (réels vs générés par VAE)  
  - Images d’art ou d’objets (réels vs générés via un modèle texte→image).

###  4. Système de scoring et base de données
- Authentification via **Flask-Login** (comptes utilisateurs, hash des mots de passe, sessions sécurisées).  
- Scores enregistrés dans une **base SQL**.  
- Affichage du **Top 10** des meilleurs scores pour chaque jeu.

###  5. Interface utilisateur
- Interface web responsive : **HTML / CSS / JavaScript**.  
- Sons, raccourcis clavier et animations pour une expérience fluide.  
- Design coloré et intuitif pensé pour un public jeune.

---

##  Partie Intelligence Artificielle

###  1. Classification
- Modèle : **ResNet18 pré-entraîné sur ImageNet**.  
- Technique : **Fine-tuning** sur 10 puis 90 classes d’animaux.  
- Outils : PyTorch, torchvision.  
- Précision obtenue : **95–99 % sur le jeu de test**.

### 🪄 2. Génération d’images (VAE)
- Modèle : **Variational Autoencoder (VAE)** entraîné sur un sous-ensemble d’images d’animaux et sur MNIST.  
- But : générer de nouvelles images à partir d’un espace latent bruité.  
- Architecture : encodeur convolutionnel, décodeur probabiliste, régularisation par divergence KL.  
- Résultats :  
  - Sur MNIST → génération nette et diversifiée.  
  - Sur animaux → résultats plausibles mais flous (structure encore incomplète).  

### ⚗️ 3. Débruiteur / Diffusion latente
- Expérimentations de **diffusion dans l’espace latent** du VAE (bruit progressif, reconstruction inverse).  
- Permet de visualiser la continuité entre bruit et structure reconstruite.  
- Sert de base conceptuelle à de futurs modèles hybrides (VAE + Diffusion).

## 🧪 Tests et intégration continue

Des **tests unitaires** sont fournis pour :
- `concat()` → conversion d’un entier en chaîne littérale.  
- `distance_levenstein()` → comparaison entre mots écrits et attendus.  
- `classifie_animals10()` → vérification du modèle de classification simplifié.

Les tests sont intégrés à une **pipeline GitHub Actions** avec vérification automatique du code (CI/CD).

---

## 🐳 Déploiement Docker

L’application est entièrement **conteneurisée** et prête à être lancée sur n’importe quel environnement compatible Docker.

##  Objectif éducatif
Le projet a été conçu pour initier les enfants et adolescents aux principes fondamentaux de l’intelligence artificielle :
- Reconnaissance d’images (classification).
- Génération de contenu (VAE).
- Différenciation entre réel et synthétique (IA ou pas IA).
L’approche est volontairement ludique, interactive et visuelle, afin de rendre l’IA plus accessible et compréhensible.

##  Références techniques
- Kingma D, Welling M. Auto-Encoding Variational Bayes. arXiv, 2014.
- He K, Zhang X, Ren S, Sun J. Deep Residual Learning for Image Recognition. arXiv, 2015.
- Ho J, Jain A, Abbeel P. Denoising Diffusion Probabilistic Models. arXiv, 2020.

# 🧠 Learn AI — Animal Guessing Game

An interactive **Dockerized web application** built with **Flask**, combining **artificial intelligence** and **educational games** around image classification and generation.

This project was developed as part of the **TDLOG course** by  
**Max Castres Saint-Martin, Maxime Muhlethaler, and Titouan Pottier**.  

---

## 🎯 Objectives

The main goal was to explore **image classification and generative models** to create a collection of **AI-based educational games**:

- Generate images (e.g., animals, digits) using a **Variational Autoencoder (VAE)**.  
- Classify these images into **more than 90 classes** using a fine-tuned model on ImageNet.  
- Integrate these components into a **smooth, visually appealing, and interactive web app** designed for playful learning.

---

## 🧩 Main Features

### 🐾 1. Animal Guessing Game
- An animal image is displayed.  
- The player must guess the species.  
- A **fine-tuned ResNet18 classifier** checks the answer among **90 animal classes**.  
- Three game modes:  
  - *Classic* (10 animals)  
  - *Extended* (90 animals)  
  - *Time Attack* (guess as many animals as possible in one minute).

### 🔢 2. Number Guessing Game
- Uses the **MNIST** handwritten digit dataset.  
- The player writes the number shown (in words, in French or English).  
- Digits can be either **real (MNIST)** or **generated by a trained VAE**.

### 🤖 3. AI or Not AI
- The player must decide whether an image is **human-made** or **AI-generated**.  
- Two variants:  
  - Digit images (real vs VAE-generated)  
  - Art or object images (real vs text-to-image model generated).

### 🏆 4. Scoring System & Database
- Authentication via **Flask-Login** (user accounts, password hashing, secure sessions).  
- Scores are stored in a **SQL database**.  
- A **Top 10 leaderboard** is displayed for each game mode.

### 🎨 5. User Interface
- Fully responsive web design using **HTML / CSS / JavaScript**.  
- Sounds, keyboard shortcuts, and animations ensure a smooth experience.  
- A colorful, intuitive interface tailored for a younger audience.

---

## 🧠 Artificial Intelligence Components

### 📚 1. Image Classification
- Model: **ResNet18 pre-trained on ImageNet**.  
- Technique: **Fine-tuning** on 10 and then 90 animal classes.  
- Tools: PyTorch, torchvision.  
- Achieved accuracy: **95–99 % on the test set**.

### 🪄 2. Image Generation (VAE)
- Model: **Variational Autoencoder (VAE)** trained on a subset of animal images and on MNIST.  
- Goal: generate new images from a noisy latent space.  
- Architecture: convolutional encoder, probabilistic decoder, KL divergence regularization.  
- Results:  
  - On MNIST → clear and diverse generations.  
  - On animal datasets → plausible but somewhat blurry outputs (incomplete structure).

### ⚗️ 3. Latent Denoising / Diffusion
- Experiments on **diffusion in the VAE latent space** (progressive noise and reverse reconstruction).  
- Allows visualizing continuity between random noise and structured images.  
- Serves as a conceptual foundation for future **hybrid models (VAE + Diffusion)**.

---

## 🧪 Testing and Continuous Integration

Unit tests are provided for:
- `concat()` → conversion of an integer into its word representation.  
- `distance_levenstein()` → comparison between written and expected words.  
- `classifie_animals10()` → verification of the simplified animal classifier.

All tests are integrated into a **GitHub Actions pipeline** for automatic CI/CD validation.

---

## 🐳 Docker Deployment

The entire application is **containerized** and can be launched on any Docker-compatible environment.


## Docker Quickstart

This app can be run completely using `Docker` and `docker-compose`. **Using Docker is recommended, as it guarantees the application is run using compatible versions of Python and Node**.

There are three main services:

To run the development version of the app

```bash
docker-compose up flask-dev
```

To run the production version of the app

```bash
docker-compose up flask-prod
```

The list of `environment:` variables in the `docker-compose.yml` file takes precedence over any variables specified in `.env`.

To run any commands using the `Flask CLI`

```bash
docker-compose run --rm manage <<COMMAND>>
```

Therefore, to initialize a database you would run

```bash
docker-compose run --rm manage db init
docker-compose run --rm manage db migrate
docker-compose run --rm manage db upgrade
```

A docker volume `node-modules` is created to store NPM packages and is reused across the dev and prod versions of the application. For the purposes of DB testing with `sqlite`, the file `dev.db` is mounted to all containers. This volume mount should be removed from `docker-compose.yml` if a production DB server is used.

Go to `http://localhost:8080`. You will see a pretty welcome screen.

### Running locally

Run the following commands to bootstrap your environment if you are unable to run the application using Docker

```bash
cd animalguessinggame
pip install -r requirements/dev.txt
npm install
npm run-script build
npm start  # run the webpack dev server and flask server using concurrently
```

Go to `http://localhost:5000`. You will see a pretty welcome screen.

#### Database Initialization (locally)

Once you have installed your DBMS, run the following to create your app's
database tables and perform the initial migration

```bash
flask db init
flask db migrate
flask db upgrade
```

## Deployment

When using Docker, reasonable production defaults are set in `docker-compose.yml`

```text
FLASK_ENV=production
FLASK_DEBUG=0
```

Therefore, starting the app in "production" mode is as simple as

```bash
docker-compose up flask-prod
```

If running without Docker

```bash
export FLASK_ENV=production
export FLASK_DEBUG=0
export DATABASE_URL="<YOUR DATABASE URL>"
npm run build   # build assets with webpack
flask run       # start the flask server
```

## Shell

To open the interactive shell, run

```bash
docker-compose run --rm manage shell
flask shell # If running locally without Docker
```

By default, you will have access to the flask `app`.

## Running Tests/Linter

To run all tests, run

```bash
docker-compose run --rm manage test
flask test # If running locally without Docker
```

To run the linter, run

```bash
docker-compose run --rm manage lint
flask lint # If running locally without Docker
```

The `lint` command will attempt to fix any linting/style errors in the code. If you only want to know if the code will pass CI and do not wish for the linter to make changes, add the `--check` argument.

## Migrations

Whenever a database migration needs to be made. Run the following commands

```bash
docker-compose run --rm manage db migrate
flask db migrate # If running locally without Docker
```

This will generate a new migration script. Then run

```bash
docker-compose run --rm manage db upgrade
flask db upgrade # If running locally without Docker
```

To apply the migration.

For a full migration command reference, run `docker-compose run --rm manage db --help`.

If you will deploy your application remotely (e.g on Heroku) you should add the `migrations` folder to version control.
You can do this after `flask db migrate` by running the following commands

```bash
git add migrations/*
git commit -m "Add migrations"
```

Make sure folder `migrations/versions` is not empty.

## Asset Management

Files placed inside the `assets` directory and its subdirectories
(excluding `js` and `css`) will be copied by webpack's
`file-loader` into the `static/build` directory. In production, the plugin
`Flask-Static-Digest` zips the webpack content and tags them with a MD5 hash.
As a result, you must use the `static_url_for` function when including static content,
as it resolves the correct file name, including the MD5 hash.
For example

```html
<link rel="shortcut icon" href="{{static_url_for('static', filename='build/favicon.ico') }}">
```

If all of your static files are managed this way, then their filenames will change whenever their
contents do, and you can ask Flask to tell web browsers that they
should cache all your assets forever by including the following line
in ``.env``:

```text
SEND_FILE_MAX_AGE_DEFAULT=31556926  # one year
```
