# TeamCity Migration (Linux)

- 2 data stores of interest
  - TeamCity Data Directory: default `~/.BuildServer`
  - [[Postgres]] Database

- TeamCity has the tools for creating a full backup
 - `TeamCity/bin/manageDB.sh --all`
 - run the script for a listing of all options
 - `JAVA_HOME` needs to be set
 - back up can be found in `~/.BuildServer/backups`

- Creating a [[SystemD]] service for Teamcity
  - Teamcity uses it's own process management but it is still nice to be able to use [[SystemD]] as with other services. 
  - ***NOTE***: The server startup script is hard wired when it comes to it's catalina (Tomcat) PID. You must remember to create the file `TeamCity/logs/catalina.pid` if you get errors when trying to use the following service
  - Example [[SystemD]] Service config:
  ```
  [Unit]
  Description=TeamCity Server
  Requires=network.target
  After=syslog.target network.target

  [Install]
  WantedBy=multi-user.target

  [Service]
  PIDFile=/opt/teamcity/server/TeamCity/logs/teamcity.pid
  ExecStart=/opt/teamcity/server/TeamCity/bin/teamcity-server.sh start 
  ExecStop=/opt/teamcity/server/TeamCity/bin/teamcity-server.sh stop
  Type=Simple
  RemainAfterExit=no
  User=teamcity
  Group=teamcity
  SyslogIdentifier=teamcity_server
  PrivateTmp=yes
  ```
