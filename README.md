# Needham-Schoeder-Project
🧑‍💻 Authors

Steven Dormady & Shea Parcell
James Madison University
CS 457 - Information Security
Fall 2025

🧱 Repository Structure
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
├── myCrypto.c            # AES, nonce operations, and cryptographic utilities
├── myCrypto.h
│
├── wrappers.c            # Utility wrapper functions for IPC, forking, pipes
├── wrappers.h
│
├── Makefile              # Build script for full project
│
└── README.md


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

