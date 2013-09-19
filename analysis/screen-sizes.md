# Screen Sizes

Screen resolutions are a tricky thing. 1080p LCD Monitors have gotten so cheap that both desktop and 'docked laptop' users are using huge monitors when we find them in a traditional office setting.

What complicates matters is that developers are increasingly seeking out non-traditional settings for at least part of the time: airplanes, hack days, cafes, the couch:

![](http://distilleryimage7.ak.instagram.com/962cc55c0fcc11e3852322000a9e288c_7.jpg)

### Fragmentation

Statcounter's stats for screen sizes worldwide is interesting, by far the most dominant screen resolution is the oddball [1366x768](http://gs.statcounter.com/#resolution-ww-monthly-201207-201307) - a native panel resolution for cheap televisions as well as the LCD display in the 11" Macbook Air and other similar machines such as the 11" [Lenova 'Yoga'](http://shop.lenovo.com/ca/en/landingpage/yoga/yoga-models.html#yoga-content).

Ultrabooks (led by the Macbook Air) are [growing steadily even though the rest of the market is declining](http://www.theverge.com/2012/6/29/3125801/ultrabook-sales-boost-notebook-market). Particularly in North America screen sizes are getting smaller and wider.

Other standard sizes that are very common include:
- 1024x768
- 1280x800
- 1280x1024
- 1920x1080

Only one of these resolutions could be considered particularly large, and most devices are using a widescreen/'cinematic' aspect ratio.

#### Uneven distribution

North America is a MacBook soap bubble, and the developer market in North America can be observed as an extreme example of this. [Apple's market share in America is over 10% in the US but does not even make it in the top 5 worldwide](http://techcrunch.com/2011/07/14/apple-continues-slow-but-steady-growth-in-us-laptop-market-share/). We see this all around us - developer events in the US and Canada ( especially in major cities ) are dominated by Apple hardware. 

Once you leave North America ( and to a lesser extent, Europe ) the Apple presence disappears. In Asia and Brazil this difference is particularly stark, and why. The developers I met tend to choose much cheaper PC laptops (and often use Linux on them) due mainly to economics. Apple's hardware is far too expensive, and this is particularly acute in places like Brazil where import taxes on fully assembled foreign products can double the retail price.

While Apple's line has relatively few models and a short list of screen resolutions, PC screen sizes present real problems to us: not only are there a lot of screen sizes in use, but many laptops have very high (1080p) resolutions paired with physical sizes that make readability challenging.

### Transitions

There are a few factors that have affected trends in the size and number of displays a developer will be using at any given time:

- large high-resolution displays are aggressively priced and almost a total commodity; [23" monitors with 1080p resolution are priced below $200USD](http://goo.gl/kBVHDH).
- ultrabooks with smaller displays are a growing segment of the otherwise slowing PC market. Real progress on laptop performance has slowed in favour of recent advances in energy efficiency, with Apple's MacBook Air leading the way. 
- start-ups and 'digital agency' type businesses are employing or contracting developers with increased location flexibility. Web developers work in an increasingly varied set of environments, including traditional offices, home offices, planes, trains, cars, cafes or co-working spaces.
- developers outside of the first world are unable or unwilling to pay the high prices necessary for systems like retina-display Macbook Pros or Airs, opting instead for much more affordable PCs.

We can see that no matter who the developer is, they likely prefer the portability and flexibility of a laptop for doing their work:

 - For first world developers their choice is often a high-end Apple or PC ultrabook, paired with a high-resolution display or two when at the office and at home.
 - Second/Third world developers are much more likely to only use a single screen, but the cheapest laptops tend to have 15" or 17" 1080P screens.

### Use cases

![](http://yakovfain.files.wordpress.com/2013/04/my_setup_3.png)

#### Single screen

- only one screen, the developer owns a laptop only.
- screen size matters hugely, at 1080p it's reasonable to have tiled windows from different apps. Browser developer tools are likely to be docked in the window though, possible to the side. 
- at lower resolutions space is constrained severely, only one app is used at a time.
- there is a productivity boost associated with always using the same screen resolution and a single screen, in particular with increased focus and less fiddling with window placements.

#### Transitions

 - pairing a laptop or ultrabook with an external monitor or two when at an office or home office explodes the amount of screen real estate while docked
 - friction in workflow is created, the developer needs to develop both docked and mobile ways of interacting with their tools. 
 - handling the transition from one to another can be handled via automation or utilities such as Moom

#### Second device

- a common use for a second monitor on a single device is for reference documentation, and we have reports from research of users using commoditized mobile devices like tablets or even smartphones.
- there are utilities that allow you to extend the computer's desktop to [the mobile device screen](http://mashable.com/2012/11/01/tablet-second-monitor/).

#### Readability, ips, etc.

Another factor in the fragmentation both of displays and of the developer experience of looking at them is the recent proliferation of higher-than-72dpi screens, for example the retina screens on Macbook Pro laptops or relatively cheap IPS WQXGA monitors. 

On the other end of the spectrum, running Windows with default font settings on a 15" 1080p monitor can yield really poor readability, with lower-end laptop manufacturers using off-the-shelf parts and not considering readability as highly as Apple does.