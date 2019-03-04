# imFexta
Image analysis software to track and calibrate extension using images acquired from optical tweezers

#### An example image correction of the extension-time profile obtained from a DNA intercalation experiment.The template images containing each bead, as chosen by the user is shown on the top left panel. The bottom left shows the bead detection. The ‘calibration with DNA’ function will cross-examine the image data with stage data for the same dsDNA molecule and determine the pixel to nm converstion factor and the offset due to DNA tether points as displayed in the corresponding text fields. The blue curve on the right shows a long-term experimenal data of extension-change as measured by the stage. The red data shows the absolute end-to-end distance as dtermined by the image information. The descrepancy between the data is indicative of long term drift, which is shown in with yellow data points. The stage data is then corrected for the drift.  

The raw extension data is the position of the stage, which we calibrate using the force-extension profile of a dsDNA molecule to find the offset and obtain the end-to-end extension between the DNA tether points. However, this offset is prone to change over time, due to thermal drift of the micropipette tip. Information from the image of the two beads can be directly used to measure the absolute distance between the bead centers and thereby determine the end-to-end distance of the tethered DNA molecule. This allows us to perform, long-term experiments with a tethered DNA molecule. For instance, to probe ssDNA-binding dynamics, one needs to first digest a strand to prepare the ssDNA substrate before performing the experiment which may consume a considerable amount of time between obtaining the FEC of a dsDNA and generating an ssDNA to perform the experiment and thus the stage offset determined by the dsDNA curve may no longer be accurate. In addition, during force-clamp experiments, the pipet-drifts may introduce artifacts in the data that are impossible to detect without the information of the absolute end-to-end extension. Therefore, I developed the image analysis module to determine the absolute DNA-extension to deconvolve the data from possible artifacts. Comparison between the extension-changes measured from images and obtained from the stage calibration allows us to eliminate artifacts from drifts while preserving the high-resolution data obtained from the stage.  
The bead centers are determined by a cross correlation method that uses a segment of the image containing each bead as a template. Therefore, the bead detection does not depend on the variables such as bead-size or image intensity. The image analysis module finds two parameters to calibrate the image information. First by comparing corresponding step sizes of the stage (in nm) and the images (in pixels), the pixel to nm conversion factor is calculated. This factor is determined by the pixel resolution and the field of view size of the camera, and therefore will not change with DNA molecules. Because the cross-correlation method provides the distance between the two bead centers, we are also required to find the total offset, which is the sum of the two distances from the center of a given bead to the DNA tether point on that bead. This offset will change for each DNA-tether but will not change for a given captured DNA molecule.  Because, the extension profile of the dsDNA is accurately calibrated, we use this information to find the offset to the tether points
