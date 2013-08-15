
* aws (dev) - [http://ec2-50-17-116-27.compute-1.amazonaws.com:8080](http://ec2-50-17-116-27.compute-1.amazonaws.com:8080)

* heroku (staging) - [http://lzcabrera-bitstarter-s-mooc.herokuapp.com/](http://lzcabrera-bitstarter-s-mooc.herokuapp.com/)

* heroku (production) - [http://lzcabrera-bitstarter-mooc.herokuapp.com/](http://lzcabrera-bitstarter-mooc.herokuapp.com/)

### Setup for A7
1. git clone https://github.com/startup-class/bitstarter-ssjs-db.git

2. cp -avr ../bitstarter-ssjs-db/models ./models
 cp -avr ../bitstarter-ssjs-db/views ./views
 cp ../bitstarter-ssjs-db/.env.dummy .env
 cp ../bitstarter-ssjs-db/.gitignore .gitignore
 cp ../bitstarter-ssjs-db/.pgpass .pgpass
 cp ../bitstarter-ssjs-db/package.json ./package.json
 cp ../bitstarter-ssjs-db/pgsetup.sh ./pgsetup.sh
 cp ../bitstarter-ssjs-db/web.js ./web.js

3. add "Orders" link to index.html

4. sudo npm install

5. heroku addons:add heroku-postgresql:dev --app YOUR-STAGING-APP-NAME
 heroku addons:add heroku-postgresql:dev --app YOUR-PRODUCTION-APP-NAME

heroku pg:promote `heroku config --app YOUR-STAGING-APP-NAME  | grep HEROKU_POSTGRESQL | cut -f1 -d':'` --app YOUR-STAGING-APP-NAME
heroku pg:promote `heroku config --app YOUR-PRODUCTION-APP-NAME  | grep HEROKU_POSTGRESQL | cut -f1 -d':'` --app YOUR-PRODUCTION-APP-NAME

heroku plugins:install git://github.com/ddollar/heroku-config.git

6. ./pgsetup.sh

7. update .env with coinbase API key

8. foreman start

9. git push staging-heroku staging:master

10. heroku config:push --app YOUR-STAGING-APP-NAME

11. git push production-heroku master:master

12. heroku config:push --app YOUR-PRODUCTION-APP-NAME



10. 

