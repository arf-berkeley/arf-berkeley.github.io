## **How to create site grid in QGIS**

Start QGIS project in UTM (metric) coordinates. Note the EPSG code and make sure you use the same one in Reachview3.


### **1. Delimit grid area**

Bring Reachview position directly into QGIS with the GPS Panel (Autodetect, port 9002)

Shoot in bounding box (or at least one edge with 2 points) with GNSS

In QGIS Create Study Area polygon (extent of grid points)

You can use the Advanced Digitizing pane to constrain vertex placement (e.g., to make a rectangular feature). Holding down CTRL- letter (y,x,a,d) limits that axis.



<p id="gdcalert1" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image1.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert2">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image1.png "image_tooltip")



### **2. Make grid of regular points inside delimited area**

Create grid of points by using Toolbox > Vector Creation > Regular Points

In ArcPro there’s a similar function called “[Create Fishnet” in the Sampling Toolset](https://pro.arcgis.com/en/pro-app/latest/tool-reference/data-management/an-overview-of-the-sampling-toolset.htm). You might have to create Polygons then convert Vertices to Points.



<p id="gdcalert2" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image2.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert3">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image2.png "image_tooltip")


The point grid can be shifted or rotated to match an existing baseline, as needed. Select all regular points and put in Edit mode. Snapping On can be helpful (or not) at this step. 

The next two tools are in the Advanced Digitizing Toolbar

**Choose Move Feature(s)**

Move one point with this tool and the all selected features should move as well.



<p id="gdcalert3" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image3.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert4">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image3.png "image_tooltip")


**Rotate Feature tool**. 

Move the centerpoint of the rotation from the centroid of the selection by holding CTRL key and moving the small crosshair from the centroid to the position you’d like to rotate the points around.



<p id="gdcalert4" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image4.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert5">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image4.png "image_tooltip")


In this case I rotated the grid around the existing lower-left corner of one of the 20x20m grids and then at the north end of the grid I rotated a few degrees (1.8 deg) to match existing baseline.


### **3. Clean up auto grid**

Delete the extraneous grid points and keep the ones you want.

Add **Name (String) **field to shapefile and name the important grid corners.

At this point you could just navigate to those points in QGIS (Connect the RTK GNSS via TCP-IP or Bluetooth). See notes concerning how to connect QGIS machine to EMLID

Or use Stakeout in EMLID Reachview3 or some other controller software.


### **4. Export to CSV for use in Stakeout in Reachview3**

Save out the coordinates to a table

Add **Easting, Northing, **and **Elevation **Fields **(**Type:** Double). **

Fill with $x and $y value to populate with UTM coordinates.

Save out table to CSV in the following format



<p id="gdcalert5" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image5.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert6">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image5.png "image_tooltip")


**Reachview3 CSV Import Window**

Use Stakeout functionality in Reachview 3 to navigate to the grid corners.

On Rover choose Position Output, TCP-IP tab. Data should be sent as NMEA stream from the Rover emlid to other devices on the same Hotspot network. 

Create Hotspot and put your field computer and the Reach rover on the same Hotspot network. In QGIS open GPS Panel and configure to Autodetect (often it's Localhost:9002). NMEA mode.

Using TCP-IP you can point multiple machines on the same network and it'll indicate your current Rover position realtime in QGIS -- good for teaching!

You could just navigate in QGIS zoomed in and find the grid corners (manual stakeout) by zooming in enough.
