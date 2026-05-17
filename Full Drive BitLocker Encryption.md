# Full Drive BitLocker Encryption (Windows 11 Pro)
Author: Kellie Hucker  

## Overview
This project documents enabling full disk encryption using BitLocker on Windows 11 Pro to protect data at rest. BitLocker ensures that sensitive data remains protected if a device is lost, stolen, or accessed outside of a trusted boot environment.

## Objective
- Encrypt the entire OS drive using BitLocker  
- Protect data at rest from unauthorized access  
- Configure secure key management and recovery options  
- Establish a hardened baseline for a cybersecurity workstation  

## Scope
- Windows 11 Pro system  
- TPM-based encryption  
- Full drive encryption (not used space only)  

## Why This Matters
Without full disk encryption:
- Data can be accessed by removing the drive  
- Attackers can boot from external media  
- Sensitive files may be recoverable from unallocated space  
BitLocker mitigates these risks by enforcing encryption tied to trusted platform integrity.


## Key Actions Taken
- Verified TPM availability and readiness  
- Enabled BitLocker on the OS drive  
- Selected full drive encryption  
- Used XTS-AES encryption mode  
- Secured recovery key in multiple locations  
- Validated encryption completion  

## Key Steps (Technical Summary)
### 1. Verify TPM Availability
Confirmed TPM is present and ready: `Get-Tpm`

### 2. Enable BitLocker
Enabled BitLocker on the OS drive using system settings or Control Panel.

### 3. Configure Startup Protection
Configured TPM-based protection.

_Optional: TPM + PIN for increased security._

### 4. Back Up Recovery Key
Stored recovery key securely in multiple locations:
- Microsoft account
- Offline backup (USB)

### 5. Select Full Drive Encryption
Choose full disk encryption to protect previously deleted data.

### 6. Select Encryption Mode
Used XTS-AES _(modern BitLocker encryption mode for fixed drives)_.

### 7. Start Encryption
Initiated encryption and allowed the process to complete while on AC power.

### 8. Validate Encryption Status
`manage-bde -status C:`

## Confirmed:
 - Fully Encrypted
 - Protection On
 - 100 percent completion

## Outcome
 - Full disk encryption successfully enabled
 - Data at rest is protected against unauthorized access
 - System aligned with security best practices
 - Device ready for secure cybersecurity lab usage

## Skills Demonstrated
 - Endpoint security
 - Encryption configuration (BitLocker)
 - Key management and recovery planning
 - OS hardening
 - Risk mitigation for data at rest

## Operational Considerations
 - Firmware or boot changes may trigger recovery key prompts
 - Always store recovery keys in multiple secure locations
 - Suspend BitLocker before major BIOS or boot changes

## Result
Established a secure, encrypted baseline that protects against unauthorized data access and supports safe cybersecurity lab operations.

## Security Notes
This project is intended for learning, personal security practice, and portfolio demonstration.
