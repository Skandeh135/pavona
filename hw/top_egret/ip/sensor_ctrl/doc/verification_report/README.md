# sensor_ctrl (egret) Verification Report Overview

The sensor_ctrl verification report lists and describes sensor_ctrl's features, tests, testpoints, and specification sections, as well as illustrating the relationship between each. This report is comprised of four documents whose purpose is explained below.

## [Feature Report](01_feature_report.md)

Here, sensor_ctrl's features are listed and mapped to both the sensor_ctrl [specification](../theory_of_operation.md) (its Theory of Operation document) and its testpoints.
These mappings are presented as two matrices: a **Feature -> Specification** matrix and a **Feature -> Testpoint** matrix.

**Note:** An IP's testplan contains a list of testpoints.
A testpoint is not a test (i.e., a complete DV simulation configuration).
Rather, it describes a verification objective and may map to zero, one, or more tests.

**Note: sensor_ctrl does not currently contain any features**

- **Feature -> Specification Matrix**
    - The columns correspond to features.
    - The rows correspond to the sections of the specification that describe each feature.
    - Clicking a matrix entry will navigate to the corresponding section of the specification.

**Note: sensor_ctrl does not currently contain a Feature -> Specification Matrix**

- **Feature -> Testpoint Matrix**
    - The columns correspond to features.
    - The rows correspond to testpoints within the IP's regular/chip-level testplan.
    - Clicking a matrix entry will navigate to the corresponding section of the **Testpoint Report** for additional information.

**Note: sensor_ctrl does not currently contain a Feature -> Testpoint Matrix**

## [IP Testpoint Report](02_testpoint_report.md)

This report provides a more detailed view of the IP's testpoints, including a description of each testpoint and its associated tests/features, if any.

Clicking a test link will navigate to the corresponding test in the **Test Report**.
Clicking a feature link will navigate to the corresponding feature in the **Feature Report**

**Note: sensor_ctrl does not currently contain any testpoints**

## [IP Test Report](03_test_report.md)

This report lists all tests associated with the IP and maps each test to its corresponding testpoints/features.

Clicking a testpoint link will navigate to the corresponding testpoint in the **Testpoint Report**.
Clicking a feature link will navigate to the corresponding feature in the **Feature Report**

**Note: sensor_ctrl does not currently contain any tests**

## [Unmapped Report](04_unmapped_report.md)

This report provides a summary of the gaps in the above mapping

It displays the features not currently mapped to a testpoint/test, the testpoints not currently mapped to a feature/test, and the tests not currently mapped to a feature/testpoint.

Clicking a feature link will navigate to the corresponding feature in the **Feature Report**
Clicking a test link will navigate to the corresponding test in the **Test Report**.
Clicking a testpoint link will navigate to the corresponding testpoint in the **Testpoint Report**.

This report is intended to provide a quick "temperature check" of sensor_ctrl's DV effort by highlighting the outstanding verification work that remains.
