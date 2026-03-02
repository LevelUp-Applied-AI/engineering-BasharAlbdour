# Docker Notes — Day 9

## Docker Version
Client:
 Version:           29.2.1
 API version:       1.53
 Go version:        go1.25.6
 Git commit:        a5c7197
 Built:             Mon Feb  2 17:20:16 2026
 OS/Arch:           windows/amd64
 Context:           desktop-linux

Server: Docker Desktop 4.63.0 (220185)
 Engine:
  Version:          29.2.1
  API version:      1.53 (minimum version 1.44)
  Go version:       go1.25.6
  Git commit:       6bc6209
  Built:            Mon Feb  2 17:17:24 2026
  OS/Arch:          linux/amd64
  Experimental:     false
 containerd:
  Version:          v2.2.1
  GitCommit:        dea7da592f5d1d2b7755e3a161be07f43fad8f75
 runc:
  Version:          1.3.4
  GitCommit:        v1.3.4-0-gd6d73eb8
 docker-init:
  Version:          0.19.0
  GitCommit:        de40ad0

## Hello World Test
Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/

## Docker logs pg-prework
The files belonging to this database system will be owned by user "postgres".
This user must also own the server process.

The database cluster will be initialized with locale "en_US.utf8".
The default database encoding has accordingly been set to "UTF8".
The default text search configuration will be set to "english".

Data page checksums are disabled.

fixing permissions on existing directory /var/lib/postgresql/data ... ok
creating subdirectories ... ok
selecting dynamic shared memory implementation ... posix
selecting default max_connections ... 100
selecting default shared_buffers ... 128MB
selecting default time zone ... UTC
creating configuration files ... ok
running bootstrap script ... ok
sh: locale: not found
2026-03-02 21:31:34.158 UTC [35] WARNING:  no usable system locales were found
performing post-bootstrap initialization ... ok
initdb: warning: enabling "trust" authentication for local connections
initdb: hint: You can change this by editing pg_hba.conf or using the option -A, or --auth-local and --auth-host, the next time you run initdb.
syncing data to disk ... ok


Success. You can now start the database server using:

    pg_ctl -D /var/lib/postgresql/data -l logfile start

waiting for server to start....2026-03-02 21:31:35.027 UTC [41] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-02 21:31:35.031 UTC [41] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-02 21:31:35.045 UTC [44] LOG:  database system was shut down at 2026-03-02 21:31:34 UTC
2026-03-02 21:31:35.053 UTC [41] LOG:  database system is ready to accept connections
 done
server started

