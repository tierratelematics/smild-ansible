# Smild Ansible

## Requirements

* Ansible 2.0 or later
* Smild 3.0 or later

## Role Variables

    project_name: ""                                                                        # the name of project
    docker_image_version: ""                                                                # the tag version of project
    docker_build_path: "{{playbook_dir}}/../docker/"                                        # the path of Docker
    project_root_dir: "{{playbook_dir}}/../"                                                # the root path of project
    typings_installer: False                                                                # the need to install type with typings
    docker_push: False                                                                      # the need to push docker image
    docker_registry: ""                                                                     # docker registry
    docker_image_tag: "{{docker_registry}}/{{project_name}}:{{docker_image_version}}"       # the complete name of image
    git_pull_required: False                                                                # the need to pull image from git repository
    project_repo: ""                                                                        # the url of git repository
    repo_branch: "remotes/origin/develop"                                                   # the branch of git repository that you want to pull


## Git pull
if you want to pull a repository you have to change the settings:
``` 
docker_build_path: "{{playbook_dir}}/../project/docker",
project_root_dir: "{{playbook_dir}}/../project/" 
```

## Example Playbook

    - hosts: localhost
      connection: local
      gather_facts: False

      roles:
        - { role: smild-ansible,
            project_name: "iot-prettygoat-fe",
            docker_image_version: "0.1.0",
        }