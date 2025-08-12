# Cybersecurity: Viruses, Attacks, Encryption/Decryption, RSA / DSA / DSS

---

## 1. Malware & Viruses — overview

**Malware** = any software intentionally designed to cause harm (viruses, worms, trojans, ransomware, spyware, rootkits, etc.).  
**Virus (classical definition)** — a type of malware that attaches to host files or programs and requires user action (or another trigger) to propagate. It typically modifies other executable code to insert copies of itself.

### Virus lifecycle (typical)
- **Dormant** — inactive until triggered.
- **Propagation / infection** — attaches to files/boot sectors/macros/etc.
- **Trigger** — an event/time/user action that starts payload.
- **Payload execution** — what the virus does (delete files, open backdoor, etc.).
- **Concealment** — stealth techniques to avoid detection.

### Common virus types & related malware taxa
- **File-infecting viruses** — attach to executable files (.exe, .dll). Infect when file is run.
- **Boot-sector viruses** — infect the Master Boot Record (MBR) or partition boot sector; run at system start.
- **Macro viruses** — written in macro languages (VBA) and target Office documents.
- **Polymorphic viruses** — change their code/signature constantly to evade signature-based detection.
- **Metamorphic viruses** — rewrite their own code entirely while preserving functionality (more advanced).
- **Multipartite viruses** — infect both boot sector and files (multi-vector).
- **Memory-resident viruses** — stay in memory and intercept OS calls.
- **Ransomware** (often not a “virus” technically) — encrypts user data and demands payment.
- **Rootkits** — hide presence by subverting OS/kernel (stealth).

### Detection & mitigation (high-level)
- Use up-to-date **antivirus/EDR** (Endpoint Detection & Response).
- **Application whitelisting**, patching, least privilege, and disabling macros by default.
- Regular **backups** (offline copies) and tested recovery plans.
- Network segmentation to limit spread.

---

## 2. Types of Attacks — classification, examples & mitigations

> Attacks can be classified by *goal* (data theft, disruption, sabotage), *vector* (email, web, network), or *technique* (exploit, social engineering).

### Major attack categories (with short definitions & mitigations)

- **Phishing / Social engineering**
  - **What**: Fraudulent messages to trick users into revealing credentials or running malware.
  - **Mitigation**: User training, email filtering, MFA, link/attachment sandboxing.

- **Malware attacks (viruses, trojans, ransomware)**
  - **What**: Malicious programs executed on endpoints/servers.
  - **Mitigation**: EDR, application whitelisting, patching, least privilege, backups.

- **Man-in-the-Middle (MitM)**
  - **What**: Intercepting/altering communications between two parties.
  - **Mitigation**: Use TLS, certificate validation, HSTS, secure DNS (DNSSEC), avoid unsecured Wi-Fi.

- **Denial-of-Service (DoS / DDoS)**
  - **What**: Flood resource to make services unavailable.
  - **Mitigation**: Rate limiting, CDN / scrubbing services, autoscaling, network filtering.

- **Injection attacks (SQLi, Command Injection)**
  - **What**: Injecting malicious input into interpreter/DB queries.
  - **Mitigation**: Parameterized queries/ORM, input validation, least privilege DB accounts, WAF.

- **Cross-Site Scripting (XSS)**
  - **What**: Injecting client-side script into web pages viewed by others.
  - **Mitigation**: Output encoding, CSP, input validation, secure frameworks.

- **Cross-Site Request Forgery (CSRF)**
  - **What**: Forcing an authenticated user to perform unwanted actions.
  - **Mitigation**: Anti-CSRF tokens, SameSite cookies.

- **Remote Code Execution (RCE)**
  - **What**: Attacker executes arbitrary code remotely via vulnerability.
  - **Mitigation**: Patch management, input sanitization, runtime protections.

- **Privilege Escalation**
  - **What**: Gaining higher privileges than intended (vertical/horizontal).
  - **Mitigation**: Minimize admin accounts, patch vulnerabilities, monitoring & EDR.

- **Supply Chain Attacks**
  - **What**: Compromise at vendor/library that propagates to consumers.
  - **Mitigation**: Dependency scanning, vendor assessment, code signing, reproducible builds.

