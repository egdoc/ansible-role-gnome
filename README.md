Ansible Role: gnome
==================

Ansible role to configure the GNOME desktop environment.

Requirements
------------
This role requires the "dbus-daemon", "dconf" and "python3-psutil" packages to be installed
on the target hosts.

Role Variables
--------------

        gnome_dock_launchers:
          - org.gnome.Software.desktop
          - org.gnome.TextEditor.desktop
          - org.gnome.Nautilus.desktop

List of application launchers to place in GNOME Shell dock.

        gnome_keyboard_layouts:
            - us

List of keyboard layouts you want to activate.

        gnome_app_folders:
            - name: Utilities
              apps:
                - org.gnome.DiskUtility.desktop
                - org.gnome.font-viewer.desktop
                - org.gnome.Loupe.desktop

List of dictionaries describing GNOME app folders and the application launchers
they should contain.

        gnome_custom_keybindings:
            - name: Launch terminal
              command: ptyxis --new-window
              binding: <Super>Return

List of dictionaries describing custom keybindings. Each dictionary must have three keys: `name`, `command` and `binding`.

        gnome_shell_enabled_extensions: []

List of GNOME shell extensions ID to enable (the role won't install the extensions).

        gnome_enable_event_sounds: false

Whether to enable GNOME event sounds.

        gnome_touchpad_tap_to_click: true

Whether to enable touchpad "tap to click".

        gnome_mouse_natural_scroll: false

Whether to enable mouse "natural scroll" feature.

        gnome_session_idle_delay: 300

Number of seconds of inactivity after which a session is considered idle. Default is 5 minutes (300 seconds).

        gnome_sleep_inactive_ac_timeout: 1800
        gnome_sleep_inactive_ac_action: suspend

These two variables describe the number of seconds of inactivity after which the specified action should
be executed on ac, and the action itself. Supported actions are: "blank", "suspend", "shutdown", "hibernate",
"interactive", "nothing" and "logout". The default is to suspend the system after 30 minutes of inactivity (1800 seconds).

        gnome_sleep_inactive_battery_timeout: 900
        gnome_sleep_inactive_battery_action: suspend

These two variables describe the number of seconds of inactivity after which the specified action should
be executed on battery, and the action itself. Supported actions are: "blank", "suspend", "shutdown", "hibernate",
"interactive", "nothing" and "logout". The default is to suspend the system after 15 minutes of inactivity (900 seconds).

        gnome_additional_dconf_rules: []

List of dictionaries specifying additional dconf keys and their values (see example playbook below).


Dependencies
------------
None

Example Playbook
----------------

        - hosts: all
          roles:
            - role: egdoc.gnome
              gnome_shell_enabled_extensions:
                - appindicatorsupport@gcjonas.gmail.com
              gnome_additional_dconf_rules:
                - key: /org/gnome/nautilus/default-zoom-level
                  value: "'small'"

License
-------

GPLv2

Author Information
------------------
Created by Egidio Docile
