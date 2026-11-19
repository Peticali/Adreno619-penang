# Adreno619 (UniXNU-penang)

The Adreno 619 (Qualcomm holi / SM4350, moto g53 "penang") GPU driver library for UniXNU, used by
[UniXNU-penang](https://github.com/Peticali/UniXNU-penang)'s `package/PenangGpuProbe.cpp` (`penang-gpu=<stage>`).

Base: xiuyityer/UniXNU-tb371fc `drivers/Adreno650` and `drivers/ArmSmmu4K` at e6eeb91 (Adreno650 is UniXNU-sheng's Adreno740
adapted to the A6xx family; ArmSmmu4K is tb371fc's fork of UniXNU's kit, with ArmSmmu4KStreams). Licenses: see LICENSE (MIT) and
ArmSmmu4K/LICENSE.

The A619 has no GMU (a "GMU wrapper"): the board brings it up itself (RPM GX vote, GPU CC GDSCs, SPTPRAC, a619_holi hw_init, SQE,
zap shader) and hands this library the live ring, as tb371fc's board does. Verified on the g53 (2026-11-19, u27-gpu3..6): the SMMU
context, CP_ME_INIT (generation 6), the first CP_MEM_WRITE, the zap shader and the secure-mode exit, the GPU interrupt, publish and
the user-client self test (36/36).
