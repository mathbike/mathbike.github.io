---
title:  Setting up Kijiji-Manager to Automatically Repost Ads
categories: [Other]
tags: [other]
---

**Kijiji-Manager is a Flask based app for viewing, posting, reposting, and deleting your Kijiji ads built and maintained by jackm.  I added a few extra things but it's kind of janky.  At some point I will update it to make it a bit more solid.  But it works for now.**

---

GitHub repo:
<a href="https://github.com/jackm/kijiji-manager" target="_blank">https://github.com/jackm/kijiji-manager</a>

---


## 1. Setup Kijiji-Manager

Clone the repo:
```terminal
git clone https://<PERSONAL_ACCESS_TOKEN>@github.com/mathbike/kijiji-manager.git
```

Setup:
```terminal
cd kijiji-manager
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
pip install .
python3 keychange.py
```

Start kijiji-manager:
```
cd kijiji-manager &&
source venv/bin/activate &&
python3 -m kijiji_manager
```

- Open a browser and go to:
<a href="http://localhost:5000/login" target="_blank">http://localhost:5000/login</a>

- Log in with your Kijiji account

You can now post your ads from here.  Kijiji-Manager saves the ads you create as XML files, which you can access in the `instance/user` directory.


## 2. Setup the `accounts.yaml` file

Add your kijiji account details to the accounts.yaml file
```yaml
account1:
  vm_name: <vm_name>
  email: <email>
  password: <password>
  name: <name>
```

If you have more than one account, number them sequentially.  You will need to create a seperate VM for each account.


## 3. Set up the `repost.py` file

Change the vm_name variable to the name of your VM. It uses the vm_name variable to get the email and password from the accounts.yaml file.


## 4. Create the repost schedule

See <a href="https://crontab.cronhub.io/" target="_blank">https://crontab.cronhub.io/</a> for details on cron scheduling

Open the crontab file with the edit flag:
```terminal
crontab -e
```

To repost all your ads every hour:
```terminal
# """ EVERY HOUR """
# start
0 * * * * /usr/bin/bash /home/<username>/kijiji-manager/startkm.sh
# repost
1 * * * * cd kijiji-manager && /home/<username>/kijiji-manager/venv/bin/python3 /home/<username>/kijiji-manager/repost.py
# stop
6 * * * * /usr/bin/bash /home/<username>/kijiji-manager/stopkm.sh
```

Replace `<username>`  with your username.  There are 3 scripts being run.  The first one starts the kijiji-manager flask server.  Then 1 minute later the `repost.py` script reposts all the ads.  There is a 3 minute delay when reposting to ensure your ads aren't flagged.  Then 5 minutes later there is a script to stop the flask server.  If you're going to make your own cron schedules, keep the time between scripts the same: 0, 1, 6, or 33, 34, 39, etc.

Let's say you want 4 reposts per day, at 12:05 AM, 6:05 AM, 12:05 PM, and 6:05 PM:
```terminal
# """ 12:05 AM """
# start
5 0 * * * /usr/bin/bash /home/<username>/kijiji-manager/startkm.sh
# repost
6 0 * * * cd kijiji-manager && /home/<username>/kijiji-manager/venv/bin/python3 /home/<username>/kijiji-manager/repost.py
# stop
12 0 * * * /usr/bin/bash /home/<username>/kijiji-manager/stopkm.sh
# """ 6:05 AM """
# start
5 6 * * * /usr/bin/bash /home/<username>/kijiji-manager/startkm.sh
# repost
6 6 * * * cd kijiji-manager && /home/<username>/kijiji-manager/venv/bin/python3 /home/<username>/kijiji-manager/repost.py
# stop
12 6 * * * /usr/bin/bash /home/<username>/kijiji-manager/stopkm.sh
# """ 12:05 PM """
# start
5 12 * * * /usr/bin/bash /home/<username>/kijiji-manager/startkm.sh
# repost
6 12 * * * cd kijiji-manager && /home/<username>/kijiji-manager/venv/bin/python3 /home/<username>/kijiji-manager/repost.py
# stop
12 12 * * * /usr/bin/bash /home/<username>/kijiji-manager/stopkm.sh
# """ 6:05 PM """
# start
5 18 * * * /usr/bin/bash /home/<username>/kijiji-manager/startkm.sh
# repost
6 18 * * * cd kijiji-manager && /home/<username>/kijiji-manager/venv/bin/python3 /home/<username>/kijiji-manager/repost.py
# stop
12 18 * * * /usr/bin/bash /home/<username>/kijiji-manager/stopkm.sh
```

This is super janky.  Everything can be done with one Python script.

---

## Kijiji-Reposter

Install Kijiji-Reposter:
```sh
git clone https://github.com/rybodiddly/Kijiji-Reposter.git &&
cd Kijiji-Reposter &&
python3 -m venv venv &&
source venv/bin/activate &&
pip3 install wheel &&
pip3 install WTForms==2.3.3 &&
pip3 install -r requirements.txt
```

Start Kijiji-Reposter:
```terminal
cd Kijiji-Reposter &&
source venv/bin/activate &&
python3 server.py
```
