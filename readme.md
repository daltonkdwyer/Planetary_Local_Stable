This program is a signalling server. 

It sends clients a webpage that gathers their RTCPeerConnection information (SDP), stores it, and sends it out if a new person tries to connect.

LAUNCH: 
    Run in terminal: python3 app.py
    Open two browser windows to: 127.0.0.1:8000

The program consists of:

    A) SERVER SIDE
        1) plntry_server1.py
            - Sends out the client page
            - Has websockets that tell the client what to do
            - Has a dictionary that stores the SDP information by room ID
            - When a new client joins, it sends out the SDP of the first person, and quarterbacks the conenction
            - Also controls for when people leave
    
    B) CLIENT SIDE
        2) vehicle_connection.js
            - connects to the main socket server
            - controls what's happening on the client
            - manages the sockets going in and out
            
        3) web_rtc_fucntions.js
            - helper functions to vehicle_connection
            - handles all the web_rtc stuff (creating/updating peer connections etc.)

        4) app.js
            - This is just a dumb thing for the index page which tells you you are a monkey (yes, that grammar was right)

        5) index.html
            - home page that distributes which car to connect you to

    C) ADMIN
        1) Procfile
            - This tells Heroku what to run on startup
                uses a Flask version of a webserver called Green Unicorn 'gunicorn'
            - You use gunicorn, but you have no idea what this is

        2) Pipfile (DELETE THIS- CANT HAVE BOTH THIS AND requirements.txt AS THEY ARE DUPLICATES)
            - This includes all the dependences for Heroku
            - You also kind of have no idea how it works, but you need to go into the environment somehow
            - See here: https://stackoverflow.com/questions/46330327/how-are-pipfile-and-pipfile-lock-used

        3) Requirements.txt
            - This might be INSTEAD of a pipfile
            - Lists everything the Heroku server will need (kind of like a virtual environment)

        4) runtime.txt
            - this just specifies which version of python to use...? 
                - (DD- why can't this just be in the requirements file...)

Hosting

    A. It is hosted on heroku
        Username: dalton.dwyer@yahoo.com
        PW: S13

    B. Need some weird files:
        - Pipfile


General:
    - To update libraries, you need to enter the virtual environment (I think)
        - launch with |pipenv shell
        - exit with |exit
    
