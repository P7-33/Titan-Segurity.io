---
title: 'The Linux codebase has over 3k TODO comments, many from over a decade ago'
date: 2019-12-30T04:55:00+01:00
draft: false
---

  
  
from Hacker News https://ift.tt/2F4pxmH

find another way \[1\] to implement this. \* Passing a zeroed structure is fragile, \* but at least we do not pass garbage. \* \* \[1\] One way would be that ndo\_neigh\_setup() never touch \* struct neigh\_parms, but propagate the new neigh\_setup() \* back to \_\_\_neigh\_create() / neigh\_parms\_alloc()

22 days ago

[drivers/net/bonding/bond\_main.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/net/bonding/bond_main.c#L3712)

Handle KVM\_MR\_MOVE

1 month ago

[arch/powerpc/kvm/book3s\_hv.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/arch/powerpc/kvm/book3s_hv.c#L4539)

\* bypass the initialize in sriov for now

1 month ago

[drivers/gpu/drm/amd/amdgpu/amdgpu\_psp.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/amdgpu/amdgpu_psp.c#L889)

\* bypass the initialize in sriov for now

1 month ago

[drivers/gpu/drm/amd/amdgpu/amdgpu\_psp.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/amdgpu/amdgpu_psp.c#L1080)

\* bypass the terminate in sriov for now

1 month ago

[drivers/gpu/drm/amd/amdgpu/amdgpu\_psp.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/amdgpu/amdgpu_psp.c#L1144)

\* bypass the terminate in sriov for now

1 month ago

[drivers/gpu/drm/amd/amdgpu/amdgpu\_psp.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/amdgpu/amdgpu_psp.c#L761)

\* bypass the initialize in sriov for now

1 month ago

[drivers/gpu/drm/amd/amdgpu/amdgpu\_psp.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/amdgpu/amdgpu_psp.c#L788)

\* bypass the terminate in sriov for now

1 month ago

[drivers/gpu/drm/amd/amdgpu/amdgpu\_psp.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/amdgpu/amdgpu_psp.c#L983)

The INTB interrupt is used for both PTP TX timestamp interrupt \* and preemption status change interrupt on each port. \* \* - Get txtstamp if have \* - handle preemption. Without handling it, driver may get \* interrupt storm.

1 month ago

[drivers/net/dsa/ocelot/felix.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/net/dsa/ocelot/felix.c#L399)

It needs to continue working on debugging with semaphore for GFXHUB as well.

1 month ago

[drivers/gpu/drm/amd/amdgpu/gmc\_v9\_0.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/amdgpu/gmc_v9_0.c#L489)

It needs to continue working on debugging with semaphore for GFXHUB as well.

1 month ago

[drivers/gpu/drm/amd/amdgpu/gmc\_v10\_0.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/amdgpu/gmc_v10_0.c#L398)

It needs to continue working on debugging with semaphore for GFXHUB as well.

1 month ago

[drivers/gpu/drm/amd/amdgpu/gmc\_v9\_0.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/amdgpu/gmc_v9_0.c#L567)

It needs to continue working on debugging with semaphore for GFXHUB as well.

1 month ago

[drivers/gpu/drm/amd/amdgpu/gmc\_v10\_0.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/amdgpu/gmc_v10_0.c#L262)

It needs to continue working on debugging with semaphore for GFXHUB as well.

1 month ago

[drivers/gpu/drm/amd/amdgpu/gmc\_v10\_0.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/amdgpu/gmc_v10_0.c#L295)

It needs to continue working on debugging with semaphore for GFXHUB as well.

1 month ago

[drivers/gpu/drm/amd/amdgpu/gmc\_v9\_0.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/amdgpu/gmc_v9_0.c#L551)

It needs to continue working on debugging with semaphore for GFXHUB as well.

1 month ago

[drivers/gpu/drm/amd/amdgpu/gmc\_v9\_0.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/amdgpu/gmc_v9_0.c#L519)

It needs to continue working on debugging with semaphore for GFXHUB as well.

1 month ago

[drivers/gpu/drm/amd/amdgpu/gmc\_v10\_0.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/amdgpu/gmc_v10_0.c#L414)

remove this once fw does it

1 month ago

[drivers/net/wireless/intel/iwlwifi/pcie/rx.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/net/wireless/intel/iwlwifi/pcie/rx.c#L204)

\* currently we don't set the antenna but letting the NIC \* to decide which antenna to use. This should come from BIOS.

1 month ago

[drivers/net/wireless/intel/iwlwifi/mvm/fw.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/net/wireless/intel/iwlwifi/mvm/fw.c#L522)

\* NOTE about '.balign 4': \* \* To make atomic update of patched instruction available we need to guarantee \* that this instruction doesn't cross L1 cache line boundary. \* \* As of today we simply align instruction which can be patched by 4 byte using \* ".balign 4" directive. In that case patched instruction is aligned with one \* 16-bit NOP\_S if this is required. \* However 'align by 4' directive is much stricter than it actually required. \* It's enough that our 32-bit instruction don't cross L1 cache line boundary / \* L1 I$ fetch block boundary which can be achieved by using \* ".bundle\_align\_mode" assembler directive. That will save us from adding \* useless NOP\_S padding in most of the cases. \* \* switch to ".bundle\_align\_mode" directive using whin it will be \* supported by ARC toolchain.

1 month ago

[arch/arc/include/asm/jump\_label.h](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/arch/arc/include/asm/jump_label.h#L12)

log? return different code?

1 month ago

[drivers/fsi/fsi-master-aspeed.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/fsi/fsi-master-aspeed.c#L228)

confirm that 0x70 was okay

1 month ago

[drivers/fsi/fsi-master-aspeed.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/fsi/fsi-master-aspeed.c#L231)

determine an appropriate value

1 month ago

[drivers/fsi/fsi-master-aspeed.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/fsi/fsi-master-aspeed.c#L455)

We could avoid skb\_cow\_data() if skb has no frag\_list \* e.g. by skb\_fill\_page\_desc() to add another page to the skb \* with the wanted tailen... However, page skbs look not often, \* so take it easy now! \* Cloned skbs e.g. from link\_xmit() seems no choice though :(

1 month ago

[net/tipc/crypto.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/net/tipc/crypto.c#L675)

handle p\_memsz != p\_filesz

1 month ago

[sound/soc/codecs/rt5677.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/sound/soc/codecs/rt5677.c#L840)

\* Rotating/reflecting YUV buffers is not supported at this time. \* Only RGB\[AX\] variants are supported.

1 month ago

[drivers/gpu/drm/mediatek/mtk\_disp\_ovl.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/mediatek/mtk_disp_ovl.c#L166)

\* If we use READ\_ONCE / WRITE\_ONCE for j\_commit\_request we can \* get rid of pointless j\_state\_lock traffic like this.

1 month ago

[fs/jbd2/transaction.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/fs/jbd2/transaction.c#L778)

\* dummy implement for pcie\_replay\_count sysfs interface \*

1 month ago

[drivers/gpu/drm/amd/amdgpu/nv.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/amdgpu/nv.c#L565)

ideally DSA ports would have a single dp->link\_dp member, \* and no dst->rtable nor this struct dsa\_link would be needed, \* but this would require some more complex tree walking, \* so keep it stupid at the moment and list them all.

1 month ago

[include/net/dsa.h](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/include/net/dsa.h#L217)

\* SNB,IVB,HSW can while VLV,CHV may hard hang on looping batchbuffer \* if GEN6\_PM\_UP\_EI\_EXPIRED is masked. \* \* verify if this can be reproduced on VLV,CHV.

2 months ago

[drivers/gpu/drm/i915/gt/intel\_rps.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/i915/gt/intel_rps.c#L1657)

\* this bit should only be enabled when really needed, then \* disabled when not needed anymore in order to save power.

2 months ago

[drivers/gpu/drm/i915/intel\_pm.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/i915/intel_pm.c#L6508)

Abort the process here.

2 months ago

[drivers/staging/media/sunxi/cedrus/cedrus\_h265.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/staging/media/sunxi/cedrus/cedrus_h265.c#L273)

VE\_DEC\_H265\_DEC\_PPS\_CTRL1\_FLAG\_TILES\_ENABLED

2 months ago

[drivers/staging/media/sunxi/cedrus/cedrus\_h265.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/staging/media/sunxi/cedrus/cedrus_h265.c#L411)

\* Reset XGMI Pstate back to default \* revise this when xgmi dpm is functional

2 months ago

[drivers/gpu/drm/amd/powerplay/arcturus\_ppt.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/powerplay/arcturus_ppt.c#L1208)

\* Force XGMI Pstate to highest or lowest \* revise this when xgmi dpm is functional

2 months ago

[drivers/gpu/drm/amd/powerplay/arcturus\_ppt.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/powerplay/arcturus_ppt.c#L1170)

convert to AQ time

2 months ago

[drivers/net/ethernet/aquantia/atlantic/aq\_ptp.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/net/ethernet/aquantia/atlantic/aq_ptp.c#L412)

\* ZONE\_DEVICE support requires to identify \* memmaps that were actually initialized.

2 months ago

[fs/proc/page.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/fs/proc/page.c#L45)

\* ZONE\_DEVICE support requires to identify \* memmaps that were actually initialized.

2 months ago

[fs/proc/page.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/fs/proc/page.c#L267)

\* ZONE\_DEVICE support requires to identify \* memmaps that were actually initialized.

2 months ago

[fs/proc/page.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/fs/proc/page.c#L221)

\* FXOS8700 - NXP IMU (accelerometer plus magnetometer) \* \* IIO core driver for FXOS8700, with support for I2C/SPI busses \* \* Buffer, trigger, and IRQ support

2 months ago

[drivers/iio/imu/fxos8700\_core.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/iio/imu/fxos8700_core.c#L2)

\* adux1020.c - Support for Analog Devices ADUX1020 photometric sensor \* \* Copyright (C) 2019 Linaro Ltd. \* Author: Manivannan Sadhasivam \* \* Triggered buffer support

2 months ago

[drivers/iio/light/adux1020.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/iio/light/adux1020.c#L2)

\* This function is called from dpu debugfs and as part of atomic \* check. When called from debugfs, the crtc->mutex must be held to \* read crtc->state. However reading crtc->state from atomic check isn't \* allowed (unless you have a good reason, a big comment, and a deep \* understanding of how the atomic/modeset locks work (<- and this is \* probably not possible)). So we'll keep the WARN\_ON here for now, but \* really we need to figure out a better way to track our operating mode

2 months ago

[drivers/gpu/drm/msm/disp/dpu1/dpu\_crtc.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/msm/disp/dpu1/dpu_crtc.c#L274)

for renoir

2 months ago

[drivers/gpu/drm/amd/amdgpu/gmc\_v9\_0.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/amdgpu/gmc_v9_0.c#L1267)

Fix this function to calcualte correct values. There are known issues with this function currently that will need to be investigated. Use hardcoded known good values for now. struct dcn21\_resource\_pool \*pool = TO\_DCN21\_RES\_POOL(dc->res\_pool); struct clk\_limit\_table \*clk\_table = &bw\_params->clk\_table; int i; dcn2\_1\_ip.max\_num\_otg = pool->base.res\_cap->num\_timing\_generator; dcn2\_1\_ip.max\_num\_dpp = pool->base.pipe\_count; dcn2\_1\_soc.num\_chans = bw\_params->num\_channels; for (i = 0; i < clk\_table->num\_entries; i++) { dcn2\_1\_soc.clock\_limits\[i\].state = i; dcn2\_1\_soc.clock\_limits\[i\].dcfclk\_mhz = clk\_table->entries\[i\].dcfclk\_mhz; dcn2\_1\_soc.clock\_limits\[i\].fabricclk\_mhz = clk\_table->entries\[i\].fclk\_mhz; dcn2\_1\_soc.clock\_limits\[i\].socclk\_mhz = clk\_table->entries\[i\].socclk\_mhz; dcn2\_1\_soc.clock\_limits\[i\].dram\_speed\_mts = clk\_table->entries\[i\].memclk\_mhz \* 16 / 1000; } dcn2\_1\_soc.clock\_limits\[i\] = dcn2\_1\_soc.clock\_limits\[i - i\]; dcn2\_1\_soc.num\_states = i;

2 months ago

[drivers/gpu/drm/amd/display/dc/dcn21/dcn21\_resource.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/display/dc/dcn21/dcn21_resource.c#L1354)

\* Ideally we really want a GPU reset here to make sure errors \* aren't propagated. Since I cannot find a stable way to reset the GPU \* at this point it is left as a .

2 months ago

[drivers/gpu/drm/i915/i915\_sysfs.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/i915/i915_sysfs.c#L232)

need to implement a proper lane mapping for Renoir.

2 months ago

[drivers/gpu/drm/amd/display/dc/dcn21/dcn21\_link\_encoder.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/display/dc/dcn21/dcn21_link_encoder.c#L180)

\* enable clock gating \* \* It is not written in DP enabling sequence but "PHY Clockgating \* programming" states that clock gating should be enabled after the \* link training but doing so causes all the following trainings to fail \* so not enabling it for now.

3 months ago

[drivers/gpu/drm/i915/display/intel\_ddi.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/i915/display/intel_ddi.c#L3528)

skip this for smb2/smb3

3 months ago

[fs/cifs/inode.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/fs/cifs/inode.c#L1699)

\* this can be optimized for huge pages: if a series of pages is \* physically contiguous and part of the same compound page, then a \* single operation to the head page should suffice.

3 months ago

[mm/gup.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/mm/gup.c#L59)

fix dc bugs and remove this split threshold thing

3 months ago

[drivers/gpu/drm/amd/display/dc/dcn20/dcn20\_resource.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/display/dc/dcn20/dcn20_resource.c#L2475)

ue will trigger an interrupt. \* \* When “Full RAS” is enabled, the per-IP interrupt sources should \* be disabled and the driver should only look for the aggregated \* interrupt via sync flood

3 months ago

[drivers/gpu/drm/amd/amdgpu/amdgpu\_gfx.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/amdgpu/amdgpu_gfx.c#L634)

\* (brendanhiggins@google.com): replace the arrays that keep track of the \* order of allocation and freeing with strict mocks using the IN\_SEQUENCE macro \* to assert allocation and freeing order when the feature becomes available.

3 months ago

[lib/kunit/test-test.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/lib/kunit/test-test.c#L259)

\* (brendanhiggins@google.com): We should probably have some type of \* variable timeout here. The only question is what that timeout value \* should be. \* \* The intention has always been, at some point, to be able to label \* tests with some type of size bucket (unit/small, integration/medium, \* large/system/end-to-end, etc), where each size bucket would get a \* default timeout value kind of like what Bazel does: \* https://ift.tt/37lsQ4U \* There is still some debate to be had on exactly how we do this. (For \* one, we probably want to have some sort of test runner level \* timeout.) \* \* For more background on this topic, see: \* https://ift.tt/2F0NmM6

3 months ago

[lib/kunit/try-catch.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/lib/kunit/try-catch.c#L36)

\* If sysctl\_hung\_task is active, just set the timeout to some \* value less than that. \* \* In regards to the above if we decide on variable \* timeouts, this logic will likely need to change.

3 months ago

[lib/kunit/try-catch.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/lib/kunit/try-catch.c#L54)

\* \* kunit\_test\_suite() - used to register a &struct kunit\_suite with KUnit. \* \* @suite: a statically allocated &struct kunit\_suite. \* \* Registers @suite with the test framework. See &struct kunit\_suite for \* more information. \* \* NOTE: Currently KUnit tests are all run as late\_initcalls; this means \* that they cannot test anything where tests must run at a different init \* phase. One significant restriction resulting from this is that KUnit \* cannot reliably test anything that is initialize in the late\_init phase; \* another is that KUnit is useless to test things that need to be run in \* an earlier init phase. \* \* (brendanhiggins@google.com): Don't run all KUnit tests as \* late\_initcalls. I have some future work planned to dispatch all KUnit \* tests from the same place, and at the very least to do so after \* everything else is definitely initialized.

3 months ago

[include/kunit/test.h](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/include/kunit/test.h#L199)

Always make new connection for now (?)

3 months ago

[fs/cifs/sess.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/fs/cifs/sess.c#L184)

check if changed channel, band

3 months ago

[drivers/staging/wfx/sta.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/staging/wfx/sta.c#L880)

Distill probe resp; remove TIM and any other beacon-specific \* IEs

3 months ago

[drivers/staging/wfx/sta.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/staging/wfx/sta.c#L925)

#define MULTICAST\_FILTERING 0

3 months ago

[drivers/staging/wfx/sta.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/staging/wfx/sta.c#L199)

BSS\_CHANGED\_QOS

3 months ago

[drivers/staging/wfx/sta.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/staging/wfx/sta.c#L1035)

add DBDC support

3 months ago

[drivers/net/wireless/mediatek/mt76/mt7615/mac.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/net/wireless/mediatek/mt76/mt7615/mac.c#L53)

\* Actions Semi Owl SoCs SD/MMC driver \* \* Copyright (c) 2014 Actions Semi Inc. \* Copyright (c) 2019 Manivannan Sadhasivam \* \* SDIO support

3 months ago

[drivers/mmc/host/owl-mmc.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/mmc/host/owl-mmc.c#L2)

ipv6 support

3 months ago

[fs/cifs/cifsroot.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/fs/cifs/cifsroot.c#L27)

The function will only serve to keep the pointers to the "oper" and "admin" \* schedules valid in relation to their base times, so when calling dump() the \* users looks at the right schedules. \* When using full offload, the admin configuration is promoted to oper at the \* base\_time in the PHC time domain. But because the system time is not \* necessarily in sync with that, we can't just trigger a hrtimer to call \* switch\_schedules at the right hardware time. \* At the moment we call this by hand right away from taprio, but in the future \* it will be useful to create a mechanism for drivers to notify taprio of the \* offload state (PENDING, ACTIVE, INACTIVE) so it can be visible in dump(). \* This is left as .

3 months ago

[net/sched/sch\_taprio.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/net/sched/sch_taprio.c#L1143)

Need input parameter to tell current DCHUB pipe tie to which OTG \* VTG is within DCHUBBUB which is commond block share by each pipe HUBP. \* VTG is 1:1 mapping with OTG. Each pipe HUBP will select which VTG

3 months ago

[drivers/gpu/drm/amd/display/dc/dcn20/dcn20\_hwseq.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/display/dc/dcn20/dcn20_hwseq.c#L1227)

:for CNVC set scale and bias registers if necessary

3 months ago

[drivers/gpu/drm/amd/display/dc/dcn20/dcn20\_hwseq.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/display/dc/dcn20/dcn20_hwseq.c#L1263)

Other registers are not yet used

3 months ago

[drivers/gpu/drm/i915/intel\_uncore.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/i915/intel_uncore.c#L944)

\* This will update the table sum with new records. \* \* What happens when the EEPROM table is to be wrapped around \* and old records from start will get overridden.

3 months ago

[drivers/gpu/drm/amd/amdgpu/amdgpu\_ras\_eeprom.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/amdgpu/amdgpu_ras_eeprom.c#L149)

\* Extend multiple boot memory regions support in the kernel \* for this platform.

3 months ago

[arch/powerpc/platforms/pseries/rtas-fadump.h](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/arch/powerpc/platforms/pseries/rtas-fadump.h#L73)

Add upper time limit for the delay

3 months ago

[arch/powerpc/platforms/pseries/rtas-fadump.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/arch/powerpc/platforms/pseries/rtas-fadump.c#L208)

Add upper time limit for the delay

3 months ago

[arch/powerpc/platforms/pseries/rtas-fadump.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/arch/powerpc/platforms/pseries/rtas-fadump.c#L183)

Add upper time limit for the delay

3 months ago

[arch/powerpc/platforms/pseries/rtas-fadump.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/arch/powerpc/platforms/pseries/rtas-fadump.c#L135)

\* Handle frame\_num wraparound as described in section \* '8.2.4.1 Decoding process for picture numbers' of the spec. \* This logic will have to be adjusted when we start \* supporting interlaced content.

3 months ago

[drivers/staging/media/hantro/hantro\_h264.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/staging/media/hantro/hantro_h264.c#L303)

\* Validated limit is 4k, but has 5k should \* work apart from the following features: \* - Ytile (already limited to 4k) \* - FP16 (already limited to 4k) \* - render compression (already limited to 4k) \* - KVMR sprite and cursor (don't care) \* - horizontal panning ( verify this) \* - pipe and plane scaling ( verify this)

3 months ago

[drivers/gpu/drm/i915/display/intel\_display.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/i915/display/intel_display.c#L3304)

evaluate how to lower or disable all dcn clocks in screen off case

3 months ago

[drivers/gpu/drm/amd/display/dc/clk\_mgr/dcn21/rn\_clk\_mgr.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/display/dc/clk_mgr/dcn21/rn_clk_mgr.c#L56)

\* Reenabling clock gating seems to break subsequent SMU operation \* on the I2C bus. My guess is that SMU doesn't disable clock gating like \* we do here before working with the bus. So for now just don't restore \* it but later work with SMU to see if they have this issue and can \* update their code appropriately

3 months ago

[drivers/gpu/drm/amd/amdgpu/smu\_v11\_0\_i2c.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/amdgpu/smu_v11_0_i2c.c#L497)

Eventually add something to printk so we can format the rad \* like this: 1.2.3

3 months ago

[drivers/gpu/drm/drm\_dp\_mst\_topology.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/drm_dp_mst_topology.c#L179)

To reduce the number of credit update messages, \* don't update credits as long as lots of space is available. \* Note: the limit chosen here is arbitrary. Setting the limit \* too high causes extra messages. Too low causes transmitter \* stalls. As stalls are in theory more expensive than extra \* messages, we set the limit to a high value. experiment \* with different values.

3 months ago

[net/vmw\_vsock/virtio\_transport\_common.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/net/vmw_vsock/virtio_transport_common.c#L377)

4 months ago

[drivers/gpu/drm/msm/disp/mdp5/mdp5\_kms.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/msm/disp/mdp5/mdp5_kms.c#L170)

4 months ago

[drivers/gpu/drm/msm/disp/mdp4/mdp4\_kms.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/msm/disp/mdp4/mdp4_kms.c#L124)

Implement support for gen-12 CCS modifiers

4 months ago

[drivers/gpu/drm/i915/display/intel\_sprite.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/i915/display/intel_sprite.c#L2933)

4 months ago

[drivers/usb/cdns3/ep0.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/usb/cdns3/ep0.c#L691)

\* Last condition latch INIT signals on vCPU when \* vCPU is in guest-mode and vmcb12 defines intercept on INIT. \* To properly emulate the INIT intercept, SVM should implement \* kvm\_x86\_ops->check\_nested\_events() and call nested\_svm\_vmexit() \* there if an INIT signal is pending.

4 months ago

[arch/x86/kvm/svm.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/arch/x86/kvm/svm.c#L7234)

add support for other clients...

4 months ago

[drivers/soc/qcom/ocmem.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/soc/qcom/ocmem.c#L268)

gpu uses phys\_to\_offset, but others do not..

4 months ago

[drivers/soc/qcom/ocmem.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/soc/qcom/ocmem.c#L160)

\* add more once ocmem\_allocate() is clever enough to \* deal with multiple clients.

4 months ago

[include/soc/qcom/ocmem.h](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/include/soc/qcom/ocmem.h#L21)

add support for other clients...

4 months ago

[drivers/soc/qcom/ocmem.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/soc/qcom/ocmem.c#L215)

4 months ago

[drivers/gpu/drm/amd/display/dc/dml/dml1\_display\_rq\_dlg\_calc.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/display/dc/dml/dml1_display_rq_dlg_calc.c#L1185)

oswin to think about what to do for cursor

4 months ago

[drivers/gpu/drm/amd/display/dc/dml/dcn20/display\_rq\_dlg\_calc\_20.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/display/dc/dml/dcn20/display_rq_dlg_calc_20.c#L1658)

4 months ago

[drivers/gpu/drm/amd/display/dc/dml/dcn20/display\_rq\_dlg\_calc\_20.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/display/dc/dml/dcn20/display_rq_dlg_calc_20.c#L962)

take the max between luma, chroma chunk size?

4 months ago

[drivers/gpu/drm/amd/display/dc/dml/dcn20/display\_rq\_dlg\_calc\_20.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/display/dc/dml/dcn20/display_rq_dlg_calc_20.c#L210)

check if ppe apply for both luma and chroma in 422 case

4 months ago

[drivers/gpu/drm/amd/display/dc/dml/dml1\_display\_rq\_dlg\_calc.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/display/dc/dml/dml1_display_rq_dlg_calc.c#L605)

ip\_param

4 months ago

[drivers/gpu/drm/amd/display/dc/dml/dml1\_display\_rq\_dlg\_calc.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/display/dc/dml/dml1_display_rq_dlg_calc.c#L1144)

check if ppe apply for both luma and chroma in 422 case

4 months ago

[drivers/gpu/drm/amd/display/dc/dml/dcn20/display\_rq\_dlg\_calc\_20.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/display/dc/dml/dcn20/display_rq_dlg_calc_20.c#L680)

take the max between luma, chroma chunk size?

4 months ago

[drivers/gpu/drm/amd/display/dc/dml/dcn20/display\_rq\_dlg\_calc\_20v2.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/display/dc/dml/dcn20/display_rq_dlg_calc_20v2.c#L210)

oswin to think about what to do for cursor

4 months ago

[drivers/gpu/drm/amd/display/dc/dml/dml1\_display\_rq\_dlg\_calc.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/display/dc/dml/dml1_display_rq_dlg_calc.c#L1840)

4 months ago

[drivers/gpu/drm/amd/display/dc/dml/dcn20/display\_rq\_dlg\_calc\_20v2.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/display/dc/dml/dcn20/display_rq_dlg_calc_20v2.c#L962)

check if ppe apply for both luma and chroma in 422 case

4 months ago

[drivers/gpu/drm/amd/display/dc/dml/dcn20/display\_rq\_dlg\_calc\_20v2.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/display/dc/dml/dcn20/display_rq_dlg_calc_20v2.c#L680)

take the max between luma, chroma chunk size? \* okay for now, as we are setting chunk\_bytes to 8kb anyways

4 months ago

[drivers/gpu/drm/amd/display/dc/dml/dml1\_display\_rq\_dlg\_calc.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/display/dc/dml/dml1_display_rq_dlg_calc.c#L246)

oswin to think about what to do for cursor

4 months ago

[drivers/gpu/drm/amd/display/dc/dml/dcn20/display\_rq\_dlg\_calc\_20v2.c](https://github.com/torvalds/linux/blob/bf8d1cd4386535004c4afe7f03d37f9864c9940e/drivers/gpu/drm/amd/display/dc/dml/dcn20/display_rq_dlg_calc_20v2.c#L1658)