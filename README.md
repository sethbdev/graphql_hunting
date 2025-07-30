# GraphQL Hunting Suite for Nuclei

A comprehensive Nuclei-based scanning suite for identifying GraphQL-related misconfigurations, vulnerabilities and reconnaissance vectors. Designed for bug bounty hunting, red teaming, and appsec testing.

---

## 📁 Directory Structure

 ```
graphql_hunting/
├── graphql-nuclei-suite.yaml
├── helpers/
│   └── wordlists/
│       └── auth-bypass.txt
├── others/
└── README.md
```

---

## 🧠 Features

This suite includes:

| Module                          | Description |
|---------------------------------|-------------|
| `graphql-introspection-post`    | Detects open GraphQL introspection endpoints via POST |
| `graphql-token-bruteforce`      | Attempts to brute-force GraphQL auth tokens using headers |
| `graphql-framework-fingerprint` | Identifies GraphQL backends like Apollo, Graphene, etc. |
| `graphql-json-introspection-heuristics` | Detects introspection leaks using JSON heuristics |
| `graphql-waf-bypass`            | Bypasses WAFs using HTTP header overrides |
| `graphql-dns-exfiltration`      | Leverages DNS-based blind exfiltration via Interactsh |
| `graphql-ssrf-chain`            | Chains introspection to possible SSRF via avatar URL |
| `graphql-sqli-chain`            | Chains introspection to GraphQL SQL injection testing |

---

## 🚀 Usage

### Run all templates:

```bash
nuclei -t graphql_hunting/ -u https://target.com
```

### Run a specific module:

```bash
nuclei -t graphql_hunting/graphql-nuclei-suite.yaml -include-templates graphql-introspection-post -u https://target.com
```

### Chain with recon tools:

```bash
cat urls.txt | nuclei -t graphql_hunting/ -o graphql_findings.txt
```

---

## 🔐 Requirements

- [Nuclei](https://github.com/projectdiscovery/nuclei)
- [Interactsh](https://github.com/projectdiscovery/interactsh) for DNS/http exfil payloads
- `auth_bypass.txt` wordlist (used in token brute-force)
📦 Recommended to run with the latest [ProjectDiscovery templates](https://github.com/projectdiscovery/nuclei-templates)

## 🧪 Wordlists
**auth_bypass.txt** should contain common token values, e.g

```bash
admin
root
bearer test
token123
```

Place it under:
`graphql_hunting/helpers/wordlists/auth_bypass.txt`

## 📚 References
- [GraphQL Introspection Docs](https://graphql.org/learn/introspection/)
- [GraphQL Security Docs](https://graphql.org/learn/security/)
- [Apollo Security Docs](https://www.apollographql.com/docs/apollo-server/security/authentication)
- [PortSwigger Introspection](https://portswigger.net/kb/issues/00200512_graphql-introspection-enabled)
- [Web Security Academy: GraphQL API vulnerabilities](https://portswigger.net/web-security/graphql)

## Shoutout
- [Dolev Farhi](https://github.com/dolevf) great repo's

## Notes
Work in progress. Contributions welcome!
