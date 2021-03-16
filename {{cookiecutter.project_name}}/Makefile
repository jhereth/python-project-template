.venv/touchfile:
	PYENV_VERSION=3.9.1 python3 -m venv .venv
	.venv/bin/python3 -m pip install -r requirements-bootstrap.txt
	.venv/bin/python3 -m pip install --upgrade pip
	touch .venv/touchfile

@PHONY: bootstrap
bootstrap: .venv/touchfile

requirements.txt: bootstrap requirements.in
	.venv/bin/pip-compile -v requirements.in

@PHONY: install-requirements
install-requirements: requirements.txt
	.venv/bin/pip-sync -v requirements.txt

{% if cookiecutter.jupyter == "Y" -%}
@PHONY: install-jupyterlab-extensions
install-jupyterlab-extensions:
	.venv/bin/nbdime extensions --enable
	.venv/bin/jupyter labextension install jupyterlab-plotly@4.14.3

{% endif -%}
@PHONY: update-requirements
update-requirements: 
	.venv/bin/pip-compile -vU requirements.in



