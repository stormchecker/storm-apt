# Debian/Ubuntu packages of Storm
We provide `.deb` packages of [Storm](https://www.stormchecker.org/) for Debian-based distributions.

## Versions
We provide packages for different systems:
- `debian12-nightly` runs on Debian 12 and Ubuntu 24.04 LTS
- `debian13-nightly` runs on Debian 13 and Ubuntu 26.04 LTS

Please select the correct version depending on your system.

## Preparation
First, we install the depedencies for obtaining the public signing key:
```
sudo apt-get install curl gnupg
```
Next, we import the public key with which the packages are signed:
```
curl -fsSL https://stormchecker.github.io/storm-apt/storm-debian.gpg \
  | sudo gpg --dearmor -o /etc/apt/keyrings/storm-debian.gpg
```
Afterward, create a new source for the Storm packages.
In this example we use `debian13-nightly`.
You can replace it with the version you need.
```
echo "deb [signed-by=/etc/apt/keyrings/storm-debian.gpg] https://stormchecker.github.io/storm-apt debian13-nightly main" \
  | sudo tee /etc/apt/sources.list.d/storm-nightly.list
```

## Installation
After finishing the preparation once, new versions of Storm can be installed as usual:
```
sudo apt-get update
sudo apt-get install storm
```
Package updates of Stom will be automatically found and installed.
