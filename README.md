# eve-ng-multitabbed-on-linux

this will use konsole as the default terminal emulator for eve-ng on linux boxes

### Requirements
Install konsole by running the command below on terminal
>sudo apt update && sudo apt upgrade -y
>sudo apt install konsole gedit
>wget -qO- https://raw.githubusercontent.com/SmartFinn/eve-ng-integration/master/install.sh | sh

### Configuring the eve-ng linux client

- Open EVE-NG file configuration.
```
cp /usr/bin/eve-ng-integration /usr/bin/eve-ng-integration.bak
sudo gedit /usr/bin/eve-ng-integration
```

- Change the _terminal_emulator_cmd(self) class
```
    def _terminal_emulator_cmd(self):
        if self.override_terminal:
            return self.override_terminal.split()
        elif self._is_command('x-terminal-emulator'):
            return ['konsole', '--new-tab', '-e']
        elif self._current_desktop('cinnamon', 'gnome', 'unity'):
            return ['konsole', '--new-tab', '-e']
        elif self._current_desktop('kde'):
            return ['konsole', '--new-tab', '-e']
        elif self._current_desktop('lxde', 'lxqt'):
            return ['konsole', '--new-tab', '-e']
        elif self._current_desktop('mate'):
            return ['konsole', '--new-tab', '-e']
        elif self._current_desktop('pantheon'):
            return ['konsole', '--new-tab', '-e']
        elif self._current_desktop('xfce'):
            return ['konsole', '--new-tab', '-e']
        elif self._is_command('urxvt'):
            return ['konsole', '--new-tab', '-e']
        else:
            return ['konsole', '--new-tab', '-e']
```
- Restart and test the terminal.
- have fun.
 
