{% set is_open_source = cookiecutter.open_source_license != 'Not open source' -%}
# {{ cookiecutter.project_name }}

{% if is_open_source %}
<p align="center">
<a href="https://pypi.python.org/pypi/{{ cookiecutter.repository_name }}">
    <img src="https://img.shields.io/pypi/v/{{ cookiecutter.repository_name }}.svg"
        alt = "Release Status">
</a>

<a href="https://github.com/{{ cookiecutter.github_user_or_org_name }}/{{ cookiecutter.repository_name }}/actions">
    <img src="https://github.com/{{ cookiecutter.github_user_or_org_name }}/{{ cookiecutter.repository_name }}/actions/workflows/main.yml/badge.svg?branch=release" alt="CI Status">
</a>

<a href="https://{{ cookiecutter.github_user_or_org_name }}.github.io/{{ cookiecutter.repository_name }}/">
    <img src="https://img.shields.io/website/https/{{ cookiecutter.github_user_or_org_name }}.github.io/{{ cookiecutter.repository_name }}/index.html.svg?label=docs&down_message=unavailable&up_message=available" alt="Documentation Status">
</a>
</p>
{% endif %}

{{ cookiecutter.project_short_description }}

{% if is_open_source %}

* Free software: {{ cookiecutter.open_source_license }}
* Documentation: <https://{{ cookiecutter.github_user_or_org_name }}.github.io/{{ cookiecutter.repository_name }}/>

{% endif %}

## Features

* TODO

## Credits

This package was created with [Cookiecutter](https://github.com/audreyr/cookiecutter) and the [innovativeSol/innovative-pip-cookiecutter-pypackage](https://github.com/innovativeSol/innovative-pip-cookiecutter-pypackage) project template.
