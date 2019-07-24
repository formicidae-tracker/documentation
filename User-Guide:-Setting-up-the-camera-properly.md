# Context

> This page is a stub, to be furtherly improved

Optimal camera, and lens choice is required in order to detect ant properly.

# Approach to follow to have optimal results.

Depending on the ant size you are studying, the tag size used, and the camera properties you would to use a proper combination of lenses, distance to object and optionally extension tube to be able to focus on the ant plane.

To find the optimal parameters, first we need to compute the magnification we will be working with. Be careful as every lenses is designed to work in a given range of magnification. Our purpose is to map an actual object height h_o ( a tag of 1.6mm) to an size in pixel in the final image h_i. Currently the tracking algorithm is tested to work well with tag size of 30-50 pixel in the final image. Depending on our camera physical pixel size (h_p) we can compute the magnification we will be working. m = - h_o / ( h_i * h_p). We have to make sure that our lenses supports that magnification.

This is not the end of the road, as a lenses also have resolution limitation. resolution for lenses are measure in lp/mm (line pair per millimiter). To simplify, the higher resolution we are working with the more two perfectly black and white line will be transformed to a pure gray by the lenses itself, due to imperfection but also light diffraction. 

You can refer to the lens datasheet to determine for a lens and aperture setting what would be the maximal resolution you should work with, which would be a MTF of more than 60-70% over the whole image. For the rodagon WA 40 mm and the Apo-Rodagon-N 50mm, that would be working at a resolution lower than 25-30 lp/mm. To decrease you working resolution given a tag size, you can always increase the desired tag size in pixel in the destination image (but it will decrease your magnification, maybe out of the lens range).

Finally once you found the pixel tag size that gives you a good working magnification and resolution of the lens, you can derive from your sensor characteristic:
 * The size of the arena that could be tracked.
 * The number of extension tube to use to be able to focus the camera on the tags

# Using the FORT experiment calculator to determine the right lens and extension tubes.

To help you determine the optimal parameter using the aforementionned methodology you cna use [this google spreadsheet](https://docs.google.com/spreadsheets/d/1O8jTYh_x0X60FvLMI6AnxPJqFTBPCzauivXxzxy9Sjo/edit?usp=sharing): 
   
1. Select the camera you are working with.
2. Select one of the available lens
3. Sets at the beginning the extension tube to zero
4. Enter the tag size
5. Enter the desired tag size in pixel
  * Verify that the automatically computed magnification column stays in green, modify the tag size until it is.
  * Verify that the resolution stays below 25-30 lp/mm (or look up the right value in the lens datasheet)
7. If you cannot find a suitable setting for the pixel size, try another lenses. At Keller's group only Rodagon WA 40 and Apo Rodagon N 50 are available
8. The spreadheet automatically compute the working area depending on the maginification and the camera characteristics. Please check that they suits the experiment you want to build
9. Select an extension tube that allow you to be in focus (if not the whole line turns red). This is when the min focus is negative and the max focus column is positive.

Now you should have determined which lens and extension tube you need to use to proceed with your experience. The spreadsheet also give you the sensor distance: distance between the tag plane and the sensor plane of the camera (which is inside the camera), or the free distance: distance between the lense and the tag plane. Use this distance to determine at which level of the frame you need to put your ants.

# Setting up physically the optical system

1. Mount the right lens and extension(s) tube(s) on the system (hint 24+12=36mm, you can combine two extension tube if needed).
2. Add the IR filter on the lense
3. Draw on piece of paper the desired working area, and put it in the system.
4. Using genicam browser start the camera and the illumination system (need to be improved)
5. Move the camera stage to be able to see the whole working area. Fix the stage firmly
6. Put a tag sheet in the system, you should be able to focus it.
7. Put the ant in the system. You will certainly need to refocus properly the system


