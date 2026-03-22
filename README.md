
---

# Multiple GitHub Accounts Quick Fix

## 1) আগে remote check করো

```bash
git remote -v
```

* যদি `https://github.com/...` থাকে → conflict হতে পারে
* multiple account হলে **SSH use করাই better**

---

## 2) SSH config check করো

```bash
cat ~/.ssh/config
```

Example:

* `github-office`
* `github-personal`

---

## 3) loaded key check করো

```bash
ssh-add -l
```

---

## 4) specific account test করো

### Personal

```bash
ssh -T git@github-personal
```

### Office

```bash
ssh -T git@github-office
```

---

## 5) correct remote set করো

### Personal repo

```bash
git remote set-url origin git@github-personal:USERNAME/REPO.git
```

### Office repo

```bash
git remote set-url origin git@github-office:ORG_OR_USERNAME/REPO.git
```

---

## 6) আবার remote verify করো

```bash
git remote -v
```

---

## 7) push দাও

```bash
git push -u origin main
```

---

# If error: `Repository not found`

Usually means:

* wrong account use হচ্ছে
* repo private
* wrong remote
* HTTPS cached credential conflict

### Fast fix:

* HTTPS থেকে SSH এ switch করো
* correct SSH alias use করো

---

# New repo rule

### Personal repo হলে:

```bash
git remote add origin git@github-personal:USERNAME/REPO.git
```

### Office repo হলে:

```bash
git remote add origin git@github-office:ORG_OR_USERNAME/REPO.git
```

---

# Your case example

```bash
git remote set-url origin git@github-cdr:Nahin-CDR/NotesApp-iOS.git
ssh -T git@github-cdr || ssh -T git@github-bealiv (for-another)
git push -u origin main
```

---

# Golden rule

**Multiple GitHub account = always use separate SSH alias**
**Avoid HTTPS for private repos with multiple accounts**
