# nifti_tools
This is a GitHub version of Jimmy Shen's popular NIFTI Tools. It is added here as a repository to allow adding it at a submodule. All credits go to Jimmy Shen:  https://www.mathworks.com/matlabcentral/fileexchange/8797-tools-for-nifti-and-analyze-image

Tools for NIfTI and ANALYZE image (Click LINK HERE for the latest update)
         Description:
If you are confused by identifying which one is the Left-hand-side / Right-hand-side of an ANALYZE image, the UseANALYZE.pdf file can help you to clarify it. You can get the document from LINK HERE.
You may also want to go through FAQ.pdf for practical solutions and real examples, which can also be obtained from the above link.
o If you are confused by the Left side / Right side of an ANALYZE image, the UseANALYZE.pdf file can help you to clarify it. You can also get it from the above link.
o Feature of load_untouch_header_only: It will load exactly whatever stored in the header section of NIfTI or ANALYZE file, and automatically detect the input format. NIfTI structure will be returned for NIfTI file, and ANALYZE structure will be returned for ANALYZE file.
o Feature of load_nii: It not only loads the file, but also transforms the affine matrix to a diagonal matrix with positive entries and re-orients the image matrix correspondingly. This feature makes it different from other software, and it is proven to be a convenient way to tell the orientation immediately, especially in the Left / Right confusion. For NIfTI file with both non-zero sform_code and qform_code, load_nii also allows you to pick your preferred form, with sform_code picked by default.
o Feature of view_nii: It can display & edit the background image, as well as the overlay activation map and ROI etc. If you use this function in your application, the display can be embedded into your existing figure window. If you use it as an individual program, it can also edit the orientation and voxel value of the image, view volume histogram, and save the modified image.
o Feature of reslice_nii: It can interpolate any oblique images with non-orthogonal rotation or shearing and save them into orthogonal orientations that can be loaded with load_nii. In addition, it can be used as a spatial re-sampling tool. If you are only interested in image blob and do not have enough computer memory, you can increase voxel size to make the size of image data file really small.
o Feature of pad_nii: It can pad NIfTI volume from any of the six sides, while keeping the originator, voxel size, data type, and description unchanged. This feature is especially useful after you use reslice_nii, since the new volume will most likely have different dimensions.
o Feature of clip_nii: It can cut off NIfTI volume from any of the six sides, while keeping the originator, voxel size, data type, and description unchanged. This feature is especially useful after you use reslice_nii, since the new volume will most likely have different dimensions.
o Feature of save_nii: It can save NIfTI data into ANALIZE compatible file extension (.img/.hdr), and can be used by other software that does not support NIfTI file format.
 Basic Programs:

1. load_untouch_heade r_only.m: Load only the header section of NIfTI or ANALYZE file. The input file will be automatically detected. NIfTI structure will be returned for NIfTI file, and ANALYZE structure will be returned for ANALYZE file. For usage, type: help load_untouch_header_only
2. load_nii.m: Load N-Dimensional NIfTI file (where N can be from 3 to 7) or ANALYZE file (where N can be from 3 to 4), and apply header info (e.g. affine geometric transform, voxel intensity scaling, etc.) to the data. If your file has more than 3-Dimension (e.g. time series etc.), you can also specify a range to extract only 1 or several volumes. For usage, type: help load_nii
3. save_nii.m: Save N-Dimensional NIfTI structure (where N can be from 3 to 7) that is loaded by "load_nii.m" or made by "make_nii.m" into a NIfTI file. For usage, type: help save_nii
4. make_nii.m: Make N-Dimensional NIfTI structure (where N can be from 3 to 7) based on the N- Dimensional matrix and other optional parameters (e.g. voxel_size, origin, etc.). Using "save_nii" command, the NIfTI structure that is made by "make_nii" can be saved into a NIfTI file. For usage, type: help make_nii
5. make_ana.m: Make 3D ANALYZE structure based on the 3D matrix and other optio nal parameters (e.g. voxel_size, origin, etc.). Using "save_untouch_nii" command, the ANALYZE structure that is made by "make_ana" can be saved into an ANALYZE file in order to be compatible with some ANALYZE only programs. For usage, type: help make_ana
6. reslice_nii.m: Re-sample 3D (or 4D) NIfTI file, or ANALYZE file with affine matrix M in .mat file, and save the re-sampled data into a new NIfTI file. The program will base on the affine matrix, which is especially useful for oblique images with non-orthogonal rotation or shearing that cannot be loaded with "load_nii.m". You can also specify voxel_size, etc. It will not cause negative effect, as long as you remember not to do slice time correction after using "reslice_nii.m". For usage, type: help reslice_nii
7. pad_nii.m: Pad the volume(s) in NIfTI structure from any of the six sides, while keeping the originator, voxel size, data type, and description unchanged. The program is especially useful after you use reslice_nii, since the new volume will most likely have different dimensions. You can choose the value for the padding voxel, which is 0 by default. For usage, type: help pad_nii
8. clip_nii.m: Clip the volume(s) in NIfTI structure from any of the six sides, while keeping the originator, voxel size, data type, and description unchanged. The program is especially useful after you use reslice_nii, since the new volume will most likely have different dimensions. For usage, type: help c lip_ nii
9. view_nii.m: View & Edit 3D (or 4D) NIfTI or ANALYZE structure that is loaded by "load_nii.m" or made by "make_nii.m". Activation map, ROI, etc. can be overlaid on top of a background image (see PICTURE HERE). Plotted view can be embedded into your existing figure window. If you use it as an individual program, it can also edit the orientation and voxel value of the image, view volume histogram, and save the modified image. For usage, type: help view_nii
10. load_untouch_nii.m: Load N-Dimensional NIfTI file (where N can be from 3 to 7) or ANALYZE file (where N can be from 3 to 4), but do not apply any changes that are indicated in the header. WARNING: Do not use "view_nii.m" to view the structure that is loaded by "load_untouch_nii.m". For usage, type: help load_untouch_nii
11. save_untouch_nii.m: Save N-Dimensional NIfTI structure (where N can be from 3 to 7) or ANALYZE structure (where N can be from 3 to 4) that is loaded by "load_untouch_nii.m" or made by "make_ana.m" into a new NIfTI or ANALYZE file. If you do not modify the loaded dataset, the header
 
