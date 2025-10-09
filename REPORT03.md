@4723229 ➜ /workspaces/WE-Docker2 (main) $ docker ps
CONTAINER ID   IMAGE         COMMAND                  CREATED          STATUS          PORTS                                         NAMES
236c8b016c8d   postgres:15   "docker-entrypoint.s…"   9 seconds ago    Up 8 seconds    5432/tcp                                      we-docker2-db-1
ecfecf5eb6da   fastapi-app   "uvicorn main:app --…"   11 minutes ago   Up 11 minutes   0.0.0.0:8000->8000/tcp, [::]:8000->8000/tcp   my-fastapi-container