/usr/local/bin/docker-entrypoint.sh: ignoring /docker-entrypoint-initdb.d/*

waiting for server to shut down....2026-03-02 21:31:35.130 UTC [41] LOG:  received fast shutdown request
2026-03-02 21:31:35.134 UTC [41] LOG:  aborting any active transactions
2026-03-02 21:31:35.143 UTC [41] LOG:  background worker "logical replication launcher" (PID 47) exited with exit code 1
2026-03-02 21:31:35.143 UTC [42] LOG:  shutting down
2026-03-02 21:31:35.147 UTC [42] LOG:  checkpoint starting: shutdown immediate
2026-03-02 21:31:35.172 UTC [42] LOG:  checkpoint complete: wrote 3 buffers (0.0%); 0 WAL file(s) added, 0 removed, 0 recycled; write=0.007 s, sync=0.004 s, total=0.030 s; sync files=2, longest=0.002 s, average=0.002 s; distance=0 kB, estimate=0 kB
2026-03-02 21:31:35.177 UTC [41] LOG:  database system is shut down
 done
server stopped

PostgreSQL init process complete; ready for start up.

2026-03-02 21:31:35.262 UTC [1] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-02 21:31:35.262 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
2026-03-02 21:31:35.262 UTC [1] LOG:  listening on IPv6 address "::", port 5432
2026-03-02 21:31:35.274 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-02 21:31:35.285 UTC [55] LOG:  database system was shut down at 2026-03-02 21:31:35 UTC
2026-03-02 21:31:35.294 UTC [1] LOG:  database system is ready to accept connections
2026-03-02 21:36:35.718 UTC [53] LOG:  checkpoint starting: time
2026-03-02 21:36:39.941 UTC [53] LOG:  checkpoint complete: wrote 43 buffers (0.3%); 0 WAL file(s) added, 0 removed, 0 recycled; write=4.180 s, sync=0.019 s, total=4.234 s; sync files=11, longest=0.014 s, average=0.002 s; distance=252 kB, estimate=252 kB

## Postgres Container

Command used:
```bash
docker run -d \
  --name pg-prework \
  -e POSTGRES_PASSWORD=prework \
  -p 5432:5432 \
  postgres:15-alpine
```
## docker stop pg-prework
pg-prework

## docker restart pg-prework
pg-prework

## docker logs pg-prework (after restart)
The files belonging to this database system will be owned by user "postgres".
This user must also own the server process.

The database cluster will be initialized with locale "en_US.utf8".
The default database encoding has accordingly been set to "UTF8".
The default text search configuration will be set to "english".

Data page checksums are disabled.

fixing permissions on existing directory /var/lib/postgresql/data ... ok
creating subdirectories ... ok
selecting dynamic shared memory implementation ... posix
selecting default max_connections ... 100
selecting default shared_buffers ... 128MB
selecting default time zone ... UTC
creating configuration files ... ok
running bootstrap script ... ok
sh: locale: not found
2026-03-02 21:31:34.158 UTC [35] WARNING:  no usable system locales were found
performing post-bootstrap initialization ... ok
initdb: warning: enabling "trust" authentication for local connections
initdb: hint: You can change this by editing pg_hba.conf or using the option -A, or --auth-local and --auth-host, the next time you run initdb.
syncing data to disk ... ok


Success. You can now start the database server using:

    pg_ctl -D /var/lib/postgresql/data -l logfile start

waiting for server to start....2026-03-02 21:31:35.027 UTC [41] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-02 21:31:35.031 UTC [41] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-02 21:31:35.045 UTC [44] LOG:  database system was shut down at 2026-03-02 21:31:34 UTC
2026-03-02 21:31:35.053 UTC [41] LOG:  database system is ready to accept connections
 done
server started

/usr/local/bin/docker-entrypoint.sh: ignoring /docker-entrypoint-initdb.d/*

waiting for server to shut down....2026-03-02 21:31:35.130 UTC [41] LOG:  received fast shutdown request
2026-03-02 21:31:35.134 UTC [41] LOG:  aborting any active transactions
2026-03-02 21:31:35.143 UTC [41] LOG:  background worker "logical replication launcher" (PID 47) exited with exit code 1
2026-03-02 21:31:35.143 UTC [42] LOG:  shutting down
2026-03-02 21:31:35.147 UTC [42] LOG:  checkpoint starting: shutdown immediate
2026-03-02 21:31:35.172 UTC [42] LOG:  checkpoint complete: wrote 3 buffers (0.0%); 0 WAL file(s) added, 0 removed, 0 recycled; write=0.007 s, sync=0.004 s, total=0.030 s; sync files=2, longest=0.002 s, average=0.002 s; distance=0 kB, estimate=0 kB
2026-03-02 21:31:35.177 UTC [41] LOG:  database system is shut down
 done
server stopped

PostgreSQL init process complete; ready for start up.

2026-03-02 21:31:35.262 UTC [1] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-02 21:31:35.262 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
2026-03-02 21:31:35.262 UTC [1] LOG:  listening on IPv6 address "::", port 5432
2026-03-02 21:31:35.274 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-02 21:31:35.285 UTC [55] LOG:  database system was shut down at 2026-03-02 21:31:35 UTC
2026-03-02 21:31:35.294 UTC [1] LOG:  database system is ready to accept connections
2026-03-02 21:36:35.718 UTC [53] LOG:  checkpoint starting: time
2026-03-02 21:36:39.941 UTC [53] LOG:  checkpoint complete: wrote 43 buffers (0.3%); 0 WAL file(s) added, 0 removed, 0 recycled; write=4.180 s, sync=0.019 s, total=4.234 s; sync files=11, longest=0.014 s, average=0.002 s; distance=252 kB, estimate=252 kB
2026-03-02 22:01:48.315 UTC [1] LOG:  received fast shutdown request
2026-03-02 22:01:48.320 UTC [1] LOG:  aborting any active transactions
2026-03-02 22:01:48.327 UTC [1] LOG:  background worker "logical replication launcher" (PID 58) exited with exit code 1
2026-03-02 22:01:48.327 UTC [53] LOG:  shutting down
2026-03-02 22:01:48.332 UTC [53] LOG:  checkpoint starting: shutdown immediate
2026-03-02 22:01:48.347 UTC [53] LOG:  checkpoint complete: wrote 0 buffers (0.0%); 0 WAL file(s) added, 0 removed, 0 recycled; write=0.003 s, sync=0.001 s, total=0.020 s; sync files=0, longest=0.000 s, average=0.000 s; distance=0 kB, estimate=227 kB
2026-03-02 22:01:48.352 UTC [1] LOG:  database system is shut down

PostgreSQL Database directory appears to contain a database; Skipping initialization

2026-03-02 22:02:58.283 UTC [1] LOG:  starting PostgreSQL 15.17 on x86_64-pc-linux-musl, compiled by gcc (Alpine 15.2.0) 15.2.0, 64-bit
2026-03-02 22:02:58.283 UTC [1] LOG:  listening on IPv4 address "0.0.0.0", port 5432
2026-03-02 22:02:58.283 UTC [1] LOG:  listening on IPv6 address "::", port 5432
2026-03-02 22:02:58.291 UTC [1] LOG:  listening on Unix socket "/var/run/postgresql/.s.PGSQL.5432"
2026-03-02 22:02:58.304 UTC [29] LOG:  database system was shut down at 2026-03-02 22:01:48 UTC
2026-03-02 22:02:58.322 UTC [1] LOG:  database system is ready to accept connections

## Describe any configuration issues and how you resolved them
During the Docker setup, the .wslconfig file did not exist in the user directory. Since Docker was running with the WSL2 backend, memory configuration must be controlled through this file. Without it, WSL used the default dynamic memory allocation.
To resolve this issue:
I navigated to C:\Users\DELL
Enabled file name extensions to ensure correct file formatting
Created a new file named .wslconfig (making sure it was not saved as .wslconfig.txt)
Added the following configuration:
``` bash
[wsl2]
memory=4GB
```
Ran wsl --shutdown to apply the changes
Restarted Docker Desktop
Verified the configuration using docker info to confirm the updated memory limit
After creating and configuring the .wslconfig file, Docker successfully applied the memory settings under WSL2.
