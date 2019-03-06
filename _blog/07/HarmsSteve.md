---
title: "All that legal stuff..."
author: "Steve Harms"
topic: "07"
layout: post
root: ../../../
---

1. **Under what license does R operate?**

R operates under the GPL-2|GPL-3 license, according to https://www.r-project.org/Licenses . The next part of this post explains what that means. There are other licenses that may be in use for individual packages.

2. **Answer the three questions listed above for the licenses: MIT, GPL-3,  LGPL-3, and CC-0. Note that some of the questions might not be answered with a simple yes/no. In that case, go into more detail, but do not just copy the terms of the license.**

**MIT**: 

1. We would be fine with other people modifying and sharing our work. The template license description says we grant free permission to deal in the software without restriction, including modifying, distributing, and selling the software
2. We would be fine with other people selling our work.
3. If our software does not work, it is on the user. The end paragraph of the license says the software is provided "as is", without a warranty of any kind.

**GPL-3**
1. We are ok with others modifying our work and then sharing those modifications, so long as the distribute the code in a way that is compatible with our original work. The GPL license says we should grant users the same freedom as we used, so long as they include a copyright and a "prominent notice" stating that it is modified. Users must include the original source, state the changes, and include install instructions
2. We are ok with others modifying our software and selling it for profit. The license says each contributor grants you a "non-exclusive, worldwide, royalty-free patent license to make, use, sell,...,modify and propagate the contents of its contributor version".
3. The Authors are not responsible if the code does not work, there is no warranty on this free license.

**LGPL-3**
1. We are NOT ok with others distributing modified versions our work. Everyone is permitted to copy and distribute verbatim copies, but changing it is not allowed without very specific attribution to the authors. However, if you do modify a copy of the Library, "then you may convey a copy of the modified version under this License, provided you make a good faith effort to ensure that...the facility still operates and performs whatever part of its purpose remains meaningful." Modified versions must follow rules similar to GPL-3.
2. If you do modify a copy of our work, it must "cause the whole of the work to be licensed at no charge to all third parties under the terms of this License". So no profit from a copy of the library, however if you use a small facility of the Library in your own library, you can (I think?) sell your library for profit as long as you make a good faith effort to ensure the borrowed work works in its intended manner.
3. Users are liable if the software does not work.

**CC-0**
1. We are ok with any modification and distribution of copies of our software for any purpose. We put our software in the public domain and relinquish all rights.
2. We are ok with others selling modifications of our work for commercial use.
3. The software is offered as-is, with no responsibility for the authors. The user is liable for any malfunctions.

3. **Assume that you are in the process of making a package for your own graduate work. Describe considerations that come into play in deciding on a license. In case you are not quite at that stage in your graduate studies yet, come up with a likely scenario. Describe it and discuss.**

Suppose we're making a new R package that makes more visually appealing plots and offers more themes and color palettes than what's currently available. The main considerations I would consider would be (1) What is the end purpose of this software, and do I want others to be able to make significant changes; (2) Am I using someone else's functions (i.e., base R functions or other dependencies) and what licenses are they using; and (3) Is this project serving a business purpose or is it something that is supposed to be open source and free to use.

For example, it's possible I want to use/modify the color palettes from RColorBrewer in my new package. I would then need to make sure I follow the instructions from their license and add their copyright, thus it might be best to use whatever license they use for continuity. Suppose I'm just building pretty plotting functions for simple histograms/boxplots, but I want to let other people build more complex spatial/faceting features into my package later if they want to. Maybe it's just better to use the CC-0 and let it out in public then. Am I using sample data for examples in my package? We can't license that, so we would need to use CC-0. If I don't need to make a profit, then any of the free licenses might be ok. Is my plotting package going to be used to facilitate a larger software project, say for analysis of a specific kind of data? Then we might want to use a license that restricts some features while allowing it to be shared.
