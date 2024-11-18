# Minihack Investigation Setup
This repository has been created as a touchstone for creating a dependency issue free version of the minihack library for Python 3.8.

I Have created this for my ongoing research into PCG using symbiotic deep learning agents consisting of both player and designer to generate balanced levels for Rogue-like games.

To use this repo the following can be used to run the environment:
Please first create a .env within the directory, setting a SECRET_TOKEN used to login to Jupyter-notebook and a LOCAL_PORT defining the port you wish to port forward,
e.g.
```
# .env
LOCAL_PORT=<your_port>
SECRET_TOCKEN=<your_secret>
```
then run the following commands.
```bash
git clone https://github.com/just-oliver/Minihack-PCGRL-research
cd Minihack-PCGRL-research
docker compose up
```
