# Install WireGuard on Raspberry PI

1. `echo "deb http://archive.raspbian.org/raspbian testing main" | sudo tee --append /etc/apt/sources.list.d/testing.list`
2. `printf 'Package: *\nPin: release a=testing\nPin-Priority: 50\n' | sudo tee --append /etc/apt/preferences.d/limit-testing` 
3. `sudo apt-get update`
4. `sudo apt install wireguard -y`
