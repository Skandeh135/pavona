# uart Verification Report Overview

The uart verification report lists and describes uart's features, tests, testpoints, and specification sections, as well as illustrating the relationship between each. This report is comprised of four documents whose purpose is explained below.

## [Feature Report](01_feature_report.md)

Here, uart's features are listed and mapped to both the uart [specification](../theory_of_operation.md) (its Theory of Operation document) and its testpoints. These testpoints are gathered from:
- [uart's standard testplan](../../../../../hw/ip/uart/data/uart_testplan.hjson)
- [the dragonfly-level testplan relevant to uart](../../../../../hw/top_dragonfly/data/ip/chip_uart_testplan.hjson)
- [the egret-level testplan relevant to uart](../../../../../hw/top_egret/data/ip/chip_uart_testplan.hjson)

These mappings are presented as two matrices: a **Feature -> Specification** matrix and a **Feature -> Testpoint** matrix.

**Note:** An IP's testplan contains a list of testpoints.
A testpoint is not a test (i.e., a complete DV simulation configuration).
Rather, it describes a verification objective and may map to zero, one, or more tests.


- **Feature -> Specification Matrix**
    - The columns correspond to features.
    - The rows correspond to the sections of the specification that describe each feature.
    - Clicking a matrix entry will navigate to the corresponding section of the specification.


- **Feature -> Testpoint Matrix**
    - The columns correspond to features.
    - The rows correspond to testpoints within the IP's regular/chip-level testplan.
    - Clicking a matrix entry will navigate to the corresponding section of the **Testpoint Report** for additional information.


## [IP Testpoint Report](02_testpoint_report.md)

This report provides a more detailed view of the IP's testpoints, including a description of each testpoint and its associated tests/features, if any.

Clicking a test link will navigate to the corresponding test in the **Test Report**.
Clicking a feature link will navigate to the corresponding feature in the **Feature Report**


## [IP Test Report](03_test_report.md)

This report lists all tests associated with the IP and maps each test to its corresponding testpoints/features.

Clicking a testpoint link will navigate to the corresponding testpoint in the **Testpoint Report**.
Clicking a feature link will navigate to the corresponding feature in the **Feature Report**


## [Unmapped Report](04_unmapped_report.md)

This report provides a summary of the gaps in the above mapping

It displays the features not currently mapped to a testpoint/test, the testpoints not currently mapped to a feature/test, and the tests not currently mapped to a feature/testpoint.

Clicking a feature link will navigate to the corresponding feature in the **Feature Report**
Clicking a test link will navigate to the corresponding test in the **Test Report**.
Clicking a testpoint link will navigate to the corresponding testpoint in the **Testpoint Report**.

This report is intended to provide a quick "temperature check" of uart's DV effort by highlighting the outstanding verification work that remains.
