# Smild Ansible

## Requirements

* Ansible 2.0 or later
* Smild 3.0 or later

## Role Variables

    create_version_files: True                                                              # the need to create version files
    docker_build_path: "{{playbook_dir}}/../docker/"                                        # the path of Docker
    docker_build: False                                                                     # the need to build docker image
    docker_image_tag: "{{docker_registry}}/{{project_name}}:{{docker_image_version}}"       # the complete name of image
    docker_image_version: ""                                                                # the tag version of project
    docker_push: False                                                                      # the need to push docker image
    docker_registry: ""                                                                     # docker registry
    git_pull_required: False                                                                # the need to pull image from git repository
    minify_smild: True                                                                      # the need to minify build
    npm_install_peers: False                                                                # the need to install peer dependencies
    project_name: ""                                                                        # the name of project
    project_repo: ""                                                                        # the url of git repository
    project_root_dir: "{{playbook_dir}}/../"                                                # the root path of project
    project_type:                                                                           # the project type (frontend | nodejs | module)
    prune_dev_dependencies: False                                                           # the need to prune devDependencies
    repo_branch: "remotes/origin/develop"                                                   # the branch of git repository that you want to pull
    s3_bucket: ""                                                                           # the s3 bucket endpoint
    s3_sync: False                                                                          # the need to sync with s3 bucket
    smild_target_build: "main"                                                              # the target of smild build
    typings_installer: False                                                                # the need to install type with typings
    version_files_path: "{{project_root_dir}}/dist/{{smild_target_build}}"                  # the path of version files

### Note
With ``npm_install_peers: True`` you must install **npm-install-peers** module globally in your machine with:

    npm install npm-install-peers -g


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
        - { role: tierratelematics.smild-ansible,
            project_name: "iot-prettygoat-fe",
            docker_image_version: "0.1.0",
        }

## License

Copyright 2016 Tierra SpA

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

[http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.