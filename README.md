# lolcat++ APT Repository

APT repository for [lolcat++](https://github.com/lolcatpp/lolcatpp) — a C++ port of lolcat.

Hosted via GitHub Pages at <https://lolcatpp.github.io/apt/>.

## Supported distributions

| Family | Versions                          | Architectures |
| ------ | --------------------------------- | ------------- |
| Debian | 13 (Trixie)                       | amd64, arm64  |
| Ubuntu | 24.04 LTS (Noble), 25.04 (Plucky) | amd64, arm64  |
| Mint   | LMDE 7 / 22 / 22.1 / 22.2 / 22.3  | amd64, arm64  |

## Installing

Pick the codename matching your distribution and run:

```bash
sudo install -d /etc/apt/keyrings
. /etc/os-release && \
    CODENAME="${UBUNTU_CODENAME:-$VERSION_CODENAME}" && \
    echo "deb [arch=amd64,arm64 signed-by=/etc/apt/keyrings/lolcatpp.asc] https://lolcatpp.github.io/apt $CODENAME main" \
    | sudo tee /etc/apt/sources.list.d/lolcatpp.list

curl -fsSL https://lolcatpp.github.io/apt/pubkey.gpg | sudo tee /etc/apt/keyrings/lolcatpp.asc > /dev/null

sudo apt update
sudo apt install lolcat++
```

## How packages get here

Packages are built and published automatically by the
[release workflow](https://github.com/lolcatpp/lolcatpp/blob/master/.github/workflows/release.yml)
in the main repository when a new tag is pushed. Each supported distribution
gets its own `.deb` built in a matching container, then `reprepro` adds it to
the corresponding suite in this repository.

The repository indexes are signed with the GPG key in `pubkey.gpg`.
