a `backend` and `frontend` overlay network are needed. Nothing different about them other then that backend will help protect database from the voting web app. (similar to how a VLAN setup might be in traditional architecture).

**To do that, it's needed to create first 2 network overlays, named 'backend' and 'frontend'**.
**The commands are:** 
- *docker network create --driver overlay frontend* 
- *docker network create --driver overlay backend*

