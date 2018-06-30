# ansible-role-irssi

[![Build Status](https://travis-ci.org/tkimball83/ansible-role-irssi.svg?branch=master)](https://travis-ci.org/tkimball83/ansible-role-irssi)
[![Ansible Galaxy](https://img.shields.io/badge/ansible--galaxy-irssi-blue.svg?style=flat)](https://galaxy.ansible.com/tkimball83/irssi)
[![License](https://img.shields.io/badge/license-GPLv3-brightgreen.svg?style=flat)](COPYING)

Linux/macOS - Your text mode chatting application since 1999

## Requirements

This role requires homebrew if executed on macOS

## Role Variables

Available variables are listed below, along with default values:

    irssi_config_dir: "{{ ansible_env.HOME }}/.irssi"
    irssi_config_file: "{{ irssi_config_dir }}/config"
    irssi_config_owner: "{{ ansible_real_user_id }}"
    irssi_config_group: "{{ ansible_real_group_id }}"
    irssi_channels:
      - name: '#linuxhq'
        chatnet: linuxhq
        autojoin: true
    irssi_chatnets:
      linuxhq:
        type: IRC
    irssi_ignores:
      - exception: false
        level:
          - CTCPS
          - DCC
        mask:
          - '*'
    irssi_servers:
      - address: irc.linuxhq.org
        autoconnect: true
        chatnet: linuxhq
        port: 6697
        ssl_verify: true
        use_ssl: true
    irssi_settings:
      core:
        nick: "{{ ansible_real_user_id }}"
        real_name: "{{ ansible_user_gecos }}"
        user_name: "{{ ansible_real_user_id }}"
    irssi_scripts: []
    irssi_theme: ''

## Dependencies

None

## Example Playbook

    - hosts: localhost
      connection: local
      roles:
        - role: tkimball83.irssi
          irssi_channels:
            - name: '#efnet'
              chatnet: efnet
              autojoin: true
          irssi_chatnets:
            efnet:
              type: IRC
          irssi_ignores: []
          irssi_servers:
            - address: irc.prison.net
              autoconnect: true
              chatnet: efnet
            - address: irc.servercentral.net
              autoconnect: true
              chatnet: efnet
          irssi_settings:
            core:
              nick: tkimball
              real_name: 'Taylor Kimball'
              user_name: tkimball
          irssi_scripts:
            - name: script.pl
              base64: |
                {...}
          irssi_theme: http://irssi-import.github.io/themes/initrd.theme

## License

Copyright (C) 2018 Taylor Kimball <tkimball@linuxhq.org>

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program. If not, see <http://www.gnu.org/licenses/>.