- **Credential stuffing / brute force**
  - **What**: Automated attempts using leaked credentials or brute force.
  - **Mitigation**: Rate limiting, MFA, detection of abnormal auth patterns.

- **Side-channel attacks**
  - **What**: Extracting secrets by measuring timing, power, cache behavior.
  - **Mitigation**: Constant-time algorithms, hardware mitigations, segmentation.

**General mitigations across attack types**
- Patching and configuration hygiene.
- Defense in depth (multiple controls).
- Monitoring & logging (SIEM).
- Strong authentication (MFA), secure coding practices.
- Regular backups and incident response plans.

---

## 3. Encryption & Decryption — core concepts

### 3.1 Goals of cryptography
- **Confidentiality** — hide content from unauthorized parties.
- **Integrity** — detect modifications (hashes, MACs).
- **Authenticity / Non-repudiation** — prove origin (digital signatures).
- **Key management** — secure creation, distribution, rotation, storage of keys.

### 3.2 Symmetric vs Asymmetric cryptography
- **Symmetric (secret-key)**  
  - Same key for encryption & decryption. Fast, suited for bulk data.
  - Examples: **AES**, 3DES (legacy), ChaCha20.
  - Key distribution is the main challenge.
- **Asymmetric (public-key)**  
  - Key pair: public key (encrypt / verify) and private key (decrypt / sign).
  - Slower; useful for key exchange, signatures, small messages.
  - Examples: **RSA**, **DSA**, **ECC** (ECDSA, ECDH), **ElGamal**.

### 3.3 Hybrid encryption
- Use asymmetric crypto to securely exchange a symmetric session key; use symmetric cipher (AES) for data. This combines performance + secure key distribution (common in TLS).

### 3.4 Hash functions vs MACs vs Signatures
- **Hash (one-way)**: SHA-256, SHA-3 — maps data → fixed digest. Used for integrity checks and signatures.
- **MAC (Message Authentication Code)**: HMAC-SHA256 — keyed hash for integrity + authenticity with a shared secret.
- **Digital signature**: Sign(hash(message)) with a private key; verify with public key (non-repudiation).

---

## 4. Encryption Standards & Methods (practical)

### 4.1 Symmetric algorithms & recommendations
- **AES** (Advanced Encryption Standard) — block cipher, 128-bit block, key sizes 128/192/256. **AES-GCM** or **AES-CCM** recommended for authenticated encryption (AEAD).
- **ChaCha20-Poly1305** — stream cipher + MAC; excellent performance on mobile/low-end CPUs; also AEAD.
- **3DES / DES** — **deprecated** (weak, small key size).
- **Modes of operation** (for block ciphers):
  - **ECB** — insecure (reveals patterns).
  - **CBC** — needs IV & padding; vulnerable to certain padding oracle attacks if misused.
  - **CTR** — turns block cipher into stream; needs unique nonce.
  - **GCM** — provides confidentiality + integrity (AEAD); widely recommended.
- **Authenticated encryption (AEAD)** — use AES-GCM or ChaCha20-Poly1305 to get both encryption and authentication in one primitive.

