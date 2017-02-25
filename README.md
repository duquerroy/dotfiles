# dotfiles

[![Aperçu](screenshot.png)](https://raw.githubusercontent.com/duquerroy/dotfiles/master/screenshot.png)

### Packages
Create a backup of what packages are currently installed:

```dpkg --get-selections > package.txt```

Then (on another system) restore installations from that list:

```
dpkg --clear-selections
sudo dpkg --set-selections < package.txt
```

To get rid of stale packages:

```sudo apt-get autoremove```

To get installed like at backup time (i.e. to install packages set by dpkg --set-selections):

```sudo apt-get dselect-upgrade```




### Remapper touches du clavier

Pour remplacer une touche par une autre. Je l'utilise pour ajouter les touches > et < qui ne sont pas sur mon clavier

#### On génère le fichier de map
```xmodmap -pke > ~/.Xmodmap```
#### On trouve la clef a remap
```xev | awk -F'[ )]+' '/^KeyPress/ { a[NR+2] } NR in a { printf "%-3s %s\n", $5, $8 }'```

```keycode  49 = greater less dollar numbersign leftdoublequotemark rightdoublequotemark endash paragraph```

#### On modifie le fichier Xmodmap et on teste avec
```xmodmap ~/.Xmodmap```
