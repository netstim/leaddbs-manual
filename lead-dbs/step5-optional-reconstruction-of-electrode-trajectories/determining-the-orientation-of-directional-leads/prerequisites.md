# Prerequisites

For a reliable detection of the rotation of directional leads the following prerequisites are needed:

1.  Adequate Slice Thickness:

    The structures the algorithm needs to detect are very small (1.5 to 2 mm) and consequently CT imaging which aims to correctly depict these structures needs to have a very small slice thickness as well. Slice thickness should be no larger than 1mm but we recommend using even thinner slices of 0.5 to 0.7 mm.
2.  Low Polar Angles:

    The polar angle describes the angle between the axis along the CT scanner (perpendicular to the CT slices) and the lead trajectory. If the polar angle is 0 °, the lead itself is perpendicular to the CT slice and imaging of the lead's substructures like electrodes is optimal. If the polar angle is large, the lead is more parallel to the CT slices and imaging gets subsequently worse. The algorithm has been shown to work for polar angles up to 60 ° when using a slice thickness of 0.7 mm which should suffice in most clinical cases. However results may worsen for even lower polar angles with larger slice thickness. While the implantation angle of course can not be modified, large polar angles can be avoided by proper positioning of the patient inside the CT scanner. For standard STN/GPi/VIM trajectories head/neck flexion in the CT scanner should be avoided and head/neck extension (e.g. using a neck cushion) can help to lower polar angles and increase imaging quality.
