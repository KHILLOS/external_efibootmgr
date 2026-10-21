# Modification Map: external/efibootmgr

## Source: BlissOS android-x86 reference (external/efibootmgr)
- BlissOS commit: 2869cca (hmtheboy154, 'install to /system/bin')
- UPSTREAM commit: 8c95456 (KhillOS port)
- Upstream base: rhboot/efibootmgr@18 (tag c3f9f05)

## Modifications Applied to UPSTREAM/external_efibootmgr (khillos-17 branch)

### 1. Android.mk Modification (BlissOS Port)
**File:** `src/Android.mk`
- Removed `LOCAL_MODULE_PATH := $(TARGET_INSTALLER_OUT)/sbin` (fork-only install path override)
- Changed `LOCAL_C_INCLUDES := $(LOCAL_PATH)/include` → `LOCAL_C_INCLUDES := $(LOCAL_PATH)`
- Fixed `DEFAULT_LOADER` escaping: `\\\\elilo.efi` → `\\elilo.efi`
- Aligns with upstream rhboot/efibootmgr@18 which already has Android.mk

### 2. AOSP 17 Compliance Metadata Files (NEW)
**Files:** `METADATA`, `NOTICE`, `MODULE_LICENSE_GPL2`, `OWNERS`
- METADATA: Package metadata per AOSP external_updater format
- NOTICE: Short license notice (replaced symlink to COPYING)
- MODULE_LICENSE_GPL2: SPDX identifier for Soong license module
- OWNERS: Standard AOSP OWNERS file

### 3. SPDX Headers to All Source Files
**Files:** 12 files (src/*.c, src/*.h, src/include/*.h)
- Added `/* SPDX-License-Identifier: GPL-2.0-or-later */` after first comment block
- Applied to: efibootmgr.c, efi.c, efibootdump.c, efibootnext.c, eficonman.c, parse_loader_data.c, error.h, fix_coverity.h, include/efi.h, include/efibootmgr.h, include/list.h, include/parse_loader_data.h

## Summary
- **Total files modified:** 16 (4 new metadata + 12 SPDX headers + 1 Android.mk change)
- **Source files unchanged:** Yes (only SPDX headers added)
- **Logic/behavior changes:** Only Android.mk path/flags adjustment (BlissOS port)
- **Build system changes:** None (still Android.mk, not migrated to Android.bp)

## Notes
- Upstream rhboot/efibootmgr@18 already provides Android.mk - BlissOS just modified install path
- Android.bp migration would be ideal for AOSP 17 but kept Android.mk to match upstream