# JTAG IDCODE Part Numbers

## IDCODE structure

This tracks the part numbers that have been allocated under the lowRISC JEDEC Manufacturer ID for use as part of a JTAG IDCODE.
The lowRISC JEDEC Manufacturer ID is 0xEF in bank 13.

The JTAG IDCODE structure (with lowRISC JEDEC Manufacturer ID) is:

| Bits  | 31 : 28 | 27 : 12     | 11 : 1  | 0   |
| ----- | ------- | ----------- | ------- | --- |
| Field | Version | Part Number | 11'h66F | 1'b1|

The 16-bit part number is further subdivided into 2 fields

| Bits      | 15 : 4    | 3 : 0    |
| --------- | --------- | -------- |
| Sub-field | Part Type | TAP Type |

Part Type indicates what part you have an IDCODE for (e.g. an OpenTitan earlgrey) where TAP Type indicates which TAP within that part the IDCODE is for (e.g. an RV_DM RISC-V debug module).
The TAP Type of 0 is reserved for all part types and shouldn't be used.
Each part type has its own unique TAP types but there will be uniformity across certain part types (e.g. OpenTitan variations all use the same set of TAP types).

## Version and Part Type Allocations

The following version and part type numbers have been allocated:

| Version | Part Type | Description | Notes |
|---------| --------- | ----------- | ----- |
| 1       |   0       | [OpenTitan Earl Grey][earlgrey]
| 1       |   1       | [OpenTitan Darjeeling][darjeeling]
| 1       | 256       | [Ibex Demo System][demo-system] | At present Ibex Demo System has no strict versioning so all instances will use version 1
| 1       | 257       | [Sonata system][sonata]

## TAP Type Allocations

Whilst there are no universal TAP type allocations, certain classes of part type have uniform TAP types.

### OpenTitan Parts

| TAP Type | Description |
| -------- | ----------- |
| 1        | RV_DM RISC-V debug module
| 2        | Lifecycle controller
| 3        | Combined TAP (RV_DM and Lifecycle)

### Ibex Demo System Parts

| TAP Type | Description |
| -------- | ----------- |
| 1        | RV_DM RISC-V debug module |

### Sonata System Parts

| TAP Type | Description |
| -------- | ----------- |
| 1        | RV_DM RISC-V debug module |

## Complete Allocation Table

This specifies all valid allocations of currently allocated version, part type and TAP type numbers:

| Version | Part Type | TAP Type | Description |
| ------- | --------- | -------- | ----------- |
| 1       | 0         | 1        | [OpenTitan Earl Grey][earlgrey] RV_DM RISC-V debug module
| 1       | 0         | 2        | [OpenTitan Earl Grey][earlgrey] Lifecycle controller
| 1       | 1         | 3        | [OpenTitan Darjeeling][darjeeling] combined TAP
| 1       | 256       | 1        | [Ibex Demo System][demo-system] RV_DM RISC-V debug module
| 1       | 257       | 1        | [Sonata System][sonata] RV_DM RISC-V debug module

[earlgrey]: https://github.com/lowRISC/opentitan/blob/6b4c43c852ea2be235dd630d7e27f25e1b38f60a/hw/top_earlgrey/rtl/jtag_id_pkg.sv
[darjeeling]: https://github.com/lowRISC/opentitan/blob/8f279ef47ba3a5c95f1416612b4f5efe8304ee0b/hw/top_darjeeling/rtl/jtag_id_pkg.sv
[demo-system]: https://github.com/lowRISC/ibex-demo-system/blob/af43c851580c89d0f24d9010865faeb0b32af1ee/rtl/system/jtag_id_pkg.sv
[sonata]: https://github.com/lowRISC/sonata-system/blob/71f2a24425d10df38107a2ae8f954400a366047f/rtl/system/jtag_id_pkg.sv
