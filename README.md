# ansible-pi

Ansible playbook for setting up and configuring my Raspberry Pi.

## Full setup

### Write image to USB stick

- [Raspberry Pi imager](https://www.raspberrypi.com/software/)
- Settings:

  ```
  OS: Raspberry Pi OS Lite (64-bit)

  Set hostname: pi

  Enable SSH:
    Allow public-key authentication only
      Set authorized_keys for 'pi': <PUBLIC KEY>

  Set username and password
    Username: pi
    Password: <PASSWORD>

  Set locale settings
    Time zone: Europe/London
    Keyboard layout: gb
  ```

### Install ansible dependencies

```sh
ansible-galaxy collection install -r requirements.yml
```

### Run playbook

```sh
ansible-playbook -v main.yml
```

### Addition manual set up

#### Pihole

1. Change password

   ```
   docker container exec -it pihole /bin/bash
   pihole -a p
   ```

1. Restore from backup in admin

   ```
   Settings > Teleporter > Restore
   ```

1. Update Gravity in admin

   ```
   Tools > Update Gravity > Update
   ```

#### Plex
