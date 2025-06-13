# 👋 Welcome to GitHub at JENSEN komvux!

This guide is for **absolute beginners** on Windows (WSL) and macOS/Linux.

---

## 🚀 What is GitHub?

- A place to **store code** and files  
- A platform to **collaborate** with teachers & classmates  
- A system to **submit** and **track** assignments  

---

## 🧰 What You Need

1. A GitHub account — [Sign up](https://github.com/join)  
2. Email address  
3. **Windows users**: a PC with WSL installed  
4. **macOS/Linux users**: Terminal (e.g., iTerm2 or default shell)  
5. An SSH key for secure Git operations  

---

## ⚙️ Windows Setup: Install WSL + Ubuntu

1. **Open PowerShell as Administrator**  
    - Press the **Windows key**, type **PowerShell**,  
      right-click **Windows PowerShell**, select **Run as administrator**.

2. **Enable necessary Windows features**  
    ```powershell
    dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
    dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
    ```
3. **Reboot your PC**

4. **Install Ubuntu via WSL**  
    ```powershell
    wsl --install -d Ubuntu
    ```
5. **Create your UNIX user**  
    - Choose a username (e.g., `tomhanks1337`) and password (hidden as you type).

---

## 🔧 Ubuntu/WSL or macOS/Linux Setup: Install Git & Configure SSH

1. **Update system packages**  
    ```bash
    sudo apt update && sudo apt upgrade -y    # Ubuntu/WSL
    # macOS: brew update
    ```

2. **Install Git**  
    ```bash
    sudo apt install git -y                   # Ubuntu/WSL
    # macOS: brew install git
    ```

3. **Configure Git**  
    ```bash
    git config --global user.name "Your Name"
    git config --global user.email "your.email@example.com"
    ```

4. **Generate an SSH key (we use the name jensen as an example, you can use anything you'd like**  
    ```bash
    ssh-keygen -t rsa -b 4096 -f ~/.ssh/jensen
    ```
    - Press **Enter** to accept defaults.  
    - (Important: set a passphrase.)

5. **Start the SSH agent & add your key**  
    ```bash
    eval "$(ssh-agent -s)"
    ssh-add ~/.ssh/jensen
    ```

6. **Copy your public key**  
    ```bash
    cat ~/.ssh/jensen.pub
    ```
    - Copy the entire output.

7. **Add SSH key to GitHub**  
    - In GitHub: **Settings → SSH and GPG keys → New SSH key**  
    - **Title**: `WSL Ubuntu` or `macOS SSH`  
    - **Key**: paste the copied public key  
    - Click **Add SSH key**

8. **(Optional) Create an SSH config file**  
    ```bash
    cat <<EOF >> ~/.ssh/config
    Host github.com
      HostName github.com
      User git
      IdentityFile ~/.ssh/jensen
    EOF
    ```

9. **Test your SSH connection**  
    ```bash
    ssh -T git@github.com
    ```
    - You should see:  
      ```
      Hi <username>! You've successfully authenticated.
      ```

---

## 📦 Quick Start: Cloning & Submitting

1. **Join a Classroom**  
    - Teacher shares an invitation link.  
    - Click it, log in via SSH, and **Accept**.

2. **Clone Your Assignment Repo**  
    ```bash
    git clone git@github.com:<org>/<assignment-repo>.git
    ```

3. **Do Your Work**  
    ```bash
    cd <assignment-repo>
    # edit files...
    git add .
    git commit -m "My submission"
    git push origin main
    ```

---

## Tips

- Commit and push **often**  
- Push **small** commits rather than **big** ones  
- Use **clear, descriptive** commit messages, avoid **verbs*  
- Open **Issues** for questions or clarifications  

Good luck and happy coding! 🎉
