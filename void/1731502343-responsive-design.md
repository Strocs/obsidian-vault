---
id: 1731502343-responsive-design
aliases:
  - Responsive Design
tags:
  - article
  - notes
---

# Responsive Design

Based on this article:  [Responsive Deesign: Best Practices](https://www.toptal.com/designers/responsive/responsive-design-best-practices)

Responsive design look for a fluid capability of a website to adapt to all devices, from desktops to mobile.

Mobile-first approach is the idea to make our designs first on a mobile devices, this is why is easier to scale up a design than a scale down, 
and helps to re evaluate the necessity of some features or over designs.

> [!NOTE]
> Some articles say that mobile-first approach is not so beneficial because limit the possibilities of the design. (search sources)

### Best Practices

#### Eliminate Friction

Concentrate on the micro interactions and user flows, mobile-first approach helps to eliminate the unnecessary friction of some 
features/functions and helps us to detect what parts of our designs are the most important.

#### Design for Thumbs

![Design for Thumbs](/files/design-for-thumbs.png)

- On mobile, users expect that navigation should be at bottom. In general, reach the top are not comfortably like reach the bottom of the mobile.
- Keep important features/functions on the center of the screen, because its more difficult reach the sides and corners of the device.
- Important element should be easily tapped, buttons and elements should have at least a height of 44px.

#### Take Advantage of Mobile Devices' Native Hardware

Mobile-first is not only a way to make everything fit in the screen, is also a way to adapt the capabilities of the hardware, like the camera on mobiles.
For example:
- Cards scanning instead of inputs
- Photo-sharing, because probably the images are in our device.
- 2FA, because we are already in our device.
- Quickly checking of some data like analytics, in mobile probably the data are simplified.
- Use the voice to search.

#### Make Layouts Fluid/Adaptive by Default

The main idea behind the responsive design, is make the design the more fluid possible, avoiding many breakpoints.
This helps to ensure that all sizes will works. Not all users have the same windows size on desktops, and sizes on mobile are too different each other.
- Using percentages
- Setting min and max sizes
- Using SVG, because not lose quality on different sizes
                                      i
#### Don't Forget Abut Landscape Orientation
 
Put attention on landscape orientations, specially on tablets.
On mobiles and tables, usually the users will be navigating in a vertical orientation, but on tablets is more possible that the user prefer a landscape
orientation, so we have make sure that content of the page will adapt that format too.

#### Typography can be Responsive Too

Since devices have different resolutions, using a fixed pixel size on fonts make our design looks too smaller on devices with a large PPI.
We can use em, or rem, where 1px is 1 point, or other techniques like a fluid resize with min and max, to ensure that typography never looks
smaller or bigger but the perfect size on every screen.





