---
date:
  created: 2025-09-22
---

# Brightness issue fix

Some users recently reported issues where brightness of blended objects would fluctuate.
To resolve this, run this command in your project console:
`r.Lumen.ScreenProbeGather.MaterialAO 0`

The setup guide has been updated to include this step.