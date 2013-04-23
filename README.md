Toy formal verification project, from when I was learning ACL2: formally verify SecVisor, a secure hypervisor.

code-injection.lisp: Seshadri, Luk, Qu, and Perrig, in their SecVisor paper, implement a hypervisor that satisfies a certain set of properties in order to prevent code injection attacks. In a later paper, the Murphi model checker is used to formally verify that their hypervisor doesn't violate their properties, but they never formally verify that the properties given are sufficient for preventing code injection attacks (model checking is incapable of proving such a statement). This file contains an ACL2 proof that the given properties are sufficient for preventing code injection attacks. Moreover, a technically weaker (but practically equivalent) version of the same properties is also sufficient.

kernel-seperation.lisp: This file develops a kernel seperation property based on the above properties, plus the condition that the kernel's data region is inaccessable while arbitrary user code is executing (which the SecVisor paper postulates in the case where a shadow page table is used). This can be trivially modified to handle the case where user processes can read but not modify kernel code and data.