and data in the new saved file should be the same as those in the original file. For usage, type: help save_ unto uc h_ nii
Other Programs:
1. collapse_nii_scan.m: Integrate multiple single-scan NIfTI or ANALYZE files into a multiple-scan NIfTI file. For usage, type: help collapse_nii_scan
2. expand_nii_scan.m: Break a multiple-scan NIfTI file into multiple single-scan NIfTI files. For usage, type: help expand_nii_scan
3. save_untouch_slice.m: Save back to the original image with a portion of slices that was loaded by load_untouch_nii. You can process those slices matrix in any way, as long as their dimension is not altered. For usage, type: help save_untouch_slice
4. get_nii_frame.m: Return the number of time frames of a NIfTI file. For usage, type: help ge t_ nii_ fra me
5. flip_lr.m: Flip NIfTI or ANALYZE file Left-Right along the plane across the originator, and save the L-R flipped data into a NIfTI file. WARNING: Please use this program with caution, although you can always flip it back. For usage, type: help flip_lr
6. load_nii_ext.m: Load header extension from a NIfTI file. For usage, type: help load_nii_ext
7. mat_into_hdr.m: Integrate affine matrix in old SPM .mat file into its .hdr header file. Thus, the ANALYZE file is converted into a NIfTI file with the updated .hdr header file. For usage, type: help mat_ into_ hdr
For NIfTI file, "load_nii.m" will take the affine matrix in its header and make appropriate space transformation. The affine matrix will be transformed to a diagonal matrix with positive entries and the image matrix in the loaded structure will be correspondingly re-oriented, which is actually in neurological convention or RAS. i.e. X axis from Left to Right, Y axis from Posterior to Anterior, and Z axis from Inferior to Superior.
For ANALYZE file, "load_nii.m" will load the image as is. Since an ANALYZE image could be in RAS or LAS depending on your assumption, many people are confused by its laterality, especially when an ANALYZE file is processed by different software. If you are still using ANALYZE file, I strongly recommend that you take a look at the table that I summarized in UseANALYZE.pdf file.
Because "load_nii.m" can only handle a subset of affine transform (flipping and orthogonal rotation with a total of 48 orientations), you need to use "reslice_nii.m" to handle the rest of the space transformation (e.g. NIfTI files with non-orthogonal rotation, shearing etc.). It will not cause negative effect, as long as you remember not to do slice time correction after using "reslice_nii.m".
If you prefer the loaded dataset untouched, you have to use "load_untouch_nii.m" and " save_untouch_nii.m" program pair. In this case, the affine matrix in NIfTI header will not be applied to the loaded dataset, and the loaded dataset should not be used for other programs, like "view_nii.m" etc.
Two example datasets, "avg152T1_LR_nifti.nii" and "avg152T1_RL_nifti.nii", are provided under NIfTI web site http://nifti.nimh.nih.gov/nifti-1/data. As is indicated on NIfTI web site, "The first image (LR) is stored in radiological convention (LAS). The second image (RL) is stored in neurological convention (RAS). Any NIfTI compliant viewing software should display these images identically". When you load them with "load_nii.m", and display them with "view_nii.m", you can expect the same result.
 
       Update History (Click LINK HERE to download the latest version):
 2013-03-06: Since voxel size can be less than 0, I changed the default voxel_size in reslice_nii.m from rounded minimum voxel_size in original NIfTI header to absolute minimum voxel_size in original NIfTI header. This fixed reslice_nii bug.
 2012-10-12:
