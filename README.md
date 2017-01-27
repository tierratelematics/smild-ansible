# Ansible Role: Frontend build

## Requirements

Ansible 2.0 or later
Smild 3.0 or later

## Role Variables

1. `project_name` (default: ``): the name of project
2. `docker_image_version` (default: ``): the tag version of project
3. `docker_build_path` (default: `{{playbook_dir}}/../docker`): the path of Docker
4. `project_root_dir` (default: `{{playbook_dir}}/../`): the root of project
5. `typings_installer` (default: `False`): <boolean> the need to install type with typings
6. `docker_push` (default: `False`): the need to push docker image
7. `docker_registry` (default: `345762685377.dkr.ecr.eu-west-1.amazonaws.com`): docker registry
8. `docker_image_tag` (default: `{{docker_registry}}/{{project_name}}:{{docker_image_version}}`): the complete name of image
9. `git_pull_required` (default: `false`): the need to pull image from git repository
10. `project_repo` (default: ``): the url of git repository
11. `repo_branch` (default: `remotes/origin/develop`): the branch of git repository that you want to pull

## Git pull
if you want to pull a repository you have to change the settings:
     - docker_build_path: "{{playbook_dir}}/../project/docker",
     - project_root_dir: "{{playbook_dir}}/../project/"

## Dependencies

None.

## Example Playbook

    - hosts: localhost
      connection: local
      gather_facts: False

      roles:
        - { role: frontend_builder,
            project_name: "iot-prettygoat-fe",
            docker_image_version: "0.1.0",
            git_pull_required: True,
            project_repo: "https://github.com/tierratelematics/prettygoat-fe.git",
            project_root_dir: "{{playbook_dir}}/../project",
            docker_build_path: "{{playbook_dir}}/../project/docker",
            project_root_dir: "{{playbook_dir}}/../project/"
        }