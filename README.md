# mongodb-recovery-
Read‑only MongoDB recovery tool. Recover corrupted WiredTiger .wt data files &amp; damaged mongodump archives, carve BSON documents from raw disk‑partition images, supports MongoDB 3.2‑8.0.
# MongoDB Recovery Tool

Read‑only offline forensic recovery utility for MongoDB WiredTiger storage‑engine databases.

## Overview
Official `mongod --repair` will discard corrupted documents during repair operations, and `mongorestore` fails against truncated or damaged mongodump archives.
This tool performs pure read‑only parsing against corrupted WiredTiger `.wt` collection files, broken mongodump backup archives. It can also carve fragmented BSON documents directly from raw disk‑partition forensic images. No modification is applied to source evidence.

> Note: This tool targets **WiredTiger storage‑engine only (MongoDB 3.2‑8.0)**. MMAPv1 engine is not supported.

## Supported Versions
‑ MongoDB 3.2
‑ MongoDB 3.4
‑ MongoDB 3.6
‑ MongoDB 4.0
‑ MongoDB 4.2
‑ MongoDB 4.4
‑ MongoDB 5.0
‑ MongoDB 6.0
‑ MongoDB 7.0
‑ MongoDB 8.0

## Core Capabilities
‑ Extract BSON documents from corrupted WiredTiger `.wt` collection files
‑ Recover data from damaged/truncated mongodump backup archives
‑ Rescue data when MongoDB instance cannot start, WT_PANIC panic error occurs
‑ Carve fragmented BSON documents from raw disk‑partition images
‑ Preview recoverable collections and BSON records before export
‑ 100% read‑only workflow; source files and disk‑image evidence remain untouched

## Use Cases
‑ WiredTiger database corruption, mongod cannot start, WT_PANIC error
‑ Missing or damaged WiredTiger metadata catalog `_mdb_catalog.wt`
‑ mongodump backup archive corrupted, `mongorestore` parse failure
‑ Accidentally deleted collections, only disk partition image available
‑ Forensic investigation for MongoDB raw disk images

## How It Works
1. Load corrupted `.wt` file, damaged mongodump archive or raw disk‑partition image in read‑only mode.
2. Parse WiredTiger page structures or scan disk image for BSON document signatures for data carving.
3. Identify and reconstruct recoverable BSON documents.
4. Preview recoverable collections and document content.
5. Export salvageable data to usable BSON / JSON output format.

## Important Notice
This is offline forensic analysis tool.
**Never run this tool directly against live production database directories.** Always work on copies or disk forensic images.
Different from official `mongod --repair`: this tool will NOT delete or modify any source data.

## Download
Get latest Windows binary release on GitHub Releases.

> Pre‑built Windows x64 zip package contains read‑only MongoDB recovery client.

## Antivirus Note
> ⚠️ Windows binary protected with VMProtect anti‑tampering. Some antivirus software may trigger heuristic false‑positive alerts. The tool runs fully read‑only and never modifies source files or disk‑image evidence.

## Contact
For bug reports, technical feedback or feature requests please open GitHub issues.
