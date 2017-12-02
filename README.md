# ansible-role-irssi

[![Build Status](https://travis-ci.org/tkimball83/ansible-role-irssi.svg?branch=master)](https://travis-ci.org/tkimball83/ansible-role-irssi)

Linux/macOS - Your text mode chatting application since 1999

## Requirements

This role requires homebrew if executed on macOS

## Role Variables

Available variables are listed below, along with default values:

    irssi_channels:
      - name: '#linuxhq'
        chatnet: linuxhq
        autojoin: True
    irssi_chatnets:
      linuxhq:
        type: IRC
    irssi_ignores:
      - exception: False
        level:
          - CTCPS
          - DCC
        mask:
          - '*'
    irssi_servers:
      - address: irc.linuxhq.org
        autoconnect: True
        chatnet: linuxhq
        port: 6697
        ssl_verify: True
        use_ssl: True
    irssi_settings:
      core:
        nick: "{{ ansible_user_id }}"
        real_name: "{{ ansible_user_gecos }}"
        user_name: "{{ ansible_user_id }}"

Additional variables not defined by default:

    irssi_scripts:
      - name: script.pl
        base64: |
          {...}
    irssi_theme: http://irssi-import.github.io/themes/initrd.theme

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
              autojoin: True
          irssi_chatnets:
            efnet:
              type: IRC
          irssi_ignores: []
          irssi_servers:
            - address: irc.prison.net
              autoconnect: True
              chatnet: efnet
            - address: irc.servercentral.net
              autoconnect: True
              chatnet: efnet
          irssi_settings:
            core:
              nick: tkimball
              real_name: 'Taylor Kimball'
              user_name: tkimball

## License

GPLv3

## Author Information

This role was created by [Taylor Kimball](http://www.linuxhq.org).
