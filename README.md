# OpenColorIO Colour Management Test

## What it Is
This is a simple OpenColorIO configuration and LUT / matrix set that is useful for testing color management.

## What it Does
Traditionally, many applications assume sRGB primaries for input and output. However, some areas remain without color management that form critical pinch points where the primaries or transfer curve cannot be correctly displayed. This configuration shifts simply rotates the sRGB primaries to make it extremely clear where color management is not working.

## How it Does It
This configuration takes the RGB triplet and rotates the primaries by one. This is accomplished using a simple matrix transformation that is merely the sRGB / 709 primaries matrix with a column swap.

## What Does it Include?
Included with the basic OpenColorIO configuration and LUT directory is a Marcie test image. This Marcie test image is an RGB image that is rotated as per the above description. When viewed on a display and dumped without colour management, the RGB values will be displayed upon the display's colour space, which is typically something close to an sRGB / 709 set of primaries, and Marcie will look extremely strange.

## How to Properly View the RotatedTesting Marcie?
Using the application of your choice, set the Marcie image to the included RotatedTesting colour space. Your view LUT should be set to sRGB, which simply corrects the RotatedTesting reference space values back to proper D65 sRGB / 709. If you are on a wide gamut display, this correction will only correct to sRGB / 709 theoretical values, and as such Marcie will appear overly saturated on your wide gamut display. If you wish to further correct for this behavior, it should be relatively simple to install an additional transform at the end of the sRGB transformation to correct for whatever wide gamut display type you have.

## Examples of Colour Management Breaking Points
Now that you are armed with the tool, what should you test for and what can you expect?

### Color Wheel Testing
Use a tool that features a colour wheel or square selection interface element. Select a colour and paint on Marcie. Does the colour you selected match the colour you see in the sRGB View transform? If not, your appplication isn't colour managed!

### Eye Dropper Tool Testing
Using an eye dropper / colour picker tool, select a colour from Marcie. Does the reported colour match the colour that the application is presenting to you? If it doesn't, your application isn't colour managed!

#### Multiple Monitor Testing
Does your application allow you to pick a custom View transform per window? If not, your application isn't colour managed! This is mandatory in order to achieve colour critical results per display in a multi-monitor setup.

Questions, comments, concerns, or other things can be offered up via the Issues tracker.


