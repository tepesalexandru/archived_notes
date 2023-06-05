The Linux filesystem's table, aka `fstab` (`/etc/fstab`), is a configuration table designed to ease the burden of mounting and unmounting file systems to a machine.

### Table Structure
The table itself is a 6 column structure, where each column designates a specific parameter and must be set up in the correct order.

The columns are:
1. Device
2. Mount Point
3. File System Type
4. Options
5. Backup Operation
6. File System Check Order