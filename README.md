# URL-Shortener Application
 ## Flask-Jinja-Gunicorn
   1. Create a project required environment
  2. Install a pipenv 
      ```
      pip3 install pipenv
      ```
  3. To create virtual env for project
     ```
     pipenv install 
     ```
   **Note: it will Creating a virtualenv for this project… and it will create the pipfile.lock for [dev-packages] and        	[packages].**

  4. To activate this project's virtualenv, run
     ```
     pipenv shell
     ```
  5. Create project in flask and install
     ```
     pipenv install flask
     ```
  7. Go to the your virtualenv in command prompt for windows
     ```
     set FLASK_APP=urlshort
     ```
     **Note: Go to the your virtualenv in terminal  for windows**
     ```
     export FLASK_APP=urlshort
     ``` 
  8. Run the flask app  
      ```
      flask run
      ``` 
  9. How to move on to the flask app to production to development in command prompt 
      ```
      set FLASK_ENV=development
      ```
 10. Then run app
       ```
       flask run
       ```

#Web server gateway interface (WSGI)
  Protocol for python application in order to server websites unified order.

deploying the application into ubuntu Servers
  1. First upload code to server
```
   sudo git clone https://github.com/sada498/url-shortener.git
   ```
  2. Move into the directory 
  ```
  cd url-shorener
  ```
  3. Install pipenv
     ```
     sudo apt install python3-pippip
     ```
     ```
     pip3 install pipenev
     ```
     ```
     pipenv shell
     ```
     ```
     export FlASK_APP=urlshort  
     ```
  (Note: I use export because of Linux terminal )
     ```
     flask run
     ```
 4. After that make your application public 
    ```
    flask run –host=0.0.0.0
    ```
 5. Visit the server public ip with port id
    ```
    Ip:portnumber
    ```
## How to integrate Flask with Gunicorn

 1.Install Gunicorn on same server 
 	Pipenv install gunicorn
2. running with Gunicorn
  Gunicorn “urlshort:create_app()” -b 0.0.0.0 
 3. Recommend to run flask on nginx (to install on Linux )
    sudo apt install nginx 
4. To check the nginx running on server
   systemctl status nginx
 Note: check the Status check Active
To quit of that enter press “ q ”
5. to fix the configuration of the file to enable  the app in nginx 
 Sudo nano /etc/ninx/sites-enabled/default

 6. Past the following code on the configuration file check the both server and location

```server {
    listen 80;
    server_name example.org;
    access_log  /var/log/nginx/example.log;

    location / {
        proxy_pass http://127.0.0.1:8000;
        proxy_set_header Host $host;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }
  }
  ```

# 7. After setting up the above code into config file
Ctrl +x ( exit )
# 8. Run the gunicorn all the time 
  gunicorn “urlshort:create_app( ) ” -b 0.0.0.0 --daemon 
# 9. upload files to correct location on server according to our app.
   Nano urlshort/urlshort.py
Change the file location to where do you want to save on  your server 
