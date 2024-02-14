---
title: "TextMeshPro Stylesheets"
categories:
  - Unity Tips
tags:
  - unity
  - unity-tip
---

Use TextMeshPro's "Font Weights" feature + stylesheets to simplify working with specs set by the design team.

**Font Weights**

When you import a family of fonts, don't explicitly reference them all in the TMP components. Instead, make the Regular font style reference all the variations.

**Stylesheets**

Create a stylesheet to add snippets for each weight (300, 400, etc.), or any other combination of markdown tags. These will appear in the "Text Style" dropdown right below the text. Finally, set both the font and stylesheet as defaults in TextMeshPro PlayerSettings.

![tmp-stylesheets1](/assets/images/tmp-stylesheets1.png)

![tmp-stylesheets2](/assets/images/tmp-stylesheets2.png)

![tmp-stylesheets3](/assets/images/tmp-stylesheets3.png)

![tmp-stylesheets4](/assets/images/tmp-stylesheets4.png)

![tmp-stylesheets5](/assets/images/tmp-stylesheets5.png)
