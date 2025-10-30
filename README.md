# Experiment 1: Decentralized Certificate Verification
## NAME : LEKASRI G
## REGISTER NUMBER : 212223100025
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
bytes32 certHash = keccak256(abi.encodePacked(studentName, degree,
year));
certificates[certHash] = true;
emit CertificateIssued(certHash);
}
function verifyCertificate(string memory studentName, string memory degree,
uint256 year) public view returns (bool) {
bytes32 certHash = keccak256(abi.encodePacked(studentName, degree,
year));
return certificates[certHash];
}
}
```
# Expected Output:

<img width="1920" height="1080" alt="Screenshot 2025-10-30 112122" src="https://github.com/user-attachments/assets/5269b7d3-d4d1-4efb-b0f5-92370e930621" />

<img width="1920" height="1080" alt="Screenshot 2025-10-30 112142" src="https://github.com/user-attachments/assets/14b16823-5153-44ee-8932-c0bee420fbc5" />

```
● When the university issues a certificate, it gets stored as a hash.
● A student or employer can verify the certificate by entering the details.
● If valid, it returns true; otherwise, false.
High-Level Overview:
● Used to prevent fake certificates.
● Enables quick verification by employers or other institutions.
● Shows how blockchain can be used in education and credential verification.
```
# Result:

Thus, the smart contract was successfully implemented to issue and verify academic certificates on Ethereum, ensuring authenticity and preventing forgery.
