# CartoLineGen
QGIS Plugin for cartographic generalisation (simplification and smoothing) of lines and polygons

REFERENCES

Tutić, D., Lapaine, M. (2009): Area Preserving Cartographic Line Generalization, Cartography and Geoinformation, Vol. 8, No. 11, 84-100, http://www.kartografija.hr/kig/upload/clanci/kig11_Tutic2.pdf.

Tutić, D., Lapaine, M. (2010): New Method for Reducing Sharp Corners in Cartographic Lines with Area Preservation Property. Proceedings of the 14th International Conference on Geometry and Graphics, Kyoto, 289-290, http://bib.irb.hr/datoteka/480211.Tutic_Lapaine_full_paper.pdf.

Author: Dražen Tutić
Institution: University of Zagreb, Faculty of Geodesy
e-mail: dtutic@geof.hr
Date: 27/05/2016

The generalization combines simplification followed by smoothing.

![alt tag](cartolinegen.png)

In process of implemented line simplification the complexity of vector features is reduced. The simplified lines preserve the areas of regions which they might bound. The module transforms a line into another line consisting of fewer vertices, that still approximate the original line. Resulting lines consist of a subset of points on the original line and new points.

By preserving the area features will have some additional properties. The maximal generalization will result in convex shape of line (polygon). Selection or filtering based on area can be performed prior or after the generalization.

In process of implemented line smoothing the sharp corners are smoothed by adding new points (with area preservation constraint). The smoothness is controled by the value of minimal angle of connected segments. The default value od 150 degrees will give good result in most cases. By increasing this value more points (short segments) are added in order to smooth sharp corners.

Smoothing and simplification algorithms implemented in this module work line by line, i.e. simplification/smoothing of one line does not affect the other lines; they are treated separately. Also, the first and the last point of each open line is never translated and/or deleted. The closed lines can be modified on every point.

The main parameter is map scale given as value of map scale denominator. The amount of generalization is controlled by modifying only those parts of line where less then minimal length of segments occure and three neighbouring segments form the "s" shape. Minimal length was determined by analysing coastlines of manually generalised paper maps in diferent scales. It's value is around 0.05 mm at the map scale.
