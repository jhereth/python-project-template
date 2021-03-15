@PHONY: bootstrap install-requirements update-requirements

.venv/touchfile:
	PYENV_VERSION=3.9.1 python3 -m venv .venv
	.venv/bin/python3 -m pip install -r requirements-bootstrap.txt
	.venv/bin/python3 -m pip install --upgrade pip
	touch .venv/touchfile

bootstrap: .venv/touchfile

requirements.txt: bootstrap requirements.in
	.venv/bin/pip-compile -v requirements.in

install-requirements: requirements.txt
	.venv/bin/pip-sync -v requirements.txt

install-jupyterlab-extensions:
	.venv/bin/nbdime extensions --enable
	.venv/bin/jupyter labextension install jupyterlab-plotly@4.14.3

update-requirements: 
	.venv/bin/pip-compile -vU requirements.in



