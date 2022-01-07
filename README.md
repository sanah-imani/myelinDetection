# myelinDetection

The overall goal of this project is to build a framework to automate/semi-automate the process of detecting myelin given the relevant electron microscopy (EM) and segmentation data. 

This could then play a role in discriminating between myelin distribution in inhibitory and excitatory neurons and perhaps even explaining electrophysiological properties of certain neural cells of interest.

<h> Algorithm Outline </h>
<ol>
  <li> Run a connected components analysis on the segmentation. </li>
  <li> Detect the bordering region of the axon by performing a logical XOR of the mask representing the axon and the mask produced by the binary dilation of the same. </li>
  <li> A “final” mask is then created by performing a logical OR of the axon mask and the border mask </li>
  <li> A euclidean distance transform (EDT) is done to create a distance map on a binary image and the mean value is calculated in order to estimate the width of the myelin.</li>
  <li> A KD-tree structure is utilized to find the shortest distance between the points on the border mask and the selected connected component. </li>
  <li> Finally, we  find the voxels that are within the threshold distance (calculated in step 4) and generate a mask to isolate the indices that belong to the estimated myelin positions. </li>
 </ol>

For more details: https://docs.google.com/presentation/d/1fBVNDw5o_EvZNgeu1wixCFIT2e9HnkALxQIK7ZGrwXY/edit?usp=sharing
