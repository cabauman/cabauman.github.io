---
title: "Image Click Area"
categories:
  - Unity Tips
tags:
  - unity
  - unity-tip
  - ugui
---

When creating image buttons, it's sometimes desirable to make the clickable area bigger than the image. One common approach to achieve this is adding an additional GameObject + Image component, setting the desired clickable area size, and making it completely transparent. But we actually don't need those extra objects. Instead, utilize the Raycast Padding property of the Image component. The editor conveniently shows the bounds via Gizmo (the white square surrounding the image).

![Image Click Area](/assets/images/image-click-area.png)