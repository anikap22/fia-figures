# fia-figures
data for map figures from "A Spatially Explicit, Empirical Estimate of Tree-Based Biological Nitrogen Fixation in Forests of the United States": https://agupubs.onlinelibrary.wiley.com/doi/10.1029/2019GB006241

### Figure 2 a-d:
`fngrid_new.RDS`: N fixation rate per forest area, accretion (a)  
`gngr_grid_new.RDS`: N fixation rate per ground area, accretion (b)  
`grn_grid_new.RDS`: N fixation rate per forest area, n demand (c)  
`grngr_grid_new.RDS`: N fixation rate per ground area, n demand (d)  

Example code for map:
```
##map of fixed nitrogen (per forest area) rate average in cell
fn.grid <- readRDS("output/fngrid_new.RDS")
nlev <- 64
ticks <- 2^(-2:6)
image.plot(lon.list, lat.list, log(fn.grid+0.1), 
           nlevel = nlev, col = tim.colors(nlev),
           axis.args = list(at = log(ticks), 
                            labels = ticks,
                            cex.axis = 1.5),
           legend.args = list(text = expression('kg N ha forest'^-1*' yr'^-1), 
                              side = 4, 
                              font = 2, 
                              line = 3.5, 
                              cex = 1,
                              mar = 5),
           xlab = "", ylab = "latitude",
           ylim = c(latminint-1, 60+1), xlim = c(-140, lonmaxint+1),
           zlim = c(log(0.1), log(64)))
title(main = "N Fixation Rate \n Per forest area \n Accretion", 
      cex.main = 1.5)
mtext("(a)", font = 2, adj = 0.01, padj = -0.5)
map('world', regions = 'usa', add = TRUE, col = 'black')
```

### Figure 5:
`dep_fo.tif`: N deposition per forest area (a)  
`dep_gr.tif`: N deposition per ground area (b)  
`tree_fo.tif`: Tree BNF per forest area (c)  
`tree_gr.tif`: Tree BNF per ground area (d)  
`under_fo.tif`: Understory BNF per forest area (e)  
`under_gr.tif`: Understory BNF per ground area (f)  
`asym_fo.tif`: Asynbiotic BNF per forest area (g)  
`asym_gr.tif`: Asymbiotic BNF per ground area (h)  
`rock_fo.tif`: rock weathering per forest area (i)  
`rock_gr.tif` rock weathering per ground area (j)  
`totaln_fo.tif`: Total non-agricultural N input per forest area (Tree BNF + Understory BNF + Asymbiotic + N deposition) (k)  
`totaln_gr.tif`: Total non-agricultural N input per ground area (Tree BNF + Understory BNF + Asymbiotic + N deposition) (l)  
`pctbio_fo.tif`: Percent N input from SNF per forest area (Tree BNF + Understory BNF) / Total N input (m)  
`pctbio_gr.tif`: Percent N input from SNF per ground area (Tree BNF + Understory BNF) / Total N input (n)  

### Figure 6 a-b:
`N_PCT_tree.tif`: Percent non-agricultural N input from tree BNF, accretion (a)  
`N_PCT_tree_ndfa.tif`: Percent non-agricultural N input from tree BNF, n demand (b)  

