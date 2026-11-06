### Experiment 1: Decentralized Certificate Verification
## NAME : YAZHINI R R
## REG NO : 212224100063
## Aim:
  To develop a smart contract for issuing and verifying academic certificates on Ethereum, preventing forgery and ensuring authenticity.
## Algorithm:
1. Deploy a smart contract where universities can issue certificates.
2. Store a hash of certificate data on-chain.
3. Provide a verification function that checks certificate authenticity.
4. Users can verify the certificate by comparing the stored hash.
## Program:
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;
contract CertificateVerification {
address public university;
mapping(bytes32 => bool) public certificates; // Store hashed certificates
event CertificateIssued(bytes32 indexed certHash);
constructor() {
university = msg.sender; // University deploys the contract
}
function issueCertificate(string memory studentName, string memory degree, uint256 year) public {
require(msg.sender == university, "Only university can issue certificates");
bytes32 certHash = keccak256(abi.encodePacked(studentName, degree, year));
certificates[certHash] = true;
emit CertificateIssued(certHash);
}
function verifyCertificate(string memory studentName, string memory degree, uint256 year) public view returns (bool) {
bytes32 certHash = keccak256(abi.encodePacked(studentName, degree, year));
return certificates[certHash];
}
}
```
# Expected Output:
```
● When the university issues a certificate, it gets stored as a hash.
● A student or employer can verify the certificate by entering the details.
● If valid, it returns true; otherwise, false.
High-Level Overview:
● Used to prevent fake certificates.
● Enables quick verification by employers or other institutions.
● Shows how blockchain can be used in education and credential verification.
```
# Output :
<img width="1600" height="923" alt="image" src="https://github.com/user-attachments/assets/e03703e2-8ade-472a-a52f-073dc43a6b21" />
<img width="1600" height="913" alt="image" src="https://github.com/user-attachments/assets/a6f0e07e-51d8-44a1-9bbb-7d0e766f3df9" />
<img width="1600" height="856" alt="image" src="https://github.com/user-attachments/assets/34d145f5-4ec3-49e8-b786-667cdf9d8759" />


# Result:
Thus, to develop a smart contract for issuing and verifying academic certificates on Ethereum, preventing forgery and ensuring authenticity is done successfully
