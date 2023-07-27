# JTAG IDCODE Part Numbers

## IDCODE structure

This tracks the part numbers that have been allocated under the lowRISC JEDEC Manufacturer ID for use as part of a JTAG IDCODE.
The lowRISC JEDEC Manufacturer ID is 0xEF in bank 13.

The JTAG IDCODE structure (with lowRISC JEDEC Manufacturer ID) is:

| Bits  | 31 : 28 | 27 : 12     | 11 : 1  | 0   |
| ----- | ------- | ----------- | ------- | --- |
| Field | Version | Part Number | 11'h337 | 1'b1|

The 16-bit part number is further subdivided into 2 fields

| Bits      | 15 : 4    | 3 : 0    |
| --------- | --------- | -------- |
| Sub-field | Part Type | TAP Type |

Part Type indicates what part you have an IDCODE for (e.g. an OpenTitan earlgrey) where TAP Type indicates which TAP within that part the IDCODE is for (e.g. an RV_DM RISC-V debug module).
The TAP Type of 0 is reserved for all part types and shouldn't be used.
Each part type has its own unique TAP types but there will be uniformity across certain part types (e.g. OpenTitan variations all use the same set of TAP types).

## Version and Part Type Allocations

The following version and part type numbers have been allocated:

| Part Type | Version | Description | Notes |
| --------- | ------- | ----------- | ----- |
| 0         | 0       | [OpenTitan Earl Grey ES M2.5.2 - RCO](https://github.com/lowRISC/opentitan/releases/tag/Earlgrey-M2.5.2-RC0) |
| 1         | 0       | [OpenTitan Darjeeling](https://github.com/lowRISC/opentitan-integrated) |
| 256       | 0       | [Ibex Demo System](https://github.com/lowRISC/ibex-demo-system) | At present Ibex Demo System has no strict versioning so all instances will use version 0 |

## TAP Type Allocations

Whilst there are no universal TAP type allocations, certain classes of part type have uniform TAP types.

### OpenTitan Parts

| TAP Type | Description |
| -------- | ----------- |
| 1        | RV_DM RISC-V debug module |
| 2        | Lifecycle controller |

### Ibex Demo System Parts

| TAP Type | Description |
| -------- | ----------- |
| 1        | RV_DM RISC-V debug module |

## Complete Allocation Table

This specifies all valid allocations of currently allocated version, part type and TAP type numbers:

| Part Type | Version | TAP Type | Description |
| --------- | ------- | -------- | ----------- |
| 0         | 0       | 1        | [OpenTitan Earl Grey ES M2.5.2 - RCO](https://github.com/lowRISC/opentitan/releases/tag/Earlgrey-M2.5.2-RC0) RV_DM RISC-V debug module
| 0         | 0       | 2        | [OpenTitan Earl Grey ES M2.5.2 - RCO](https://github.com/lowRISC/opentitan/releases/tag/Earlgrey-M2.5.2-RC0) Lifecycle controller
| 1         | 0       | 1        | [OpenTitan Darjeeling](https://github.com/lowRISC/opentitan-integrated) OpenTitan Darjeeling RV_DM RISC-V debug module
| 1         | 0       | 2        | [OpenTitan Darjeeling](https://github.com/lowRISC/opentitan-integrated) OpenTitan Darjeeling Lifecycle controller
| 256       | 0       | 1        | Ibex Demo System RV_DM RISC-V debug module
