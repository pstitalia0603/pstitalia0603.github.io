---
{"dg-publish":true,"permalink":"/technology/dev/apache-superset/","tags":["Data","Projects"],"noteIcon":"","created":"2024-04-27 3:27:06 pm","updated":"2024-04-27 3:27:53 pm"}
---

[[TRACK/CURRENT PROJECTS\|CURRENT PROJECTS]]

- [x] Superset - Install in docker image: https://docs.docker.com/engine/install/debian/ 🛫  ✅ 2024-04-30
https://superset.apache.org/docs/intro

## Remove old Docker containers
https://www.digitalocean.com/community/tutorials/how-to-remove-docker-images-containers-and-volumes

LIST:
```
sudo docker images -a
```

REMOVE ALL:
```
sudo docker system prune -a
```

---
# Install Apache Superset in venv 
- [x] Install apache superset/venv 🛫 2024-04-30 ✅ 2024-04-30

-- reference: https://www.youtube.com/watch?v=yE5oFC0VAKo

- python -m venv supersetvenv
- . ./supersetvenv/bin/activate
- pip install apache-superset
- pip install --upgrade pip
- export FLASK_APP=superset
- openssl rand -base64 42
- </copy SECRET_KEY>
- cd/supersetvenv/lib/python3.11/site-packages/superset
- sudo nano config.py
- </below SECRET_KEY = os.environ.get("SUPERSET_SECRET_KEY") or CHANGE_ME SECRET_KEY/> ... add
- SECRET_KEY='</ SECRET_ _KEY CREATED ABOVE />'
- superset db upgrade
- pip install pillow
- superset fab create-admin
	- username: admin
	- password: admin
- superset load_examples
- superset init
- Open UFW Port
	- sudo ufw allow 8089
- superset run -h 192.168.1.167 -p 8089 --with-threads --reload --debugger
- http://192.168.1.167:8089/login/
- </ctrl c/>
- to end: deactivate
- To spin up again: 
	- First time only:
		- pip install python-dotenv
		- Create a ".flaskenv" in your project's root directory
				- sudo nano .flaskenv
				- Enter this-->
					- FLASK_APP=superset  
	- cd ~ 
	- source supersetvenv/bin/activate 
	- superset run -h 192.168.1.167 -p 8089 --with-threads --reload --debugger

# Next --> connect to sqlite db 

https://superset.apache.org/docs/databases/installing-database-drivers/

- SQLITE --> SUPERSET 
	- [x] sqlite://path/to/file.db?check_same_thread=false 🛫 2024-05-02 ✅ 2024-05-02

