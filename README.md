# JHipster Cheatsheet
**Summary**

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Environment](#environment)
  - [Prerequisites](#prerequisites)
  - [Check](#check)
  - [Git Configuration](#git-configuration)
- [Application generation](#application-generation)
  - [Generate your application with the following options:](#generate-your-application-with-the-following-options)
  - [Test that everything is correct](#test-that-everything-is-correct)
  - [Start your application](#start-your-application)
- [Push your application to Github](#push-your-application-to-github)
- [Setup continuous integration](#setup-continuous-integration)
  - [Run the continuous delivery sub-generator](#run-the-continuous-delivery-sub-generator)
  - [Test that builds are automatically triggered](#test-that-builds-are-automatically-triggered)
- [Deploy to Heroku](#deploy-to-heroku)
- [Generate Entities](#generate-entities)
  - [Define your entities with the JDL Studio](#define-your-entities-with-the-jdl-studio)
  - [Generate entities on your application](#generate-entities-on-your-application)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->
## Environment

### Prerequisites

To use JHipster, you need:

- Git
- Java 8
- NodeJS 8.9+
- NPM or Yarn
- Docker 17.03+
- JHipster

### Check your configuration

- Git: `git version`
- Java: `java -version`
- NodeJS: `node -v`
- NPM: `npm -v`
- Yarn: `yarn -v`
- Docker: `docker version`
- JHipster: `jhipster --help`

### Git Configuration

Configure your local Git configuration

    git config --global user.name YOUR_USERNAME
    git config --global user.email YOUR_ACCOUNT@ippon.fr

## Application generation

### Generate your application with the following options:

- Type of application: `Monolithic`
- Name of your application
- Java package name
- JHipster registry: `No`
- Type of authentification (recommanded: `JWT`)
- Type of database: `SQL`
- Production database: `PostgreSQL` (as it's free on Heroku)
- Development database: `H2 with disk-based persistence`
- Spring cache abstraction : `ehcache`
- Hibernate 2nd level cache: `yes`
- Backend build tool: `Maven`
- Additional technologies: nothing
- Framework for client: `Angular 5`
- SASS support: `No`
- Internationalization: `No`
- Testing framework: nothing
- JHipster Marketplace: nothing

Note that a README file was generated with useful instructions.

Additional documentation : [jhipster.tech/creating-an-app](http://www.jhipster.tech/creating-an-app/)

### Test that everything is correct

To run back-end tests:

    ./mvnw test

To run front-end tests

    yarn test


### Start your application

To start the back-end:

    ./mvnw

To start the front end:

    yarn start

Hot reload should work for everything !


## Push your application to Github

Create a repository on [Github](https://github.com) and upload your code to it:

    git init
    git add .
    git commit -m "initial commit"
    git remote add origin https://github.com/YOUR_ACCOUNT/YOUR_REPO.git
    git push -u origin master

Refresh your project’s GitHub page, your code should be available!

## Setup continuous integration

### Run the continuous delivery sub-generator

    jhipster ci-cd

- Select `Travis CI`
- Do not select auto deployment to Heroku
- Commit and push: `git add . && git commit -m 'Add Travis CI' && git push`
- Authenticate to [Travis CI :construction_worker:](https://travis-ci.org/) using your GitHub account
- Go to your Travis account and select "sync account"
- Enable the build for your project

### Test that builds are automatically triggered

- Change a line of code, for example in your `home.component.html`
- Commit & push your code, a build should be automatically triggered
- You should see a new build at: [https://travis-ci.org/YOUR_ACCOUNT/YOUR_REPO/builds](https://travis-ci.org/YOUR_ACCOUNT/YOUR_REPO/builds)

## Deploy to Heroku

- Create an account on https://www.heroku.com/home
- Install the Heroku toolbelt: https://devcenter.heroku.com/articles/heroku-cli
- Log in by typing `heroku login`
- Run `jhipster heroku` in your application root

## Generate Entities

### Define your entities with the JDL Studio

Model your entities with the [JDL Studio](http://www.jhipster.tech/jdl-studio/) and refer to the following pages:

- [JDL (JHipster Domain Language) documentation](https://www.jhipster.tech/jdl/)
- [JHipster entity documentation](https://www.jhipster.tech/creating-an-entity/)
- [JHipster relationship documentation](https://www.jhipster.tech/managing-relationships/)

Then export the file (jhipster.jdl) and add it to your project.

### Generate entities on your application

Generate entities from JDL:

    jhipster import-jdl yourfile.jh

Restart and test your application: `./mvnw`
