# spi_ip

SPI IP project UVM verification description

## Contents

- [spi\_ip](#spi_ip)
  - [Contents](#contents)
  - [Git configuration](#git-configuration)
  - [Generate an SSH key](#generate-an-ssh-key)
  - [Add the SSH key to GitHub](#add-the-ssh-key-to-github)
  - [Configure SSH for GitHub](#configure-ssh-for-github)
  - [Repository download](#repository-download)
  - [Git flow](#git-flow)
  - [Bring changes from `main` into a feature branch](#bring-changes-from-main-into-a-feature-branch)
  - [Weekly meetings](#weekly-meetings)
    - [Indico](#indico)
  - [Toolchain](#toolchain)
    - [Vivado](#vivado)
  - [Contacts](#contacts)

## Git configuration

Ensure that the version of your Git installation is > 1.8 with:

```bash
git --version
```

The first time you use `git` you need to configure:

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

You can check your configuration at any time with:

```bash
git config --list
```

## Generate an SSH key

You can interact with GitHub using either **HTTPS** or **SSH**. The **recommended** protocol is SSH,
because it uses a pair of **private/public keys** and does not require password authentication.

To use SSH you first need to [generate a new SSH key pair](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#generating-a-new-ssh-key) with:

```bash
cd ~/.ssh
ssh-keygen -t ed25519 -C "your_email@example.com"
```

- If the `~/.ssh` directory doesn't already exist, create it with:

  ```bash
  mkdir ~/.ssh
  ```

- When prompted for the file name, use a meaningful name such as `id_ed25519_github`.
- Enter a passphrase when asked (recommended for security).

## Add the SSH key to GitHub

Next, add your SSH **public key** to your GitHub account.

Display the public key with:

```bash
cat id_ed25519_github.pub
```

Then:

- Click you GitHub profile picture.
- Navigate to **Settings > SSH and GPG keys > New SSH Key**. See your [SSH keys](https://github.com/settings/keys).
- Create a new key entry and paste the public key content.

## Configure SSH for GitHub

Finally create (or edit) the `~/.ssh/config` file to tell SSH which key to use for GitHub:

```bash
# GitHub account
Host github.com
  HostName github.com
  PreferredAuthentications publickey
  IdentityFile ~/.ssh/id_ed25519_github
```

## Repository download

Download the repository using:

```bash
cd /path/to/your/working/area
git clone git@github.com:uvm-collab/spi_ip.git
```

When prompted for authentication, enter the chosen SSH key passphrase to complete the download.

## Git flow

Use Git [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/)

1. Create branch

```bash
git switch -c feat/uvc-monitor-logic
# ot
git branch feat/uvc-monitor-logic && git switch feat/uvc-monitor-logic
```

2. Work, add, commit (small commits, Conventional Commits)

```bash
git add monitor.sv
git commit -m "feat: add monitor logic"
```

3. Push your branch to GitHub

```bash
git push -u origin feat/uvm-monitor-logic
```

4. Open **Pull Request** in GitHub.

   - Use a clear Conventional Commit PR tittle
   - Push more commits as needed

5. Merge **Pull Request**

    - Use yout team's choice (Merge commits/Squash)
    - Click **Delete branch** in GitHub

6. Clean up locally and prune stale remotes

```bash
git switch main
git fetch --prune origin
git branch -D feat/uvm-monitor-logic
```

7. Sync your local `main` branch (fast-forward only)

```bash
git pull --ff-only origin main
```

## Bring changes from `main` into a feature branch

When working on a feature branch, you often need to update it with the latest changes from `main`.
The recommended approach is:

```bash
git switch feat/branch
git fetch origin main
git merge origin/main
# resolve conflicts if any, then commit
```

## Weekly meetings

[Zoom link](https://cern.zoom.us/j/65700168865?pwd=9QOp3oZxutaNAaiJuaPSUa6tDaOdw3.1)

### Indico

[indico.global - UVM Verification Collaboration](https://indico.global/category/1375/)

## Toolchain

### Vivado

- [Installing Vivado](docs/vivado_install.md)
- [Setting Up Environment](docs/setup_env.md)

### Manuals

1. [(UG900) Vivado Design Suite User Guide - Logic Simulation](https://docs.amd.com/viewer/book-attachment/U8cK6J65oySTywrNQQKQKw/etODWMMLPls2y3sy8nmaMg-U8cK6J65oySTywrNQQKQKw)
2. [(UG937) Vivado Design Suite Tutorial - Logic Simulation](https://docs.amd.com/viewer/book-attachment/AQgD74oGsbut9Xk6PJxfeg/ru_jonSSGpL1ZaPwb3D3cA-AQgD74oGsbut9Xk6PJxfeg)
3. [(UG906) Vivado Design Suite User Guide - Design Analysis and Closure Techniques](https://docs.amd.com/viewer/book-attachment/HKXDYGChb9XYiCDCLp4tqA/1UwxVI3GMJjdVgdG3TrZBQ-HKXDYGChb9XYiCDCLp4tqA)

> [!IMPORTANT]  
> All manuals are from the year 2025

## Contacts

| Person                        | Email                           | Institute |
| ----------------------------- | ------------------------------- | --------- |
| Ciro Fabian Bermudez Marquez  | <cirofabian.bermudez@gmail.com> | INFN Bari |
| Luis Enrique Namigtle Jimenez | <namigtle066@gmail.com>         | INAOE     |
| Miguel Angel Aleman Arce      | <alemanmig@gmail.com>           | CIC IPN   |
