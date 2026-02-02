# bad_usernames

A curated list of **usernames that should not be allowed** in real-world applications where users can choose their own username.

This list helps prevent issues such as:
- URL path conflicts
- Subdomain misuse
- Confusing or deceptive usernames
- Email alias abuse
- Security and phishing risks

---

## 🛡️ Why This Matters

Usernames may appear in URLs, subdomains, and email addresses. Some names are harmless (e.g., `john_smith`), but others — like `support`, `admin`, or `root` — can conflict with application routes, trusted services, or reserved aliases.

For more details on the motivations and risks behind these restrictions, see the original documentation in this repository.

---

## 📂 Included Files

This repository contains:

- `COMBINED_bad_usernames.json` – The combined list of all blacklisted usernames
- Additional language-specific JSON files (if added in future)
- `README.md` – This documentation
- `LICENSE` – MIT License

---

## 🚫 Example Use Cases for Blacklisting

### 🔗 URL Paths

If your app exposes user content at a path like:

- https://example.com/<username>/...
- 
A username like `support` could collide with important application routes, e.g.:


---

### 🌍 Subdomains

Some apps use usernames as subdomains:

If `username = secure`, this could expose or impersonate:

---

### 📧 Email Aliases

If usernames are used to generate email addresses:


 usernames like `admin`, `root`, `support`, etc., could be misused for phishing or social engineering.

---

## 🧠 Recommended Username Validation Rules

In addition to using this blacklist:

### ✅ Character Set

- Restrict to **ASCII** characters (e.g., `a–z`, `0–9`)
- Avoid confusing Unicode look-alikes

### 🔡 Normalization

- Convert all usernames to **lowercase**
- Reject duplicates after normalization

### ➕ Limited Symbols

- Only allow a small set of symbols (e.g., `_`)
- Disallow at beginning or end

### 📏 Length Requirements

- Minimum length: **3 characters**
- Maximum length: **128 characters**

### 📌 Prefix/Suffix Rules

- Reject usernames that begin or end with blacklisted terms (e.g., `admin-web`)
- Reject simple pluralizations (`admins`, `supporters`) unless explicitly safe

---

## 🚀 How to Use

1. Import the JSON file into your application
2. Check proposed usernames against this blacklist
3. Reject or sanitize usernames before account creation

Example (JavaScript):

```js
const blacklist = require('./COMBINED_bad_usernames.json');

function isValidUsername(username) {
  return !blacklist.includes(username.toLowerCase());
}
```

## 🤝 Contributing

Please send pull requests to https://github.com/6abc/bad_usernames/pulls. Especially for other languages.
