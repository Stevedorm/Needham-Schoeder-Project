# Needham-Schoeder-Project
🧑‍💻 Authors

Steven Dormady & Shea Parcell
James Madison University
CS 457 - Information Security
Fall 2025

🧱 Repository Structure
```text
.
├── amal/
│   ├── amal.c
│   ├── logAmal.txt
│   └── amalKey.bin
│
├── basim/
│   ├── basim.c
│   ├── logBasim.txt
│   └── basimKey.bin
│
├── kdc/
│   ├── kdc.c
│   ├── logKDC.txt
│   └── sessionKey.bin
│
├── dispatcher.c
├── myCrypto.c
├── myCrypto.h
├── wrappers.c
├── wrappers.h
├── Makefile
└── README.md
```


🛡️ Enhanced Needham–Schroeder Symmetric Key Protocol

Secure Mutual Authentication & Session Key Establishment

This repository implements an enhanced version of the Needham–Schroeder Symmetric Key Protocol, designed to provide secure authentication between two parties (traditionally Alice and Bob) using a trusted Key Distribution Center (KDC).

The enhanced version addresses weaknesses in the original protocol (notably replay attacks) through the use of nonces.

🔐 Protocol Summary
Original Needham–Schroeder (Symmetric Key)
<ol>
  A → KDC : IDa, IDb, Na
  
  KDC → A : E - Ka {Ks, len(IDb), IDb, Na, len(tkt), E - Kb {Ks, len(IDa), IDa}}
  
  A → B : E - Kb{Ks, IDa} || Na2
  
  B → A : E - Ks{f(Na2), Nb}
  
  A → B : E - Ks{f(Nb)}
</ol>

