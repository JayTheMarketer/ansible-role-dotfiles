# Ansible Role: Dotfiles

[![Build Status](https://travis-ci.org/jaythemarketer/ansible-role-dotfiles.svg?branch=master)](https://travis-ci.org/jaythemarketer/ansible-role-dotfiles)

Installs a set of dotfiles from a given Git repository. By default, it will install my (jaythemarketer's) [dotfiles](https://github.com/jaythemarketer/dotfiles), but you can use any set of dotfiles you'd like, as long as they follow a conventional format.

## Requirements

Requires `git` on the managed machine (you can easily install it with `jaythemarketer.git` if required).

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    dotfiles_repo: "https://github.com/jaythemarketer/dotfiles.git"
    dotfiles_repo_version: master

The git repository and branch/tag/commit hash to use for retrieving dotfiles. Dotfiles should generally be laid out within the root directory of the repository.

    dotfiles_repo_accept_hostkey: false

Add the hostkey for the repo url if not already added. If ssh_opts contains "-o StrictHostKeyChecking=no", this parameter is ignored.

    dotfiles_repo_local_destination: "~/dotfiles"

The local path where the `dotfiles_repo` will be cloned.

    dotfiles_home: "~"

The home directory where dotfiles will be linked. Generally, the default should work, but in some circumstances, or when running the role as sudo on behalf of another user, you may want to specify the full path.

    dotfiles_files:
      - .bash_profile
      - .gitignore
      - .inputrc
      - .vimrc

Which files from the dotfiles repository should be linked to the `dotfiles_home`.

## Dependencies

None

## Example Playbook

    - hosts: localhost
      roles:
        - { role: jaythemarketer.dotfiles }

## License

Apache 2.0

## Author Information

This role was created in 2018 by [JayTheMarketer](https://linkedin.com/in/JayTheMarketer), a Marketing Technology Consultant for [Bulldog Solutions](https://www.bulldogsolutions.com/).
