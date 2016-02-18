









# Simplify Your System

## with NPM Scripts





### by @dylanized

































baked-in


simple


composable



























OFFICIAL DOCUMENTATION

https://docs.npmjs.com/misc/scripts




Nordic.js 2015 • Kate Hudson - Advanced front-end automation with npm scripts

https://www.youtube.com/watch?v=0RYETb9YVrk




How to Use NPM as a Build Tool

http://blog.keithcirkel.co.uk/how-to-use-npm-as-a-build-tool/




The @dylanized App Boilerplate

https://github.com/dylanized/app-boilerplate












01 Basic Scripts



{
  "name": "basic-scripts",
  "version": "0.0.1",
  "description": "Basic scripts example",
  "author": "dylanized",
  "license": "MIT",
  "dependencies": {
    "request": "^2.69.0"
  },
  "devDependencies": {
    "mocha": "^2.4.4"
  },  
  "scripts": {
    "stop": " ",
    "test": "mocha test/*.js",
    "clean": "rm tmp/*.*"
  }
}
















01.5  Shortcuts




start
stop
restart
test

























02  Build Basics


{
  "name": "build-basics",
  "version": "0.0.1",
  "description": "Build script basics",
  "main": "index.js",
  "author": "dylanized",
  "license": "MIT",
  "scripts": {
    "build": "cp package.json tmp",
    "postinstall": "build",
    "start": "node foo.js",
    "test": "mocha test/*.js",
    "clean": "rm tmp/*.*",
    "pretest": "npm run clean && npm run build"
  }
}

















03  Complex Builds



  "scripts": {
    "==BUILDING==": " ",
    "postinstall": "bower install && npm run build",
    "postupdate": "bower update && npm run build",
    "build": "npm run compile",
    "compile": "npm run compile-css && npm run compile-js",
    "compile-css": " ",
    "compile-js": " ",
    "==WATCHING==": " ",
    "watch": "npm run watch-css & npm run watch-js & npm run watch-server",
    "watch-css": " ",
    "watch-js": " ",
    "watch-server": " ",
    "==RUNNING==": " ",
    "start": "node server.js",
    "build-start": "npm run build && npm run start",
    "watch-start": "npm run watch && npm run start",
    "dev": "npm run reload && npm run build && npm run watch-start",
    "stop": "npm run stopDB && npm run stopSQL"
  }
  
  
  
  
  
  
  
  
  
  
  
  
04 Simplifying Complexity


  "scripts": {
    "==BUILDING==": " ",
    "postinstall": "npm-run-all bower-install build",
    "postupdate": "npm-run-all bower-update build",
    "build": "npm run compile",
    "compile": "npm-run-all compile-css compile-js",
    "compile-css": " ",
    "compile-js": " ",
    "bower-install": "bower install",
    "bower-update": "bower update",
    "==WATCHING==": " ",
    "watch": "npm-run-all watch-css watch-js watch-server",
    "watch-css": " ",
    "watch-js": " ",
    "watch-server": " ",
    "==RUNNING==": " ",
    "start": "node server.js",
    "build-start": "npm-run-all build start",
    "watch-start": "npm-run-all watch start",
    "dev": "npm-run-all reload build watch-start",
    "stop": "npm-run-all stopDB stopSQL",
    "uninstall": "npm-run-all destroyDB destroySQL clean"    
  }
  







05 Database Handling


    "==DATABASE1==": " ",
    "createDB": " ",
    "importDB": " ",
    "seedDB": " ",
    "dropDB": " ",
    "reloadDB": "npm-run-all dropDB seedDB",
    "exportDB": " ",
    "startDB": " ",
    "stopDB": " ",
    "destroyDB": " ",
    
    
    "==DATABASE2==": " ",
    "createSQL": " ",
    "importSQL": " ",
    "seedSQL": " ",
    "dropSQL": " ",
    "loadSQL": " ",
    "reloadSQL": "npm-run-all dropSQL seedSQL",
    "exportSQL": " ",
    "startSQL": " ",
    "stopSQL": " ",
    "destroySQL": " "










06 Variables



    "==DATABASE1==": " ",
    "createDB": " ",
    "seedDB": "mongoimport -d $npm_package_config_db_name -c $npm_package_config_db_collection --file $npm_package_config_db_seed",
    "dropDB": "mongo legislators_development --eval 'db.dropDatabase()'",
    "reloadDB": "npm-run-all dropDB seedDB",
    "exportDB": " ",
    "startDB": " ",
    "stopDB": " ",
    "destroyDB": " ",
    "==DATABASE2==": " ",
    "createSQL": "echo \"create database $npm_package_config_sql_dbname\" | mysql -u $npm_package_config_sql_user -p$npm_package_config_sql_pass",
    "seedSQL": "mysql -u $npm_package_config_sql_user -p$npm_package_config_sql_pass $npm_package_config_sql_dbname < $npm_package_config_sql_seed",
    "dropSQL": "echo \"DROP DATABASE IF EXISTS $npm_package_config_sql_dbname\" | mysql -u $npm_package_config_sql_user -p$npm_package_config_sql_pass",
    "loadSQL": "npm-run-all createSQL seedSQL",
    "reloadSQL": "npm-run-all dropSQL loadSQL",
    "exportSQL": " ",
    "startSQL": " ",
    "stopSQL": " ",
    "destroySQL": " ",
    "==UNINSTALL==": " ",
    "uninstall": "npm-run-all destroyDB destroySQL clean",
    "clean": " ", 



















07 Testing





    "==TESTING==": " ",
    "test": "mocha test/[^_]*.js --bail",
    "mocha": "mocha",
    "test-grep": "mocha --grep",
    "env": "env",
    "bin": "ls ./node_modules/.bin/",























Happy DevOps!


Follow: @dylanized

d@dylanized.com

https://github.com/dylanized/app-boilerplate

https://github.com/dylanized/npm-scripts



















