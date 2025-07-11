---
icon: truck-container-empty
---

# Manage Containers

### Practice Questions: "Manage Containers" (RHCSA v9)

Below are exam-style questions covering every subtopic in both "Manage security" and "Manage containers" as required by RHCSA v9.

## <mark style="color:green;">Questions</mark>

**Find and retrieve container images from a remote registry**

* Search for the latest `nginx` image on a remote registry (e.g., `registry.redhat.io` or `docker.io`).
* Pull the `nginx` image to your local system using `podman`.

**Inspect container images**

* Inspect the `nginx` image and display its environment variables and exposed ports.

**Perform container management using commands such as podman and skopeo**

* List all local container images.
* Use `skopeo` to inspect a remote image without pulling it.

**Perform basic container management such as running, starting, stopping, and listing running containers**

* Run a container from the `nginx` image in detached mode, mapping port 8080 on the host to port 80 in the container.
* List all running containers.
* Stop and remove the running `nginx` container.

**Run a service inside a container**

* Run an `httpd` container and ensure the web service is accessible on port 8081 of the host.

**Configure a container to start automatically as a systemd service**

* Generate a systemd unit file for a `podman` container and enable it to start at boot.

**Attach persistent storage to a container**

* Create a directory `/srv/webdata` on the host.
* Run an `nginx` container with `/srv/webdata` mounted as `/usr/share/nginx/html` inside the container.
* Verify that files created in `/srv/webdata` are visible from within the container.

***

## <mark style="color:yellow;">Answers</mark>

**Find and retrieve container images from a remote registry**

* podman search nginx
* podman pull nginx

**Inspect container images**

* podman inspect nginx

**Perform container management using commands such as podman and skopeo**

* podman images
* skopeo inspect docker://docker.io/library/nginx

**Perform basic container management such as running, starting, stopping, and listing running containers**

* podman run -d -p 8080:80 nginx
* podman ps
* podman stop 8abc5adefdaa
* podman rm 8abc5adefdaa

**Run a service inside a container**

* podman run -d --name httpdwebsite -p 8081:80 httpd

**Configure a container to start automatically as a systemd service**

* podman generate systemd --name httpdwebsite --files
* mkdir -p .config/systemd/user
* cp container-httpdwebsite.service ./.config/systemd/user/
* systemctl enable --now container-httpdwebsite.service
* systemctl status container-httpdwebsite.service

**Attach persistent storage to a container**

* mkdir -p /srv/webdata
* podman run -d --name nginx -p 8083:80 -v /srv/webdata:/usr/share/nginx/html nginx
* Open a web browser and search for localhost:8083



⁂