### 4.2 Asymmetric algorithms & uses
- **RSA** — public-key encryption and signatures (PKCS#1); performance slower, used for key exchange & signatures.
- **Diffie-Hellman (DH / ECDH)** — secure key exchange (no encryption by itself).
- **DSA** — Digital Signature Algorithm (signature only).
- **ECDSA / EdDSA (Ed25519)** — elliptic-curve signatures; smaller keys, faster, increasingly preferred.

### 4.3 Hash & signature standards
- **SHA-2** family (SHA-256/384/512) — recommended for hashing.
- **SHA-1**, **MD5** — deprecated (collision weaknesses).
- **HMAC** — HMAC-SHA256 for authenticated messages.
- **FIPS 186 (DSS)** — Digital Signature Standard (specifies DSA; later revisions include ECDSA as approved).

### 4.4 Key derivation & password hashing
- **KDFs**: PBKDF2, bcrypt, scrypt, Argon2 — use for deriving keys from passwords; Argon2 recommended for new systems.
- **Salts**: Always use a unique salt per password.

### 4.5 Transport & application standards
- **TLS 1.3** — current recommended for secure transport (uses AEAD ciphers, ephemeral key exchange).
- **SSH** — secure remote shell (modern configs use strong key types like Ed25519/ECDSA).
- **S/MIME / PGP** — email encryption/signing schemes using PKI.

---

## 5. RSA — deeper dive

### 5.1 Basic math & key generation (high level)
- Choose two large primes `p` and `q`. Compute `n = p * q`.  
- Compute φ(n) = (p-1)(q-1).  
- Choose public exponent `e` (commonly 65537).  
- Compute private exponent `d` such that `d * e ≡ 1 (mod φ(n))`.  
- **Public key** = (n, e). **Private key** = d (and optionally p, q for fast math).

### 5.2 Encryption / Decryption (concept)
- **Encrypt**: `c = m^e mod n`  
- **Decrypt**: `m = c^d mod n`  
*(In practice, padding and encoding schemes are used — you should never use raw RSA without padding.)*

### 5.3 Signatures (concept)
- **Sign**: `s = (hash(m))^d mod n` (conceptual; in practice use RSA-PSS or PKCS#1 v2.2)
- **Verify**: Check `s^e mod n == hash(m)` (again, real schemes use secure padding).

### 5.4 Padding & security
- **OAEP** (Optimal Asymmetric Encryption Padding) — recommended for RSA encryption.
- **PSS** (Probabilistic Signature Scheme) — recommended for RSA signatures.
- **Key sizes**: **2048-bit** minimum (short-term); **3072/4096** for longer-term protection. Use ECC if you need similar strength with smaller keys.

### 5.5 Notes & pitfalls
- RSA is slow for large data — use hybrid encryption (RSA to protect symmetric key).
- Never implement crypto primitives yourself — use vetted libraries.
- Protect private keys (HSM, secure key stores), rotate keys, and use secure random sources.

---

## 6. DSA and DSS — what they are

### 6.1 DSA (Digital Signature Algorithm)
- **Purpose**: Digital signatures only (does not encrypt data).
- Based on the **discrete logarithm problem** modulo a prime `p` and subgroup order `q`.
- Signing requires an ephemeral random value `k` for each signature:
  - `r = (g^k mod p) mod q`
  - `s = k^-1 (H(m) + x * r) mod q`  (where `x` is private key)
- **Security note**: Reusing or leaking `k` across signatures completely exposes the private key.

### 6.2 DSS (Digital Signature Standard)
- **DSS** = a U.S. federal standard (FIPS 186) that *specifies* algorithms for digital signatures — originally DSA; later revisions include other approved algorithms (e.g., ECDSA).
- DSS sets parameter sizes, hash function choices, and algorithm usage policies for federal systems.

### 6.3 ECDSA / EdDSA
- **ECDSA** — elliptic-curve variant of DSA (smaller key, similar security).
- **EdDSA (Ed25519)** — modern, fast, deterministic signature scheme with good performance and security properties.

---

## 7. Practical recommendations / best practices

- **Use AEAD ciphers** (AES-GCM or ChaCha20-Poly1305) for confidentiality + integrity.
- **Prefer TLS 1.3** for communications (uses modern cipher suites).
- **Use strong hashes** (SHA-256/384) — avoid SHA-1/MD5.
- **Prefer ECC/Ed25519** for signatures and ECDHE for ephemeral key exchange when possible (smaller keys, faster).
- **RSA**: If required, use RSA-OAEP for encryption & RSA-PSS for signatures; use at least 2048-bit keys.
- **Key management**: secure key storage (HSMs), rotate keys, use hardware-backed keys for critical assets.
- **Don’t invent crypto**: rely on well-reviewed libraries (OpenSSL, libsodium, BoringSSL, WebCrypto).
- **Randomness**: use OS-provided CSPRNGs (e.g., `/dev/urandom`, Windows CryptoAPI) — entropy is crucial.
- **Defense in depth**: combine cryptography with access control, monitoring, and secure development lifecycle.

---

## 8. Quick glossary
- **AEAD** — Authenticated Encryption with Associated Data.
- **KDF** — Key Derivation Function (PBKDF2, Argon2).
- **OAEP / PSS** — Secure padding schemes for RSA.
- **PKI** — Public Key Infrastructure; X.509 certificates bind public keys to identities.
