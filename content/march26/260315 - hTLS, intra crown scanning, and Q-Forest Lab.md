## hTLS - high TLS
- hTLS is a method introduced in Griese et. al 2026 that involves mounting the scanner on an 8m tripod to capture more detail of crown
- TODO: which forest did the study did this in? how tall are the trees? what other forest structure elements do they have? 
- NOTE: this study used a Leica <...> scanner, which is 9x lighter than our VZ-400i 
![[assets/Pasted image 20260316001817.png]]
- However, their results are consistent with another study using our VZ-400i, see below

## [Griese et. al 2026](https://doi.org/10.1093/aob/mcab051) intra crown scanning 
- introduces canopy laser scanning (CLS): "We lifted a high-end laser scanner into the canopy of six large, old trees by using scaffolding or climbers."
- WHERE: tropical rainforests in Colombia, Brazil and Peru. Tasmania giant eucalypt forests.
- HOW: using ours lasers! 
	-  1 horizontal scan + 1 zenith (90 deg) scans. 
	-  "Exact scan locations were picked opportunistically based on ease of access and to minimize occlusion", 1-2, 3-5, 20+ meters from the tree, around 5m away from each other. More scans were taken than needed, many were discarded
	- Appendix mentions coloring points in CloudCompare
	- NOTE: This study focused on scanning specific trees instead of an entire forest area.
	-  ![[assets/Pasted image 20260316113347.png]]
	- ![[assets/Pasted image 20260316103339.png]]
- CLS + TLS combined -> a consistent high point cloud quality.
	- RESULTS -> Our results show that CLS improves point cloud precision and reduces occlusion, enabling more accurate assessments of tree architecture and canopy biodiversity. Where feasible, this advancement creates new opportunities for 3D modelling of **microhabitats, estimating aboveground carbon stocks, monitoring species and studying ecological dynamics**.
	- RESULTS 2 -> Potential for understory tree identification

## Q-Forest Lab
- Q-Forest Lab is an AMAZING resource to analyze forest lidar data from VZ-400i. 
- Their [Github account](https://github.com/qforestlab/riscan-general) has a bunch of guides and resources
- notable programs: GBSepartion
