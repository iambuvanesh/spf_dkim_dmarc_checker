# 🔍 SPF-DKIM-DMARC Checker

A bash-based tool for checking the **SPF**, **DKIM**, and **DMARC** records of multiple domains from a list. Ideal for cybersecurity researchers, red teamers, and email security auditors. 💻

---

## ✨ Features

- ✅ Bulk domain scanning
- ✅ Validates SPF records
- ✅ Checks for DKIM with a given selector
- ✅ Extracts DMARC policy and reports syntax issues
- ✅ Lightweight and terminal-based

---

## 🔧 Installation

```bash
git clone https://github.com/iambuvanesh/spf_dkim_dmarc_checker.git
cd spf_dkim_dmarc_checker
chmod +x spf_dkim_dmarc_checker.sh
````

---

## 🚀 Usage

```bash
./spf_dkim_dmarc_checker.sh <domain_list.txt> <dkim_selector>
```

**Example:**

```bash
./spf_dkim_dmarc_checker.sh domains.txt default

(or)

bash spf_dkim_dmarc_checker.sh domains.txt default
```

* `domain_list.txt`: A file with one domain per line.
* `dkim_selector`: Common selectors are `default`, `google`, `mail`, etc.

---

## 📥 Input Format

Example `domains.txt`:

```
example.com
gmail.com
yahoo.com
```

---

## 🖼️ How to use

![How to use](https://github.com/iambuvanesh/spf_dkim_dmarc_checker/blob/main/static/How%20to%20use.png)

---

## 📚 What is SPF/DKIM/DMARC?

* **SPF (Sender Policy Framework):** Specifies which servers can send emails on behalf of a domain.
* **DKIM (DomainKeys Identified Mail):** Adds a cryptographic signature to emails for integrity.
* **DMARC (Domain-based Message Authentication, Reporting, and Conformance):** Provides instructions on how to handle messages that fail SPF/DKIM and sends feedback reports.

---

## 🤝 Contributing

Contributions are welcome!

1. Fork this repo
2. Create your feature branch: `git checkout -b feature/your-feature`
3. Commit your changes
4. Push to the branch and submit a pull request

See [CONTRIBUTING.md](https://github.com/iambuvanesh/spf_dkim_dmarc_checker/blob/main/CONTRIBUTING.md) for full guidelines.

---

## 📝 License

This project is licensed under the [LICENSE](https://github.com/iambuvanesh/spf_dkim_dmarc_checker/blob/main/LICENSE).

---

## 👨‍💻 Author

Maintained by [@iambuvanesh](https://github.com/iambuvanesh) – Cybersecurity Researcher 🕵️‍♂️

---

