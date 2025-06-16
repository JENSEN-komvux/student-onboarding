# 👋 Välkommen till GitHub på JENSEN komvux!

Den här guiden är för **helt nybörjare** på Windows (WSL) och macOS/Linux.

---

## 🚀 Vad är GitHub?

- En plats för att **lagra kod** och filer  
- En plattform för att **samarbeta** med lärare och klasskamrater  
- Ett system för att **lämna in** och **följa upp** uppgifter  

---

## 🧰 Vad du behöver

1. Ett GitHub-konto — [Registrera dig](https://github.com/join)  
2. E-postadress  
3. **Windows-användare**: en PC med WSL installerat  
4. **macOS/Linux-användare**: Terminal (t.ex. iTerm2 eller standardskal)  
5. En SSH-nyckel för säkra Git-operationer  

---

## ⚙️ Windows-installation: Installera WSL + Ubuntu

1. **Öppna PowerShell som administratör**  
    - Tryck på **Windows-tangenten**, skriv **PowerShell**,  
      högerklicka på **Windows PowerShell**, välj **Kör som administratör**.

2. **Aktivera nödvändiga Windows-funktioner**  
    ```powershell
    dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
    dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
    ```

3. **Starta om datorn**

4. **Installera Ubuntu via WSL**  
    ```powershell
    wsl --install -d Ubuntu
    ```

5. **Skapa din UNIX-användare**  
    - Välj ett användarnamn (t.ex. `tomhanks1337`) och lösenord (dolt medan du skriver).

---

## 🔧 Ubuntu/WSL eller macOS/Linux: Installera Git & konfigurera SSH

1. **Uppdatera systempaket**  
    ```bash
    sudo apt update && sudo apt upgrade -y    # Ubuntu/WSL
    # macOS: brew update
    ```

2. **Installera Git**  
    ```bash
    sudo apt install git -y                   # Ubuntu/WSL
    # macOS: brew install git
    ```

3. **Konfigurera Git**  
    ```bash
    git config --global user.name "Ditt Namn"
    git config --global user.email "din.email@exempel.com"
    ```

4. **Skapa en SSH-nyckel (vi använder namnet jensen som exempel)**  
    ```bash
    ssh-keygen -t rsa -b 4096 -f ~/.ssh/jensen
    ```
    - Tryck **Enter** för att godkänna standardvärden.  
    - (Viktigt: sätt en lösenfras.)

5. **Starta SSH-agenten & lägg till nyckeln**  
    ```bash
    eval "$(ssh-agent -s)"
    ssh-add ~/.ssh/jensen
    ```

6. **Kopiera din publika nyckel**  
    ```bash
    cat ~/.ssh/jensen.pub
    ```
    - Kopiera hela utskriften.

7. **Lägg till SSH-nyckeln i GitHub**  
    - I GitHub: **Settings → SSH and GPG keys → New SSH key**  
    - **Titel**: `WSL Ubuntu` eller `macOS SSH`  
    - **Nyckel**: klistra in den kopierade publika nyckeln  
    - Klicka på **Add SSH key**

8. **(Valfritt) Skapa en SSH-konfigfil**  
    ```bash
    cat <<EOF >> ~/.ssh/config
    Host github.com
      HostName github.com
      User git
      IdentityFile ~/.ssh/jensen
    EOF
    ```

9. **Testa SSH-anslutningen**  
    ```bash
    ssh -T git@github.com
    ```
    - Du bör se:  
      ```
      Hej <användarnamn>! Du har autentiserats korrekt.
      ```

---

## 📦 Kom igång: Klona & Lämna in

1. **Gå med i ett Klassrum**  
    - Läraren delar en inbjudningslänk.  
    - Klicka på länken, logga in via SSH och **acceptera**.

2. **Klona ditt uppgiftsrepo**  
    ```bash
    git clone git@github.com:<org>/<uppgifts-repo>.git
    ```

3. **Gör ditt arbete**  
    ```bash
    cd <uppgifts-repo>
    # redigera filer...
    git add .
    git commit -m "Min inlämning"
    git push origin main
    ```

---

## Tips

- Committa och pusha **ofta**  
- Skicka hellre **flera små** commits än **stora**  
- Använd **tydliga, beskrivande** commit-meddelanden – undvik verb  
- Öppna **Issues** vid frågor eller oklarheter  

Lycka till och ha kul med kodandet! 🎉
