# osslsigncode change log

### 2.4 (unreleased)

- set the default message digest to sha256
- set of cryptographic hash functions for "attach -signature"
  and "add" commands ("-h" option)
- compute and compare the leaf certificate hash for "attach-signature"
  command ("-require-leaf-hash" option)
- "-st" option renamed to "-time"
- user-specified signing and/or verifying time ("-time" option)
- remove "-timestamp-expiration" option
- disable verification of the Timestamp Server signature
  ("-ignore-timestamp" option)
- use CMake instead of Makefile

### 2.3 (2022.03.06)

**CRITICAL SECURITY VULNERABILITIES**

This release fixes several critical memory corruption vulnerabilities.
A malicious attacker could create a file, which, when processed with
osslsigncode, triggers arbitrary code execution.  Any previous version
of osslsigncode should be immediately upgraded if the tool is used for
processing of untrusted files.

- fixed several memory safety issues
- fixed non-interactive PVK (MSBLOB) key decryption
- added a bash completion script
- added CA bundle path auto-detection

### 2.2 (2021.08.15)

- CAT files support (thanks to James McKenzie)
- MSI support rewritten without libgsf dependency, which allows
  for handling of all the needed MSI metadata, such as dates
- "-untrusted" option renamed to "-TSA-CAfile"
- "-CRLuntrusted" option renamed to "-TSA-CRLfile"
- numerous bug fixes and improvements

### 2.1 (2020-10-11)

- certificate chain verification support
- timestamp verification support
- CRL verification support ("-CRLfile" option)
- improved CAB signature support
- nested signatures support
- user-specified signing time ("-st" option) by vszakats
- added more tests
- fixed numerous bugs
- dropped OpenSSL 1.1.0 support

### 2.0 (2018-12-04)

- orphaned project adopted by Michał Trojnara
- ported to OpenSSL 1.1.x
- ported to SoftHSM2
- add support for pkcs11-based hardware tokens
  (Patch from Leif Johansson)
- improved error reporting of timestamping errors
  (Patch from Carlo Teubner)

### 1.7.1 (2014-07-11)

- MSI: added -add-msi-dse option
  (Patch from Mikkel Krautz)
- MSI: fix build when GSF_CAN_READ_MSI_METADATA defined
  (Patch from Mikkel Krautz)

### 1.7 (2014-07-10)

- add support for nested signatures
  (Patch from Mikkel Krautz)
- fix compilation problem with OpenSSL < 1.0.0
- added OpenSSL linkage exception to license

### 1.6 (2014-01-21)

- add support for reading password from file
- add support for asking for password (on systems that
  provide support for it)
- add support for compiling and running on Windows
  (Patch from Heiko Hund)
- fix compilation without curl
  (Fix from Heiko Hund)
- added support for giving multiple timestamp servers
  as arguments (first one that succeeds will be used)
- signatures on hierarchical MSI files were broken
  (Fix from Mikkel Krautz)
- MSI: Add support for MsiDigitalSignatureEx signature
  (Patch from Mikkel Krautz)
- add support for adding additional/cross certificates
  through -ac option
  (Thanks to Lars Munch for idea + testing)
- MSI: Add support for signature extract/remove/verify
  (Patches from Mikkel Krautz)
- PE/MSI: Implement -require-leaf-hash for verify.
  (Patch from Mikkel Krautz)

### 1.5.2 (2013-03-13)

- added support for signing with SHA-384 and SHA-512
- added support for page hashing (-ph option)

### 1.5.1 (2013-03-12)

- forgot to bump version number...

### 1.5 (2013-03-12)

- added support for signing MSI files (patch from Marc-André Lureau)
- calculate correct PE checksum instead of setting it to 0
  (patch from Roland Schwingel)
- added support for RFC3161 timestamping (-ts option)
- added support for extracting/removing/verifying signature on PE files
- fixed problem with not being able to decode timestamps with no newlines
- added stricter checks for PE file validity
- added support for reading keys from PVK files (requires OpenSSL 1.0.0 or later)
- added support for reading certificates from PEM files
- renamed program option: -spc to -certs (old option name still valid)

### 1.4 (2011-08-12)

- improved build system (patch from Alon Bar-Lev)
- support reading cert+key from PKCS12 file (patch from Alon Bar-Lev)
- support reading key from PEM file
- added support for sha1/sha256 - default hash is now sha1
- added flag for commercial signing (default is individual)

### 1.3.1 (2009-08-07)

- support signing of 64-bit executables (fix  from Paul Kendall)

### 1.3 (2008-01-31)

- fixed padding problem (fix from Ryan Rubley)
- allow signing of already signed files (fix from Ryan Rubley)
- added Ryan Rubley's PVK-to-DER guide into the README

### 1.2 (2005-01-21)

- autoconf:ed (Thanks to Roy Keene)
- added documentation
- don't override PKCS7_get_signed_attribute, it wasn't
  actually needed, it was me being confused.
- compiles without curl, which means no timestamping
- version number output

### 1.1 (2005-01-19)

- Initial release
