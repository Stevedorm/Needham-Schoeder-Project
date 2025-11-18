# Needham-Schoeder-Project
🧑‍💻 Authors

Steven Dormady & <a href="https://github.com/Shea-Parcell">Shea Parcell</a><br>
James Madison University<br>
CS 457 - Information Security<br>
Fall 2025<br>

🛡️ Enhanced Needham–Schroeder Symmetric Key Protocol

Secure Mutual Authentication & Session Key Establishment

This repository implements an enhanced version of the Needham–Schroeder Symmetric Key Protocol, designed to provide secure authentication between two parties (traditionally Alice and Bob) using a trusted Key Distribution Center (KDC).

The enhanced version addresses weaknesses in the original protocol (notably replay attacks) through the use of nonces.


🧱 Repository Structure
```text
.
├── amal/
│   ├── amal.c            # Client A (Amal)
│   ├── logAmal.txt       # Amal runtime log
│   └── amalKey.bin       # Amal's long-term symmetric key
│
├── basim/
│   ├── basim.c           # Client B (Basim)
│   ├── logBasim.txt      # Basim runtime log
│   └── basimKey.bin      # Basim's long-term symmetric key
│
├── kdc/
│   ├── kdc.c             # Key Distribution Center (KDC)
│   ├── logKDC.txt        # KDC runtime log
│   └── sessionKey.bin    # Latest issued session key
│
├── dispatcher.c          # Orchestrates running Amal, Basim, and the KDC
│
├── myCrypto.c            # AES, nonce ops, crypto utilities
├── myCrypto.h
│
├── wrappers.c            # Utility wrappers for forking, pipes, I/O
├── wrappers.h
│
├── Makefile              # Build script
│
└── README.md
```


🔐 Protocol Summary
Original Needham–Schroeder (Symmetric Key)
<ol>
  <li>A → KDC : IDa, IDb, Na</li>
  
  <li>KDC → A : E - Ka {Ks, len(IDb), IDb, Na, len(tkt), E - Kb {Ks, len(IDa), IDa}}</li>
  
  <li>A → B : E - Kb{Ks, IDa} || Na2</li>
  
  <li>B → A : E - Ks{f(Na2), Nb}</li>
  
  <li>A → B : E - Ks{f(Nb)}</li>
</ol>

