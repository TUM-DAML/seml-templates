# `SEML` Templates

This repository contains templates for [`seml`](https://github.com/TUM-DAML/seml-templates.git).

## Project structure
This repository has the following structure 
```
.
├── LICENSE
├── README.md
└── templates
    ├── default
    └── ...
```
where each subdirectory of `templates` represents a separate template.

### Template structure
Templates may be represented by an arbitrary file structure. To allow for custom paths and names, python string formatting is performed on file paths, e.g., `src/{project_name}` will be translated to `src/my_first_project`. To perform formatting within files, simply store them as `.template` files.

This `pyproject.toml.template`
```toml
[project]
name = "{project_name}"
version = "0.0.1"
```
will be translated to the following `pyproject.toml`:
```toml
[project]
name = "my_first_project"
version = "0.0.1"
```
when initializing a new project with
```sh
seml project init -t default my_first_project
```

## Using templates
To use these templates, install [`seml`](https://github.com/TUM-DAML/seml-templates.git) via
```sh
pip install seml
```
Navigate into an empty directory
```sh
mkdir my_project
cd my_project
```
And create the project via
```sh
seml project init -t default .
```
where `-t` allows you to specify the template and `.` specifies the directory where the project should be initialized.

### Using other templates
You may want to initialize a template from a different origin, in this case you can supply the exact git remote via `-r`, git commit/branch/tag via `-c`
```sh
seml project init -t my_template -o my_remote.git -c commit_hash .
```