1. New program "clip_nii.m" is provided to cut off NIfTI volume from any of the six sides, while
keeping the originator, voxel size, data type, and description unchanged.
2. In "view_nii.m" program, volume histogram plot feature is added under its view menu.
3. Thanks to the feedback and contribution of Andrew Davis from McMaster University, now you can load and save .gz file if you are using MATLAB 7.1 (with java enabled) and above.
4. Thanks to the feedback and contribution of Félix Morency from Centre Hospitalier Universitaire de Sherbrooke, bug with filename containing path is fixed.
 2011-09-21: Thanks to the feedback of Matthew Bickell from University of Cape Town, a bug is fixed when edit voxel in millimeter unit.
 2011-09-01: "make_nii.m" is now able to automatically detect both single and double complex data typ e.
 2011-06-10: You can now create RGB NIfTI / ANALYZE file structure using make_nii / make_ana program.
 2011-05-02:
1. New program "load_untouch_header_only.m" is provided to load only the header section of NIfTI or
ANALYZE data.
2. New program "save_untouch_slice.m" is provided to save back a portion of processed data that were loaded by load_untouch_nii.
 2011-03-10:
1. Added a new feature in "view_nii" program to edit voxel value or set landmarks and save the
modified image.
2. Thanks to the code from Roman, which speed up "load_untouch_nii_img" program when the slices are not loaded at once.
 2011-02-15:
1. Fixed an overlay problem in view_nii.m, so the color of minimum / maximum value is now showing
properly.
2. Included an overlay example in FAQ.pdf.
 2011-02-03: Thanks to the feedback of Roman Fleysher from Yeshiva University, I fixed a bug when loading a quaternion form NIfTI data.
 2010-08-19: Thanks to Rembrandt from Radboud University Nijmegen (Netherlands), I made 2 small changes to handle the exceptions.
 2010-04-13: Fixed a bug in "collapse_nii_scan" to collapse Analyze format data.
 2010-01-06: "load_untouch_nii" now supports loading specific slices of NIfTI or Analyze format.
 
 2009-09-09: While an N-Dimensional matrix can be saved into a NIfTI file using "make_nii / save_nii" command pair, a 3D matrix can also be saved into an ANALYZE file using "make_ana / save_untouch_nii" in order to be compatible with some ANALYZE only programs.
 2009-07-03: Fixed several bugs, and posted informative UseANALYZE.pdf table.
 2009-03-25: Thanks to the feedback of Kate Fissell from University of Pittsburgh, transformation matrix
M will no longer be saved by save_untouch_nii.m.
 2009-03-17:
1. Thanks to the feedback of Bryce Wilkins from USC, a typo in one of my message display is fixed.
2. Thanks to the suggestion of Ashish Raj from Cornell, 'expand_nii_scan.m' is modified and 'collapse_nii_scan.m' is added.
 2008-12-05: Default data type for 'make_nii.m' now follows the data type of 'img' matrix, instead of float32.
 2008-12-04: Fixed a bug in fliplr.m when reading files.
 2008-10-23:
1. Properly handle fread/'*char' problem with foreign characters in MATLAB 7 and above.
2. Reordered input parameters for 'reslice_nii.m' program.
 2008-09-04: Extended Load / Save / Make programs to N-Dimension, where N can be from 3 to 7 for NIfTI data and from 3 to 4 for ANALYZE data.
 2008-08-28: Added "load_untouch_nii.m" and "save_untouch_nii.m" program pair. See detail in Description above and in FAQ.pdf file.
 2008-08-21: Added a "verbose" parameter for "reslice_nii.m" to provide an opportunity to disable the progress display.
 2008-08-19:
1. Program "load_nii.m" is modified to take tolerance parameter, which is the distortion allowed in the loaded image for a non-orthogonal affine matrix. If you set 'tolerance' to 0, it means that you do not allow any distortion. If you set 'tolerance' to 1, it means that you do not care any distortion. The image will fail to be loaded if it can not be tolerated. By default, it is 0.1 (10%).
2. New program "reslice_nii.m" is provided to perform any 3D affine transform defined by a NIfTI format image, especially for those non-orthogonal affine transform (oblique image) that cannot be loaded by "load_nii.m".
3. New program "reslice_nii.m" can also be applied to generate an isotropic image from either a NIfTI format image or an ANALYZE format image.
4. New program "flip_lr.m" is provided for LAS->RAS (or RAS->LAS) conversion.
 2008-07-07: Thanks to the feedback of Holger Krause from Heinrich-Heine University Dusseldorf, the bug in "mat_into_hdr.m" when input file containing a path has been fixed.
 2008-04-08:
