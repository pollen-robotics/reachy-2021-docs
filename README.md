## Installer Hugo

Sur MacOS :

```bash
brew install hugo
```

Sur Ubuntu 20.04

```bash
cd ~/Downloads
curl -s https://api.github.com/repos/gohugoio/hugo/releases/latest \
 | grep  browser_download_url \
 | grep Linux-64bit.deb \
 | grep -v extended \
 | cut -d '"' -f 4 \
 | wget -i -
sudo dpkg -i hugo*_Linux-64bit.deb
```

## Installer npm

Sur MacOS :

```bash
brew install npm
```

Sur Ubuntu 20.04

```bash
sudo apt install npm
```

## Cloner reachy-2023-docs et installer les dépendances

```bash
git clone https://github.com/pollen-robotics/reachy-2023-docs.git
npm install
```

Pour générer le site en local :

```bash
hugo server -D
```

L’option -D permet de régénerer le site automatiquement à chaque modification du contenu.

Le site est accessible à l’adresse [http://localhost:1313/](http://localhost:1313/)

### Note

Si un problème survient lors de la génération du site en local, supprimer le dossier /node_modules et refaire un npm install, cela peut résoudre le problème.
