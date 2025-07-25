# ✅ GitHub Codespaces SSH Setup Cheat Sheet

## 🛠 Use this if you get a `403: Permission Denied` error when pushing to GitHub in Codespaces.

---

### 🔧 1. **Switch Remote URL to SSH**

```bash
git remote set-url origin git@github.com:USERNAME/REPO.git
```

---

### 🧪 2. **Test SSH Connection**

```bash
ssh -T git@github.com
```

- If you see `Permission denied (publickey)`, continue with the steps below.

---

### 🔍 3. **Check for Existing SSH Keys**

```bash
ls -al ~/.ssh
```

---

### 🔐 4. **Generate a New SSH Key (if needed)**

```bash
ssh-keygen -t ed25519 -C "your-email@example.com"
```

- Press **Enter** to accept default file path.
- Leave passphrase empty (optional).

---

### 🔑 5. **Add the SSH Key to the Agent**

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

---

### 📋 6. **Copy Your Public Key**

```bash
cat ~/.ssh/id_ed25519.pub
```

---

### 🌐 7. **Add SSH Key to GitHub**

- Go to [GitHub → Settings → SSH and GPG Keys](https://github.com/settings/keys)
- Click **"New SSH key"**
- Paste your copied key
- Save

---

### 🔁 8. **Test SSH Again**

```bash
ssh -T git@github.com
```

- You should see:  
  `Hi USERNAME! You've successfully authenticated...`

---

### 🚀 9. **Push to GitHub**

```bash
git push origin main
```

---

Now you’re fully connected to GitHub via SSH from Codespaces!
