# broctopusdundee
bruv, this is it.

## Devcontainer info

-   /opt/conda/bin/python → Python 3.12

-   fastapi, uvicorn, scikit-learn installed

-   Ports 8000 (FastAPI) & 8888 (JupyterLab) forwarded

-   Linting, formatting & Jupyter extensions ready to go

-   To edit FastAPI app, spin it up with:

    -   `uvicorn app.main:app --reload --host 0.0.0.0 --port 8000`

-   to launch JupyterLab:

    -   `jupyter lab --ip=0.0.0.0 --port=8888 --no-browser --allow-root`

-   Note:

    -   All dependency changes—adding new libraries, locking versions, etc.—go into environment.yml, and a quick rebuild (or micromamba install -f environment.yml) will keep everyone in sync.

-   To switch to root
    -   `sudo -i     # drops you into a root shell` or `sudo su     # equivalent`