1. Added a new feature to load and save NIfTI's header extension. Program nii.ext = load_nii_ext(NIfTI_file_name) will return empty if there is no header extension, and save_nii(nii, NIfTI_file_name) will save header extension if there is a valid nii.ext structure.
2. Fixed a bug when loading qform data, which was introduced on 01-FEB-2008.

 2008-02-01: Thanks to Jeff Gunter from Mayo who suggested to display a warning message instead of throwing an error for a very oblique image. Especially thanks to his code of checking qform rotation before applying voxel size modulation.
 2007-05-03: Fixed a bug that caused the "value at crosshair" and "value at cursor" always displaying the value of the first 3D volume when viewing a 4D image using view_nii. Thanks to Ning Cao from UKY who reported and fixed this bug.
 2007-04-26:
1. Modified save_nii command, so earlier versions of SPM can also open it with correct originator.
2. Modified FAQ.pdf file with several categories.
 2007-04-19:
1. Many users asked for a direct load of the affine matrix in the .mat file of earlier versions of SPM. Now if "load_nii" in the tools detects that the file you are loading is an Analyze file and there is a .mat file with the same file, it will automatically integrate the affine matrix in the .mat file into the .hdr structure.
2. Fixed a bug in "mat_into_hdr.m" program.
 2006-12-20:
1. In "view_nii" window, a new menu item "Save displayed image as ..." is added in the "File" menu. This is especially helpful if people use "Convert orientation" item in the "Edit" menu to convert their old non-RAS Analyze image to RAS orientation. After conversion, the displayed RAS image can now be saved.
2. Removed integer rounding for "hdr.hist.originator" in "load_nii", but origin voxel will still be rounded by "view_nii".
 2006-12-15:
1. Improved data scaling process. If scl_slope=1 and scl_inter=0, nothing has to be scaled, which is the same as scl_slope=0 situation. Otherwise, all values of scaled img will be stored in 32-bit rather than double precision, unless original img is 64-bit. This improvement dramatically reduced the size of the scaled image, unless the original image has double precision.
2. Fixed a bug in calculating origin position when original origin position is [0 0 0] (an invalid origin).
 2006-09-25: Added "mat_into_hdr.m" script to convert the ANALYZE 7.5 SPM Reoriented image file into NIfTI format, and integrate the affine matrix in its matlab file into its header file.
 2006-07-26: Due to round-off of quaternions (quatern_b/c/d), sqrt(1.0-(b*b+c*c+d*d)) may become complex because value inside sqrt may go below 0 (e.g. -1e-6). Instead of complex, now 0 will be used in this case. Thanks to Jeff Gunter who reported this issue.
 2006-07-04: Thanks to Michael Harms from WUSTL who reported and fixed some bugs in loading and making RGB data. He also added codes to save AnalyzeDirect compatible RGB data.
 2006-06-28:
1. "unxform_nii" from Jeff is included to provide an option of putting image orientation back to its
original status.
2. "expand_nii_scan" is modified so the expanded image files will be appended with a 4-digit number starting from 0000.
 2006-06-03:

1. There was a bug in converting some permuted images to RAS orientation. It has been fixed now. Thanks to Jeff Gunter from Mayo Clinic who reported this bug.
2. hdr.dime.glmax and glmin are updated if hdr.dime.scl_slope is non-zero.
 2006-04-20: Image data is now always loaded according to the size that is specified in its header. This is because that the size of some image data is incorrectly larger than what specified in "hdr.dime.dim" field, which has caused problem to load image data.
 2006-03-22: It now supports both COMPLEX64 and COMPLEX128 data type.
 2006-03-10: "nii.hdr.scl_slope" will take "avw.hdr.roi_scale" value, which is a non-ANALYZE7.5 field
but exclusively used by SPM.
 2006-03-07: Image data type will be converted to "double" in the case that "scl_slope" is used.
 2006-02-24:
1. Fixed a bug to reorder "pixdim" and "originator" field for some NIfTI data.
2. Added "rot_orient" and "flip_orient" fields under "hdr.hist" if package make conversion of the NIfTI data into RAS orientation system.
 2005-11-16: It now supports both new_RGB (RGB triple) & old_RGB (used by Analyze 6.0 from AnalyzeDirect Inc).
 2005-11-07: Images whose cardinal planes are slightly off Cartesian coordinates will also be loaded. See detail in "xform_nii.m".
(Click LINK HERE to download, which is also available on MathWorks File Exchange)
Contact: Please send your feed back to me (jimmytoolbox@gmail.com)
          
