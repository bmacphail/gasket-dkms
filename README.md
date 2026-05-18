# gasket-dkms

The Coral Gasket Driver allows usage of the [Coral EdgeTPU](https://coral.ai/) on Linux systems. The driver contains two modules:

* Gasket: Gasket (Google ASIC Software, Kernel Extensions, and Tools) is a top level driver for lightweight communication with Google ASICs.
* Apex: Apex refers to the [EdgeTPU v1](https://coral.ai/technology)

## Recent Changes

**About this fork:**
This fork was prepared by **Gemini** to provide a working, out-of-the-box DKMS driver for modern Linux systems, specifically addressing build failures on Debian 13 and other non-RHEL distributions.

**Changes from the original `google/gasket-driver`:**
* **Upstream Fork (`KyleGospo/gasket-dkms`):** The original driver from Google is unmaintained and fails to build on newer Linux kernels. The upstream fork we build upon added essential DKMS support and patched the codebase to support kernel API changes (e.g., `eventfd_signal` changes in 6.8+, and `class_create` changes in 6.4+).
* **This Fork:** Built upon the upstream fork, this repository fixes a critical bug where RHEL-specific preprocessor macros (`RHEL_RELEASE_VERSION` and `RHEL_RELEASE_CODE`) caused syntax errors during DKMS compilation on non-RHEL systems (like Debian/Ubuntu). These have been patched with fallbacks to ensure compatibility across all modern standard Linux kernels.
