# Basic NodeJS Project Structure

This is a base node js project template, which anyone can use as it has been prepared, by keeping some of the most important code practices and project management recommendations. Feel free to change anything.

`src` -> Inside the src folder all the actual source code regarding the project will reside but this will not include any kind of tests. (You might want to make separate tests folder)

Lets take a look inside the `src` folder

- `config` -> In this folder anything and everything regarding any configurations or setup of a library or module will be done. For example: setting up `dotenv` so that we can use the environment variables anywhere in a cleaner fashion, this is done in the `server-config.js`. One more example can be to setup you logging library that can help you to prepare meaningful logs, so configuration for this library should also be done here.

- `routes` -> In the routes folder, we register a route and the corresponding middleware and controllers to it.

- `middlewares` -> they are just going to intercept the incoming requests where we can write our validators, authenticators etc.

- `controllers` -> they are kind of the last middlewares as post them you call your business layer to execute the budiness logic. In controllers we just receive the incoming requests and data and then pass it to the business layer, and once business layer returns an output, we structure the API response in controllers and send the output.

- `repositories` -> this folder contains all the logic using which we interact the DB by writing queries, all the raw queries or ORM queries will go here.

- `services` -> contains the buiness logic and interacts with repositories for data from the database

- `utils` -> contains helper methods, error classes etc.

- `seeders` -> If we want to have some set of data that is not going to change, we can include in seeders folder. This is given by sequelize-cli we used in our project.

- `migrations` -> In simple terms, migrations file are used to do version controlling of our database. These are simple language scripts.
  As we are using Nodejs and sequelize, it will be a JavaScript file. Here, we will programatically write on how to maintain versions of your database. Every version will have unique id or version. Sequelize provides us the command to create migration file.

  - `seeders` -> If we want to have some starter data/default data that is not going to change in the table. This puts some seed data (starting data for our table) For example:  
    Our app has some roles like normal user, admin, seller etc. Role will be in development as well as production. So, we can create seeder file for roles where we will define the roles and run the file which will automatically populate the roles database. This way we don't have to manually to insert into.

### Setup the project

- Download this template from github and open it in your favourite text editor.
- Go inside the folder path and execute the following command:

```
npm install
```

- In the root directory create a `.env` file and add the following env variables
  ```
      PORT=<port number of your choice>
  ```
  ex:
  ```
      PORT=3000
  ```
- go inside the `src` folder and execute the following command:
  ```
    npx sequelize init
  ```
- By executing the above command you will get migrations and seeders folder along with a config.json inside the config folder.

- If you're setting up your development environment, then write the username of your db, password of your db and in dialect mention whatever db you are using for ex: mysql, mariadb etc.

- If you're setting up test or prod environment, make sure you also replace the host with the hosted db url.

- To run the server execute

```
npm run dev
```
