## A. Deploy live

1. Create a Dokku DO droplet 
2. Access the IP of that droplet to finish the configuration

3. On the Remote (DO droplet)
    - create an app : `dokku apps:create *appname*`
    - if needed : install a db
        ```
        sudo dokku plugin:install https://github.com/dokku/dokku-postgres.git
        dokku postgres:create *dbname*
        dokku postgres:link *dbname* *appname*
        ```
    - set up environemnt variables
    `dokku config:set id_website DJANGO_OPBEAT_ORGANIZATION_ID='cfcfb67ca6624d4a95e84df2e4811bfc'`
    

4. On the  local machine

Link the two machines

`git remote add dokku dokku@IP:*appname*`

Deploy
`git push dokku master`


### Checking logs - on the remote

docker ps -a

docker logs <container ID>

## B. Starting dev

1. Create virtual environment

python -m venv dokku_django

2. Activate it

source dokku_django/bin/activate

## C. Creating VM

### 1.start vm
```
deploy/vagrant/dokku
vagrant up
```

### 2. change /etc/hosts
```
sudo vim /etc/hosts
10.0.0.2 dokku.me
```


### 3. copy your ssh key 


`cat ~/.ssh/id_rsa.pub | pbcopy`

got to `http://dokku.me/` in your browser

paste the key

### 4. create an alias to run custom commands

`alias dokku="ssh -t root@<machine-address> dokku"`

### 5. Start the staging

follow point A.3 then A.4
app should be available at `dokku.me:port`

