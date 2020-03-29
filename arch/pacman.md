# Pacman / AUR / trizen


## Searching with trizen

```
trizen -Ss paket
```

## Which packages depend on another packager?

```
# normal
pacman -Qi <paket> 
# AUR
pacman -Sii <paket> 
```
## Cleanup

```
# clear package cache
pacman -Sc 
# clear package cache including installed packages (only the packages, not the installation itself)
pacman -Scc 
installiertes)
#???
pacman -Rns $(pacman -Qtdq)
```
