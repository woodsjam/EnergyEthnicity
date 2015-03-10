Research Notes for Housing Market Institutions Drive Race and Ethnicity Differences in Energy Consumption
========================================================

Load in the raw data.

```r
RECS <- read.csv("~/Research/EnergyEthnicity/Data/recs2009_public.csv")

summary(RECS)
```

```
##      DOEID          REGIONC         DIVISION      REPORTABLE_DOMAIN
##  Min.   :    1   Min.   :1.000   Min.   : 1.000   Min.   : 1.00    
##  1st Qu.: 3022   1st Qu.:2.000   1st Qu.: 3.000   1st Qu.: 8.00    
##  Median : 6042   Median :3.000   Median : 5.000   Median :15.00    
##  Mean   : 6042   Mean   :2.628   Mean   : 5.373   Mean   :14.78    
##  3rd Qu.: 9062   3rd Qu.:3.000   3rd Qu.: 7.000   3rd Qu.:21.00    
##  Max.   :12083   Max.   :4.000   Max.   :10.000   Max.   :27.00    
##                                                                    
##     TYPEHUQ        NWEIGHT            HDD65           CDD65     
##  Min.   :1.00   Min.   :  476.1   Min.   :    0   Min.   :   0  
##  1st Qu.:2.00   1st Qu.: 6297.0   1st Qu.: 2198   1st Qu.: 561  
##  Median :2.00   Median : 7970.6   Median : 4483   Median :1045  
##  Mean   :2.66   Mean   : 9403.0   Mean   : 4141   Mean   :1415  
##  3rd Qu.:3.00   3rd Qu.:11330.0   3rd Qu.: 5913   3rd Qu.:1897  
##  Max.   :5.00   Max.   :95779.1   Max.   :12525   Max.   :5480  
##                                                                 
##     HDD30YR         CDD30YR     Climate_Region_Pub    AIA_Zone    
##  Min.   :    0   Min.   :   0   Min.   :1.000      Min.   :1.000  
##  1st Qu.: 2224   1st Qu.: 712   1st Qu.:1.000      1st Qu.:2.000  
##  Median : 4502   Median :1179   Median :3.000      Median :3.000  
##  Mean   : 4135   Mean   :1444   Mean   :2.601      Mean   :3.265  
##  3rd Qu.: 5854   3rd Qu.:1842   3rd Qu.:4.000      3rd Qu.:4.000  
##  Max.   :13346   Max.   :5357   Max.   :5.000      Max.   :5.000  
##                                                                   
##  METROMICRO    UR          KOWNRENT        CONDCOOP         YEARMADE   
##  METRO:10302   R:2427   Min.   :1.000   Min.   :-2.000   Min.   :1920  
##  MICRO: 1109   U:9656   1st Qu.:1.000   1st Qu.:-2.000   1st Qu.:1955  
##  NONE :  672            Median :1.000   Median :-2.000   Median :1975  
##                         Mean   :1.338   Mean   :-1.801   Mean   :1971  
##                         3rd Qu.:2.000   3rd Qu.:-2.000   3rd Qu.:1991  
##                         Max.   :3.000   Max.   : 2.000   Max.   :2009  
##                                                                        
##  YEARMADERANGE    OCCUPYYRANGE     CONVERSION        ORIG1FAM     
##  Min.   :1.000   Min.   :1.000   Min.   :-2.000   Min.   :-2.000  
##  1st Qu.:2.000   1st Qu.:6.000   1st Qu.:-2.000   1st Qu.:-2.000  
##  Median :4.000   Median :7.000   Median :-2.000   Median :-2.000  
##  Mean   :4.028   Mean   :6.692   Mean   :-1.753   Mean   :-1.952  
##  3rd Qu.:6.000   3rd Qu.:8.000   3rd Qu.:-2.000   3rd Qu.:-2.000  
##  Max.   :8.000   Max.   :8.000   Max.   : 2.000   Max.   : 1.000  
##                                                                   
##     LOOKLIKE         NUMFLRS          NUMAPTS           WALLTYPE    
##  Min.   :-2.000   Min.   :-2.000   Min.   : -2.000   Min.   :1.000  
##  1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.: -2.000   1st Qu.:2.000  
##  Median :-2.000   Median :-2.000   Median : -2.000   Median :3.000  
##  Mean   :-1.956   Mean   :-1.067   Mean   :  4.487   Mean   :2.739  
##  3rd Qu.:-2.000   3rd Qu.:-2.000   3rd Qu.: -2.000   3rd Qu.:3.000  
##  Max.   : 2.000   Max.   :35.000   Max.   :365.000   Max.   :9.000  
##                                                                     
##     ROOFTYPE          STUDIO          NAPTFLRS        STORIES     
##  Min.   :-2.000   Min.   :-2.000   Min.   :-2.00   Min.   :-2.00  
##  1st Qu.: 2.000   1st Qu.:-2.000   1st Qu.:-2.00   1st Qu.:10.00  
##  Median : 5.000   Median :-2.000   Median :-2.00   Median :10.00  
##  Mean   : 3.676   Mean   :-1.511   Mean   :-1.27   Mean   :10.51  
##  3rd Qu.: 5.000   3rd Qu.:-2.000   3rd Qu.:-2.00   3rd Qu.:20.00  
##  Max.   : 8.000   Max.   : 1.000   Max.   : 3.00   Max.   :40.00  
##                                                                   
##     TYPEHUQ4       BEDROOMS         NCOMBATH        NHAFBATH     
##  Min.   :-2.0   Min.   :-2.000   Min.   :0.000   Min.   :0.0000  
##  1st Qu.:-2.0   1st Qu.: 2.000   1st Qu.:1.000   1st Qu.:0.0000  
##  Median :-2.0   Median : 3.000   Median :2.000   Median :0.0000  
##  Mean   :-1.9   Mean   : 2.773   Mean   :1.672   Mean   :0.3078  
##  3rd Qu.:-2.0   3rd Qu.: 3.000   3rd Qu.:2.000   3rd Qu.:1.0000  
##  Max.   : 1.0   Max.   :13.000   Max.   :8.000   Max.   :9.0000  
##                                                                  
##     OTHROOMS         TOTROOMS          CELLAR             CRAWL        
##  Min.   : 1.000   Min.   : 1.000   Min.   :-2.00000   Min.   :-2.0000  
##  1st Qu.: 2.000   1st Qu.: 5.000   1st Qu.: 0.00000   1st Qu.: 0.0000  
##  Median : 3.000   Median : 6.000   Median : 0.00000   Median : 0.0000  
##  Mean   : 3.187   Mean   : 5.995   Mean   :-0.08168   Mean   :-0.1886  
##  3rd Qu.: 4.000   3rd Qu.: 7.000   3rd Qu.: 1.00000   3rd Qu.: 0.0000  
##  Max.   :17.000   Max.   :23.000   Max.   : 1.00000   Max.   : 1.0000  
##                                                                        
##     CONCRETE           BASEFIN         FINBASERMS       BASEHEAT     
##  Min.   :-2.00000   Min.   :-2.000   Min.   :-2.00   Min.   :-2.000  
##  1st Qu.: 0.00000   1st Qu.:-2.000   1st Qu.:-2.00   1st Qu.:-2.000  
##  Median : 0.00000   Median :-2.000   Median :-2.00   Median :-2.000  
##  Mean   :-0.02822   Mean   :-1.184   Mean   :-1.33   Mean   :-1.171  
##  3rd Qu.: 1.00000   3rd Qu.: 0.000   3rd Qu.:-2.00   3rd Qu.: 0.000  
##  Max.   : 1.00000   Max.   : 1.000   Max.   : 5.00   Max.   : 1.000  
##                                                                      
##     BASEHT2          PCTBSTHT         BASECOOL         BASECL2      
##  Min.   :-2.000   Min.   :-2.000   Min.   :-2.000   Min.   :-2.000  
##  1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.000  
##  Median :-2.000   Median :-2.000   Median :-2.000   Median :-2.000  
##  Mean   :-1.419   Mean   :-1.741   Mean   :-1.255   Mean   :-1.699  
##  3rd Qu.:-2.000   3rd Qu.:-2.000   3rd Qu.: 0.000   3rd Qu.:-2.000  
##  Max.   : 2.000   Max.   : 5.000   Max.   : 1.000   Max.   : 2.000  
##                                                                     
##     PCTBSTCL         BASEUSE           ATTIC            ATTICFIN     
##  Min.   :-2.000   Min.   :-2.000   Min.   :-2.0000   Min.   :-2.000  
##  1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.: 0.0000   1st Qu.:-2.000  
##  Median :-2.000   Median :-2.000   Median : 0.0000   Median :-2.000  
##  Mean   :-1.882   Mean   :-1.024   Mean   :-0.1554   Mean   :-1.473  
##  3rd Qu.:-2.000   3rd Qu.: 1.000   3rd Qu.: 1.0000   3rd Qu.: 0.000  
##  Max.   : 5.000   Max.   : 2.000   Max.   : 1.0000   Max.   : 1.000  
##                                                                      
##    FINATTRMS         ATTCHEAT         ATTCHT2          PCTATTHT     
##  Min.   :-2.000   Min.   :-2.000   Min.   :-2.000   Min.   :-2.000  
##  1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.000  
##  Median :-2.000   Median :-2.000   Median :-2.000   Median :-2.000  
##  Mean   :-1.929   Mean   :-1.486   Mean   :-1.969   Mean   :-1.988  
##  3rd Qu.:-2.000   3rd Qu.: 0.000   3rd Qu.:-2.000   3rd Qu.:-2.000  
##  Max.   : 4.000   Max.   : 1.000   Max.   : 2.000   Max.   : 4.000  
##                                                                     
##     ATTCCOOL         ATTCCL2          PCTATTCL        ATTICUSE     
##  Min.   :-2.000   Min.   :-2.000   Min.   :-2.00   Min.   :-2.000  
##  1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.00   1st Qu.:-2.000  
##  Median :-2.000   Median :-2.000   Median :-2.00   Median :-2.000  
##  Mean   :-1.488   Mean   :-1.976   Mean   :-1.99   Mean   :-1.243  
##  3rd Qu.: 0.000   3rd Qu.:-2.000   3rd Qu.:-2.00   3rd Qu.: 1.000  
##  Max.   : 1.000   Max.   : 2.000   Max.   : 5.00   Max.   : 2.000  
##                                                                    
##     PRKGPLC1         SIZEOFGARAGE        GARGLOC           GARGHEAT     
##  Min.   :-2.00000   Min.   :-2.0000   Min.   :-2.0000   Min.   :-2.000  
##  1st Qu.: 0.00000   1st Qu.:-2.0000   1st Qu.:-2.0000   1st Qu.:-2.000  
##  Median : 0.00000   Median :-2.0000   Median :-2.0000   Median :-2.000  
##  Mean   :-0.06306   Mean   :-0.4104   Mean   :-0.3878   Mean   :-1.161  
##  3rd Qu.: 1.00000   3rd Qu.: 2.0000   3rd Qu.: 2.0000   3rd Qu.: 0.000  
##  Max.   : 1.00000   Max.   : 3.0000   Max.   : 3.0000   Max.   : 1.000  
##                                                                         
##     GARGCOOL         PRKGPLC2       SIZEOFDETACH        OUTLET       
##  Min.   :-2.000   Min.   :-2.000   Min.   :-2.000   Min.   :-9.0000  
##  1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.: 0.0000  
##  Median :-2.000   Median :-2.000   Median :-2.000   Median : 0.0000  
##  Mean   :-1.172   Mean   :-1.117   Mean   :-1.282   Mean   : 0.2273  
##  3rd Qu.: 0.000   3rd Qu.: 0.000   3rd Qu.:-2.000   3rd Qu.: 1.0000  
##  Max.   : 1.000   Max.   : 1.000   Max.   : 4.000   Max.   : 1.0000  
##                                                                      
##    ZKOWNRENT           ZCONDCOOP          ZYEARMADE      ZYEARMADERANGE   
##  Min.   :0.0000000   Min.   :0.000000   Min.   :0.0000   Min.   :0.00000  
##  1st Qu.:0.0000000   1st Qu.:0.000000   1st Qu.:0.0000   1st Qu.:0.00000  
##  Median :0.0000000   Median :0.000000   Median :0.0000   Median :0.00000  
##  Mean   :0.0007448   Mean   :0.001159   Mean   :0.1491   Mean   :0.02532  
##  3rd Qu.:0.0000000   3rd Qu.:0.000000   3rd Qu.:0.0000   3rd Qu.:0.00000  
##  Max.   :1.0000000   Max.   :1.000000   Max.   :1.0000   Max.   :1.00000  
##                                                                           
##  ZOCCUPYYRANGE        ZCONVERSION         ZORIG1FAM       
##  Min.   :0.0000000   Min.   :0.000000   Min.   :0.000000  
##  1st Qu.:0.0000000   1st Qu.:0.000000   1st Qu.:0.000000  
##  Median :0.0000000   Median :0.000000   Median :0.000000  
##  Mean   :0.0002483   Mean   :0.005545   Mean   :0.002483  
##  3rd Qu.:0.0000000   3rd Qu.:0.000000   3rd Qu.:0.000000  
##  Max.   :1.0000000   Max.   :1.000000   Max.   :1.000000  
##                                                           
##    ZLOOKLIKE           ZNUMFLRS            ZNUMAPTS       
##  Min.   :0.000000   Min.   :0.0000000   Min.   :0.000000  
##  1st Qu.:0.000000   1st Qu.:0.0000000   1st Qu.:0.000000  
##  Median :0.000000   Median :0.0000000   Median :0.000000  
##  Mean   :0.002152   Mean   :0.0005793   Mean   :0.006124  
##  3rd Qu.:0.000000   3rd Qu.:0.0000000   3rd Qu.:0.000000  
##  Max.   :1.000000   Max.   :1.0000000   Max.   :1.000000  
##                                                           
##    ZWALLTYPE          ZROOFTYPE          ZSTUDIO    ZNAPTFLRS
##  Min.   :0.000000   Min.   :0.00000   Min.   :0   Min.   :0  
##  1st Qu.:0.000000   1st Qu.:0.00000   1st Qu.:0   1st Qu.:0  
##  Median :0.000000   Median :0.00000   Median :0   Median :0  
##  Mean   :0.002648   Mean   :0.02648   Mean   :0   Mean   :0  
##  3rd Qu.:0.000000   3rd Qu.:0.00000   3rd Qu.:0   3rd Qu.:0  
##  Max.   :1.000000   Max.   :1.00000   Max.   :0   Max.   :0  
##                                                              
##     ZSTORIES          ZTYPEHUQ4         ZBEDROOMS        
##  Min.   :0.00e+00   Min.   :0.00000   Min.   :0.0000000  
##  1st Qu.:0.00e+00   1st Qu.:0.00000   1st Qu.:0.0000000  
##  Median :0.00e+00   Median :0.00000   Median :0.0000000  
##  Mean   :8.28e-05   Mean   :0.00331   Mean   :0.0002483  
##  3rd Qu.:0.00e+00   3rd Qu.:0.00000   3rd Qu.:0.0000000  
##  Max.   :1.00e+00   Max.   :1.00000   Max.   :1.0000000  
##                                                          
##    ZNCOMBATH          ZNHAFBATH           ZOTHROOMS        
##  Min.   :0.000000   Min.   :0.0000000   Min.   :0.0000000  
##  1st Qu.:0.000000   1st Qu.:0.0000000   1st Qu.:0.0000000  
##  Median :0.000000   Median :0.0000000   Median :0.0000000  
##  Mean   :0.000331   Mean   :0.0002483   Mean   :0.0009104  
##  3rd Qu.:0.000000   3rd Qu.:0.0000000   3rd Qu.:0.0000000  
##  Max.   :1.000000   Max.   :1.0000000   Max.   :1.0000000  
##                                                            
##     ZCELLAR              ZCRAWL         ZCONCRETE         ZBASEFIN       
##  Min.   :0.0000000   Min.   :0.0000   Min.   :0.0000   Min.   :0.000000  
##  1st Qu.:0.0000000   1st Qu.:0.0000   1st Qu.:0.0000   1st Qu.:0.000000  
##  Median :0.0000000   Median :0.0000   Median :0.0000   Median :0.000000  
##  Mean   :0.0008276   Mean   :0.0048   Mean   :0.0144   Mean   :0.001324  
##  3rd Qu.:0.0000000   3rd Qu.:0.0000   3rd Qu.:0.0000   3rd Qu.:0.000000  
##  Max.   :1.0000000   Max.   :1.0000   Max.   :1.0000   Max.   :1.000000  
##                                                                          
##   ZFINBASERMS         ZBASEHEAT           ZBASEHT2        
##  Min.   :0.000000   Min.   :0.000000   Min.   :0.0000000  
##  1st Qu.:0.000000   1st Qu.:0.000000   1st Qu.:0.0000000  
##  Median :0.000000   Median :0.000000   Median :0.0000000  
##  Mean   :0.001241   Mean   :0.001159   Mean   :0.0005793  
##  3rd Qu.:0.000000   3rd Qu.:0.000000   3rd Qu.:0.0000000  
##  Max.   :1.000000   Max.   :1.000000   Max.   :1.0000000  
##                                                           
##    ZPCTBSTHT           ZBASECOOL           ZBASECL2        
##  Min.   :0.0000000   Min.   :0.000000   Min.   :0.0000000  
##  1st Qu.:0.0000000   1st Qu.:0.000000   1st Qu.:0.0000000  
##  Median :0.0000000   Median :0.000000   Median :0.0000000  
##  Mean   :0.0002483   Mean   :0.001821   Mean   :0.0004138  
##  3rd Qu.:0.0000000   3rd Qu.:0.000000   3rd Qu.:0.0000000  
##  Max.   :1.0000000   Max.   :1.000000   Max.   :1.0000000  
##                                                            
##    ZPCTBSTCL            ZBASEUSE             ZATTIC       
##  Min.   :0.0000000   Min.   :0.0000000   Min.   :0.00000  
##  1st Qu.:0.0000000   1st Qu.:0.0000000   1st Qu.:0.00000  
##  Median :0.0000000   Median :0.0000000   Median :0.00000  
##  Mean   :0.0001655   Mean   :0.0004138   Mean   :0.00389  
##  3rd Qu.:0.0000000   3rd Qu.:0.0000000   3rd Qu.:0.00000  
##  Max.   :1.0000000   Max.   :1.0000000   Max.   :1.00000  
##                                                           
##    ZATTICFIN          ZFINATTRMS          ZATTCHEAT       
##  Min.   :0.000000   Min.   :0.0000000   Min.   :0.000000  
##  1st Qu.:0.000000   1st Qu.:0.0000000   1st Qu.:0.000000  
##  Median :0.000000   Median :0.0000000   Median :0.000000  
##  Mean   :0.003145   Mean   :0.0009104   Mean   :0.001407  
##  3rd Qu.:0.000000   3rd Qu.:0.0000000   3rd Qu.:0.000000  
##  Max.   :1.000000   Max.   :1.0000000   Max.   :1.000000  
##                                                           
##     ZATTCHT2           ZPCTATTHT          ZATTCCOOL          ZPCTATTCL
##  Min.   :0.0000000   Min.   :0.00e+00   Min.   :0.000000   Min.   :0  
##  1st Qu.:0.0000000   1st Qu.:0.00e+00   1st Qu.:0.000000   1st Qu.:0  
##  Median :0.0000000   Median :0.00e+00   Median :0.000000   Median :0  
##  Mean   :0.0001655   Mean   :8.28e-05   Mean   :0.001407   Mean   :0  
##  3rd Qu.:0.0000000   3rd Qu.:0.00e+00   3rd Qu.:0.000000   3rd Qu.:0  
##  Max.   :1.0000000   Max.   :1.00e+00   Max.   :1.000000   Max.   :0  
##                                                                       
##     ZATTCCL2           ZATTICUSE           ZPRKGPLC1       
##  Min.   :0.0000000   Min.   :0.0000000   Min.   :0.000000  
##  1st Qu.:0.0000000   1st Qu.:0.0000000   1st Qu.:0.000000  
##  Median :0.0000000   Median :0.0000000   Median :0.000000  
##  Mean   :0.0001655   Mean   :0.0002483   Mean   :0.001159  
##  3rd Qu.:0.0000000   3rd Qu.:0.0000000   3rd Qu.:0.000000  
##  Max.   :1.0000000   Max.   :1.0000000   Max.   :1.000000  
##                                                            
##  ZSIZEOFGARAGE          ZGARGLOC           ZGARGHEAT        
##  Min.   :0.0000000   Min.   :0.0000000   Min.   :0.0000000  
##  1st Qu.:0.0000000   1st Qu.:0.0000000   1st Qu.:0.0000000  
##  Median :0.0000000   Median :0.0000000   Median :0.0000000  
##  Mean   :0.0007448   Mean   :0.0007448   Mean   :0.0009931  
##  3rd Qu.:0.0000000   3rd Qu.:0.0000000   3rd Qu.:0.0000000  
##  Max.   :1.0000000   Max.   :1.0000000   Max.   :1.0000000  
##                                                             
##    ZGARGCOOL           ZPRKGPLC2         ZSIZEOFDETACH      
##  Min.   :0.0000000   Min.   :0.0000000   Min.   :0.0000000  
##  1st Qu.:0.0000000   1st Qu.:0.0000000   1st Qu.:0.0000000  
##  Median :0.0000000   Median :0.0000000   Median :0.0000000  
##  Mean   :0.0009104   Mean   :0.0009104   Mean   :0.0002483  
##  3rd Qu.:0.0000000   3rd Qu.:0.0000000   3rd Qu.:0.0000000  
##  Max.   :1.0000000   Max.   :1.0000000   Max.   :1.0000000  
##                                                             
##      STOVEN         STOVENFUEL         STOVE          STOVEFUEL     
##  Min.   :0.0000   Min.   :-2.000   Min.   :0.0000   Min.   :-2.000  
##  1st Qu.:1.0000   1st Qu.: 1.000   1st Qu.:0.0000   1st Qu.:-2.000  
##  Median :1.0000   Median : 5.000   Median :0.0000   Median :-2.000  
##  Mean   :0.9112   Mean   : 2.953   Mean   :0.1233   Mean   :-1.352  
##  3rd Qu.:1.0000   3rd Qu.: 5.000   3rd Qu.:0.0000   3rd Qu.:-2.000  
##  Max.   :3.0000   Max.   :21.000   Max.   :2.0000   Max.   : 5.000  
##                                                                     
##       OVEN           OVENFUEL         OVENUSE         OVENCLN       
##  Min.   :0.0000   Min.   :-2.000   Min.   :-2.00   Min.   :-2.0000  
##  1st Qu.:0.0000   1st Qu.:-2.000   1st Qu.: 3.00   1st Qu.: 0.0000  
##  Median :0.0000   Median :-2.000   Median : 4.00   Median : 1.0000  
##  Mean   :0.1567   Mean   :-1.214   Mean   : 3.75   Mean   : 0.6128  
##  3rd Qu.:0.0000   3rd Qu.:-2.000   3rd Qu.: 5.00   3rd Qu.: 1.0000  
##  Max.   :3.0000   Max.   : 5.000   Max.   : 6.00   Max.   : 1.0000  
##                                                                     
##     TYPECLN            MICRO           AMTMICRO         DEFROST       
##  Min.   :-2.0000   Min.   :0.0000   Min.   :-2.000   Min.   :-2.0000  
##  1st Qu.:-2.0000   1st Qu.:1.0000   1st Qu.: 1.000   1st Qu.: 0.0000  
##  Median : 2.0000   Median :1.0000   Median : 2.000   Median : 0.0000  
##  Mean   : 0.4501   Mean   :0.9614   Mean   : 2.189   Mean   : 0.3449  
##  3rd Qu.: 2.0000   3rd Qu.:1.0000   3rd Qu.: 3.000   3rd Qu.: 1.0000  
##  Max.   : 2.0000   Max.   :1.0000   Max.   : 4.000   Max.   : 1.0000  
##                                                                       
##     OUTGRILL       OUTGRILLFUEL     TOPGRILL          STGRILA      
##  Min.   :0.0000   Min.   :-2.0   Min.   :0.00000   Min.   :-2.000  
##  1st Qu.:0.0000   1st Qu.:-2.0   1st Qu.:0.00000   1st Qu.:-2.000  
##  Median :1.0000   Median : 2.0   Median :0.00000   Median :-2.000  
##  Mean   :0.6106   Mean   : 4.1   Mean   :0.01357   Mean   :-1.917  
##  3rd Qu.:1.0000   3rd Qu.: 2.0   3rd Qu.:0.00000   3rd Qu.:-2.000  
##  Max.   :1.0000   Max.   :21.0   Max.   :1.00000   Max.   :21.000  
##                                                                    
##     TOASTER          NUMMEAL        FUELFOOD          COFFEE      
##  Min.   :0.0000   Min.   :0.00   Min.   :-2.000   Min.   :0.0000  
##  1st Qu.:0.0000   1st Qu.:2.00   1st Qu.: 1.000   1st Qu.:0.0000  
##  Median :0.0000   Median :3.00   Median : 5.000   Median :1.0000  
##  Mean   :0.3699   Mean   :2.98   Mean   : 3.456   Mean   :0.6348  
##  3rd Qu.:1.0000   3rd Qu.:4.00   3rd Qu.: 5.000   3rd Qu.:1.0000  
##  Max.   :1.0000   Max.   :6.00   Max.   :21.000   Max.   :1.0000  
##                                                                   
##     NUMFRIG         TYPERFR1        SIZRFRI1         REFRIGT1     
##  Min.   :0.000   Min.   :-2.00   Min.   :-2.000   Min.   :-2.000  
##  1st Qu.:1.000   1st Qu.:21.00   1st Qu.: 3.000   1st Qu.: 2.000  
##  Median :1.000   Median :22.00   Median : 4.000   Median : 2.000  
##  Mean   :1.265   Mean   :19.82   Mean   : 3.531   Mean   : 1.925  
##  3rd Qu.:1.000   3rd Qu.:22.00   3rd Qu.: 4.000   3rd Qu.: 2.000  
##  Max.   :7.000   Max.   :23.00   Max.   : 5.000   Max.   : 3.000  
##                                                                   
##       ICE             AGERFRI1         ESFRIG           REPLCFRI    
##  Min.   :-2.0000   Min.   :-2.00   Min.   :-9.0000   Min.   :-9.00  
##  1st Qu.: 0.0000   1st Qu.: 2.00   1st Qu.:-2.0000   1st Qu.:-2.00  
##  Median : 0.0000   Median : 3.00   Median : 0.0000   Median :-2.00  
##  Mean   : 0.3421   Mean   :11.76   Mean   :-0.9294   Mean   :-1.19  
##  3rd Qu.: 1.0000   3rd Qu.: 5.00   3rd Qu.: 1.0000   3rd Qu.: 1.00  
##  Max.   : 1.0000   Max.   :42.00   Max.   : 1.0000   Max.   : 1.00  
##                                                                     
##     HELPFRI          HELPFRIY         TYPERFR2         SIZRFRI2      
##  Min.   :-9.000   Min.   :-9.000   Min.   :-2.000   Min.   :-2.0000  
##  1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.0000  
##  Median :-2.000   Median :-2.000   Median :-2.000   Median :-2.0000  
##  Mean   :-1.474   Mean   :-1.879   Mean   : 2.178   Mean   :-0.8464  
##  3rd Qu.: 0.000   3rd Qu.:-2.000   3rd Qu.:-2.000   3rd Qu.:-2.0000  
##  Max.   : 5.000   Max.   : 6.000   Max.   :23.000   Max.   : 5.0000  
##                                                                      
##     REFRIGT2         MONRFRI2         AGERFRI2        ESFRIG2      
##  Min.   :-2.000   Min.   :-2.000   Min.   :-2.00   Min.   :-9.000  
##  1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.00   1st Qu.:-2.000  
##  Median :-2.000   Median :-2.000   Median :-2.00   Median :-2.000  
##  Mean   :-1.097   Mean   : 1.109   Mean   : 2.39   Mean   :-1.831  
##  3rd Qu.:-2.000   3rd Qu.:-2.000   3rd Qu.:-2.00   3rd Qu.:-2.000  
##  Max.   : 3.000   Max.   :12.000   Max.   :42.00   Max.   : 1.000  
##                                                                    
##     TYPERFR3         SIZRFRI3         REFRIGT3         MONRFRI3     
##  Min.   :-2.000   Min.   :-2.000   Min.   :-2.000   Min.   :-2.000  
##  1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.000  
##  Median :-2.000   Median :-2.000   Median :-2.000   Median :-2.000  
##  Mean   :-1.755   Mean   :-1.911   Mean   :-1.918   Mean   :-1.718  
##  3rd Qu.:-2.000   3rd Qu.:-2.000   3rd Qu.:-2.000   3rd Qu.:-2.000  
##  Max.   :23.000   Max.   : 5.000   Max.   : 3.000   Max.   :12.000  
##                                                                     
##     AGERFRI3         ESFRIG3          SEPFREEZ         NUMFREEZ     
##  Min.   :-2.000   Min.   :-9.000   Min.   :0.0000   Min.   :-2.000  
##  1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:0.0000   1st Qu.:-2.000  
##  Median :-2.000   Median :-2.000   Median :0.0000   Median :-2.000  
##  Mean   :-1.653   Mean   :-1.979   Mean   :0.2969   Mean   :-1.084  
##  3rd Qu.:-2.000   3rd Qu.:-2.000   3rd Qu.:1.0000   3rd Qu.: 1.000  
##  Max.   :42.000   Max.   : 1.000   Max.   :1.0000   Max.   : 3.000  
##                                                                     
##     UPRTFRZR         SIZFREEZ          FREEZER           AGEFRZR      
##  Min.   :-2.000   Min.   :-2.0000   Min.   :-2.0000   Min.   :-2.000  
##  1st Qu.:-2.000   1st Qu.:-2.0000   1st Qu.:-2.0000   1st Qu.:-2.000  
##  Median :-2.000   Median :-2.0000   Median :-2.0000   Median :-2.000  
##  Mean   :-0.956   Mean   :-0.8145   Mean   :-0.9796   Mean   : 3.032  
##  3rd Qu.: 1.000   3rd Qu.: 1.0000   3rd Qu.: 1.0000   3rd Qu.: 2.000  
##  Max.   : 2.000   Max.   : 4.0000   Max.   : 2.0000   Max.   :42.000  
##                                                                       
##     REPLCFRZ         HELPFRZ          HELPFRZY        UPRTFRZR2     
##  Min.   :-9.000   Min.   :-9.000   Min.   :-9.000   Min.   :-2.000  
##  1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.000  
##  Median :-2.000   Median :-2.000   Median :-2.000   Median :-2.000  
##  Mean   :-1.811   Mean   :-1.884   Mean   :-1.989   Mean   :-1.917  
##  3rd Qu.:-2.000   3rd Qu.:-2.000   3rd Qu.:-2.000   3rd Qu.:-2.000  
##  Max.   : 1.000   Max.   : 3.000   Max.   : 5.000   Max.   : 2.000  
##                                                                     
##    SIZFREEZ2        FREEZER2         AGEFRZR2         DISHWASH     
##  Min.   :-2.00   Min.   :-2.000   Min.   :-2.000   Min.   :0.0000  
##  1st Qu.:-2.00   1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:0.0000  
##  Median :-2.00   Median :-2.000   Median :-2.000   Median :1.0000  
##  Mean   :-1.91   Mean   :-1.925   Mean   :-1.645   Mean   :0.6109  
##  3rd Qu.:-2.00   3rd Qu.:-2.000   3rd Qu.:-2.000   3rd Qu.:1.0000  
##  Max.   : 4.00   Max.   : 2.000   Max.   :42.000   Max.   :1.0000  
##                                                                    
##     DWASHUSE          AGEDW           ESDISHW          REPLCDW     
##  Min.   :-2.000   Min.   :-2.000   Min.   :-9.000   Min.   :-9.00  
##  1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.00  
##  Median :12.000   Median : 2.000   Median :-2.000   Median :-2.00  
##  Mean   : 9.493   Mean   : 6.018   Mean   :-1.339   Mean   :-1.47  
##  3rd Qu.:13.000   3rd Qu.: 3.000   3rd Qu.: 1.000   3rd Qu.:-2.00  
##  Max.   :30.000   Max.   :42.000   Max.   : 1.000   Max.   : 1.00  
##                                                                    
##      HELPDW          HELPDWY          ZSTOVEN          ZSTOVENFUEL       
##  Min.   :-9.000   Min.   :-9.000   Min.   :0.00e+00   Min.   :0.0000000  
##  1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:0.00e+00   1st Qu.:0.0000000  
##  Median :-2.000   Median :-2.000   Median :0.00e+00   Median :0.0000000  
##  Mean   :-1.679   Mean   :-1.928   Mean   :8.28e-05   Mean   :0.0006621  
##  3rd Qu.:-2.000   3rd Qu.:-2.000   3rd Qu.:0.00e+00   3rd Qu.:0.0000000  
##  Max.   : 4.000   Max.   : 6.000   Max.   :1.00e+00   Max.   :1.0000000  
##                                                                          
##      ZSTOVE    ZSTOVEFUEL           ZOVEN     ZOVENFUEL        
##  Min.   :0   Min.   :0.00e+00   Min.   :0   Min.   :0.0000000  
##  1st Qu.:0   1st Qu.:0.00e+00   1st Qu.:0   1st Qu.:0.0000000  
##  Median :0   Median :0.00e+00   Median :0   Median :0.0000000  
##  Mean   :0   Mean   :8.28e-05   Mean   :0   Mean   :0.0002483  
##  3rd Qu.:0   3rd Qu.:0.00e+00   3rd Qu.:0   3rd Qu.:0.0000000  
##  Max.   :0   Max.   :1.00e+00   Max.   :0   Max.   :1.0000000  
##                                                                
##     ZOVENUSE            ZOVENCLN          ZTYPECLN      
##  Min.   :0.0000000   Min.   :0.00000   Min.   :0.00000  
##  1st Qu.:0.0000000   1st Qu.:0.00000   1st Qu.:0.00000  
##  Median :0.0000000   Median :0.00000   Median :0.00000  
##  Mean   :0.0006621   Mean   :0.01498   Mean   :0.02268  
##  3rd Qu.:0.0000000   3rd Qu.:0.00000   3rd Qu.:0.00000  
##  Max.   :1.0000000   Max.   :1.00000   Max.   :1.00000  
##                                                         
##      ZMICRO           ZAMTMICRO            ZDEFROST           ZOUTGRILL
##  Min.   :0.00e+00   Min.   :0.0000000   Min.   :0.0000000   Min.   :0  
##  1st Qu.:0.00e+00   1st Qu.:0.0000000   1st Qu.:0.0000000   1st Qu.:0  
##  Median :0.00e+00   Median :0.0000000   Median :0.0000000   Median :0  
##  Mean   :8.28e-05   Mean   :0.0002483   Mean   :0.0005793   Mean   :0  
##  3rd Qu.:0.00e+00   3rd Qu.:0.0000000   3rd Qu.:0.0000000   3rd Qu.:0  
##  Max.   :1.00e+00   Max.   :1.0000000   Max.   :1.0000000   Max.   :0  
##                                                                        
##  ZOUTGRILLFUEL        ZTOPGRILL           ZSTGRILA    ZTOASTER        
##  Min.   :0.000000   Min.   :0.00e+00   Min.   :0   Min.   :0.0000000  
##  1st Qu.:0.000000   1st Qu.:0.00e+00   1st Qu.:0   1st Qu.:0.0000000  
##  Median :0.000000   Median :0.00e+00   Median :0   Median :0.0000000  
##  Mean   :0.000331   Mean   :8.28e-05   Mean   :0   Mean   :0.0002483  
##  3rd Qu.:0.000000   3rd Qu.:0.00e+00   3rd Qu.:0   3rd Qu.:0.0000000  
##  Max.   :1.000000   Max.   :1.00e+00   Max.   :0   Max.   :1.0000000  
##                                                                       
##     ZNUMMEAL          ZFUELFOOD           ZCOFFEE     ZNUMFRIG       
##  Min.   :0.00e+00   Min.   :0.000000   Min.   :0   Min.   :0.00e+00  
##  1st Qu.:0.00e+00   1st Qu.:0.000000   1st Qu.:0   1st Qu.:0.00e+00  
##  Median :0.00e+00   Median :0.000000   Median :0   Median :0.00e+00  
##  Mean   :8.28e-05   Mean   :0.001241   Mean   :0   Mean   :8.28e-05  
##  3rd Qu.:0.00e+00   3rd Qu.:0.000000   3rd Qu.:0   3rd Qu.:0.00e+00  
##  Max.   :1.00e+00   Max.   :1.000000   Max.   :0   Max.   :1.00e+00  
##                                                                      
##    ZTYPERFR1          ZSIZRFRI1          ZREFRIGT1       
##  Min.   :0.00e+00   Min.   :0.000000   Min.   :0.000000  
##  1st Qu.:0.00e+00   1st Qu.:0.000000   1st Qu.:0.000000  
##  Median :0.00e+00   Median :0.000000   Median :0.000000  
##  Mean   :8.28e-05   Mean   :0.003062   Mean   :0.007862  
##  3rd Qu.:0.00e+00   3rd Qu.:0.000000   3rd Qu.:0.000000  
##  Max.   :1.00e+00   Max.   :1.000000   Max.   :1.000000  
##                                                          
##       ZICE             ZAGERFRI1         ZTYPERFR2       
##  Min.   :0.0000000   Min.   :0.00000   Min.   :0.000000  
##  1st Qu.:0.0000000   1st Qu.:0.00000   1st Qu.:0.000000  
##  Median :0.0000000   Median :0.00000   Median :0.000000  
##  Mean   :0.0001655   Mean   :0.02797   Mean   :0.000331  
##  3rd Qu.:0.0000000   3rd Qu.:0.00000   3rd Qu.:0.000000  
##  Max.   :1.0000000   Max.   :1.00000   Max.   :1.000000  
##                                                          
##    ZSIZRFRI2           ZREFRIGT2          ZMONRFRI2       
##  Min.   :0.0000000   Min.   :0.000000   Min.   :0.000000  
##  1st Qu.:0.0000000   1st Qu.:0.000000   1st Qu.:0.000000  
##  Median :0.0000000   Median :0.000000   Median :0.000000  
##  Mean   :0.0009104   Mean   :0.002731   Mean   :0.000331  
##  3rd Qu.:0.0000000   3rd Qu.:0.000000   3rd Qu.:0.000000  
##  Max.   :1.0000000   Max.   :1.000000   Max.   :1.000000  
##                                                           
##    ZAGERFRI2          ZTYPERFR3          ZSIZRFRI3   ZREFRIGT3        
##  Min.   :0.000000   Min.   :0.00e+00   Min.   :0   Min.   :0.0000000  
##  1st Qu.:0.000000   1st Qu.:0.00e+00   1st Qu.:0   1st Qu.:0.0000000  
##  Median :0.000000   Median :0.00e+00   Median :0   Median :0.0000000  
##  Mean   :0.004883   Mean   :8.28e-05   Mean   :0   Mean   :0.0004138  
##  3rd Qu.:0.000000   3rd Qu.:0.00e+00   3rd Qu.:0   3rd Qu.:0.0000000  
##  Max.   :1.000000   Max.   :1.00e+00   Max.   :0   Max.   :1.0000000  
##                                                                       
##    ZMONRFRI3           ZAGERFRI3           ZSEPFREEZ   ZNUMFREEZ
##  Min.   :0.0000000   Min.   :0.0000000   Min.   :0   Min.   :0  
##  1st Qu.:0.0000000   1st Qu.:0.0000000   1st Qu.:0   1st Qu.:0  
##  Median :0.0000000   Median :0.0000000   Median :0   Median :0  
##  Mean   :0.0001655   Mean   :0.0004966   Mean   :0   Mean   :0  
##  3rd Qu.:0.0000000   3rd Qu.:0.0000000   3rd Qu.:0   3rd Qu.:0  
##  Max.   :1.0000000   Max.   :1.0000000   Max.   :0   Max.   :0  
##                                                                 
##    ZUPRTFRZR           ZSIZFREEZ            ZFREEZER       
##  Min.   :0.0000000   Min.   :0.0000000   Min.   :0.000000  
##  1st Qu.:0.0000000   1st Qu.:0.0000000   1st Qu.:0.000000  
##  Median :0.0000000   Median :0.0000000   Median :0.000000  
##  Mean   :0.0001655   Mean   :0.0007448   Mean   :0.002234  
##  3rd Qu.:0.0000000   3rd Qu.:0.0000000   3rd Qu.:0.000000  
##  Max.   :1.0000000   Max.   :1.0000000   Max.   :1.000000  
##                                                            
##     ZAGEFRZR          ZUPRTFRZR2   ZSIZFREEZ2   ZFREEZER2       
##  Min.   :0.000000   Min.   :0    Min.   :0    Min.   :0.00e+00  
##  1st Qu.:0.000000   1st Qu.:0    1st Qu.:0    1st Qu.:0.00e+00  
##  Median :0.000000   Median :0    Median :0    Median :0.00e+00  
##  Mean   :0.005379   Mean   :0    Mean   :0    Mean   :8.28e-05  
##  3rd Qu.:0.000000   3rd Qu.:0    3rd Qu.:0    3rd Qu.:0.00e+00  
##  Max.   :1.000000   Max.   :0    Max.   :0    Max.   :1.00e+00  
##                                                                 
##    ZAGEFRZR2   ZDISHWASH   ZDWASHUSE     ZAGEDW           CWASHER      
##  Min.   :0   Min.   :0   Min.   :0   Min.   :0.00000   Min.   :0.0000  
##  1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0.00000   1st Qu.:1.0000  
##  Median :0   Median :0   Median :0   Median :0.00000   Median :1.0000  
##  Mean   :0   Mean   :0   Mean   :0   Mean   :0.01539   Mean   :0.8303  
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0.00000   3rd Qu.:1.0000  
##  Max.   :0   Max.   :0   Max.   :0   Max.   :1.00000   Max.   :1.0000  
##                                                                        
##     TOPFRONT          WASHLOAD         WASHTEMP         RNSETEMP     
##  Min.   :-2.0000   Min.   :-2.000   Min.   :-2.000   Min.   :-2.000  
##  1st Qu.: 1.0000   1st Qu.: 2.000   1st Qu.: 2.000   1st Qu.: 2.000  
##  Median : 1.0000   Median : 2.000   Median : 2.000   Median : 3.000  
##  Mean   : 0.6517   Mean   : 1.774   Mean   : 1.651   Mean   : 1.977  
##  3rd Qu.: 1.0000   3rd Qu.: 3.000   3rd Qu.: 3.000   3rd Qu.: 3.000  
##  Max.   : 2.0000   Max.   : 5.000   Max.   : 3.000   Max.   : 3.000  
##                                                                      
##     AGECWASH         ESCWASH           REPLCCW           HELPCW      
##  Min.   :-2.000   Min.   :-9.0000   Min.   :-9.000   Min.   :-9.000  
##  1st Qu.: 1.000   1st Qu.:-2.0000   1st Qu.:-2.000   1st Qu.:-2.000  
##  Median : 3.000   Median : 0.0000   Median :-2.000   Median :-2.000  
##  Mean   : 8.979   Mean   :-0.9281   Mean   :-1.181   Mean   :-1.449  
##  3rd Qu.: 3.000   3rd Qu.: 1.0000   3rd Qu.: 1.000   3rd Qu.: 0.000  
##  Max.   :42.000   Max.   : 1.0000   Max.   : 1.000   Max.   : 4.000  
##                                                                      
##     HELPCWY           DRYER           DRYRFUEL         DRYRUSE      
##  Min.   :-9.000   Min.   :0.0000   Min.   :-2.000   Min.   :-2.000  
##  1st Qu.:-2.000   1st Qu.:1.0000   1st Qu.: 1.000   1st Qu.: 1.000  
##  Median :-2.000   Median :1.0000   Median : 5.000   Median : 1.000  
##  Mean   :-1.866   Mean   :0.8048   Mean   : 2.981   Mean   : 0.576  
##  3rd Qu.:-2.000   3rd Qu.:1.0000   3rd Qu.: 5.000   3rd Qu.: 1.000  
##  Max.   : 6.000   Max.   :1.0000   Max.   : 5.000   Max.   : 3.000  
##                                                                     
##    AGECDRYER        TVCOLOR          TVSIZE1          TVTYPE1     
##  Min.   :-2.00   Min.   : 0.000   Min.   :-2.000   Min.   :-2.00  
##  1st Qu.: 1.00   1st Qu.: 2.000   1st Qu.: 2.000   1st Qu.: 1.00  
##  Median : 3.00   Median : 2.000   Median : 2.000   Median : 2.00  
##  Mean   : 9.24   Mean   : 2.588   Mean   : 2.264   Mean   : 1.73  
##  3rd Qu.: 3.00   3rd Qu.: 3.000   3rd Qu.: 3.000   3rd Qu.: 2.00  
##  Max.   :42.00   Max.   :14.000   Max.   : 3.000   Max.   : 5.00  
##                                                                   
##    CABLESAT1       COMBODVR1             DVR1           DIGITSTB1      
##  Min.   :-2.00   Min.   :-2.00000   Min.   :-2.0000   Min.   :-2.0000  
##  1st Qu.: 1.00   1st Qu.: 0.00000   1st Qu.:-2.0000   1st Qu.: 0.0000  
##  Median : 1.00   Median : 0.00000   Median : 0.0000   Median : 0.0000  
##  Mean   : 1.02   Mean   :-0.08797   Mean   :-0.5565   Mean   : 0.2013  
##  3rd Qu.: 1.00   3rd Qu.: 1.00000   3rd Qu.: 0.0000   3rd Qu.: 0.0000  
##  Max.   : 2.00   Max.   : 1.00000   Max.   : 1.0000   Max.   : 1.0000  
##                                                                        
##     PLAYSTA1        COMBOVCRDVD1          VCR1              DVD1        
##  Min.   :-2.0000   Min.   :-2.0000   Min.   :-2.0000   Min.   :-2.0000  
##  1st Qu.: 0.0000   1st Qu.: 0.0000   1st Qu.: 0.0000   1st Qu.: 0.0000  
##  Median : 0.0000   Median : 0.0000   Median : 0.0000   Median : 1.0000  
##  Mean   : 0.2414   Mean   : 0.2362   Mean   : 0.1518   Mean   : 0.4888  
##  3rd Qu.: 1.0000   3rd Qu.: 1.0000   3rd Qu.: 0.0000   3rd Qu.: 1.0000  
##  Max.   : 1.0000   Max.   : 1.0000   Max.   : 1.0000   Max.   : 1.0000  
##                                                                         
##   TVAUDIOSYS1        OTHERSTB1            TVONWD1        TVONWDWATCH1    
##  Min.   :-2.0000   Min.   :-2.000000   Min.   :-2.000   Min.   :-2.0000  
##  1st Qu.: 0.0000   1st Qu.: 0.000000   1st Qu.: 2.000   1st Qu.:-2.0000  
##  Median : 0.0000   Median : 0.000000   Median : 3.000   Median :-2.0000  
##  Mean   : 0.1655   Mean   : 0.005048   Mean   : 3.017   Mean   :-0.6851  
##  3rd Qu.: 0.0000   3rd Qu.: 0.000000   3rd Qu.: 4.000   3rd Qu.: 0.0000  
##  Max.   : 1.0000   Max.   : 1.000000   Max.   : 5.000   Max.   : 4.0000  
##                                                                          
##     TVONWE1        TVONWEWATCH1        TVSIZE2           TVTYPE2       
##  Min.   :-2.000   Min.   :-2.0000   Min.   :-2.0000   Min.   :-2.0000  
##  1st Qu.: 2.000   1st Qu.:-2.0000   1st Qu.: 1.0000   1st Qu.: 1.0000  
##  Median : 3.000   Median :-2.0000   Median : 2.0000   Median : 1.0000  
##  Mean   : 3.207   Mean   :-0.7073   Mean   : 0.9695   Mean   : 0.7196  
##  3rd Qu.: 4.000   3rd Qu.: 0.0000   3rd Qu.: 2.0000   3rd Qu.: 2.0000  
##  Max.   : 5.000   Max.   : 4.0000   Max.   : 3.0000   Max.   : 5.0000  
##                                                                        
##    CABLESAT2         COMBODVR2            DVR2           DIGITSTB2      
##  Min.   :-2.0000   Min.   :-2.0000   Min.   :-2.0000   Min.   :-2.0000  
##  1st Qu.: 0.0000   1st Qu.:-2.0000   1st Qu.:-2.0000   1st Qu.: 0.0000  
##  Median : 1.0000   Median : 0.0000   Median : 0.0000   Median : 0.0000  
##  Mean   : 0.3147   Mean   :-0.7687   Mean   :-0.6075   Mean   :-0.3138  
##  3rd Qu.: 1.0000   3rd Qu.: 0.0000   3rd Qu.: 0.0000   3rd Qu.: 0.0000  
##  Max.   : 2.0000   Max.   : 1.0000   Max.   : 1.0000   Max.   : 1.0000  
##                                                                         
##     PLAYSTA2        COMBOVCRDVD2          VCR2              DVD2        
##  Min.   :-2.0000   Min.   :-2.0000   Min.   :-2.0000   Min.   :-2.0000  
##  1st Qu.: 0.0000   1st Qu.: 0.0000   1st Qu.: 0.0000   1st Qu.: 0.0000  
##  Median : 0.0000   Median : 0.0000   Median : 0.0000   Median : 0.0000  
##  Mean   :-0.2986   Mean   :-0.3251   Mean   :-0.3344   Mean   :-0.1868  
##  3rd Qu.: 0.0000   3rd Qu.: 0.0000   3rd Qu.: 0.0000   3rd Qu.: 0.0000  
##  Max.   : 1.0000   Max.   : 1.0000   Max.   : 1.0000   Max.   : 1.0000  
##                                                                         
##   TVAUDIOSYS2       OTHERSTB2          TVONWD2        TVONWDWATCH2   
##  Min.   :-2.000   Min.   :-2.0000   Min.   :-2.000   Min.   :-2.000  
##  1st Qu.: 0.000   1st Qu.: 0.0000   1st Qu.: 1.000   1st Qu.:-2.000  
##  Median : 0.000   Median : 0.0000   Median : 2.000   Median :-2.000  
##  Mean   :-0.391   Mean   :-0.4185   Mean   : 1.238   Mean   :-1.415  
##  3rd Qu.: 0.000   3rd Qu.: 0.0000   3rd Qu.: 2.000   3rd Qu.:-2.000  
##  Max.   : 1.000   Max.   : 1.0000   Max.   : 5.000   Max.   : 4.000  
##                                                                      
##     TVONWE2        TVONWEWATCH2      TVSIZE3           TVTYPE3       
##  Min.   :-2.000   Min.   :-2.00   Min.   :-2.0000   Min.   :-2.0000  
##  1st Qu.: 1.000   1st Qu.:-2.00   1st Qu.:-2.0000   1st Qu.:-2.0000  
##  Median : 2.000   Median :-2.00   Median :-2.0000   Median :-2.0000  
##  Mean   : 1.337   Mean   :-1.41   Mean   :-0.3485   Mean   :-0.4546  
##  3rd Qu.: 3.000   3rd Qu.:-2.00   3rd Qu.: 1.0000   3rd Qu.: 1.0000  
##  Max.   : 5.000   Max.   : 4.00   Max.   : 3.0000   Max.   : 5.0000  
##                                                                      
##    CABLESAT3         COMBODVR3           DVR3         DIGITSTB3     
##  Min.   :-2.0000   Min.   :-2.000   Min.   :-2.00   Min.   :-2.000  
##  1st Qu.:-2.0000   1st Qu.:-2.000   1st Qu.:-2.00   1st Qu.:-2.000  
##  Median :-2.0000   Median :-2.000   Median :-2.00   Median :-2.000  
##  Mean   :-0.6968   Mean   :-1.373   Mean   :-1.15   Mean   :-1.034  
##  3rd Qu.: 1.0000   3rd Qu.: 0.000   3rd Qu.: 0.00   3rd Qu.: 0.000  
##  Max.   : 2.0000   Max.   : 1.000   Max.   : 1.00   Max.   : 1.000  
##                                                                     
##     PLAYSTA3       COMBOVCRDVD3         VCR3             DVD3        
##  Min.   :-2.000   Min.   :-2.000   Min.   :-2.000   Min.   :-2.0000  
##  1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.0000  
##  Median :-2.000   Median :-2.000   Median :-2.000   Median :-2.0000  
##  Mean   :-1.015   Mean   :-1.042   Mean   :-1.039   Mean   :-0.9701  
##  3rd Qu.: 0.000   3rd Qu.: 0.000   3rd Qu.: 0.000   3rd Qu.: 0.0000  
##  Max.   : 1.000   Max.   : 1.000   Max.   : 1.000   Max.   : 1.0000  
##                                                                      
##   TVAUDIOSYS3       OTHERSTB3         TVONWD3         TVONWDWATCH3   
##  Min.   :-2.000   Min.   :-2.000   Min.   :-2.0000   Min.   :-2.000  
##  1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.0000   1st Qu.:-2.000  
##  Median :-2.000   Median :-2.000   Median :-2.0000   Median :-2.000  
##  Mean   :-1.068   Mean   :-1.082   Mean   :-0.2859   Mean   :-1.689  
##  3rd Qu.: 0.000   3rd Qu.: 0.000   3rd Qu.: 1.0000   3rd Qu.:-2.000  
##  Max.   : 1.000   Max.   : 1.000   Max.   : 5.0000   Max.   : 4.000  
##                                                                      
##     TVONWE3         TVONWEWATCH3       COMPUTER          NUMPC       
##  Min.   :-2.0000   Min.   :-2.000   Min.   :0.0000   Min.   : 0.000  
##  1st Qu.:-2.0000   1st Qu.:-2.000   1st Qu.:1.0000   1st Qu.: 1.000  
##  Median :-2.0000   Median :-2.000   Median :1.0000   Median : 1.000  
##  Mean   :-0.2326   Mean   :-1.693   Mean   :0.7837   Mean   : 1.387  
##  3rd Qu.: 1.0000   3rd Qu.:-2.000   3rd Qu.:1.0000   3rd Qu.: 2.000  
##  Max.   : 5.0000   Max.   : 4.000   Max.   :1.0000   Max.   :15.000  
##                                                                      
##     PCTYPE1        MONITOR1          TIMEON1          PCONOFF1       
##  Min.   :-2.0   Min.   :-2.0000   Min.   :-2.000   Min.   :-2.00000  
##  1st Qu.: 1.0   1st Qu.:-2.0000   1st Qu.: 1.000   1st Qu.: 0.00000  
##  Median : 1.0   Median :-2.0000   Median : 2.000   Median : 0.00000  
##  Mean   : 0.7   Mean   :-0.7836   Mean   : 1.643   Mean   : 0.02375  
##  3rd Qu.: 2.0   3rd Qu.: 1.0000   3rd Qu.: 3.000   3rd Qu.: 1.00000  
##  Max.   : 2.0   Max.   : 1.0000   Max.   : 5.000   Max.   : 1.00000  
##                                                                      
##     PCSLEEP1         PCTYPE2           MONITOR2         TIMEON2       
##  Min.   :-2.000   Min.   :-2.0000   Min.   :-2.000   Min.   :-2.0000  
##  1st Qu.:-2.000   1st Qu.:-2.0000   1st Qu.:-2.000   1st Qu.:-2.0000  
##  Median :-2.000   Median :-2.0000   Median :-2.000   Median :-2.0000  
##  Mean   :-1.048   Mean   :-0.6606   Mean   :-1.596   Mean   :-0.4117  
##  3rd Qu.: 1.000   3rd Qu.: 1.0000   3rd Qu.:-2.000   3rd Qu.: 1.0000  
##  Max.   : 1.000   Max.   : 2.0000   Max.   : 1.000   Max.   : 5.0000  
##                                                                       
##     PCONOFF2          PCSLEEP2         PCTYPE3          MONITOR3     
##  Min.   :-2.0000   Min.   :-2.000   Min.   :-2.000   Min.   :-2.000  
##  1st Qu.:-2.0000   1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.000  
##  Median :-2.0000   Median :-2.000   Median :-2.000   Median :-2.000  
##  Mean   :-0.9959   Mean   :-1.679   Mean   :-1.478   Mean   :-1.843  
##  3rd Qu.: 1.0000   3rd Qu.:-2.000   3rd Qu.:-2.000   3rd Qu.:-2.000  
##  Max.   : 1.0000   Max.   : 1.000   Max.   : 2.000   Max.   : 1.000  
##                                                                      
##     TIMEON3          PCONOFF3         PCSLEEP3         INTERNET      
##  Min.   :-2.000   Min.   :-2.000   Min.   :-2.000   Min.   :-2.0000  
##  1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.: 0.0000  
##  Median :-2.000   Median :-2.000   Median :-2.000   Median : 1.0000  
##  Mean   :-1.418   Mean   :-1.602   Mean   :-1.893   Mean   : 0.3077  
##  3rd Qu.:-2.000   3rd Qu.:-2.000   3rd Qu.:-2.000   3rd Qu.: 1.0000  
##  Max.   : 5.000   Max.   : 1.000   Max.   : 1.000   Max.   : 1.0000  
##                                                                      
##     INDIALUP           INDSL            INCABLE          INSATEL       
##  Min.   :-2.0000   Min.   :-2.0000   Min.   :-2.000   Min.   :-2.0000  
##  1st Qu.:-2.0000   1st Qu.:-2.0000   1st Qu.:-2.000   1st Qu.:-2.0000  
##  Median : 0.0000   Median : 0.0000   Median : 0.000   Median : 0.0000  
##  Mean   :-0.4709   Mean   :-0.2103   Mean   :-0.183   Mean   :-0.4957  
##  3rd Qu.: 0.0000   3rd Qu.: 1.0000   3rd Qu.: 1.000   3rd Qu.: 0.0000  
##  Max.   : 1.0000   Max.   : 1.0000   Max.   : 1.000   Max.   : 1.0000  
##                                                                        
##    INWIRELESS          PCPRINT             FAX              COPIER      
##  Min.   :-2.00000   Min.   :-2.0000   Min.   :0.00000   Min.   :0.0000  
##  1st Qu.:-2.00000   1st Qu.: 0.0000   1st Qu.:0.00000   1st Qu.:0.0000  
##  Median : 0.00000   Median : 1.0000   Median :0.00000   Median :0.0000  
##  Mean   :-0.03567   Mean   : 0.3046   Mean   :0.09203   Mean   :0.0864  
##  3rd Qu.: 1.00000   3rd Qu.: 1.0000   3rd Qu.:0.00000   3rd Qu.:0.0000  
##  Max.   : 1.00000   Max.   : 6.0000   Max.   :1.00000   Max.   :1.0000  
##                                                                         
##     WELLPUMP          DIPSTICK         SWAMPCOL         AQUARIUM      
##  Min.   :-2.0000   Min.   :-2.000   Min.   :-2.000   Min.   :0.00000  
##  1st Qu.: 0.0000   1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:0.00000  
##  Median : 0.0000   Median :-2.000   Median :-2.000   Median :0.00000  
##  Mean   :-0.3561   Mean   :-1.394   Mean   :-1.155   Mean   :0.03815  
##  3rd Qu.: 0.0000   3rd Qu.: 0.000   3rd Qu.: 0.000   3rd Qu.:0.00000  
##  Max.   : 1.0000   Max.   : 1.000   Max.   : 1.000   Max.   :1.00000  
##                                                                       
##      STEREO           NOCORD          ANSMACH          BATTOOLS     
##  Min.   :0.0000   Min.   :0.0000   Min.   :0.0000   Min.   :0.0000  
##  1st Qu.:0.0000   1st Qu.:0.0000   1st Qu.:0.0000   1st Qu.:0.0000  
##  Median :0.0000   Median :1.0000   Median :0.0000   Median :1.0000  
##  Mean   :0.4313   Mean   :0.6338   Mean   :0.4686   Mean   :0.8629  
##  3rd Qu.:1.0000   3rd Qu.:1.0000   3rd Qu.:1.0000   3rd Qu.:1.0000  
##  Max.   :1.0000   Max.   :1.0000   Max.   :1.0000   Max.   :3.0000  
##                                                                     
##     BATCHRG           CHRGPLGT          ELECDEV         ELECCHRG     
##  Min.   :-2.0000   Min.   :-2.0000   Min.   :0.000   Min.   :-2.000  
##  1st Qu.:-2.0000   1st Qu.:-2.0000   1st Qu.:1.000   1st Qu.: 2.000  
##  Median : 2.0000   Median : 0.0000   Median :1.000   Median : 2.000  
##  Mean   : 0.5469   Mean   :-0.6638   Mean   :1.402   Mean   : 1.721  
##  3rd Qu.: 2.0000   3rd Qu.: 0.0000   3rd Qu.:2.000   3rd Qu.: 2.000  
##  Max.   : 3.0000   Max.   : 2.0000   Max.   :3.000   Max.   : 3.000  
##                                                                      
##     CHRGPLGE          ZCWASHER   ZTOPFRONT   ZWASHLOAD        
##  Min.   :-2.0000   Min.   :0   Min.   :0   Min.   :0.0000000  
##  1st Qu.: 0.0000   1st Qu.:0   1st Qu.:0   1st Qu.:0.0000000  
##  Median : 0.0000   Median :0   Median :0   Median :0.0000000  
##  Mean   : 0.2355   Mean   :0   Mean   :0   Mean   :0.0005793  
##  3rd Qu.: 1.0000   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0.0000000  
##  Max.   : 2.0000   Max.   :0   Max.   :0   Max.   :1.0000000  
##                                                               
##    ZWASHTEMP          ZRNSETEMP          ZAGECWASH           ZDRYER 
##  Min.   :0.000000   Min.   :0.000000   Min.   :0.00000   Min.   :0  
##  1st Qu.:0.000000   1st Qu.:0.000000   1st Qu.:0.00000   1st Qu.:0  
##  Median :0.000000   Median :0.000000   Median :0.00000   Median :0  
##  Mean   :0.005048   Mean   :0.008276   Mean   :0.01266   Mean   :0  
##  3rd Qu.:0.000000   3rd Qu.:0.000000   3rd Qu.:0.00000   3rd Qu.:0  
##  Max.   :1.000000   Max.   :1.000000   Max.   :1.00000   Max.   :0  
##                                                                     
##    ZDRYRFUEL           ZDRYRUSE           ZAGECDRYER         ZTVCOLOR
##  Min.   :0.000000   Min.   :0.0000000   Min.   :0.00000   Min.   :0  
##  1st Qu.:0.000000   1st Qu.:0.0000000   1st Qu.:0.00000   1st Qu.:0  
##  Median :0.000000   Median :0.0000000   Median :0.00000   Median :0  
##  Mean   :0.003228   Mean   :0.0001655   Mean   :0.01308   Mean   :0  
##  3rd Qu.:0.000000   3rd Qu.:0.0000000   3rd Qu.:0.00000   3rd Qu.:0  
##  Max.   :1.000000   Max.   :1.0000000   Max.   :1.00000   Max.   :0  
##                                                                      
##     ZTVSIZE1            ZTVTYPE1          ZCABLESAT1       
##  Min.   :0.0000000   Min.   :0.000000   Min.   :0.0000000  
##  1st Qu.:0.0000000   1st Qu.:0.000000   1st Qu.:0.0000000  
##  Median :0.0000000   Median :0.000000   Median :0.0000000  
##  Mean   :0.0005793   Mean   :0.005876   Mean   :0.0005793  
##  3rd Qu.:0.0000000   3rd Qu.:0.000000   3rd Qu.:0.0000000  
##  Max.   :1.0000000   Max.   :1.000000   Max.   :1.0000000  
##                                                            
##    ZCOMBODVR1           ZDVR1            ZDIGITSTB1      
##  Min.   :0.000000   Min.   :0.000000   Min.   :0.000000  
##  1st Qu.:0.000000   1st Qu.:0.000000   1st Qu.:0.000000  
##  Median :0.000000   Median :0.000000   Median :0.000000  
##  Mean   :0.008442   Mean   :0.007366   Mean   :0.004883  
##  3rd Qu.:0.000000   3rd Qu.:0.000000   3rd Qu.:0.000000  
##  Max.   :1.000000   Max.   :1.000000   Max.   :1.000000  
##                                                          
##    ZPLAYSTA1         ZCOMBOVCRDVD1           ZVCR1          
##  Min.   :0.0000000   Min.   :0.0000000   Min.   :0.0000000  
##  1st Qu.:0.0000000   1st Qu.:0.0000000   1st Qu.:0.0000000  
##  Median :0.0000000   Median :0.0000000   Median :0.0000000  
##  Mean   :0.0004966   Mean   :0.0008276   Mean   :0.0004138  
##  3rd Qu.:0.0000000   3rd Qu.:0.0000000   3rd Qu.:0.0000000  
##  Max.   :1.0000000   Max.   :1.0000000   Max.   :1.0000000  
##                                                             
##      ZDVD1            ZTVAUDIOSYS1         ZOTHERSTB1       
##  Min.   :0.0000000   Min.   :0.0000000   Min.   :0.0000000  
##  1st Qu.:0.0000000   1st Qu.:0.0000000   1st Qu.:0.0000000  
##  Median :0.0000000   Median :0.0000000   Median :0.0000000  
##  Mean   :0.0005793   Mean   :0.0002483   Mean   :0.0006621  
##  3rd Qu.:0.0000000   3rd Qu.:0.0000000   3rd Qu.:0.0000000  
##  Max.   :1.0000000   Max.   :1.0000000   Max.   :1.0000000  
##                                                             
##     ZTVONWD1         ZTVONWDWATCH1          ZTVONWE1        
##  Min.   :0.0000000   Min.   :0.0000000   Min.   :0.0000000  
##  1st Qu.:0.0000000   1st Qu.:0.0000000   1st Qu.:0.0000000  
##  Median :0.0000000   Median :0.0000000   Median :0.0000000  
##  Mean   :0.0004966   Mean   :0.0002483   Mean   :0.0007448  
##  3rd Qu.:0.0000000   3rd Qu.:0.0000000   3rd Qu.:0.0000000  
##  Max.   :1.0000000   Max.   :1.0000000   Max.   :1.0000000  
##                                                             
##  ZTVONWEWATCH1         ZTVSIZE2            ZTVTYPE2       
##  Min.   :0.000000   Min.   :0.0000000   Min.   :0.000000  
##  1st Qu.:0.000000   1st Qu.:0.0000000   1st Qu.:0.000000  
##  Median :0.000000   Median :0.0000000   Median :0.000000  
##  Mean   :0.000331   Mean   :0.0004966   Mean   :0.002152  
##  3rd Qu.:0.000000   3rd Qu.:0.0000000   3rd Qu.:0.000000  
##  Max.   :1.000000   Max.   :1.0000000   Max.   :1.000000  
##                                                           
##    ZCABLESAT2          ZCOMBODVR2           ZDVR2         
##  Min.   :0.0000000   Min.   :0.000000   Min.   :0.000000  
##  1st Qu.:0.0000000   1st Qu.:0.000000   1st Qu.:0.000000  
##  Median :0.0000000   Median :0.000000   Median :0.000000  
##  Mean   :0.0005793   Mean   :0.002814   Mean   :0.002897  
##  3rd Qu.:0.0000000   3rd Qu.:0.000000   3rd Qu.:0.000000  
##  Max.   :1.0000000   Max.   :1.000000   Max.   :1.000000  
##                                                           
##    ZDIGITSTB2         ZPLAYSTA2         ZCOMBOVCRDVD2      
##  Min.   :0.000000   Min.   :0.0000000   Min.   :0.0000000  
##  1st Qu.:0.000000   1st Qu.:0.0000000   1st Qu.:0.0000000  
##  Median :0.000000   Median :0.0000000   Median :0.0000000  
##  Mean   :0.002648   Mean   :0.0005793   Mean   :0.0006621  
##  3rd Qu.:0.000000   3rd Qu.:0.0000000   3rd Qu.:0.0000000  
##  Max.   :1.000000   Max.   :1.0000000   Max.   :1.0000000  
##                                                            
##      ZVCR2               ZDVD2            ZTVAUDIOSYS2      
##  Min.   :0.0000000   Min.   :0.0000000   Min.   :0.0000000  
##  1st Qu.:0.0000000   1st Qu.:0.0000000   1st Qu.:0.0000000  
##  Median :0.0000000   Median :0.0000000   Median :0.0000000  
##  Mean   :0.0004966   Mean   :0.0004966   Mean   :0.0005793  
##  3rd Qu.:0.0000000   3rd Qu.:0.0000000   3rd Qu.:0.0000000  
##  Max.   :1.0000000   Max.   :1.0000000   Max.   :1.0000000  
##                                                             
##    ZOTHERSTB2          ZTVONWD2         ZTVONWDWATCH2      
##  Min.   :0.000000   Min.   :0.0000000   Min.   :0.0000000  
##  1st Qu.:0.000000   1st Qu.:0.0000000   1st Qu.:0.0000000  
##  Median :0.000000   Median :0.0000000   Median :0.0000000  
##  Mean   :0.000331   Mean   :0.0009931   Mean   :0.0005793  
##  3rd Qu.:0.000000   3rd Qu.:0.0000000   3rd Qu.:0.0000000  
##  Max.   :1.000000   Max.   :1.0000000   Max.   :1.0000000  
##                                                            
##     ZTVONWE2         ZTVONWEWATCH2          ZTVSIZE3        
##  Min.   :0.0000000   Min.   :0.0000000   Min.   :0.0000000  
##  1st Qu.:0.0000000   1st Qu.:0.0000000   1st Qu.:0.0000000  
##  Median :0.0000000   Median :0.0000000   Median :0.0000000  
##  Mean   :0.0009931   Mean   :0.0006621   Mean   :0.0007448  
##  3rd Qu.:0.0000000   3rd Qu.:0.0000000   3rd Qu.:0.0000000  
##  Max.   :1.0000000   Max.   :1.0000000   Max.   :1.0000000  
##                                                             
##     ZTVTYPE3         ZCABLESAT3          ZCOMBODVR3      
##  Min.   :0.00000   Min.   :0.0000000   Min.   :0.000000  
##  1st Qu.:0.00000   1st Qu.:0.0000000   1st Qu.:0.000000  
##  Median :0.00000   Median :0.0000000   Median :0.000000  
##  Mean   :0.00149   Mean   :0.0006621   Mean   :0.001324  
##  3rd Qu.:0.00000   3rd Qu.:0.0000000   3rd Qu.:0.000000  
##  Max.   :1.00000   Max.   :1.0000000   Max.   :1.000000  
##                                                          
##      ZDVR3            ZDIGITSTB3         ZPLAYSTA3        
##  Min.   :0.000000   Min.   :0.000000   Min.   :0.0000000  
##  1st Qu.:0.000000   1st Qu.:0.000000   1st Qu.:0.0000000  
##  Median :0.000000   Median :0.000000   Median :0.0000000  
##  Mean   :0.001821   Mean   :0.001159   Mean   :0.0004966  
##  3rd Qu.:0.000000   3rd Qu.:0.000000   3rd Qu.:0.0000000  
##  Max.   :1.000000   Max.   :1.000000   Max.   :1.0000000  
##                                                           
##  ZCOMBOVCRDVD3          ZVCR3               ZDVD3          
##  Min.   :0.000000   Min.   :0.0000000   Min.   :0.0000000  
##  1st Qu.:0.000000   1st Qu.:0.0000000   1st Qu.:0.0000000  
##  Median :0.000000   Median :0.0000000   Median :0.0000000  
##  Mean   :0.001076   Mean   :0.0007448   Mean   :0.0007448  
##  3rd Qu.:0.000000   3rd Qu.:0.0000000   3rd Qu.:0.0000000  
##  Max.   :1.000000   Max.   :1.0000000   Max.   :1.0000000  
##                                                            
##   ZTVAUDIOSYS3         ZOTHERSTB3           ZTVONWD3        
##  Min.   :0.0000000   Min.   :0.0000000   Min.   :0.0000000  
##  1st Qu.:0.0000000   1st Qu.:0.0000000   1st Qu.:0.0000000  
##  Median :0.0000000   Median :0.0000000   Median :0.0000000  
##  Mean   :0.0004138   Mean   :0.0006621   Mean   :0.0009931  
##  3rd Qu.:0.0000000   3rd Qu.:0.0000000   3rd Qu.:0.0000000  
##  Max.   :1.0000000   Max.   :1.0000000   Max.   :1.0000000  
##                                                             
##  ZTVONWDWATCH3          ZTVONWE3         ZTVONWEWATCH3      
##  Min.   :0.0000000   Min.   :0.0000000   Min.   :0.0000000  
##  1st Qu.:0.0000000   1st Qu.:0.0000000   1st Qu.:0.0000000  
##  Median :0.0000000   Median :0.0000000   Median :0.0000000  
##  Mean   :0.0004138   Mean   :0.0009931   Mean   :0.0004966  
##  3rd Qu.:0.0000000   3rd Qu.:0.0000000   3rd Qu.:0.0000000  
##  Max.   :1.0000000   Max.   :1.0000000   Max.   :1.0000000  
##                                                             
##    ZCOMPUTER             ZNUMPC             ZPCTYPE1        
##  Min.   :0.0000000   Min.   :0.0000000   Min.   :0.0000000  
##  1st Qu.:0.0000000   1st Qu.:0.0000000   1st Qu.:0.0000000  
##  Median :0.0000000   Median :0.0000000   Median :0.0000000  
##  Mean   :0.0001655   Mean   :0.0002483   Mean   :0.0004138  
##  3rd Qu.:0.0000000   3rd Qu.:0.0000000   3rd Qu.:0.0000000  
##  Max.   :1.0000000   Max.   :1.0000000   Max.   :1.0000000  
##                                                             
##    ZMONITOR1            ZTIMEON1          ZPCONOFF1       
##  Min.   :0.0000000   Min.   :0.000000   Min.   :0.000000  
##  1st Qu.:0.0000000   1st Qu.:0.000000   1st Qu.:0.000000  
##  Median :0.0000000   Median :0.000000   Median :0.000000  
##  Mean   :0.0009931   Mean   :0.001986   Mean   :0.001986  
##  3rd Qu.:0.0000000   3rd Qu.:0.000000   3rd Qu.:0.000000  
##  Max.   :1.0000000   Max.   :1.000000   Max.   :1.000000  
##                                                           
##    ZPCSLEEP1           ZPCTYPE2           ZMONITOR2        
##  Min.   :0.000000   Min.   :0.0000000   Min.   :0.0000000  
##  1st Qu.:0.000000   1st Qu.:0.0000000   1st Qu.:0.0000000  
##  Median :0.000000   Median :0.0000000   Median :0.0000000  
##  Mean   :0.001655   Mean   :0.0001655   Mean   :0.0002483  
##  3rd Qu.:0.000000   3rd Qu.:0.0000000   3rd Qu.:0.0000000  
##  Max.   :1.000000   Max.   :1.0000000   Max.   :1.0000000  
##                                                            
##     ZTIMEON2          ZPCONOFF2          ZPCSLEEP2        
##  Min.   :0.000000   Min.   :0.000000   Min.   :0.0000000  
##  1st Qu.:0.000000   1st Qu.:0.000000   1st Qu.:0.0000000  
##  Median :0.000000   Median :0.000000   Median :0.0000000  
##  Mean   :0.001407   Mean   :0.001738   Mean   :0.0002483  
##  3rd Qu.:0.000000   3rd Qu.:0.000000   3rd Qu.:0.0000000  
##  Max.   :1.000000   Max.   :1.000000   Max.   :1.0000000  
##                                                           
##     ZPCTYPE3          ZMONITOR3            ZTIMEON3        
##  Min.   :0.00e+00   Min.   :0.0000000   Min.   :0.0000000  
##  1st Qu.:0.00e+00   1st Qu.:0.0000000   1st Qu.:0.0000000  
##  Median :0.00e+00   Median :0.0000000   Median :0.0000000  
##  Mean   :8.28e-05   Mean   :0.0001655   Mean   :0.0004138  
##  3rd Qu.:0.00e+00   3rd Qu.:0.0000000   3rd Qu.:0.0000000  
##  Max.   :1.00e+00   Max.   :1.0000000   Max.   :1.0000000  
##                                                            
##    ZPCONOFF3           ZPCSLEEP3           ZINTERNET        
##  Min.   :0.0000000   Min.   :0.0000000   Min.   :0.0000000  
##  1st Qu.:0.0000000   1st Qu.:0.0000000   1st Qu.:0.0000000  
##  Median :0.0000000   Median :0.0000000   Median :0.0000000  
##  Mean   :0.0006621   Mean   :0.0004966   Mean   :0.0009104  
##  3rd Qu.:0.0000000   3rd Qu.:0.0000000   3rd Qu.:0.0000000  
##  Max.   :1.0000000   Max.   :1.0000000   Max.   :1.0000000  
##                                                             
##    ZINDIALUP           ZINDSL            ZINCABLE       
##  Min.   :0.00000   Min.   :0.000000   Min.   :0.000000  
##  1st Qu.:0.00000   1st Qu.:0.000000   1st Qu.:0.000000  
##  Median :0.00000   Median :0.000000   Median :0.000000  
##  Mean   :0.00389   Mean   :0.007531   Mean   :0.005628  
##  3rd Qu.:0.00000   3rd Qu.:0.000000   3rd Qu.:0.000000  
##  Max.   :1.00000   Max.   :1.000000   Max.   :1.000000  
##                                                         
##     ZINSATEL         ZINWIRELESS          ZPCPRINT        
##  Min.   :0.000000   Min.   :0.000000   Min.   :0.0000000  
##  1st Qu.:0.000000   1st Qu.:0.000000   1st Qu.:0.0000000  
##  Median :0.000000   Median :0.000000   Median :0.0000000  
##  Mean   :0.005214   Mean   :0.004552   Mean   :0.0008276  
##  3rd Qu.:0.000000   3rd Qu.:0.000000   3rd Qu.:0.0000000  
##  Max.   :1.000000   Max.   :1.000000   Max.   :1.0000000  
##                                                           
##       ZFAX              ZCOPIER            ZWELLPUMP       
##  Min.   :0.0000000   Min.   :0.0000000   Min.   :0.000000  
##  1st Qu.:0.0000000   1st Qu.:0.0000000   1st Qu.:0.000000  
##  Median :0.0000000   Median :0.0000000   Median :0.000000  
##  Mean   :0.0004138   Mean   :0.0007448   Mean   :0.002731  
##  3rd Qu.:0.0000000   3rd Qu.:0.0000000   3rd Qu.:0.000000  
##  Max.   :1.0000000   Max.   :1.0000000   Max.   :1.000000  
##                                                            
##    ZDIPSTICK           ZSWAMPCOL          ZAQUARIUM       
##  Min.   :0.0000000   Min.   :0.00e+00   Min.   :0.00e+00  
##  1st Qu.:0.0000000   1st Qu.:0.00e+00   1st Qu.:0.00e+00  
##  Median :0.0000000   Median :0.00e+00   Median :0.00e+00  
##  Mean   :0.0002483   Mean   :8.28e-05   Mean   :8.28e-05  
##  3rd Qu.:0.0000000   3rd Qu.:0.00e+00   3rd Qu.:0.00e+00  
##  Max.   :1.0000000   Max.   :1.00e+00   Max.   :1.00e+00  
##                                                           
##     ZSTEREO             ZNOCORD            ZANSMACH        
##  Min.   :0.0000000   Min.   :0.00e+00   Min.   :0.0000000  
##  1st Qu.:0.0000000   1st Qu.:0.00e+00   1st Qu.:0.0000000  
##  Median :0.0000000   Median :0.00e+00   Median :0.0000000  
##  Mean   :0.0001655   Mean   :8.28e-05   Mean   :0.0001655  
##  3rd Qu.:0.0000000   3rd Qu.:0.00e+00   3rd Qu.:0.0000000  
##  Max.   :1.0000000   Max.   :1.00e+00   Max.   :1.0000000  
##                                                            
##    ZBATTOOLS           ZBATCHRG           ZCHRGPLGT        
##  Min.   :0.000000   Min.   :0.0000000   Min.   :0.0000000  
##  1st Qu.:0.000000   1st Qu.:0.0000000   1st Qu.:0.0000000  
##  Median :0.000000   Median :0.0000000   Median :0.0000000  
##  Mean   :0.001241   Mean   :0.0005793   Mean   :0.0009931  
##  3rd Qu.:0.000000   3rd Qu.:0.0000000   3rd Qu.:0.0000000  
##  Max.   :1.000000   Max.   :1.0000000   Max.   :1.0000000  
##                                                            
##     ZELECDEV           ZELECCHRG           ZCHRGPLGE        
##  Min.   :0.0000000   Min.   :0.0000000   Min.   :0.0000000  
##  1st Qu.:0.0000000   1st Qu.:0.0000000   1st Qu.:0.0000000  
##  Median :0.0000000   Median :0.0000000   Median :0.0000000  
##  Mean   :0.0005793   Mean   :0.0004138   Mean   :0.0004138  
##  3rd Qu.:0.0000000   3rd Qu.:0.0000000   3rd Qu.:0.0000000  
##  Max.   :1.0000000   Max.   :1.0000000   Max.   :1.0000000  
##                                                             
##     HEATHOME         DNTHEAT        EQUIPNOHEAT       FUELNOHEAT    
##  Min.   :0.0000   Min.   :-2.000   Min.   :-2.000   Min.   :-2.000  
##  1st Qu.:1.0000   1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.000  
##  Median :1.0000   Median :-2.000   Median :-2.000   Median :-2.000  
##  Mean   :0.9631   Mean   :-1.877   Mean   :-1.826   Mean   :-1.866  
##  3rd Qu.:1.0000   3rd Qu.:-2.000   3rd Qu.:-2.000   3rd Qu.:-2.000  
##  Max.   :1.0000   Max.   : 2.000   Max.   :21.000   Max.   :21.000  
##                                                                     
##      EQUIPM          FUELHEAT         MAINTHT           EQUIPAGE    
##  Min.   :-2.000   Min.   :-2.000   Min.   :-2.0000   Min.   :-2.00  
##  1st Qu.: 3.000   1st Qu.: 1.000   1st Qu.: 0.0000   1st Qu.: 2.00  
##  Median : 3.000   Median : 1.000   Median : 0.0000   Median : 5.00  
##  Mean   : 3.446   Mean   : 2.612   Mean   : 0.3137   Mean   :13.65  
##  3rd Qu.: 3.000   3rd Qu.: 5.000   3rd Qu.: 1.0000   3rd Qu.:41.00  
##  Max.   :21.000   Max.   :21.000   Max.   : 1.0000   Max.   :42.00  
##                                                                     
##     REPLCHT           HELPHT          HELPHTY          HEATOTH          
##  Min.   :-9.000   Min.   :-9.000   Min.   :-9.000   Min.   :-2.0000000  
##  1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.: 0.0000000  
##  Median :-2.000   Median :-2.000   Median :-2.000   Median : 0.0000000  
##  Mean   :-1.589   Mean   :-1.133   Mean   :-1.855   Mean   :-0.0008276  
##  3rd Qu.:-2.000   3rd Qu.: 0.000   3rd Qu.:-2.000   3rd Qu.: 0.0000000  
##  Max.   : 1.000   Max.   : 5.000   Max.   : 6.000   Max.   : 1.0000000  
##                                                                         
##     EQUIPAUX          REVERSE            WARMAIR            FURNFUEL     
##  Min.   :-2.0000   Min.   :-2.00000   Min.   :-2.00000   Min.   :-2.000  
##  1st Qu.: 0.0000   1st Qu.: 0.00000   1st Qu.: 0.00000   1st Qu.:-2.000  
##  Median : 0.0000   Median : 0.00000   Median : 0.00000   Median :-2.000  
##  Mean   : 0.3029   Mean   :-0.06257   Mean   :-0.05139   Mean   :-1.901  
##  3rd Qu.: 1.0000   3rd Qu.: 0.00000   3rd Qu.: 0.00000   3rd Qu.:-2.000  
##  Max.   : 1.0000   Max.   : 1.00000   Max.   : 1.00000   Max.   : 7.000  
##                                                                          
##      STEAMR            RADFUEL          PERMELEC           PIPELESS       
##  Min.   :-2.00000   Min.   :-2.000   Min.   :-2.00000   Min.   :-2.00000  
##  1st Qu.: 0.00000   1st Qu.:-2.000   1st Qu.: 0.00000   1st Qu.: 0.00000  
##  Median : 0.00000   Median :-2.000   Median : 0.00000   Median : 0.00000  
##  Mean   :-0.06894   Mean   :-1.976   Mean   :-0.05322   Mean   :-0.07184  
##  3rd Qu.: 0.00000   3rd Qu.:-2.000   3rd Qu.: 0.00000   3rd Qu.: 0.00000  
##  Max.   : 1.00000   Max.   :21.000   Max.   : 1.00000   Max.   : 1.00000  
##                                                                           
##     PIPEFUEL         ROOMHEAT           RMHTFUEL         WOODKILN       
##  Min.   :-2.000   Min.   :-2.00000   Min.   :-2.000   Min.   :-2.00000  
##  1st Qu.:-2.000   1st Qu.: 0.00000   1st Qu.:-2.000   1st Qu.: 0.00000  
##  Median :-2.000   Median : 0.00000   Median :-2.000   Median : 0.00000  
##  Mean   :-1.992   Mean   :-0.06331   Mean   :-1.963   Mean   :-0.04941  
##  3rd Qu.:-2.000   3rd Qu.: 0.00000   3rd Qu.:-2.000   3rd Qu.: 0.00000  
##  Max.   : 5.000   Max.   : 1.00000   Max.   : 4.000   Max.   : 1.00000  
##                                                                         
##      HSFUEL          CARRYEL           CARRYKER           CHIMNEY        
##  Min.   :-2.000   Min.   :-2.0000   Min.   :-2.00000   Min.   :-2.00000  
##  1st Qu.:-2.000   1st Qu.: 0.0000   1st Qu.: 0.00000   1st Qu.: 0.00000  
##  Median :-2.000   Median : 0.0000   Median : 0.00000   Median : 0.00000  
##  Mean   :-1.771   Mean   : 0.1242   Mean   :-0.06778   Mean   : 0.04593  
##  3rd Qu.:-2.000   3rd Qu.: 0.0000   3rd Qu.: 0.00000   3rd Qu.: 0.00000  
##  Max.   :21.000   Max.   : 1.0000   Max.   : 1.00000   Max.   : 1.00000  
##                                                                          
##      FPFUEL          NGFPFLUE         USENGFP           RANGE         
##  Min.   :-2.000   Min.   :-2.000   Min.   :-2.000   Min.   :-2.00000  
##  1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.: 0.00000  
##  Median :-2.000   Median :-2.000   Median :-2.000   Median : 0.00000  
##  Mean   :-1.194   Mean   :-1.815   Mean   :-1.763   Mean   :-0.06671  
##  3rd Qu.:-2.000   3rd Qu.:-2.000   3rd Qu.:-2.000   3rd Qu.: 0.00000  
##  Max.   :21.000   Max.   : 2.000   Max.   : 3.000   Max.   : 1.00000  
##                                                                       
##     RNGFUEL          DIFEQUIP           DIFFUEL           EQMAMT       
##  Min.   :-2.000   Min.   :-2.00000   Min.   :-2.000   Min.   :-2.0000  
##  1st Qu.:-2.000   1st Qu.: 0.00000   1st Qu.:-2.000   1st Qu.:-2.0000  
##  Median :-2.000   Median : 0.00000   Median :-2.000   Median :-2.0000  
##  Mean   :-1.962   Mean   :-0.06728   Mean   :-1.958   Mean   :-0.7244  
##  3rd Qu.:-2.000   3rd Qu.: 0.00000   3rd Qu.:-2.000   3rd Qu.: 1.0000  
##  Max.   : 7.000   Max.   : 1.00000   Max.   :21.000   Max.   : 3.0000  
##                                                                        
##     HEATROOM         THERMAIN          NUMTHERM          PROTHERM       
##  Min.   :-2.000   Min.   :-2.0000   Min.   :-2.0000   Min.   :-2.00000  
##  1st Qu.: 4.000   1st Qu.: 1.0000   1st Qu.: 1.0000   1st Qu.: 0.00000  
##  Median : 5.000   Median : 1.0000   Median : 1.0000   Median : 0.00000  
##  Mean   : 5.352   Mean   : 0.6735   Mean   : 0.7921   Mean   : 0.08615  
##  3rd Qu.: 7.000   3rd Qu.: 1.0000   3rd Qu.: 1.0000   3rd Qu.: 1.00000  
##  Max.   :23.000   Max.   : 1.0000   Max.   : 5.0000   Max.   : 1.00000  
##                                                                         
##   AUTOHEATNITE      AUTOHEATDAY        TEMPHOME        TEMPGONE    
##  Min.   :-2.0000   Min.   :-2.000   Min.   :-2.00   Min.   :-2.00  
##  1st Qu.:-2.0000   1st Qu.:-2.000   1st Qu.:68.00   1st Qu.:62.00  
##  Median :-2.0000   Median :-2.000   Median :70.00   Median :68.00  
##  Mean   :-0.9814   Mean   :-1.016   Mean   :67.03   Mean   :63.85  
##  3rd Qu.: 0.0000   3rd Qu.: 0.000   3rd Qu.:72.00   3rd Qu.:70.00  
##  Max.   : 1.0000   Max.   : 1.000   Max.   :90.00   Max.   :90.00  
##                                                                    
##     TEMPNITE        MOISTURE       USEMOISTURE       ZHEATHOME    ZDNTHEAT
##  Min.   :-2.00   Min.   :0.0000   Min.   :-2.000   Min.   :0   Min.   :0  
##  1st Qu.:65.00   1st Qu.:0.0000   1st Qu.:-2.000   1st Qu.:0   1st Qu.:0  
##  Median :68.00   Median :0.0000   Median :-2.000   Median :0   Median :0  
##  Mean   :65.12   Mean   :0.1525   Mean   :-1.434   Mean   :0   Mean   :0  
##  3rd Qu.:70.00   3rd Qu.:0.0000   3rd Qu.:-2.000   3rd Qu.:0   3rd Qu.:0  
##  Max.   :91.00   Max.   :1.0000   Max.   : 5.000   Max.   :0   Max.   :0  
##                                                                           
##   ZEQUIPNOHEAT        ZFUELNOHEAT           ZEQUIPM        
##  Min.   :0.0000000   Min.   :0.0000000   Min.   :0.000000  
##  1st Qu.:0.0000000   1st Qu.:0.0000000   1st Qu.:0.000000  
##  Median :0.0000000   Median :0.0000000   Median :0.000000  
##  Mean   :0.0004966   Mean   :0.0007448   Mean   :0.007697  
##  3rd Qu.:0.0000000   3rd Qu.:0.0000000   3rd Qu.:0.000000  
##  Max.   :1.0000000   Max.   :1.0000000   Max.   :1.000000  
##                                                            
##    ZFUELHEAT         ZMAINTHT         ZEQUIPAGE          ZHEATOTH       
##  Min.   :0.0000   Min.   :0.00000   Min.   :0.00000   Min.   :0.000000  
##  1st Qu.:0.0000   1st Qu.:0.00000   1st Qu.:0.00000   1st Qu.:0.000000  
##  Median :0.0000   Median :0.00000   Median :0.00000   Median :0.000000  
##  Mean   :0.0144   Mean   :0.02359   Mean   :0.07192   Mean   :0.003062  
##  3rd Qu.:0.0000   3rd Qu.:0.00000   3rd Qu.:0.00000   3rd Qu.:0.000000  
##  Max.   :1.0000   Max.   :1.00000   Max.   :1.00000   Max.   :1.000000  
##                                                                         
##    ZFURNFUEL           ZRADFUEL           ZPIPEFUEL   ZRMHTFUEL
##  Min.   :0.000000   Min.   :0.0000000   Min.   :0   Min.   :0  
##  1st Qu.:0.000000   1st Qu.:0.0000000   1st Qu.:0   1st Qu.:0  
##  Median :0.000000   Median :0.0000000   Median :0   Median :0  
##  Mean   :0.001159   Mean   :0.0004138   Mean   :0   Mean   :0  
##  3rd Qu.:0.000000   3rd Qu.:0.0000000   3rd Qu.:0   3rd Qu.:0  
##  Max.   :1.000000   Max.   :1.0000000   Max.   :0   Max.   :0  
##                                                                
##     ZHSFUEL     ZFPFUEL            ZNGFPFLUE           ZUSENGFP        
##  Min.   :0   Min.   :0.0000000   Min.   :0.000000   Min.   :0.0000000  
##  1st Qu.:0   1st Qu.:0.0000000   1st Qu.:0.000000   1st Qu.:0.0000000  
##  Median :0   Median :0.0000000   Median :0.000000   Median :0.0000000  
##  Mean   :0   Mean   :0.0002483   Mean   :0.001324   Mean   :0.0006621  
##  3rd Qu.:0   3rd Qu.:0.0000000   3rd Qu.:0.000000   3rd Qu.:0.0000000  
##  Max.   :0   Max.   :1.0000000   Max.   :1.000000   Max.   :1.0000000  
##                                                                        
##     ZRNGFUEL    ZDIFFUEL           ZEQMAMT           ZHEATROOM        
##  Min.   :0   Min.   :0.00e+00   Min.   :0.000000   Min.   :0.0000000  
##  1st Qu.:0   1st Qu.:0.00e+00   1st Qu.:0.000000   1st Qu.:0.0000000  
##  Median :0   Median :0.00e+00   Median :0.000000   Median :0.0000000  
##  Mean   :0   Mean   :8.28e-05   Mean   :0.001904   Mean   :0.0009104  
##  3rd Qu.:0   3rd Qu.:0.00e+00   3rd Qu.:0.000000   3rd Qu.:0.0000000  
##  Max.   :0   Max.   :1.00e+00   Max.   :1.000000   Max.   :1.0000000  
##                                                                       
##    ZTHERMAIN           ZNUMTHERM           ZPROTHERM       
##  Min.   :0.0000000   Min.   :0.0000000   Min.   :0.000000  
##  1st Qu.:0.0000000   1st Qu.:0.0000000   1st Qu.:0.000000  
##  Median :0.0000000   Median :0.0000000   Median :0.000000  
##  Mean   :0.0004966   Mean   :0.0005793   Mean   :0.003228  
##  3rd Qu.:0.0000000   3rd Qu.:0.0000000   3rd Qu.:0.000000  
##  Max.   :1.0000000   Max.   :1.0000000   Max.   :1.000000  
##                                                            
##  ZAUTOHEATNITE       ZAUTOHEATDAY      ZTEMPHOME         ZTEMPGONE      
##  Min.   :0.000000   Min.   :0.0000   Min.   :0.00000   Min.   :0.00000  
##  1st Qu.:0.000000   1st Qu.:0.0000   1st Qu.:0.00000   1st Qu.:0.00000  
##  Median :0.000000   Median :0.0000   Median :0.00000   Median :0.00000  
##  Mean   :0.002234   Mean   :0.0024   Mean   :0.02499   Mean   :0.03542  
##  3rd Qu.:0.000000   3rd Qu.:0.0000   3rd Qu.:0.00000   3rd Qu.:0.00000  
##  Max.   :1.000000   Max.   :1.0000   Max.   :1.00000   Max.   :1.00000  
##                                                                         
##    ZTEMPNITE         ZMOISTURE          ZUSEMOISTURE      
##  Min.   :0.00000   Min.   :0.0000000   Min.   :0.0000000  
##  1st Qu.:0.00000   1st Qu.:0.0000000   1st Qu.:0.0000000  
##  Median :0.00000   Median :0.0000000   Median :0.0000000  
##  Mean   :0.02797   Mean   :0.0007448   Mean   :0.0006621  
##  3rd Qu.:0.00000   3rd Qu.:0.0000000   3rd Qu.:0.0000000  
##  Max.   :1.00000   Max.   :1.0000000   Max.   :1.0000000  
##                                                           
##   NUMH2ONOTNK        NUMH2OHTRS       H2OTYPE1         FUELH2O      
##  Min.   :0.00000   Min.   :0.000   Min.   :-2.000   Min.   :-2.000  
##  1st Qu.:0.00000   1st Qu.:1.000   1st Qu.: 1.000   1st Qu.: 1.000  
##  Median :0.00000   Median :1.000   Median : 1.000   Median : 1.000  
##  Mean   :0.03269   Mean   :0.999   Mean   : 1.018   Mean   : 2.711  
##  3rd Qu.:0.00000   3rd Qu.:1.000   3rd Qu.: 1.000   3rd Qu.: 5.000  
##  Max.   :3.00000   Max.   :4.000   Max.   : 2.000   Max.   :21.000  
##                                                                     
##     WHEATOTH          WHEATSIZ         WHEATAGE        WHEATBKT       
##  Min.   :-2.0000   Min.   :-2.000   Min.   :-2.00   Min.   :-2.00000  
##  1st Qu.: 0.0000   1st Qu.: 2.000   1st Qu.: 2.00   1st Qu.: 0.00000  
##  Median : 0.0000   Median : 2.000   Median : 3.00   Median : 0.00000  
##  Mean   : 0.1049   Mean   : 2.081   Mean   :13.23   Mean   : 0.07374  
##  3rd Qu.: 0.0000   3rd Qu.: 3.000   3rd Qu.:41.00   3rd Qu.: 0.00000  
##  Max.   : 1.0000   Max.   : 3.000   Max.   :42.00   Max.   : 1.00000  
##                                                                       
##      HELPWH          HELPWHY          H2OTYPE2         FUELH2O2    
##  Min.   :-9.000   Min.   :-9.000   Min.   :-2.000   Min.   :-2.00  
##  1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.00  
##  Median :-2.000   Median :-2.000   Median :-2.000   Median :-2.00  
##  Mean   :-1.895   Mean   :-1.986   Mean   :-1.898   Mean   :-1.83  
##  3rd Qu.:-2.000   3rd Qu.:-2.000   3rd Qu.:-2.000   3rd Qu.:-2.00  
##  Max.   : 5.000   Max.   : 6.000   Max.   : 2.000   Max.   :21.00  
##                                                                    
##    WHEATSIZ2       WHEATAGE2       ZNUMH2OHTRS       ZNUMH2ONOTNK   
##  Min.   :-2.00   Min.   :-2.000   Min.   :0.00000   Min.   :0.0000  
##  1st Qu.:-2.00   1st Qu.:-2.000   1st Qu.:0.00000   1st Qu.:0.0000  
##  Median :-2.00   Median :-2.000   Median :0.00000   Median :0.0000  
##  Mean   :-1.89   Mean   :-1.539   Mean   :0.01812   Mean   :0.0163  
##  3rd Qu.:-2.00   3rd Qu.:-2.000   3rd Qu.:0.00000   3rd Qu.:0.0000  
##  Max.   : 3.00   Max.   :42.000   Max.   :1.00000   Max.   :1.0000  
##                                                                     
##    ZH2OTYPE1            ZFUELH2O         ZWHEATOTH         ZWHEATSIZ      
##  Min.   :0.0000000   Min.   :0.00000   Min.   :0.00000   Min.   :0.00000  
##  1st Qu.:0.0000000   1st Qu.:0.00000   1st Qu.:0.00000   1st Qu.:0.00000  
##  Median :0.0000000   Median :0.00000   Median :0.00000   Median :0.00000  
##  Mean   :0.0006621   Mean   :0.06753   Mean   :0.02259   Mean   :0.07341  
##  3rd Qu.:0.0000000   3rd Qu.:0.00000   3rd Qu.:0.00000   3rd Qu.:0.00000  
##  Max.   :1.0000000   Max.   :1.00000   Max.   :1.00000   Max.   :1.00000  
##                                                                           
##    ZWHEATAGE        ZWHEATBKT        ZH2OTYPE2   ZFUELH2O2       
##  Min.   :0.0000   Min.   :0.0000   Min.   :0   Min.   :0.000000  
##  1st Qu.:0.0000   1st Qu.:0.0000   1st Qu.:0   1st Qu.:0.000000  
##  Median :0.0000   Median :0.0000   Median :0   Median :0.000000  
##  Mean   :0.1241   Mean   :0.1148   Mean   :0   Mean   :0.001241  
##  3rd Qu.:0.0000   3rd Qu.:0.0000   3rd Qu.:0   3rd Qu.:0.000000  
##  Max.   :1.0000   Max.   :1.0000   Max.   :0   Max.   :1.000000  
##                                                                  
##    ZWHEATSIZ2         ZWHEATAGE2          AIRCOND           DNTAC       
##  Min.   :0.000000   Min.   :0.000000   Min.   :0.0000   Min.   :-2.000  
##  1st Qu.:0.000000   1st Qu.:0.000000   1st Qu.:1.0000   1st Qu.:-2.000  
##  Median :0.000000   Median :0.000000   Median :1.0000   Median :-2.000  
##  Mean   :0.002152   Mean   :0.002897   Mean   :0.8226   Mean   :-1.334  
##  3rd Qu.:0.000000   3rd Qu.:0.000000   3rd Qu.:1.0000   3rd Qu.:-2.000  
##  Max.   :1.000000   Max.   :1.000000   Max.   :1.0000   Max.   : 2.000  
##                                                                         
##   COOLTYPENOAC       COOLTYPE           DUCTS           CENACHP       
##  Min.   :-2.000   Min.   :-2.0000   Min.   :-2.000   Min.   :-2.0000  
##  1st Qu.:-2.000   1st Qu.: 1.0000   1st Qu.:-2.000   1st Qu.:-2.0000  
##  Median :-2.000   Median : 1.0000   Median :-2.000   Median : 0.0000  
##  Mean   :-1.843   Mean   : 0.7005   Mean   :-1.892   Mean   :-0.6588  
##  3rd Qu.:-2.000   3rd Qu.: 1.0000   3rd Qu.:-2.000   3rd Qu.: 0.0000  
##  Max.   : 3.000   Max.   : 3.0000   Max.   : 1.000   Max.   : 1.0000  
##                                                                       
##     ACOTHERS          MAINTAC           AGECENAC        REPLCCAC     
##  Min.   :-2.0000   Min.   :-2.0000   Min.   :-2.00   Min.   :-9.000  
##  1st Qu.:-2.0000   1st Qu.:-2.0000   1st Qu.:-2.00   1st Qu.:-2.000  
##  Median : 0.0000   Median : 0.0000   Median : 2.00   Median :-2.000  
##  Mean   :-0.7529   Mean   :-0.5124   Mean   : 8.46   Mean   :-1.689  
##  3rd Qu.: 0.0000   3rd Qu.: 1.0000   3rd Qu.: 5.00   3rd Qu.:-2.000  
##  Max.   : 1.0000   Max.   : 1.0000   Max.   :42.00   Max.   : 1.000  
##                                                                      
##     HELPCAC          HELPCACY       ACROOMS         USECENAC      
##  Min.   :-9.000   Min.   :-9.0   Min.   :-2.00   Min.   :-2.0000  
##  1st Qu.:-2.000   1st Qu.:-2.0   1st Qu.:-2.00   1st Qu.:-2.0000  
##  Median :-2.000   Median :-2.0   Median : 4.00   Median : 1.0000  
##  Mean   :-1.406   Mean   :-1.9   Mean   : 2.93   Mean   : 0.6051  
##  3rd Qu.: 0.000   3rd Qu.:-2.0   3rd Qu.: 6.00   3rd Qu.: 3.0000  
##  Max.   : 5.000   Max.   : 6.0   Max.   :23.00   Max.   : 3.0000  
##                                                                   
##    THERMAINAC        PROTHERMAC       AUTOCOOLNITE     AUTOCOOLDAY    
##  Min.   :-2.0000   Min.   :-2.0000   Min.   :-2.000   Min.   :-2.000  
##  1st Qu.:-2.0000   1st Qu.:-2.0000   1st Qu.:-2.000   1st Qu.:-2.000  
##  Median : 1.0000   Median : 0.0000   Median :-2.000   Median :-2.000  
##  Mean   :-0.1658   Mean   :-0.4903   Mean   :-1.212   Mean   :-1.213  
##  3rd Qu.: 1.0000   3rd Qu.: 1.0000   3rd Qu.: 0.000   3rd Qu.: 0.000  
##  Max.   : 1.0000   Max.   : 1.0000   Max.   : 1.000   Max.   : 1.000  
##                                                                       
##    TEMPHOMEAC     TEMPGONEAC      TEMPNITEAC       NUMBERAC     
##  Min.   :-2.0   Min.   :-2.00   Min.   :-2.00   Min.   :-2.000  
##  1st Qu.:-2.0   1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.000  
##  Median :-2.0   Median :-2.00   Median :-2.00   Median :-2.000  
##  Mean   :31.2   Mean   :32.05   Mean   :31.11   Mean   :-1.162  
##  3rd Qu.:72.0   3rd Qu.:75.00   3rd Qu.:72.00   3rd Qu.:-2.000  
##  Max.   :88.0   Max.   :96.00   Max.   :96.00   Max.   : 9.000  
##                                                                 
##     WWACAGE            ESWWAC        REPLCWWAC         HELPWWAC     
##  Min.   :-2.0000   Min.   :-9.00   Min.   :-9.000   Min.   :-9.000  
##  1st Qu.:-2.0000   1st Qu.:-2.00   1st Qu.:-2.000   1st Qu.:-2.000  
##  Median :-2.0000   Median :-2.00   Median :-2.000   Median :-2.000  
##  Mean   : 0.3709   Mean   :-1.71   Mean   :-1.772   Mean   :-1.841  
##  3rd Qu.:-2.0000   3rd Qu.:-2.00   3rd Qu.:-2.000   3rd Qu.:-2.000  
##  Max.   :42.0000   Max.   : 1.00   Max.   : 1.000   Max.   : 5.000  
##                                                                     
##    HELPWWACY         USEWWAC          NUMCFAN          USECFAN       
##  Min.   :-9.000   Min.   :-2.000   Min.   : 0.000   Min.   :-2.0000  
##  1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.: 0.000   1st Qu.:-2.0000  
##  Median :-2.000   Median :-2.000   Median : 2.000   Median : 1.0000  
##  Mean   :-1.994   Mean   :-1.195   Mean   : 2.116   Mean   : 0.9992  
##  3rd Qu.:-2.000   3rd Qu.:-2.000   3rd Qu.: 3.000   3rd Qu.: 3.0000  
##  Max.   : 4.000   Max.   : 3.000   Max.   :15.000   Max.   : 4.0000  
##                                                                      
##     TREESHAD         NOTMOIST       USENOTMOIST        ZAIRCOND       
##  Min.   :0.0000   Min.   :0.0000   Min.   :-2.000   Min.   :0.000000  
##  1st Qu.:0.0000   1st Qu.:0.0000   1st Qu.:-2.000   1st Qu.:0.000000  
##  Median :0.0000   Median :0.0000   Median :-2.000   Median :0.000000  
##  Mean   :0.4474   Mean   :0.1342   Mean   :-1.444   Mean   :0.001986  
##  3rd Qu.:1.0000   3rd Qu.:0.0000   3rd Qu.:-2.000   3rd Qu.:0.000000  
##  Max.   :1.0000   Max.   :1.0000   Max.   : 5.000   Max.   :1.000000  
##                                                                       
##      ZDNTAC          ZCOOLTYPENOAC         ZCOOLTYPE       
##  Min.   :0.0000000   Min.   :0.0000000   Min.   :0.000000  
##  1st Qu.:0.0000000   1st Qu.:0.0000000   1st Qu.:0.000000  
##  Median :0.0000000   Median :0.0000000   Median :0.000000  
##  Mean   :0.0004966   Mean   :0.0002483   Mean   :0.001904  
##  3rd Qu.:0.0000000   3rd Qu.:0.0000000   3rd Qu.:0.000000  
##  Max.   :1.0000000   Max.   :1.0000000   Max.   :1.000000  
##                                                            
##      ZDUCTS           ZCENACHP         ZACOTHERS           ZMAINTAC       
##  Min.   :0.00000   Min.   :0.00000   Min.   :0.000000   Min.   :0.000000  
##  1st Qu.:0.00000   1st Qu.:0.00000   1st Qu.:0.000000   1st Qu.:0.000000  
##  Median :0.00000   Median :0.00000   Median :0.000000   Median :0.000000  
##  Mean   :0.01266   Mean   :0.04635   Mean   :0.002731   Mean   :0.009021  
##  3rd Qu.:0.00000   3rd Qu.:0.00000   3rd Qu.:0.000000   3rd Qu.:0.000000  
##  Max.   :1.00000   Max.   :1.00000   Max.   :1.000000   Max.   :1.000000  
##                                                                           
##    ZAGECENAC         ZUSECENAC          ZACROOMS         ZTHERMAINAC      
##  Min.   :0.00000   Min.   :0.00000   Min.   :0.000000   Min.   :0.000000  
##  1st Qu.:0.00000   1st Qu.:0.00000   1st Qu.:0.000000   1st Qu.:0.000000  
##  Median :0.00000   Median :0.00000   Median :0.000000   Median :0.000000  
##  Mean   :0.03716   Mean   :0.01068   Mean   :0.009931   Mean   :0.002069  
##  3rd Qu.:0.00000   3rd Qu.:0.00000   3rd Qu.:0.000000   3rd Qu.:0.000000  
##  Max.   :1.00000   Max.   :1.00000   Max.   :1.000000   Max.   :1.000000  
##                                                                           
##   ZPROTHERMAC       ZAUTOCOOLNITE       ZAUTOCOOLDAY       ZTEMPHOMEAC    
##  Min.   :0.000000   Min.   :0.000000   Min.   :0.000000   Min.   :0.0000  
##  1st Qu.:0.000000   1st Qu.:0.000000   1st Qu.:0.000000   1st Qu.:0.0000  
##  Median :0.000000   Median :0.000000   Median :0.000000   Median :0.0000  
##  Mean   :0.003559   Mean   :0.002648   Mean   :0.002566   Mean   :0.0101  
##  3rd Qu.:0.000000   3rd Qu.:0.000000   3rd Qu.:0.000000   3rd Qu.:0.0000  
##  Max.   :1.000000   Max.   :1.000000   Max.   :1.000000   Max.   :1.0000  
##                                                                           
##   ZTEMPGONEAC       ZTEMPNITEAC      ZNUMBERAC           ZWWACAGE      
##  Min.   :0.00000   Min.   :0.000   Min.   :0.000000   Min.   :0.00000  
##  1st Qu.:0.00000   1st Qu.:0.000   1st Qu.:0.000000   1st Qu.:0.00000  
##  Median :0.00000   Median :0.000   Median :0.000000   Median :0.00000  
##  Mean   :0.01324   Mean   :0.012   Mean   :0.000331   Mean   :0.01035  
##  3rd Qu.:0.00000   3rd Qu.:0.000   3rd Qu.:0.000000   3rd Qu.:0.00000  
##  Max.   :1.00000   Max.   :1.000   Max.   :1.000000   Max.   :1.00000  
##                                                                        
##     ZUSEWWAC           ZNUMCFAN            ZUSECFAN     
##  Min.   :0.000000   Min.   :0.0000000   Min.   :0.0000  
##  1st Qu.:0.000000   1st Qu.:0.0000000   1st Qu.:0.0000  
##  Median :0.000000   Median :0.0000000   Median :0.0000  
##  Mean   :0.004138   Mean   :0.0006621   Mean   :0.0115  
##  3rd Qu.:0.000000   3rd Qu.:0.0000000   3rd Qu.:0.0000  
##  Max.   :1.000000   Max.   :1.0000000   Max.   :1.0000  
##                                                         
##    ZTREESHAD          ZNOTMOIST         ZUSENOTMOIST      
##  Min.   :0.000000   Min.   :0.000000   Min.   :0.0000000  
##  1st Qu.:0.000000   1st Qu.:0.000000   1st Qu.:0.0000000  
##  Median :0.000000   Median :0.000000   Median :0.0000000  
##  Mean   :0.000331   Mean   :0.001159   Mean   :0.0008276  
##  3rd Qu.:0.000000   3rd Qu.:0.000000   3rd Qu.:0.0000000  
##  Max.   :1.000000   Max.   :1.000000   Max.   :1.0000000  
##                                                           
##     HIGHCEIL         CATHCEIL         SWIMPOOL            POOL       
##  Min.   :-2.000   Min.   :-2.000   Min.   :-2.0000   Min.   :-2.000  
##  1st Qu.: 0.000   1st Qu.:-2.000   1st Qu.:-2.0000   1st Qu.:-2.000  
##  Median : 0.000   Median :-2.000   Median : 0.0000   Median :-2.000  
##  Mean   : 0.194   Mean   :-1.262   Mean   :-0.4869   Mean   :-1.832  
##  3rd Qu.: 1.000   3rd Qu.: 0.000   3rd Qu.: 0.0000   3rd Qu.:-2.000  
##  Max.   : 1.000   Max.   : 1.000   Max.   : 1.0000   Max.   : 1.000  
##                                                                      
##     FUELPOOL         RECBATH           FUELTUB           LGT12        
##  Min.   :-2.000   Min.   :0.00000   Min.   :-2.000   Min.   : 0.0000  
##  1st Qu.:-2.000   1st Qu.:0.00000   1st Qu.:-2.000   1st Qu.: 0.0000  
##  Median :-2.000   Median :0.00000   Median :-2.000   Median : 0.0000  
##  Mean   :-1.899   Mean   :0.05744   Mean   :-1.654   Mean   : 0.4418  
##  3rd Qu.:-2.000   3rd Qu.:0.00000   3rd Qu.:-2.000   3rd Qu.: 0.0000  
##  Max.   :21.000   Max.   :1.00000   Max.   :21.000   Max.   :40.0000  
##                                                                       
##     LGT12EE            LGT4            LGT4EE             LGT1       
##  Min.   :-9.000   Min.   : 0.000   Min.   :-9.0000   Min.   : 0.000  
##  1st Qu.:-2.000   1st Qu.: 0.000   1st Qu.:-2.0000   1st Qu.: 1.000  
##  Median :-2.000   Median : 1.000   Median : 0.0000   Median : 2.000  
##  Mean   :-1.345   Mean   : 1.712   Mean   : 0.1146   Mean   : 2.396  
##  3rd Qu.:-2.000   3rd Qu.: 2.000   3rd Qu.: 1.0000   3rd Qu.: 3.000  
##  Max.   :15.000   Max.   :30.000   Max.   :30.0000   Max.   :40.000  
##                                                                      
##      LGT1EE          NOUTLGTNT           LGTOEE         NGASLIGHT     
##  Min.   :-9.0000   Min.   :-2.0000   Min.   :-9.000   Min.   :-2.000  
##  1st Qu.: 0.0000   1st Qu.:-2.0000   1st Qu.:-2.000   1st Qu.:-2.000  
##  Median : 0.0000   Median : 0.0000   Median :-2.000   Median :-2.000  
##  Mean   : 0.8155   Mean   :-0.1512   Mean   :-1.358   Mean   :-1.528  
##  3rd Qu.: 2.0000   3rd Qu.: 0.0000   3rd Qu.:-2.000   3rd Qu.:-2.000  
##  Max.   :40.0000   Max.   :15.0000   Max.   :15.000   Max.   : 2.000  
##                                                                       
##     INSTLCFL          HELPCFL           HELPCFLY          SLDDRS      
##  Min.   :-9.0000   Min.   :-9.0000   Min.   :-9.000   Min.   :0.0000  
##  1st Qu.:-2.0000   1st Qu.:-2.0000   1st Qu.:-2.000   1st Qu.:0.0000  
##  Median : 1.0000   Median : 0.0000   Median :-2.000   Median :0.0000  
##  Mean   :-0.2306   Mean   :-0.8498   Mean   :-1.818   Mean   :0.3627  
##  3rd Qu.: 1.0000   3rd Qu.: 0.0000   3rd Qu.:-2.000   3rd Qu.:1.0000  
##  Max.   : 1.0000   Max.   : 5.0000   Max.   : 6.000   Max.   :1.0000  
##                                                                       
##     DOOR1SUM         WINDOWS        TYPEGLASS         NEWGLASS     
##  Min.   :-9.000   Min.   : 0.00   Min.   :-2.000   Min.   :-2.000  
##  1st Qu.: 0.000   1st Qu.:30.00   1st Qu.: 1.000   1st Qu.: 2.000  
##  Median : 0.000   Median :41.00   Median : 2.000   Median : 3.000  
##  Mean   : 0.488   Mean   :36.32   Mean   : 1.572   Mean   : 2.518  
##  3rd Qu.: 1.000   3rd Qu.:42.00   3rd Qu.: 2.000   3rd Qu.: 3.000  
##  Max.   :10.000   Max.   :60.00   Max.   : 3.000   Max.   : 3.000  
##                                                                    
##     HELPWIN          HELPWINY         ADQINSUL        INSTLINS     
##  Min.   :-9.000   Min.   :-9.000   Min.   :1.000   Min.   :0.0000  
##  1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:1.000   1st Qu.:0.0000  
##  Median :-2.000   Median :-2.000   Median :2.000   Median :0.0000  
##  Mean   :-1.339   Mean   :-1.844   Mean   :1.855   Mean   :0.2247  
##  3rd Qu.: 0.000   3rd Qu.:-2.000   3rd Qu.:2.000   3rd Qu.:0.0000  
##  Max.   : 5.000   Max.   : 6.000   Max.   :4.000   Max.   :1.0000  
##                                                                    
##      AGEINS           HELPINS         HELPINSY          DRAFTY     
##  Min.   :-2.0000   Min.   :-9.00   Min.   :-9.000   Min.   :1.000  
##  1st Qu.:-2.0000   1st Qu.:-2.00   1st Qu.:-2.000   1st Qu.:3.000  
##  Median :-2.0000   Median :-2.00   Median :-2.000   Median :4.000  
##  Mean   : 0.9855   Mean   :-1.78   Mean   :-1.922   Mean   :3.308  
##  3rd Qu.:-2.0000   3rd Qu.:-2.00   3rd Qu.:-2.000   3rd Qu.:4.000  
##  Max.   :42.0000   Max.   : 5.00   Max.   : 5.000   Max.   :4.000  
##                                                                    
##     INSTLWS           AGEWS            HELPWS          HELPWSY      
##  Min.   :0.0000   Min.   :-2.000   Min.   :-9.000   Min.   :-2.000  
##  1st Qu.:0.0000   1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.000  
##  Median :0.0000   Median :-2.000   Median :-2.000   Median :-2.000  
##  Mean   :0.3593   Mean   : 0.681   Mean   :-1.493   Mean   :-1.946  
##  3rd Qu.:1.0000   3rd Qu.: 1.000   3rd Qu.: 0.000   3rd Qu.:-2.000  
##  Max.   :1.0000   Max.   :42.000   Max.   : 5.000   Max.   : 6.000  
##                                                                     
##      AUDIT             AGEAUD          HELPAUD          HELPAUDY    
##  Min.   :0.00000   Min.   :-2.000   Min.   :-9.000   Min.   :-9.00  
##  1st Qu.:0.00000   1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.00  
##  Median :0.00000   Median :-2.000   Median :-2.000   Median :-2.00  
##  Mean   :0.04875   Mean   :-1.427   Mean   :-1.927   Mean   :-1.95  
##  3rd Qu.:0.00000   3rd Qu.:-2.000   3rd Qu.:-2.000   3rd Qu.:-2.00  
##  Max.   :1.00000   Max.   :42.000   Max.   : 5.000   Max.   : 6.00  
##                                                                     
##    ZHIGHCEIL           ZCATHCEIL           ZSWIMPOOL       
##  Min.   :0.0000000   Min.   :0.0000000   Min.   :0.000000  
##  1st Qu.:0.0000000   1st Qu.:0.0000000   1st Qu.:0.000000  
##  Median :0.0000000   Median :0.0000000   Median :0.000000  
##  Mean   :0.0001655   Mean   :0.0006621   Mean   :0.001738  
##  3rd Qu.:0.0000000   3rd Qu.:0.0000000   3rd Qu.:0.000000  
##  Max.   :1.0000000   Max.   :1.0000000   Max.   :1.000000  
##                                                            
##      ZPOOL            ZFUELPOOL           ZRECBATH       
##  Min.   :0.00e+00   Min.   :0.000000   Min.   :0.00e+00  
##  1st Qu.:0.00e+00   1st Qu.:0.000000   1st Qu.:0.00e+00  
##  Median :0.00e+00   Median :0.000000   Median :0.00e+00  
##  Mean   :8.28e-05   Mean   :0.000331   Mean   :8.28e-05  
##  3rd Qu.:0.00e+00   3rd Qu.:0.000000   3rd Qu.:0.00e+00  
##  Max.   :1.00e+00   Max.   :1.000000   Max.   :1.00e+00  
##                                                          
##     ZFUELTUB             ZLGT12             ZLGT4         
##  Min.   :0.0000000   Min.   :0.000000   Min.   :0.000000  
##  1st Qu.:0.0000000   1st Qu.:0.000000   1st Qu.:0.000000  
##  Median :0.0000000   Median :0.000000   Median :0.000000  
##  Mean   :0.0006621   Mean   :0.003807   Mean   :0.004717  
##  3rd Qu.:0.0000000   3rd Qu.:0.000000   3rd Qu.:0.000000  
##  Max.   :1.0000000   Max.   :1.000000   Max.   :1.000000  
##                                                           
##      ZLGT1            ZNOUTLGTNT         ZNGASLIGHT      
##  Min.   :0.000000   Min.   :0.000000   Min.   :0.000000  
##  1st Qu.:0.000000   1st Qu.:0.000000   1st Qu.:0.000000  
##  Median :0.000000   Median :0.000000   Median :0.000000  
##  Mean   :0.006207   Mean   :0.002731   Mean   :0.001324  
##  3rd Qu.:0.000000   3rd Qu.:0.000000   3rd Qu.:0.000000  
##  Max.   :1.000000   Max.   :1.000000   Max.   :1.000000  
##                                                          
##     ZSLDDRS            ZDOOR1SUM            ZWINDOWS        
##  Min.   :0.0000000   Min.   :0.0000000   Min.   :0.0000000  
##  1st Qu.:0.0000000   1st Qu.:0.0000000   1st Qu.:0.0000000  
##  Median :0.0000000   Median :0.0000000   Median :0.0000000  
##  Mean   :0.0001655   Mean   :0.0005793   Mean   :0.0009931  
##  3rd Qu.:0.0000000   3rd Qu.:0.0000000   3rd Qu.:0.0000000  
##  Max.   :1.0000000   Max.   :1.0000000   Max.   :1.0000000  
##                                                             
##    ZTYPEGLASS       ZNEWGLASS          ZADQINSUL          ZINSTLINS       
##  Min.   :0.0000   Min.   :0.000000   Min.   :0.000000   Min.   :0.000000  
##  1st Qu.:0.0000   1st Qu.:0.000000   1st Qu.:0.000000   1st Qu.:0.000000  
##  Median :0.0000   Median :0.000000   Median :0.000000   Median :0.000000  
##  Mean   :0.0096   Mean   :0.001904   Mean   :0.005876   Mean   :0.007449  
##  3rd Qu.:0.0000   3rd Qu.:0.000000   3rd Qu.:0.000000   3rd Qu.:0.000000  
##  Max.   :1.0000   Max.   :1.000000   Max.   :1.000000   Max.   :1.000000  
##                                                                           
##     ZAGEINS            ZDRAFTY             ZINSTLWS       
##  Min.   :0.000000   Min.   :0.0000000   Min.   :0.000000  
##  1st Qu.:0.000000   1st Qu.:0.0000000   1st Qu.:0.000000  
##  Median :0.000000   Median :0.0000000   Median :0.000000  
##  Mean   :0.002234   Mean   :0.0006621   Mean   :0.004966  
##  3rd Qu.:0.000000   3rd Qu.:0.0000000   3rd Qu.:0.000000  
##  Max.   :1.000000   Max.   :1.0000000   Max.   :1.000000  
##                                                           
##      ZAGEWS             ZAUDIT            ZAGEAUD              USEEL  
##  Min.   :0.000000   Min.   :0.000000   Min.   :0.0000000   Min.   :1  
##  1st Qu.:0.000000   1st Qu.:0.000000   1st Qu.:0.0000000   1st Qu.:1  
##  Median :0.000000   Median :0.000000   Median :0.0000000   Median :1  
##  Mean   :0.003724   Mean   :0.002648   Mean   :0.0004138   Mean   :1  
##  3rd Qu.:0.000000   3rd Qu.:0.000000   3rd Qu.:0.0000000   3rd Qu.:1  
##  Max.   :1.000000   Max.   :1.000000   Max.   :1.0000000   Max.   :1  
##                                                                       
##      USENG            USELP            USEFO            USEKERO       
##  Min.   :0.0000   Min.   :0.0000   Min.   :0.00000   Min.   :0.00000  
##  1st Qu.:0.0000   1st Qu.:0.0000   1st Qu.:0.00000   1st Qu.:0.00000  
##  Median :1.0000   Median :0.0000   Median :0.00000   Median :0.00000  
##  Mean   :0.6202   Mean   :0.4321   Mean   :0.07482   Mean   :0.01374  
##  3rd Qu.:1.0000   3rd Qu.:1.0000   3rd Qu.:0.00000   3rd Qu.:0.00000  
##  Max.   :1.0000   Max.   :1.0000   Max.   :1.00000   Max.   :1.00000  
##                                                                       
##     USEWOOD          USESOLAR           USEOTH           ELWARM      
##  Min.   :0.0000   Min.   :0.00000   Min.   :0.0000   Min.   :0.0000  
##  1st Qu.:0.0000   1st Qu.:0.00000   1st Qu.:0.0000   1st Qu.:0.0000  
##  Median :0.0000   Median :0.00000   Median :0.0000   Median :1.0000  
##  Mean   :0.1187   Mean   :0.01217   Mean   :0.2045   Mean   :0.5093  
##  3rd Qu.:0.0000   3rd Qu.:0.00000   3rd Qu.:0.0000   3rd Qu.:1.0000  
##  Max.   :1.0000   Max.   :1.00000   Max.   :1.0000   Max.   :1.0000  
##                                                                      
##     ELECAUX           ELCOOL          ELWATER           ELFOOD      
##  Min.   :0.0000   Min.   :0.0000   Min.   :0.0000   Min.   :0.0000  
##  1st Qu.:0.0000   1st Qu.:1.0000   1st Qu.:0.0000   1st Qu.:0.0000  
##  Median :0.0000   Median :1.0000   Median :0.0000   Median :1.0000  
##  Mean   :0.2354   Mean   :0.8226   Mean   :0.3983   Mean   :0.6369  
##  3rd Qu.:0.0000   3rd Qu.:1.0000   3rd Qu.:1.0000   3rd Qu.:1.0000  
##  Max.   :1.0000   Max.   :1.0000   Max.   :1.0000   Max.   :1.0000  
##                                                                     
##     ELOTHER           UGWARM          UGASAUX           UGWATER      
##  Min.   :0.0000   Min.   :0.0000   Min.   :0.00000   Min.   :0.0000  
##  1st Qu.:1.0000   1st Qu.:0.0000   1st Qu.:0.00000   1st Qu.:0.0000  
##  Median :1.0000   Median :1.0000   Median :0.00000   Median :1.0000  
##  Mean   :0.9999   Mean   :0.5038   Mean   :0.06712   Mean   :0.5287  
##  3rd Qu.:1.0000   3rd Qu.:1.0000   3rd Qu.:0.00000   3rd Qu.:1.0000  
##  Max.   :1.0000   Max.   :1.0000   Max.   :1.00000   Max.   :1.0000  
##                                                                      
##      UGCOOK           UGOTH            LPWARM            LPGAUX       
##  Min.   :0.0000   Min.   :0.0000   Min.   :0.00000   Min.   :0.00000  
##  1st Qu.:0.0000   1st Qu.:0.0000   1st Qu.:0.00000   1st Qu.:0.00000  
##  Median :0.0000   Median :0.0000   Median :0.00000   Median :0.00000  
##  Mean   :0.3478   Mean   :0.1938   Mean   :0.05901   Mean   :0.02235  
##  3rd Qu.:1.0000   3rd Qu.:0.0000   3rd Qu.:0.00000   3rd Qu.:0.00000  
##  Max.   :1.0000   Max.   :1.0000   Max.   :1.00000   Max.   :1.00000  
##                                                                       
##     LPWATER           LPCOOK           LPOTHER           FOWARM       
##  Min.   :0.0000   Min.   :0.00000   Min.   :0.0000   Min.   :0.00000  
##  1st Qu.:0.0000   1st Qu.:0.00000   1st Qu.:0.0000   1st Qu.:0.00000  
##  Median :0.0000   Median :0.00000   Median :0.0000   Median :0.00000  
##  Mean   :0.0336   Mean   :0.04121   Mean   :0.3949   Mean   :0.07109  
##  3rd Qu.:0.0000   3rd Qu.:0.00000   3rd Qu.:1.0000   3rd Qu.:0.00000  
##  Max.   :1.0000   Max.   :1.00000   Max.   :1.0000   Max.   :1.00000  
##                                                                       
##     FOILAUX            FOWATER          FOOTHER             KRWARM       
##  Min.   :0.000000   Min.   :0.0000   Min.   :0.000000   Min.   :0.00000  
##  1st Qu.:0.000000   1st Qu.:0.0000   1st Qu.:0.000000   1st Qu.:0.00000  
##  Median :0.000000   Median :0.0000   Median :0.000000   Median :0.00000  
##  Mean   :0.004386   Mean   :0.0384   Mean   :0.001738   Mean   :0.01051  
##  3rd Qu.:0.000000   3rd Qu.:0.0000   3rd Qu.:0.000000   3rd Qu.:0.00000  
##  Max.   :1.000000   Max.   :1.0000   Max.   :1.000000   Max.   :1.00000  
##                                                                          
##     KEROAUX           KRWATER             KROTHER             WDWARM      
##  Min.   :0.00000   Min.   :0.0000000   Min.   :0.000000   Min.   :0.0000  
##  1st Qu.:0.00000   1st Qu.:0.0000000   1st Qu.:0.000000   1st Qu.:0.0000  
##  Median :0.00000   Median :0.0000000   Median :0.000000   Median :0.0000  
##  Mean   :0.00629   Mean   :0.0002483   Mean   :0.003145   Mean   :0.1045  
##  3rd Qu.:0.00000   3rd Qu.:0.0000000   3rd Qu.:0.000000   3rd Qu.:0.0000  
##  Max.   :1.00000   Max.   :1.0000000   Max.   :1.000000   Max.   :1.0000  
##                                                                           
##     WOODAUX           WDWATER             WDOTHUSE      
##  Min.   :0.00000   Min.   :0.0000000   Min.   :0.00000  
##  1st Qu.:0.00000   1st Qu.:0.0000000   1st Qu.:0.00000  
##  Median :0.00000   Median :0.0000000   Median :0.00000  
##  Mean   :0.08111   Mean   :0.0009931   Mean   :0.01523  
##  3rd Qu.:0.00000   3rd Qu.:0.0000000   3rd Qu.:0.00000  
##  Max.   :1.00000   Max.   :1.0000000   Max.   :1.00000  
##                                                         
##     SOLWARM            SOLARAUX            SOLWATER       
##  Min.   :0.000000   Min.   :0.0000000   Min.   :0.000000  
##  1st Qu.:0.000000   1st Qu.:0.0000000   1st Qu.:0.000000  
##  Median :0.000000   Median :0.0000000   Median :0.000000  
##  Mean   :0.000331   Mean   :0.0002483   Mean   :0.001821  
##  3rd Qu.:0.000000   3rd Qu.:0.0000000   3rd Qu.:0.000000  
##  Max.   :1.000000   Max.   :1.0000000   Max.   :1.000000  
##                                                           
##     SOLOTHER          OTHWARM            OTHERAUX       
##  Min.   :0.00000   Min.   :0.000000   Min.   :0.000000  
##  1st Qu.:0.00000   1st Qu.:0.000000   1st Qu.:0.000000  
##  Median :0.00000   Median :0.000000   Median :0.000000  
##  Mean   :0.01043   Mean   :0.008938   Mean   :0.005379  
##  3rd Qu.:0.00000   3rd Qu.:0.000000   3rd Qu.:0.000000  
##  Max.   :1.00000   Max.   :1.000000   Max.   :1.000000  
##                                                         
##     OTHWATER            OTHCOOK             ONSITE        
##  Min.   :0.0000000   Min.   :0.000000   Min.   :0.000000  
##  1st Qu.:0.0000000   1st Qu.:0.000000   1st Qu.:0.000000  
##  Median :0.0000000   Median :0.000000   Median :0.000000  
##  Mean   :0.0009931   Mean   :0.001572   Mean   :0.005876  
##  3rd Qu.:0.0000000   3rd Qu.:0.000000   3rd Qu.:0.000000  
##  Max.   :1.0000000   Max.   :1.000000   Max.   :1.000000  
##                                                           
##    ONSITEGRID        PELHEAT           PELHOTWA          PELCOOK        
##  Min.   :-2.000   Min.   :-2.0000   Min.   :-2.0000   Min.   :-2.00000  
##  1st Qu.:-2.000   1st Qu.:-2.0000   1st Qu.:-2.0000   1st Qu.:-2.00000  
##  Median :-2.000   Median : 1.0000   Median :-2.0000   Median : 1.00000  
##  Mean   :-1.986   Mean   :-0.4424   Mean   :-0.7813   Mean   :-0.05206  
##  3rd Qu.:-2.000   3rd Qu.: 1.0000   3rd Qu.: 1.0000   3rd Qu.: 1.00000  
##  Max.   : 1.000   Max.   : 3.0000   Max.   : 3.0000   Max.   : 3.00000  
##                                                                         
##      PELAC            PELLIGHT        OTHERWAYEL        PGASHEAT      
##  Min.   :-2.0000   Min.   :-2.000   Min.   :-2.000   Min.   :-2.0000  
##  1st Qu.:-2.0000   1st Qu.: 1.000   1st Qu.:-2.000   1st Qu.:-2.0000  
##  Median : 1.0000   Median : 1.000   Median :-2.000   Median : 1.0000  
##  Mean   :-0.1279   Mean   : 1.066   Mean   :-1.951   Mean   :-0.4384  
##  3rd Qu.: 1.0000   3rd Qu.: 1.000   3rd Qu.:-2.000   3rd Qu.: 1.0000  
##  Max.   : 3.0000   Max.   : 3.000   Max.   : 3.000   Max.   : 3.0000  
##                                                                       
##     PGASHTWA          PUGCOOK            PUGOTH         OTHERWAYNG    
##  Min.   :-2.0000   Min.   :-2.0000   Min.   :-9.000   Min.   :-2.000  
##  1st Qu.:-2.0000   1st Qu.:-2.0000   1st Qu.:-2.000   1st Qu.:-2.000  
##  Median : 1.0000   Median :-2.0000   Median :-2.000   Median :-2.000  
##  Mean   :-0.3525   Mean   :-0.9196   Mean   :-1.525   Mean   :-1.965  
##  3rd Qu.: 1.0000   3rd Qu.: 1.0000   3rd Qu.:-2.000   3rd Qu.:-2.000  
##  Max.   : 3.0000   Max.   : 3.0000   Max.   : 3.000   Max.   : 3.000  
##                                                                       
##      FOPAY          OTHERWAYFO         LPGPAY        OTHERWAYLPG   
##  Min.   :-2.000   Min.   :-2.000   Min.   :-2.000   Min.   :-2.00  
##  1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.00  
##  Median :-2.000   Median :-2.000   Median :-2.000   Median :-2.00  
##  Mean   :-1.759   Mean   :-1.992   Mean   :-1.286   Mean   :-1.99  
##  3rd Qu.:-2.000   3rd Qu.:-2.000   3rd Qu.:-2.000   3rd Qu.:-2.00  
##  Max.   : 3.000   Max.   : 3.000   Max.   : 3.000   Max.   : 3.00  
##                                                                    
##     LPGDELV          KERODEL          KEROCASH         NOCRCASH     
##  Min.   :-9.000   Min.   :-2.000   Min.   :-2.000   Min.   :-2.000  
##  1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.000  
##  Median :-2.000   Median :-2.000   Median :-2.000   Median :-2.000  
##  Mean   :-1.508   Mean   :-1.969   Mean   :-1.964   Mean   :-1.921  
##  3rd Qu.:-2.000   3rd Qu.:-2.000   3rd Qu.:-2.000   3rd Qu.:-2.000  
##  Max.   : 1.000   Max.   : 1.000   Max.   : 1.000   Max.   :55.000  
##                                                     NA's   :2       
##     NKRGALNC        WOODLOGS         WDSCRAP          WDPELLET     
##  Min.   :-2.00   Min.   :-2.000   Min.   :-2.000   Min.   :-2.000  
##  1st Qu.:-2.00   1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.000  
##  Median :-2.00   Median :-2.000   Median :-2.000   Median :-2.000  
##  Mean   :-1.93   Mean   :-1.659   Mean   :-1.754   Mean   :-1.754  
##  3rd Qu.:-2.00   3rd Qu.:-2.000   3rd Qu.:-2.000   3rd Qu.:-2.000  
##  Max.   :77.00   Max.   : 1.000   Max.   : 1.000   Max.   : 1.000  
##  NA's   :2                                                         
##     WDOTHER          WOODAMT          NUMCORDS         ZONSITE         
##  Min.   :-2.000   Min.   :-2.000   Min.   :-2.000   Min.   :0.0000000  
##  1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:0.0000000  
##  Median :-2.000   Median :-2.000   Median :-2.000   Median :0.0000000  
##  Mean   :-1.757   Mean   :-1.498   Mean   :-1.916   Mean   :0.0004966  
##  3rd Qu.:-2.000   3rd Qu.:-2.000   3rd Qu.:-2.000   3rd Qu.:0.0000000  
##  Max.   : 1.000   Max.   : 5.000   Max.   :30.000   Max.   :1.0000000  
##                                                                        
##   ZONSITEGRID           ZPELHEAT          ZPELHOTWA      
##  Min.   :0.0000000   Min.   :0.000000   Min.   :0.00000  
##  1st Qu.:0.0000000   1st Qu.:0.000000   1st Qu.:0.00000  
##  Median :0.0000000   Median :0.000000   Median :0.00000  
##  Mean   :0.0004138   Mean   :0.003642   Mean   :0.02326  
##  3rd Qu.:0.0000000   3rd Qu.:0.000000   3rd Qu.:0.00000  
##  Max.   :1.0000000   Max.   :1.000000   Max.   :1.00000  
##                                                          
##     ZPELCOOK            ZPELAC           ZPELLIGHT        
##  Min.   :0.000000   Min.   :0.000000   Min.   :0.0000000  
##  1st Qu.:0.000000   1st Qu.:0.000000   1st Qu.:0.0000000  
##  Median :0.000000   Median :0.000000   Median :0.0000000  
##  Mean   :0.001076   Mean   :0.001821   Mean   :0.0005793  
##  3rd Qu.:0.000000   3rd Qu.:0.000000   3rd Qu.:0.0000000  
##  Max.   :1.000000   Max.   :1.000000   Max.   :1.0000000  
##                                                           
##   ZOTHERWAYEL         ZPGASHEAT          ZPGASHTWA      
##  Min.   :0.000000   Min.   :0.000000   Min.   :0.00000  
##  1st Qu.:0.000000   1st Qu.:0.000000   1st Qu.:0.00000  
##  Median :0.000000   Median :0.000000   Median :0.00000  
##  Mean   :0.000331   Mean   :0.009104   Mean   :0.04155  
##  3rd Qu.:0.000000   3rd Qu.:0.000000   3rd Qu.:0.00000  
##  Max.   :1.000000   Max.   :1.000000   Max.   :1.00000  
##                                                         
##     ZPUGCOOK            ZPUGOTH          ZOTHERWAYNG       
##  Min.   :0.0000000   Min.   :0.000000   Min.   :0.0000000  
##  1st Qu.:0.0000000   1st Qu.:0.000000   1st Qu.:0.0000000  
##  Median :0.0000000   Median :0.000000   Median :0.0000000  
##  Mean   :0.0005793   Mean   :0.001076   Mean   :0.0007448  
##  3rd Qu.:0.0000000   3rd Qu.:0.000000   3rd Qu.:0.0000000  
##  Max.   :1.0000000   Max.   :1.000000   Max.   :1.0000000  
##                                                            
##      ZFOPAY          ZOTHERWAYFO    ZLPGPAY          ZOTHERWAYLPG     
##  Min.   :0.000000   Min.   :0    Min.   :0.000000   Min.   :0.00e+00  
##  1st Qu.:0.000000   1st Qu.:0    1st Qu.:0.000000   1st Qu.:0.00e+00  
##  Median :0.000000   Median :0    Median :0.000000   Median :0.00e+00  
##  Mean   :0.005214   Mean   :0    Mean   :0.003807   Mean   :8.28e-05  
##  3rd Qu.:0.000000   3rd Qu.:0    3rd Qu.:0.000000   3rd Qu.:0.00e+00  
##  Max.   :1.000000   Max.   :0    Max.   :1.000000   Max.   :1.00e+00  
##                                                                       
##     ZKERODEL           ZKEROCASH           ZNOCRCASH   ZNKRGALNC
##  Min.   :0.0000000   Min.   :0.0000000   Min.   :0   Min.   :0  
##  1st Qu.:0.0000000   1st Qu.:0.0000000   1st Qu.:0   1st Qu.:0  
##  Median :0.0000000   Median :0.0000000   Median :0   Median :0  
##  Mean   :0.0001655   Mean   :0.0001655   Mean   :0   Mean   :0  
##  3rd Qu.:0.0000000   3rd Qu.:0.0000000   3rd Qu.:0   3rd Qu.:0  
##  Max.   :1.0000000   Max.   :1.0000000   Max.   :0   Max.   :0  
##                                                                 
##    ZWOODLOGS           ZWDSCRAP          ZWDPELLET       
##  Min.   :0.000000   Min.   :0.000000   Min.   :0.000000  
##  1st Qu.:0.000000   1st Qu.:0.000000   1st Qu.:0.000000  
##  Median :0.000000   Median :0.000000   Median :0.000000  
##  Mean   :0.000331   Mean   :0.000331   Mean   :0.000331  
##  3rd Qu.:0.000000   3rd Qu.:0.000000   3rd Qu.:0.000000  
##  Max.   :1.000000   Max.   :1.000000   Max.   :1.000000  
##                                                          
##     ZWDOTHER           ZWOODAMT          ZNUMCORDS        
##  Min.   :0.000000   Min.   :0.000000   Min.   :0.0000000  
##  1st Qu.:0.000000   1st Qu.:0.000000   1st Qu.:0.0000000  
##  Median :0.000000   Median :0.000000   Median :0.0000000  
##  Mean   :0.000331   Mean   :0.005876   Mean   :0.0009104  
##  3rd Qu.:0.000000   3rd Qu.:0.000000   3rd Qu.:0.0000000  
##  Max.   :1.000000   Max.   :1.000000   Max.   :1.0000000  
##                                                           
##     KFUELOT            HHSEX         EMPLOYHH          SPOUSE      
##  Min.   :0.00000   Min.   :1.00   Min.   :0.0000   Min.   :0.0000  
##  1st Qu.:0.00000   1st Qu.:1.00   1st Qu.:0.0000   1st Qu.:0.0000  
##  Median :0.00000   Median :1.00   Median :1.0000   Median :1.0000  
##  Mean   :0.01134   Mean   :1.47   Mean   :0.7304   Mean   :0.5942  
##  3rd Qu.:0.00000   3rd Qu.:2.00   3rd Qu.:1.0000   3rd Qu.:1.0000  
##  Max.   :1.00000   Max.   :2.00   Max.   :2.0000   Max.   :1.0000  
##                                                                    
##     SDESCENT      Householder_Race   EDUCATION        NHSLDMEM     
##  Min.   :0.0000   Min.   :1.000    Min.   :0.000   Min.   : 1.000  
##  1st Qu.:0.0000   1st Qu.:1.000    1st Qu.:2.000   1st Qu.: 2.000  
##  Median :0.0000   Median :1.000    Median :3.000   Median : 2.000  
##  Mean   :0.1385   Mean   :1.442    Mean   :3.391   Mean   : 2.666  
##  3rd Qu.:0.0000   3rd Qu.:1.000    3rd Qu.:5.000   3rd Qu.: 4.000  
##  Max.   :1.0000   Max.   :7.000    Max.   :8.000   Max.   :14.000  
##                                                                    
##      HHAGE        AGEHHMEMCAT2     AGEHHMEMCAT3      AGEHHMEMCAT4    
##  Min.   :16.00   Min.   :-2.000   Min.   :-2.0000   Min.   :-2.0000  
##  1st Qu.:37.00   1st Qu.: 3.000   1st Qu.:-2.0000   1st Qu.:-2.0000  
##  Median :49.00   Median : 8.000   Median :-2.0000   Median :-2.0000  
##  Mean   :49.74   Mean   : 6.925   Mean   : 0.7683   Mean   :-0.6506  
##  3rd Qu.:62.00   3rd Qu.:11.000   3rd Qu.: 3.0000   3rd Qu.: 1.0000  
##  Max.   :85.00   Max.   :18.000   Max.   :18.0000   Max.   :14.0000  
##                                                                      
##   AGEHHMEMCAT5     AGEHHMEMCAT6     AGEHHMEMCAT7     AGEHHMEMCAT8   
##  Min.   :-2.000   Min.   :-2.000   Min.   :-2.000   Min.   :-2.000  
##  1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.000  
##  Median :-2.000   Median :-2.000   Median :-2.000   Median :-2.000  
##  Mean   :-1.457   Mean   :-1.791   Mean   :-1.921   Mean   :-1.968  
##  3rd Qu.:-2.000   3rd Qu.:-2.000   3rd Qu.:-2.000   3rd Qu.:-2.000  
##  Max.   :18.000   Max.   :16.000   Max.   :11.000   Max.   : 9.000  
##                                                                     
##   AGEHHMEMCAT9    AGEHHMEMCAT10    AGEHHMEMCAT11    AGEHHMEMCAT12   
##  Min.   :-2.000   Min.   :-2.000   Min.   :-2.000   Min.   :-2.000  
##  1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.000  
##  Median :-2.000   Median :-2.000   Median :-2.000   Median :-2.000  
##  Mean   :-1.986   Mean   :-1.993   Mean   :-1.996   Mean   :-1.998  
##  3rd Qu.:-2.000   3rd Qu.:-2.000   3rd Qu.:-2.000   3rd Qu.:-2.000  
##  Max.   : 8.000   Max.   : 8.000   Max.   : 4.000   Max.   : 2.000  
##                                                                     
##  AGEHHMEMCAT13    AGEHHMEMCAT14       HBUSNESS           ATHOME      
##  Min.   :-2.000   Min.   :-2.000   Min.   :0.00000   Min.   :0.0000  
##  1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:0.00000   1st Qu.:0.0000  
##  Median :-2.000   Median :-2.000   Median :0.00000   Median :1.0000  
##  Mean   :-1.999   Mean   :-1.999   Mean   :0.08516   Mean   :0.5695  
##  3rd Qu.:-2.000   3rd Qu.:-2.000   3rd Qu.:0.00000   3rd Qu.:1.0000  
##  Max.   : 2.000   Max.   : 1.000   Max.   :1.00000   Max.   :1.0000  
##                                                                      
##     TELLWORK         TELLDAYS          OTHWORK           WORKPAY      
##  Min.   :0.0000   Min.   :-2.0000   Min.   :0.00000   Min.   :0.0000  
##  1st Qu.:0.0000   1st Qu.:-2.0000   1st Qu.:0.00000   1st Qu.:1.0000  
##  Median :0.0000   Median :-2.0000   Median :0.00000   Median :1.0000  
##  Mean   :0.0869   Mean   :-0.9135   Mean   :0.01945   Mean   :0.7668  
##  3rd Qu.:0.0000   3rd Qu.:-2.0000   3rd Qu.:0.00000   3rd Qu.:1.0000  
##  Max.   :1.0000   Max.   :31.0000   Max.   :1.00000   Max.   :1.0000  
##                                                                       
##     RETIREPY         SSINCOME          CASHBEN           INVESTMT    
##  Min.   :0.0000   Min.   :0.00000   Min.   :0.00000   Min.   :0.000  
##  1st Qu.:0.0000   1st Qu.:0.00000   1st Qu.:0.00000   1st Qu.:0.000  
##  Median :0.0000   Median :0.00000   Median :0.00000   Median :0.000  
##  Mean   :0.2952   Mean   :0.07755   Mean   :0.02516   Mean   :0.228  
##  3rd Qu.:1.0000   3rd Qu.:0.00000   3rd Qu.:0.00000   3rd Qu.:0.000  
##  Max.   :1.0000   Max.   :1.00000   Max.   :1.00000   Max.   :1.000  
##                                                                      
##     RGLRPAY          MONEYPY        POVERTY100       POVERTY150    
##  Min.   :0.0000   Min.   : 1.00   Min.   :0.0000   Min.   :0.0000  
##  1st Qu.:0.0000   1st Qu.: 8.00   1st Qu.:0.0000   1st Qu.:0.0000  
##  Median :0.0000   Median :12.00   Median :0.0000   Median :0.0000  
##  Mean   :0.1513   Mean   :13.03   Mean   :0.1386   Mean   :0.2312  
##  3rd Qu.:0.0000   3rd Qu.:19.00   3rd Qu.:0.0000   3rd Qu.:0.0000  
##  Max.   :1.0000   Max.   :24.00   Max.   :1.0000   Max.   :1.0000  
##                                                                    
##      HUPROJ          RENTHELP         FOODASST          ZHHSEX        
##  Min.   :-2.000   Min.   :-2.000   Min.   :0.0000   Min.   :0.000000  
##  1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:0.0000   1st Qu.:0.000000  
##  Median :-2.000   Median :-2.000   Median :0.0000   Median :0.000000  
##  Mean   :-1.306   Mean   :-1.415   Mean   :0.1066   Mean   :0.001407  
##  3rd Qu.: 0.000   3rd Qu.: 0.000   3rd Qu.:0.0000   3rd Qu.:0.000000  
##  Max.   : 1.000   Max.   : 1.000   Max.   :1.0000   Max.   :1.000000  
##                                                                       
##      ZHHAGE          ZEMPLOYHH           ZSPOUSE        
##  Min.   :0.00000   Min.   :0.000000   Min.   :0.000000  
##  1st Qu.:0.00000   1st Qu.:0.000000   1st Qu.:0.000000  
##  Median :0.00000   Median :0.000000   Median :0.000000  
##  Mean   :0.01672   Mean   :0.004552   Mean   :0.003807  
##  3rd Qu.:0.00000   3rd Qu.:0.000000   3rd Qu.:0.000000  
##  Max.   :1.00000   Max.   :1.000000   Max.   :1.000000  
##                                                         
##    ZSDESCENT        ZHouseholder_Race   ZEDUCATION        ZNHSLDMEM      
##  Min.   :0.000000   Min.   :0.0000    Min.   :0.00000   Min.   :0.00000  
##  1st Qu.:0.000000   1st Qu.:0.0000    1st Qu.:0.00000   1st Qu.:0.00000  
##  Median :0.000000   Median :0.0000    Median :0.00000   Median :0.00000  
##  Mean   :0.003559   Mean   :0.0744    Mean   :0.01084   Mean   :0.00389  
##  3rd Qu.:0.000000   3rd Qu.:0.0000    3rd Qu.:0.00000   3rd Qu.:0.00000  
##  Max.   :1.000000   Max.   :1.0000    Max.   :1.00000   Max.   :1.00000  
##                                                                          
##  ZAGEHHMEMCAT2     ZAGEHHMEMCAT3      ZAGEHHMEMCAT4     
##  Min.   :0.00000   Min.   :0.000000   Min.   :0.000000  
##  1st Qu.:0.00000   1st Qu.:0.000000   1st Qu.:0.000000  
##  Median :0.00000   Median :0.000000   Median :0.000000  
##  Mean   :0.01374   Mean   :0.005711   Mean   :0.003973  
##  3rd Qu.:0.00000   3rd Qu.:0.000000   3rd Qu.:0.000000  
##  Max.   :1.00000   Max.   :1.000000   Max.   :1.000000  
##                                                         
##  ZAGEHHMEMCAT5      ZAGEHHMEMCAT6       ZAGEHHMEMCAT7      
##  Min.   :0.000000   Min.   :0.0000000   Min.   :0.0000000  
##  1st Qu.:0.000000   1st Qu.:0.0000000   1st Qu.:0.0000000  
##  Median :0.000000   Median :0.0000000   Median :0.0000000  
##  Mean   :0.001904   Mean   :0.0007448   Mean   :0.0002483  
##  3rd Qu.:0.000000   3rd Qu.:0.0000000   3rd Qu.:0.0000000  
##  Max.   :1.000000   Max.   :1.0000000   Max.   :1.0000000  
##                                                            
##  ZAGEHHMEMCAT8       ZAGEHHMEMCAT9       ZAGEHHMEMCAT10     
##  Min.   :0.0000000   Min.   :0.0000000   Min.   :0.0000000  
##  1st Qu.:0.0000000   1st Qu.:0.0000000   1st Qu.:0.0000000  
##  Median :0.0000000   Median :0.0000000   Median :0.0000000  
##  Mean   :0.0002483   Mean   :0.0002483   Mean   :0.0001655  
##  3rd Qu.:0.0000000   3rd Qu.:0.0000000   3rd Qu.:0.0000000  
##  Max.   :1.0000000   Max.   :1.0000000   Max.   :1.0000000  
##                                                             
##  ZAGEHHMEMCAT11      ZAGEHHMEMCAT12      ZAGEHHMEMCAT13    
##  Min.   :0.0000000   Min.   :0.0000000   Min.   :0.00e+00  
##  1st Qu.:0.0000000   1st Qu.:0.0000000   1st Qu.:0.00e+00  
##  Median :0.0000000   Median :0.0000000   Median :0.00e+00  
##  Mean   :0.0001655   Mean   :0.0001655   Mean   :8.28e-05  
##  3rd Qu.:0.0000000   3rd Qu.:0.0000000   3rd Qu.:0.00e+00  
##  Max.   :1.0000000   Max.   :1.0000000   Max.   :1.00e+00  
##                                                            
##  ZAGEHHMEMCAT14       ZHBUSNESS           ZATHOME        
##  Min.   :0.00e+00   Min.   :0.000000   Min.   :0.000000  
##  1st Qu.:0.00e+00   1st Qu.:0.000000   1st Qu.:0.000000  
##  Median :0.00e+00   Median :0.000000   Median :0.000000  
##  Mean   :8.28e-05   Mean   :0.002979   Mean   :0.005793  
##  3rd Qu.:0.00e+00   3rd Qu.:0.000000   3rd Qu.:0.000000  
##  Max.   :1.00e+00   Max.   :1.000000   Max.   :1.000000  
##                                                          
##    ZTELLWORK         ZTELLDAYS            ZOTHWORK       
##  Min.   :0.00000   Min.   :0.0000000   Min.   :0.000000  
##  1st Qu.:0.00000   1st Qu.:0.0000000   1st Qu.:0.000000  
##  Median :0.00000   Median :0.0000000   Median :0.000000  
##  Mean   :0.00331   Mean   :0.0004138   Mean   :0.002566  
##  3rd Qu.:0.00000   3rd Qu.:0.0000000   3rd Qu.:0.000000  
##  Max.   :1.00000   Max.   :1.0000000   Max.   :1.000000  
##                                                          
##     ZWORKPAY          ZRETIREPY         ZSSINCOME        ZCASHBEN     
##  Min.   :0.000000   Min.   :0.00000   Min.   :0.000   Min.   :0.0000  
##  1st Qu.:0.000000   1st Qu.:0.00000   1st Qu.:0.000   1st Qu.:0.0000  
##  Median :0.000000   Median :0.00000   Median :0.000   Median :0.0000  
##  Mean   :0.009352   Mean   :0.01134   Mean   :0.012   Mean   :0.0115  
##  3rd Qu.:0.000000   3rd Qu.:0.00000   3rd Qu.:0.000   3rd Qu.:0.0000  
##  Max.   :1.000000   Max.   :1.00000   Max.   :1.000   Max.   :1.0000  
##                                                                       
##    ZINVESTMT          ZRGLRPAY          ZMONEYPY        ZHUPROJ        
##  Min.   :0.00000   Min.   :0.00000   Min.   :0.000   Min.   :0.000000  
##  1st Qu.:0.00000   1st Qu.:0.00000   1st Qu.:0.000   1st Qu.:0.000000  
##  Median :0.00000   Median :0.00000   Median :0.000   Median :0.000000  
##  Mean   :0.01672   Mean   :0.01399   Mean   :0.125   Mean   :0.005793  
##  3rd Qu.:0.00000   3rd Qu.:0.00000   3rd Qu.:0.000   3rd Qu.:0.000000  
##  Max.   :1.00000   Max.   :1.00000   Max.   :1.000   Max.   :1.000000  
##                                                                        
##    ZRENTHELP          ZFOODASST           TOTSQFT        TOTSQFT_EN   
##  Min.   :0.000000   Min.   :0.000000   Min.   :  100   Min.   :  100  
##  1st Qu.:0.000000   1st Qu.:0.000000   1st Qu.: 1088   1st Qu.: 1052  
##  Median :0.000000   Median :0.000000   Median : 1863   Median : 1696  
##  Mean   :0.002483   Mean   :0.009352   Mean   : 2172   Mean   : 2022  
##  3rd Qu.:0.000000   3rd Qu.:0.000000   3rd Qu.: 2816   3rd Qu.: 2606  
##  Max.   :1.000000   Max.   :1.000000   Max.   :16122   Max.   :15472  
##                                                                       
##     TOTHSQFT        TOTUSQFT         TOTCSQFT       TOTUCSQFT      
##  Min.   :    0   Min.   :   0.0   Min.   :    0   Min.   :    0.0  
##  1st Qu.:  888   1st Qu.:   0.0   1st Qu.:  264   1st Qu.:  204.0  
##  Median : 1400   Median : 400.0   Median : 1025   Median :  533.0  
##  Mean   : 1676   Mean   : 496.4   Mean   : 1254   Mean   :  918.1  
##  3rd Qu.: 2160   3rd Qu.: 652.0   3rd Qu.: 1830   3rd Qu.: 1358.5  
##  Max.   :13776   Max.   :7589.0   Max.   :13776   Max.   :10783.0  
##                                                                    
##     ZTOTSQFT        ZTOTSQFT_EN        ZTOTHSQFT         ZTOTUSQFT      
##  Min.   :0.00000   Min.   :0.00000   Min.   :0.00000   Min.   :0.00000  
##  1st Qu.:0.00000   1st Qu.:0.00000   1st Qu.:0.00000   1st Qu.:0.00000  
##  Median :0.00000   Median :0.00000   Median :0.00000   Median :0.00000  
##  Mean   :0.09749   Mean   :0.09749   Mean   :0.09749   Mean   :0.09749  
##  3rd Qu.:0.00000   3rd Qu.:0.00000   3rd Qu.:0.00000   3rd Qu.:0.00000  
##  Max.   :1.00000   Max.   :1.00000   Max.   :1.00000   Max.   :1.00000  
##                                                                         
##    ZTOTCSQFT         ZTOTUCSQFT           KWH             KWHSPH       
##  Min.   :0.00000   Min.   :0.00000   Min.   :    17   Min.   :    0.0  
##  1st Qu.:0.00000   1st Qu.:0.00000   1st Qu.:  5837   1st Qu.:    0.0  
##  Median :0.00000   Median :0.00000   Median :  9623   Median :  211.8  
##  Mean   :0.09749   Mean   :0.09749   Mean   : 11288   Mean   :  999.0  
##  3rd Qu.:0.00000   3rd Qu.:0.00000   3rd Qu.: 14765   3rd Qu.: 1459.2  
##  Max.   :1.00000   Max.   :1.00000   Max.   :150254   Max.   :13843.3  
##                                                                        
##      KWHCOL            KWHWTH          KWHRFG            KWHOTH        
##  Min.   :    0.0   Min.   :    0   Min.   :    0.0   Min.   :    9.59  
##  1st Qu.:  142.1   1st Qu.:    0   1st Qu.:  722.9   1st Qu.: 3208.62  
##  Median :  751.1   Median :    0   Median : 1046.2   Median : 5429.25  
##  Mean   : 1685.3   Mean   : 1061   Mean   : 1243.2   Mean   : 6299.52  
##  3rd Qu.: 2290.8   3rd Qu.: 2000   3rd Qu.: 1561.7   3rd Qu.: 8317.44  
##  Max.   :60995.4   Max.   :18916   Max.   :11069.0   Max.   :65056.75  
##                                                                        
##      BTUEL           BTUELSPH          BTUELCOL           BTUELWTH    
##  Min.   :    58   Min.   :    0.0   Min.   :     0.0   Min.   :    0  
##  1st Qu.: 19916   1st Qu.:    0.0   1st Qu.:   484.9   1st Qu.:    0  
##  Median : 32834   Median :  722.8   Median :  2562.9   Median :    0  
##  Mean   : 38515   Mean   : 3408.7   Mean   :  5750.1   Mean   : 3621  
##  3rd Qu.: 50378   3rd Qu.: 4978.9   3rd Qu.:  7816.2   3rd Qu.: 6823  
##  Max.   :512667   Max.   :47233.4   Max.   :208116.5   Max.   :64542  
##                                                                       
##     BTUELRFG        BTUELOTH            DOLLAREL        DOLELSPH      
##  Min.   :    0   Min.   :    32.72   Min.   :    0   Min.   :   0.00  
##  1st Qu.: 2467   1st Qu.: 10947.80   1st Qu.:  739   1st Qu.:   0.00  
##  Median : 3570   Median : 18524.72   Median : 1151   Median :  25.55  
##  Mean   : 4242   Mean   : 21493.96   Mean   : 1352   Mean   : 108.39  
##  3rd Qu.: 5328   3rd Qu.: 28378.85   3rd Qu.: 1732   3rd Qu.: 176.04  
##  Max.   :37768   Max.   :221973.78   Max.   :19040   Max.   :1497.12  
##                                                                       
##     DOLELCOL          DOLELWTH         DOLELRFG          DOLELOTH     
##  Min.   :   0.00   Min.   :   0.0   Min.   :   0.00   Min.   :   0.0  
##  1st Qu.:  18.33   1st Qu.:   0.0   1st Qu.:  86.34   1st Qu.: 396.2  
##  Median :  89.76   Median :   0.0   Median : 126.99   Median : 649.3  
##  Mean   : 202.54   Mean   : 119.6   Mean   : 154.14   Mean   : 767.1  
##  3rd Qu.: 263.28   3rd Qu.: 225.5   3rd Qu.: 192.44   3rd Qu.: 990.6  
##  Max.   :7729.27   Max.   :2155.3   Max.   :2490.05   Max.   :9213.1  
##                                                                       
##     CUFEETNG       CUFEETNGSPH       CUFEETNGWTH      CUFEETNGOTH     
##  Min.   :   0.0   Min.   :   0.00   Min.   :   0.0   Min.   :   0.00  
##  1st Qu.:   0.0   1st Qu.:   0.00   1st Qu.:   0.0   1st Qu.:   0.00  
##  Median : 279.0   Median :  41.31   Median :  57.1   Median :   0.00  
##  Mean   : 405.3   Mean   : 249.09   Mean   : 110.1   Mean   :  46.17  
##  3rd Qu.: 683.0   3rd Qu.: 449.87   3rd Qu.: 189.0   3rd Qu.:  59.66  
##  Max.   :4501.0   Max.   :3296.03   Max.   :2772.0   Max.   :3767.00  
##                                                                       
##      BTUNG           BTUNGSPH         BTUNGWTH         BTUNGOTH     
##  Min.   :     0   Min.   :     0   Min.   :     0   Min.   :     0  
##  1st Qu.:     0   1st Qu.:     0   1st Qu.:     0   1st Qu.:     0  
##  Median : 28598   Median :  4235   Median :  5853   Median :     0  
##  Mean   : 41544   Mean   : 25532   Mean   : 11280   Mean   :  4732  
##  3rd Qu.: 70008   3rd Qu.: 46111   3rd Qu.: 19374   3rd Qu.:  6115  
##  Max.   :461353   Max.   :337844   Max.   :284130   Max.   :386118  
##                                                                     
##     DOLLARNG         DOLNGSPH          DOLNGWTH          DOLNGOTH      
##  Min.   :   0.0   Min.   :   0.00   Min.   :   0.00   Min.   :   0.00  
##  1st Qu.:   0.0   1st Qu.:   0.00   1st Qu.:   0.00   1st Qu.:   0.00  
##  Median : 347.0   Median :  67.08   Median :  68.04   Median :   0.00  
##  Mean   : 490.6   Mean   : 300.43   Mean   : 133.25   Mean   :  56.92  
##  3rd Qu.: 804.0   3rd Qu.: 533.89   3rd Qu.: 221.40   3rd Qu.:  73.00  
##  Max.   :6355.0   Max.   :3591.15   Max.   :2355.00   Max.   :2759.00  
##                                                                        
##     GALLONLP        GALLONLPSPH       GALLONLPWTH        GALLONLPOTH      
##  Min.   :   0.00   Min.   :   0.00   Min.   :   0.000   Min.   :   0.000  
##  1st Qu.:   0.00   1st Qu.:   0.00   1st Qu.:   0.000   1st Qu.:   0.000  
##  Median :   0.00   Median :   0.00   Median :   0.000   Median :   0.000  
##  Mean   :  41.08   Mean   :  28.24   Mean   :   6.803   Mean   :   6.036  
##  3rd Qu.:   0.00   3rd Qu.:   0.00   3rd Qu.:   0.000   3rd Qu.:   0.000  
##  Max.   :6388.00   Max.   :6008.00   Max.   :1069.000   Max.   :2256.647  
##                                                                           
##      BTULP           BTULPSPH         BTULPWTH          BTULPOTH       
##  Min.   :     0   Min.   :     0   Min.   :    0.0   Min.   :     0.0  
##  1st Qu.:     0   1st Qu.:     0   1st Qu.:    0.0   1st Qu.:     0.0  
##  Median :     0   Median :     0   Median :    0.0   Median :     0.0  
##  Mean   :  3752   Mean   :  2580   Mean   :  621.4   Mean   :   551.3  
##  3rd Qu.:     0   3rd Qu.:     0   3rd Qu.:    0.0   3rd Qu.:     0.0  
##  Max.   :583416   Max.   :548711   Max.   :97588.0   Max.   :206110.7  
##                                                                        
##     DOLLARLP          DOLLPSPH         DOLLPWTH          DOLLPOTH      
##  Min.   :    0.0   Min.   :   0.0   Min.   :   0.00   Min.   :   0.00  
##  1st Qu.:    0.0   1st Qu.:   0.0   1st Qu.:   0.00   1st Qu.:   0.00  
##  Median :    0.0   Median :   0.0   Median :   0.00   Median :   0.00  
##  Mean   :   85.5   Mean   :  56.4   Mean   :  14.75   Mean   :  14.36  
##  3rd Qu.:    0.0   3rd Qu.:   0.0   3rd Qu.:   0.00   3rd Qu.:   0.00  
##  Max.   :12972.0   Max.   :8389.7   Max.   :1946.38   Max.   :4582.28  
##                                                                        
##     GALLONFO        GALLONFOSPH       GALLONFOWTH       GALLONFOOTH      
##  Min.   :   0.00   Min.   :   0.00   Min.   :  0.000   Min.   :  0.0000  
##  1st Qu.:   0.00   1st Qu.:   0.00   1st Qu.:  0.000   1st Qu.:  0.0000  
##  Median :   0.00   Median :   0.00   Median :  0.000   Median :  0.0000  
##  Mean   :  43.06   Mean   :  37.23   Mean   :  5.293   Mean   :  0.5369  
##  3rd Qu.:   0.00   3rd Qu.:   0.00   3rd Qu.:  0.000   3rd Qu.:  0.0000  
##  Max.   :3078.00   Max.   :2407.22   Max.   :896.600   Max.   :777.0000  
##                                                                          
##      BTUFO           BTUFOSPH         BTUFOWTH           BTUFOOTH        
##  Min.   :     0   Min.   :     0   Min.   :     0.0   Min.   :     0.00  
##  1st Qu.:     0   1st Qu.:     0   1st Qu.:     0.0   1st Qu.:     0.00  
##  Median :     0   Median :     0   Median :     0.0   Median :     0.00  
##  Mean   :  5972   Mean   :  5164   Mean   :   734.1   Mean   :    74.45  
##  3rd Qu.:     0   3rd Qu.:     0   3rd Qu.:     0.0   3rd Qu.:     0.00  
##  Max.   :426888   Max.   :333791   Max.   :124285.1   Max.   :107761.69  
##                                                                          
##     DOLLARFO         DOLFOSPH          DOLFOWTH          DOLFOOTH      
##  Min.   :   0.0   Min.   :   0.00   Min.   :   0.00   Min.   :   0.00  
##  1st Qu.:   0.0   1st Qu.:   0.00   1st Qu.:   0.00   1st Qu.:   0.00  
##  Median :   0.0   Median :   0.00   Median :   0.00   Median :   0.00  
##  Mean   : 104.5   Mean   :  90.38   Mean   :  12.83   Mean   :   1.26  
##  3rd Qu.:   0.0   3rd Qu.:   0.00   3rd Qu.:   0.00   3rd Qu.:   0.00  
##  Max.   :7665.0   Max.   :5993.05   Max.   :2139.43   Max.   :1766.27  
##                                                                        
##    GALLONKER        GALLONKERSPH      GALLONKERWTH       GALLONKEROTH     
##  Min.   :  0.000   Min.   :  0.000   Min.   :  0.0000   Min.   :  0.0000  
##  1st Qu.:  0.000   1st Qu.:  0.000   1st Qu.:  0.0000   1st Qu.:  0.0000  
##  Median :  0.000   Median :  0.000   Median :  0.0000   Median :  0.0000  
##  Mean   :  1.567   Mean   :  1.329   Mean   :  0.0677   Mean   :  0.1702  
##  3rd Qu.:  0.000   3rd Qu.:  0.000   3rd Qu.:  0.0000   3rd Qu.:  0.0000  
##  Max.   :561.000   Max.   :550.000   Max.   :382.0000   Max.   :425.0000  
##                                                                           
##      BTUKER          BTUKERSPH         BTUKERWTH          BTUKEROTH       
##  Min.   :    0.0   Min.   :    0.0   Min.   :    0.00   Min.   :    0.00  
##  1st Qu.:    0.0   1st Qu.:    0.0   1st Qu.:    0.00   1st Qu.:    0.00  
##  Median :    0.0   Median :    0.0   Median :    0.00   Median :    0.00  
##  Mean   :  211.5   Mean   :  179.4   Mean   :    9.13   Mean   :   22.98  
##  3rd Qu.:    0.0   3rd Qu.:    0.0   3rd Qu.:    0.00   3rd Qu.:    0.00  
##  Max.   :75740.0   Max.   :74183.0   Max.   :51584.00   Max.   :57308.16  
##                                                                           
##    DOLLARKER          DOLKERSPH          DOLKERWTH       
##  Min.   :   0.000   Min.   :   0.000   Min.   :  0.0000  
##  1st Qu.:   0.000   1st Qu.:   0.000   1st Qu.:  0.0000  
##  Median :   0.000   Median :   0.000   Median :  0.0000  
##  Mean   :   4.199   Mean   :   3.589   Mean   :  0.1675  
##  3rd Qu.:   0.000   3rd Qu.:   0.000   3rd Qu.:  0.0000  
##  Max.   :1394.000   Max.   :1391.000   Max.   :944.0000  
##                                                          
##    DOLKEROTH            BTUWOOD          CORDSWD           TOTALBTU      
##  Min.   :   0.0000   Min.   :     0   Min.   : 0.0000   Min.   :     58  
##  1st Qu.:   0.0000   1st Qu.:     0   1st Qu.: 0.0000   1st Qu.:  51509  
##  Median :   0.0000   Median :     0   Median : 0.0000   Median :  80673  
##  Mean   :   0.4427   Mean   :  4508   Mean   : 0.2254   Mean   :  89996  
##  3rd Qu.:   0.0000   3rd Qu.:     0   3rd Qu.: 0.0000   3rd Qu.: 117214  
##  Max.   :1117.3710   Max.   :600000   Max.   :30.0000   Max.   :1096083  
##                                                                          
##   TOTALBTUSPH      TOTALBTUCOL      TOTALBTUWTH      TOTALBTURFG   
##  Min.   :     0   Min.   :     0   Min.   :     0   Min.   :    0  
##  1st Qu.:  8748   1st Qu.:   485   1st Qu.:  7710   1st Qu.: 2466  
##  Median : 27291   Median :  2563   Median : 12754   Median : 3570  
##  Mean   : 36864   Mean   :  5750   Mean   : 16266   Mean   : 4242  
##  3rd Qu.: 55646   3rd Qu.:  7816   3rd Qu.: 21158   3rd Qu.: 5328  
##  Max.   :548711   Max.   :208117   Max.   :284130   Max.   :37768  
##                                                                    
##   TOTALBTUOTH        TOTALDOL      TOTALDOLSPH      TOTALDOLCOL    
##  Min.   :    33   Min.   :    6   Min.   :   0.0   Min.   :   0.0  
##  1st Qu.: 13936   1st Qu.: 1271   1st Qu.: 222.0   1st Qu.:  18.0  
##  Median : 23014   Median : 1829   Median : 429.0   Median :  90.0  
##  Mean   : 26875   Mean   : 2037   Mean   : 559.2   Mean   : 202.5  
##  3rd Qu.: 34790   3rd Qu.: 2539   3rd Qu.: 761.0   3rd Qu.: 263.0  
##  Max.   :428085   Max.   :32012   Max.   :9264.0   Max.   :7729.0  
##                                                                    
##   TOTALDOLWTH      TOTALDOLRFG      TOTALDOLOTH         KAVALEL     
##  Min.   :   0.0   Min.   :   0.0   Min.   :    3.0   Min.   :1.000  
##  1st Qu.: 161.0   1st Qu.:  86.0   1st Qu.:  441.5   1st Qu.:1.000  
##  Median : 240.0   Median : 127.0   Median :  713.0   Median :1.000  
##  Mean   : 280.6   Mean   : 154.1   Mean   :  840.1   Mean   :1.247  
##  3rd Qu.: 350.0   3rd Qu.: 192.0   3rd Qu.: 1070.0   3rd Qu.:1.000  
##  Max.   :3019.0   Max.   :2490.0   Max.   :12826.0   Max.   :3.000  
##                                                                     
##     PERIODEL        SCALEEL          KAVALNG           PERIODNG      
##  Min.   :1.000   Min.   :0.0000   Min.   :-2.0000   Min.   :-2.0000  
##  1st Qu.:1.000   1st Qu.:0.0000   1st Qu.:-2.0000   1st Qu.:-2.0000  
##  Median :1.000   Median :0.0000   Median : 1.0000   Median : 1.0000  
##  Mean   :1.512   Mean   :0.3564   Mean   : 0.1316   Mean   : 0.4098  
##  3rd Qu.:1.000   3rd Qu.:0.0000   3rd Qu.: 1.0000   3rd Qu.: 1.0000  
##  Max.   :5.000   Max.   :3.0000   Max.   : 3.0000   Max.   : 5.0000  
##                                                                      
##     SCALENG           PERIODLP         SCALELP          PERIODFO     
##  Min.   :-2.0000   Min.   :-2.000   Min.   :-2.000   Min.   :-2.000  
##  1st Qu.:-2.0000   1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.000  
##  Median : 0.0000   Median :-2.000   Median :-2.000   Median :-2.000  
##  Mean   :-0.3657   Mean   :-1.558   Mean   :-1.699   Mean   :-1.651  
##  3rd Qu.: 0.0000   3rd Qu.:-2.000   3rd Qu.:-2.000   3rd Qu.:-2.000  
##  Max.   : 3.0000   Max.   : 5.000   Max.   : 3.000   Max.   : 5.000  
##                                                                      
##     SCALEFO          PERIODKR         SCALEKER     
##  Min.   :-2.000   Min.   :-2.000   Min.   :-2.000  
##  1st Qu.:-2.000   1st Qu.:-2.000   1st Qu.:-2.000  
##  Median :-2.000   Median :-2.000   Median :-2.000  
##  Mean   :-1.761   Mean   :-1.936   Mean   :-1.955  
##  3rd Qu.:-2.000   3rd Qu.:-2.000   3rd Qu.:-2.000  
##  Max.   : 3.000   Max.   : 5.000   Max.   : 3.000  
## 
```

Lots of recodes in there.


```r
library(plyr)
#ID
RECS$DOEID<-as.factor(RECS$DOEID)  

#Region
RECS$REGIONC<-revalue(as.factor(RECS$REGIONC),c("1"="NE", "2"="MidWest","3"="South","4"="West"))

#Type of Structure
RECS$TYPEHUQ<-revalue(as.factor(RECS$TYPEHUQ), c("1"="Mobile", "2"="SFDetached", "3"="SFAttached", "4"="SmApartment", "5"="LgApartment"))

#Climate zone
RECS$Climate_Region_Pub<-revalue(as.factor(RECS$Climate_Region_Pub),c("1"="VColdCold","2"="HotDryMixedDry","3"="HotHumid","4"="MixedHumid","5"="Marine"))

#Urban vs Rural
RECS$UR<-revalue(as.factor(RECS$UR), c("U"="Urban","R"="Rural"))

RECS$KOWNRENT<-revalue(as.factor(RECS$KOWNRENT),c("1"="Own","2"="Rent","3"="Free"))

#Year Built
summary(RECS$YEARMADE)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    1920    1955    1975    1971    1991    2009
```

```r
#Moved in
RECS$OCCUPYYRANGE<-revalue(as.factor(RECS$OCCUPYYRANGE),c("1"="Pre50", "2"="5059","3"="6069","4"="7079","5"="8089","6"="9099", "7"="0004","8"="0509"))

#Bedrooms
RECS$BEDROOMS[RECS$BEDROOMS==-2]<-NA
summary(RECS$BEDROOMS)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max.    NA's 
##    0.00    2.00    3.00    2.86    3.00   13.00     215
```

```r
#Working with cooking end use
summary(RECS$STOVEN)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##  0.0000  1.0000  1.0000  0.9112  1.0000  3.0000
```

```r
summary(RECS$STOVE)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##  0.0000  0.0000  0.0000  0.1233  0.0000  2.0000
```

```r
summary(RECS$OVEN)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##  0.0000  0.0000  0.0000  0.1567  0.0000  3.0000
```

```r
#Stove and oven fuel are only reported if separate

RECS$CookTopElectric<-FALSE
RECS$CookTopElectric[RECS$STOVENFUEL=='5' | RECS$STOVEFUEL=='5' ]<-TRUE

RECS$OvenElectric<-FALSE
RECS$OvenElectric[RECS$STOVENFUEL=='5' | RECS$OVENFUEL=='5' ]<-TRUE

#Just indicating that that cook with electricity
summary(RECS$CookTopElectric)
```

```
##    Mode   FALSE    TRUE    NA's 
## logical    4750    7333       0
```

```r
summary(RECS$OvenElectric)
```

```
##    Mode   FALSE    TRUE    NA's 
## logical    4395    7688       0
```

```r
#How much they use it
RECS$NUMMEAL<-revalue(as.factor(RECS$NUMMEAL),c("0"="Never","1"="ThreeDay","2"="TwoDay", "3"="OneDay", "4"="FewWeek","5"="OneWeek","6"="LessWeek"))

#this is better on cooking fuel.  Don't use the separate oven and cook top from above
RECS$ELectricCook<-FALSE
RECS$ELectricCook[RECS$FUELFOOD=="5"]<-TRUE

#Number of fridges.  Watch out for those with more than 4.
table(RECS$NUMFRIG)
```

```
## 
##    0    1    2    3    4    5    6    7 
##   19 9167 2626  226   34    9    1    1
```

```r
#age of fridge
RECS$AgeFridge<-revalue(as.factor(RECS$AGERFRI1), c("1"="Less2", "2"="2to4Years", "3"="5to9Years","41"="10to14Years","42"="15to19Years","5"="20PlusYears","-2"=NA))

summary(RECS$AgeFridge)
```

```
##       Less2   2to4Years   5to9Years 20PlusYears 10to14Years 15to19Years 
##        1523        2886        4212         546        2163         734 
##        NA's 
##          19
```

```r
#Has Dishwasher
RECS$DishwaherTrue<-revalue(as.factor(RECS$DISHWASH),c("0"=TRUE, "1"=FALSE))

RECS$WASHLOAD<-revalue(as.factor(RECS$WASHLOAD),c("1"="1Less","2"="2to4Loads","3"="5to9Loads","4"="10to15Loads","5"="15PlusLoads","-2"=NA))

RECS$DRYER<-revalue(as.factor(RECS$DRYER), c("0"=FALSE,"1"=TRUE))

RECS$DRYRFUEL<-revalue(as.factor(RECS$DRYRFUEL), c("1"="NG","2"="LPG","5"="Elec","-2"=NA))

##Start Recoding HERE
summary(RECS$AGECDRYER)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   -2.00    1.00    3.00    9.24    3.00   42.00
```

```r
summary(RECS$TVCOLOR)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   0.000   2.000   2.000   2.588   3.000  14.000
```

```r
summary(RECS$TVTYPE1)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   -2.00    1.00    2.00    1.73    2.00    5.00
```

```r
summary(RECS$TVONWD1)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##  -2.000   2.000   3.000   3.017   4.000   5.000
```

```r
summary(RECS$NUMPC)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   0.000   1.000   1.000   1.387   2.000  15.000
```

```r
summary(RECS$TIMEON1)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##  -2.000   1.000   2.000   1.643   3.000   5.000
```

```r
summary(RECS$WELLPUMP)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
## -2.0000  0.0000  0.0000 -0.3561  0.0000  1.0000
```

```r
summary(RECS$EQUIPM)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##  -2.000   3.000   3.000   3.446   3.000  21.000
```

```r
summary(RECS$FUELHEAT)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##  -2.000   1.000   1.000   2.612   5.000  21.000
```

```r
summary(RECS$EQUIPAGE)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   -2.00    2.00    5.00   13.65   41.00   42.00
```

```r
summary(RECS$TEMPHOME)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   -2.00   68.00   70.00   67.03   72.00   90.00
```

```r
summary(RECS$TEMPGONE)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   -2.00   62.00   68.00   63.85   70.00   90.00
```

```r
summary(RECS$TEMPNITE)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   -2.00   65.00   68.00   65.12   70.00   91.00
```

```r
summary(RECS$H2OTYPE1)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##  -2.000   1.000   1.000   1.018   1.000   2.000
```

```r
summary(RECS$FUELH2O)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##  -2.000   1.000   1.000   2.711   5.000  21.000
```

```r
summary(RECS$WHEATSIZ)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##  -2.000   2.000   2.000   2.081   3.000   3.000
```

```r
summary(RECS$WHEATAGE)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   -2.00    2.00    3.00   13.23   41.00   42.00
```

```r
summary(RECS$AIRCOND)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##  0.0000  1.0000  1.0000  0.8226  1.0000  1.0000
```

```r
summary(RECS$COOLTYPE)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
## -2.0000  1.0000  1.0000  0.7005  1.0000  3.0000
```

```r
summary(RECS$CENACHP)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
## -2.0000 -2.0000  0.0000 -0.6588  0.0000  1.0000
```

```r
summary(RECS$AGECENAC)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   -2.00   -2.00    2.00    8.46    5.00   42.00
```

```r
summary(RECS$USECENAC)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
## -2.0000 -2.0000  1.0000  0.6051  3.0000  3.0000
```

```r
summary(RECS$TEMPHOMEAC)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##    -2.0    -2.0    -2.0    31.2    72.0    88.0
```

```r
summary(RECS$TEMPGONEAC)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   -2.00   -2.00   -2.00   32.05   75.00   96.00
```

```r
summary(RECS$TEMPNITEAC)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   -2.00   -2.00   -2.00   31.11   72.00   96.00
```

```r
summary(RECS$NUMBERAC)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##  -2.000  -2.000  -2.000  -1.162  -2.000   9.000
```

```r
summary(RECS$WWACAGE)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
## -2.0000 -2.0000 -2.0000  0.3709 -2.0000 42.0000
```

```r
summary(RECS$ESWWAC)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   -9.00   -2.00   -2.00   -1.71   -2.00    1.00
```

```r
summary(RECS$USEWWAC)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##  -2.000  -2.000  -2.000  -1.195  -2.000   3.000
```

```r
summary(RECS$SWIMPOOL)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
## -2.0000 -2.0000  0.0000 -0.4869  0.0000  1.0000
```

```r
summary(RECS$POOL)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##  -2.000  -2.000  -2.000  -1.832  -2.000   1.000
```

```r
#Fuel used for pool
RECS$FUELPOOL<-revalue(as.factor(RECS$FUELPOOL),c("1"="NG","2"="LPG", "3"="FuelOil","4"="Kerosene", "5"="Elec","8"="Solar","21"="Other", "-2"=NA))
```

```
## The following `from` values were not present in `x`: 4
```

```r
summary(RECS$FUELPOOL)
```

```
##      NG     LPG FuelOil    Elec   Solar   Other    NA's 
##     118      24       2      60      32       1   11846
```

```r
#Hot Tub used
RECS$RECBATH<-revalue(as.factor(RECS$RECBATH),c("0"=FALSE,"1"=TRUE))
summary(RECS$RECBATH)
```

```
## FALSE  TRUE 
## 11389   694
```

```r
#Hot tub fuel
RECS$FUELTUB<-revalue(as.factor(RECS$FUELTUB),c("1"="NG","2"="LPG", "3"="FuelOil","4"="Kerosene", "5"="Elec","8"="Solar","21"="Other", "-2"=NA))
```

```
## The following `from` values were not present in `x`: 4
```

```r
summary(RECS$FUELTUB)
```

```
##      NG     LPG FuelOil    Elec   Solar   Other    NA's 
##     168      18       7     493       5       3   11389
```

```r
RECS$TYPEGLASS<-revalue(as.factor(RECS$TYPEGLASS),c("1"="SinglePane","2"="DoublePane", "3"="TriplePane", "-2"=NA))
summary(RECS$TYPEGLASS)
```

```
## SinglePane DoublePane TriplePane       NA's 
##       5071       6766        177         69
```

```r
#Electricity used for cooling
RECS$ELCOOL<-revalue(as.factor(RECS$ELCOOL),c("0"=FALSE,"1"=TRUE))
summary(RECS$ELCOOL)
```

```
## FALSE  TRUE 
##  2143  9940
```

```r
#Electricity used for space heating
RECS$ELWARM<-revalue(as.factor(RECS$ELWARM),c("0"=FALSE,"1"=TRUE))
summary(RECS$ELWARM)
```

```
## FALSE  TRUE 
##  5929  6154
```

```r
#Electricity used for water heating
RECS$ELWATER<-revalue(as.factor(RECS$ELWATER),c("0"=FALSE,"1"=TRUE))
summary(RECS$ELWATER)
```

```
## FALSE  TRUE 
##  7270  4813
```

```r
#Electricity used for cooking
RECS$ELFOOD<-revalue(as.factor(RECS$ELFOOD),c("0"=FALSE,"1"=TRUE))
summary(RECS$ELFOOD)
```

```
## FALSE  TRUE 
##  4387  7696
```

```r
#May need to do some editing on this.  Low values are too low
summary(RECS$KWH)/12
```

```
##      Min.   1st Qu.    Median      Mean   3rd Qu.      Max. 
##     1.417   486.417   801.917   940.833  1230.000 12525.000
```

```r
#This is the sqft variable to use
summary(RECS$TOTSQFT_EN)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##     100    1052    1696    2022    2606   15470
```

```r
#Get income working two ways
#MONEYPY 
RECS$MONEYPY<-revalue(as.factor(RECS$MONEYPY),c("1"="Less2500", "2"="Less5K", "3"="Less7500","4"="Less10K","5"="Less15K","6"="Less20K","7"="Less25K","8"="Less30K", "9"="Less35K","10"="Less40K","11"="Less45K","12"="Less50K","13"="Less55K","14"="Less60","15"="Less65","16"="Less70","17"="Less75","18"="Less80", "19"="Less85", "20"="Less90","21"="Less95","22"="Less100K","23"="Less120K","24"="Gr120K"))
summary(RECS$MONEYPY)
```

```
## Less2500   Less5K Less7500  Less10K  Less15K  Less20K  Less25K  Less30K 
##      310      152      176      328      686      602      746      755 
##  Less35K  Less40K  Less45K  Less50K  Less55K   Less60   Less65   Less70 
##      698      671      622      787      526      374      450      406 
##   Less75   Less80   Less85   Less90   Less95 Less100K Less120K   Gr120K 
##      393      302      289      287      231      250      653     1389
```

```r
RECS$RENTHELP<-revalue(as.factor(RECS$RENTHELP),c("0"=FALSE, "1"=TRUE, "-2"=FALSE))
summary(RECS$RENTHELP)
```

```
## FALSE  TRUE 
## 11913   170
```

```r
RECS$FOODASST<-revalue(as.factor(RECS$FOODASST),c("0"=FALSE, "1"=TRUE))
summary(RECS$FOODASST)
```

```
## FALSE  TRUE 
## 10795  1288
```

```r
#Age of HH looks ok
summary(RECS$HHAGE)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   16.00   37.00   49.00   49.74   62.00   85.00
```

```r
#number of people
summary(RECS$NHSLDMEM)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   1.000   2.000   2.000   2.666   4.000  14.000
```

```r
#Ed level of HH
RECS$EDUCATION<-revalue(as.factor(RECS$EDUCATION),c("0"="None","1"="NoHS","2"="HS","3"="SomeCol","4"="AA","5"="BA", "6"="MA", "7"="Prof", "8"="PHD"))
summary(RECS$EDUCATION)
```

```
##    None    NoHS      HS SomeCol      AA      BA      MA    Prof     PHD 
##     200    1033    3193    2701    1193    2428     957     221     157
```

```r
#HH Race
RECS$Householder_Race<-revalue(as.factor(RECS$Householder_Race),c("1"="Wt","2"="AfAm","3"="NativeAm","4"="Asian","5"="Pacific", "6"="Other", "7"="Multi"))
summary(RECS$Householder_Race)
```

```
##       Wt     AfAm NativeAm    Asian  Pacific    Other    Multi 
##     9578     1517      110      457       40      211      170
```

```r
#Hispanic
RECS$Hispanic<-FALSE
RECS$Hispanic[RECS$SDESCENT=="1"]<-TRUE
summary(RECS$Hispanic)
```

```
##    Mode   FALSE    TRUE    NA's 
## logical   10409    1674       0
```

```r
#Need state ie REPORTABLE_DOMAIN
```
Checkign out the weight variable

```r
summary(RECS$NWEIGHT)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   476.1  6297.0  7971.0  9403.0 11330.0 95780.0
```

```r
plot(hist(RECS$NWEIGHT))
```

![plot of chunk unnamed-chunk-3](figure/unnamed-chunk-3-1.png) ![plot of chunk unnamed-chunk-3](figure/unnamed-chunk-3-2.png) 
Looks like it is the number of equivelent HH in population style.

the weights are a little odd, too large differences.  Investigate the top end to find.

```r
summary(RECS[RECS$NWEIGHT>40000,])
```

```
##      DOEID       REGIONC      DIVISION    REPORTABLE_DOMAIN
##  184    : 1   NE     : 3   Min.   :2.00   Min.   : 4.00    
##  1246   : 1   MidWest:11   1st Qu.:3.00   1st Qu.: 7.00    
##  1611   : 1   South  :10   Median :3.00   Median : 7.00    
##  2008   : 1   West   : 1   Mean   :4.24   Mean   :11.08    
##  2355   : 1                3rd Qu.:5.00   3rd Qu.:14.00    
##  2477   : 1                Max.   :8.00   Max.   :22.00    
##  (Other):19                                                
##         TYPEHUQ     NWEIGHT          HDD65          CDD65     
##  Mobile     :9   Min.   :40963   Min.   :2075   Min.   :  58  
##  SFDetached :9   1st Qu.:43671   1st Qu.:4483   1st Qu.: 603  
##  SFAttached :0   Median :46747   Median :5244   Median : 872  
##  SmApartment:7   Mean   :50783   Mean   :5091   Mean   : 901  
##  LgApartment:0   3rd Qu.:51285   3rd Qu.:5754   3rd Qu.: 954  
##                  Max.   :95779   Max.   :8312   Max.   :2194  
##                                                               
##     HDD30YR        CDD30YR          Climate_Region_Pub    AIA_Zone  
##  Min.   :2139   Min.   : 153   VColdCold     :12       Min.   :1.0  
##  1st Qu.:4450   1st Qu.: 794   HotDryMixedDry: 0       1st Qu.:2.0  
##  Median :5496   Median : 998   HotHumid      : 2       Median :3.0  
##  Mean   :5102   Mean   :1071   MixedHumid    :11       Mean   :2.8  
##  3rd Qu.:5890   3rd Qu.:1112   Marine        : 0       3rd Qu.:3.0  
##  Max.   :7674   Max.   :2165                           Max.   :5.0  
##                                                                     
##  METROMICRO     UR     KOWNRENT     CONDCOOP     YEARMADE   
##  METRO:14   Rural:15   Own :17   Min.   :-2   Min.   :1920  
##  MICRO: 7   Urban:10   Rent: 8   1st Qu.:-2   1st Qu.:1958  
##  NONE : 4              Free: 0   Median :-2   Median :1973  
##                                  Mean   :-2   Mean   :1969  
##                                  3rd Qu.:-2   3rd Qu.:1990  
##                                  Max.   :-2   Max.   :2006  
##                                                             
##  YEARMADERANGE   OCCUPYYRANGE   CONVERSION       ORIG1FAM    
##  Min.   :1.00   0509   :10    Min.   :-2.00   Min.   :-2.00  
##  1st Qu.:2.00   0004   : 6    1st Qu.:-2.00   1st Qu.:-2.00  
##  Median :4.00   9099   : 4    Median :-2.00   Median :-2.00  
##  Mean   :3.88   6069   : 3    Mean   :-1.04   Mean   :-1.64  
##  3rd Qu.:6.00   Pre50  : 1    3rd Qu.: 1.00   3rd Qu.:-2.00  
##  Max.   :8.00   8089   : 1    Max.   : 2.00   Max.   : 1.00  
##                 (Other): 0                                   
##     LOOKLIKE       NUMFLRS      NUMAPTS      WALLTYPE       ROOFTYPE   
##  Min.   :-2.0   Min.   :-2   Min.   :-2   Min.   :1.00   Min.   :2.00  
##  1st Qu.:-2.0   1st Qu.:-2   1st Qu.:-2   1st Qu.:2.00   1st Qu.:3.00  
##  Median :-2.0   Median :-2   Median :-2   Median :3.00   Median :5.00  
##  Mean   :-1.6   Mean   :-2   Mean   :-2   Mean   :3.04   Mean   :4.24  
##  3rd Qu.:-2.0   3rd Qu.:-2   3rd Qu.:-2   3rd Qu.:3.00   3rd Qu.:5.00  
##  Max.   : 2.0   Max.   :-2   Max.   :-2   Max.   :7.00   Max.   :7.00  
##                                                                        
##      STUDIO        NAPTFLRS        STORIES         TYPEHUQ4   
##  Min.   :-2.0   Min.   :-2.00   Min.   :-2.00   Min.   :-2.0  
##  1st Qu.:-2.0   1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.0  
##  Median :-2.0   Median :-2.00   Median :10.00   Median :-2.0  
##  Mean   :-1.4   Mean   :-1.16   Mean   : 8.24   Mean   :-1.2  
##  3rd Qu.: 0.0   3rd Qu.: 1.00   3rd Qu.:10.00   3rd Qu.: 0.0  
##  Max.   : 1.0   Max.   : 1.00   Max.   :20.00   Max.   : 1.0  
##                                                               
##     BEDROOMS        NCOMBATH       NHAFBATH       OTHROOMS  
##  Min.   :1.000   Min.   :1.00   Min.   :0.00   Min.   :1.0  
##  1st Qu.:2.000   1st Qu.:1.00   1st Qu.:0.00   1st Qu.:2.0  
##  Median :2.500   Median :1.00   Median :0.00   Median :2.0  
##  Mean   :2.417   Mean   :1.28   Mean   :0.12   Mean   :2.6  
##  3rd Qu.:3.000   3rd Qu.:2.00   3rd Qu.:0.00   3rd Qu.:3.0  
##  Max.   :4.000   Max.   :2.00   Max.   :1.00   Max.   :5.0  
##  NA's   :1                                                  
##     TOTROOMS        CELLAR          CRAWL          CONCRETE    
##  Min.   :1.00   Min.   :-2.00   Min.   :-2.00   Min.   :-2.00  
##  1st Qu.:4.00   1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.00  
##  Median :5.00   Median : 0.00   Median : 0.00   Median : 0.00  
##  Mean   :4.92   Mean   :-0.36   Mean   :-0.44   Mean   :-0.52  
##  3rd Qu.:6.00   3rd Qu.: 1.00   3rd Qu.: 1.00   3rd Qu.: 0.00  
##  Max.   :9.00   Max.   : 1.00   Max.   : 1.00   Max.   : 1.00  
##                                                                
##     BASEFIN        FINBASERMS       BASEHEAT       BASEHT2     
##  Min.   :-2.00   Min.   :-2.00   Min.   :-2.0   Min.   :-2.00  
##  1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.0   1st Qu.:-2.00  
##  Median :-2.00   Median :-2.00   Median :-2.0   Median :-2.00  
##  Mean   :-1.24   Mean   :-1.88   Mean   :-1.2   Mean   :-1.76  
##  3rd Qu.: 0.00   3rd Qu.:-2.00   3rd Qu.: 0.0   3rd Qu.:-2.00  
##  Max.   : 1.00   Max.   : 1.00   Max.   : 1.0   Max.   : 1.00  
##                                                                
##     PCTBSTHT     BASECOOL        BASECL2      PCTBSTCL     BASEUSE     
##  Min.   :-2   Min.   :-2.00   Min.   :-2   Min.   :-2   Min.   :-2.00  
##  1st Qu.:-2   1st Qu.:-2.00   1st Qu.:-2   1st Qu.:-2   1st Qu.:-2.00  
##  Median :-2   Median :-2.00   Median :-2   Median :-2   Median :-2.00  
##  Mean   :-2   Mean   :-1.28   Mean   :-2   Mean   :-2   Mean   :-0.96  
##  3rd Qu.:-2   3rd Qu.: 0.00   3rd Qu.:-2   3rd Qu.:-2   3rd Qu.: 1.00  
##  Max.   :-2   Max.   : 0.00   Max.   :-2   Max.   :-2   Max.   : 2.00  
##                                                                        
##      ATTIC          ATTICFIN       FINATTRMS     ATTCHEAT        ATTCHT2  
##  Min.   :-2.00   Min.   :-2.00   Min.   :-2   Min.   :-2.00   Min.   :-2  
##  1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2   1st Qu.:-2.00   1st Qu.:-2  
##  Median : 0.00   Median :-2.00   Median :-2   Median :-2.00   Median :-2  
##  Mean   :-0.68   Mean   :-1.92   Mean   :-2   Mean   :-1.92   Mean   :-2  
##  3rd Qu.: 0.00   3rd Qu.:-2.00   3rd Qu.:-2   3rd Qu.:-2.00   3rd Qu.:-2  
##  Max.   : 1.00   Max.   : 0.00   Max.   :-2   Max.   : 0.00   Max.   :-2  
##                                                                           
##     PCTATTHT     ATTCCOOL        ATTCCL2      PCTATTCL     ATTICUSE    
##  Min.   :-2   Min.   :-2.00   Min.   :-2   Min.   :-2   Min.   :-2.00  
##  1st Qu.:-2   1st Qu.:-2.00   1st Qu.:-2   1st Qu.:-2   1st Qu.:-2.00  
##  Median :-2   Median :-2.00   Median :-2   Median :-2   Median :-2.00  
##  Mean   :-2   Mean   :-1.92   Mean   :-2   Mean   :-2   Mean   :-1.88  
##  3rd Qu.:-2   3rd Qu.:-2.00   3rd Qu.:-2   3rd Qu.:-2   3rd Qu.:-2.00  
##  Max.   :-2   Max.   : 0.00   Max.   :-2   Max.   :-2   Max.   : 1.00  
##                                                                        
##     PRKGPLC1      SIZEOFGARAGE     GARGLOC         GARGHEAT    
##  Min.   :-2.00   Min.   :-2.0   Min.   :-2.00   Min.   :-2.00  
##  1st Qu.:-2.00   1st Qu.:-2.0   1st Qu.:-2.00   1st Qu.:-2.00  
##  Median : 0.00   Median :-2.0   Median :-2.00   Median :-2.00  
##  Mean   :-0.32   Mean   :-1.2   Mean   :-1.08   Mean   :-1.52  
##  3rd Qu.: 0.00   3rd Qu.:-2.0   3rd Qu.:-2.00   3rd Qu.:-2.00  
##  Max.   : 1.00   Max.   : 2.0   Max.   : 2.00   Max.   : 0.00  
##                                                                
##     GARGCOOL        PRKGPLC2     SIZEOFDETACH      OUTLET     
##  Min.   :-2.00   Min.   :-2.0   Min.   :-2.0   Min.   :-2.00  
##  1st Qu.:-2.00   1st Qu.:-2.0   1st Qu.:-2.0   1st Qu.: 0.00  
##  Median :-2.00   Median :-2.0   Median :-2.0   Median : 1.00  
##  Mean   :-1.52   Mean   :-0.8   Mean   :-0.6   Mean   : 0.36  
##  3rd Qu.:-2.00   3rd Qu.: 0.0   3rd Qu.:-2.0   3rd Qu.: 1.00  
##  Max.   : 0.00   Max.   : 1.0   Max.   : 4.0   Max.   : 1.00  
##                                                               
##    ZKOWNRENT      ZCONDCOOP   ZYEARMADE   ZYEARMADERANGE ZOCCUPYYRANGE
##  Min.   :0.00   Min.   :0   Min.   :0.0   Min.   :0.00   Min.   :0    
##  1st Qu.:0.00   1st Qu.:0   1st Qu.:0.0   1st Qu.:0.00   1st Qu.:0    
##  Median :0.00   Median :0   Median :0.0   Median :0.00   Median :0    
##  Mean   :0.04   Mean   :0   Mean   :0.2   Mean   :0.08   Mean   :0    
##  3rd Qu.:0.00   3rd Qu.:0   3rd Qu.:0.0   3rd Qu.:0.00   3rd Qu.:0    
##  Max.   :1.00   Max.   :0   Max.   :1.0   Max.   :1.00   Max.   :0    
##                                                                       
##   ZCONVERSION     ZORIG1FAM   ZLOOKLIKE    ZNUMFLRS    ZNUMAPTS
##  Min.   :0.00   Min.   :0   Min.   :0   Min.   :0   Min.   :0  
##  1st Qu.:0.00   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0  
##  Median :0.00   Median :0   Median :0   Median :0   Median :0  
##  Mean   :0.04   Mean   :0   Mean   :0   Mean   :0   Mean   :0  
##  3rd Qu.:0.00   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0  
##  Max.   :1.00   Max.   :0   Max.   :0   Max.   :0   Max.   :0  
##                                                                
##    ZWALLTYPE   ZROOFTYPE       ZSTUDIO    ZNAPTFLRS    ZSTORIES
##  Min.   :0   Min.   :0.00   Min.   :0   Min.   :0   Min.   :0  
##  1st Qu.:0   1st Qu.:0.00   1st Qu.:0   1st Qu.:0   1st Qu.:0  
##  Median :0   Median :0.00   Median :0   Median :0   Median :0  
##  Mean   :0   Mean   :0.04   Mean   :0   Mean   :0   Mean   :0  
##  3rd Qu.:0   3rd Qu.:0.00   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0  
##  Max.   :0   Max.   :1.00   Max.   :0   Max.   :0   Max.   :0  
##                                                                
##    ZTYPEHUQ4      ZBEDROOMS   ZNCOMBATH   ZNHAFBATH   ZOTHROOMS
##  Min.   :0.00   Min.   :0   Min.   :0   Min.   :0   Min.   :0  
##  1st Qu.:0.00   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0  
##  Median :0.00   Median :0   Median :0   Median :0   Median :0  
##  Mean   :0.04   Mean   :0   Mean   :0   Mean   :0   Mean   :0  
##  3rd Qu.:0.00   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0  
##  Max.   :1.00   Max.   :0   Max.   :0   Max.   :0   Max.   :0  
##                                                                
##     ZCELLAR      ZCRAWL    ZCONCRETE    ZBASEFIN  ZFINBASERMS  
##  Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0.00  
##  1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0.00  
##  Median :0   Median :0   Median :0   Median :0   Median :0.00  
##  Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0.04  
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0.00  
##  Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :1.00  
##                                                                
##    ZBASEHEAT    ZBASEHT2   ZPCTBSTHT   ZBASECOOL    ZBASECL2   ZPCTBSTCL
##  Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0  
##  1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0  
##  Median :0   Median :0   Median :0   Median :0   Median :0   Median :0  
##  Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0  
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0  
##  Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0  
##                                                                         
##     ZBASEUSE     ZATTIC    ZATTICFIN   ZFINATTRMS   ZATTCHEAT    ZATTCHT2
##  Min.   :0   Min.   :0   Min.   :0   Min.   :0    Min.   :0   Min.   :0  
##  1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0    1st Qu.:0   1st Qu.:0  
##  Median :0   Median :0   Median :0   Median :0    Median :0   Median :0  
##  Mean   :0   Mean   :0   Mean   :0   Mean   :0    Mean   :0   Mean   :0  
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0    3rd Qu.:0   3rd Qu.:0  
##  Max.   :0   Max.   :0   Max.   :0   Max.   :0    Max.   :0   Max.   :0  
##                                                                          
##    ZPCTATTHT   ZATTCCOOL   ZPCTATTCL    ZATTCCL2   ZATTICUSE   ZPRKGPLC1
##  Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0  
##  1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0  
##  Median :0   Median :0   Median :0   Median :0   Median :0   Median :0  
##  Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0  
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0  
##  Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0  
##                                                                         
##  ZSIZEOFGARAGE    ZGARGLOC   ZGARGHEAT   ZGARGCOOL   ZPRKGPLC2
##  Min.   :0     Min.   :0   Min.   :0   Min.   :0   Min.   :0  
##  1st Qu.:0     1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0  
##  Median :0     Median :0   Median :0   Median :0   Median :0  
##  Mean   :0     Mean   :0   Mean   :0   Mean   :0   Mean   :0  
##  3rd Qu.:0     3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0  
##  Max.   :0     Max.   :0   Max.   :0   Max.   :0   Max.   :0  
##                                                               
##  ZSIZEOFDETACH     STOVEN       STOVENFUEL        STOVE     
##  Min.   :0     Min.   :0.00   Min.   :-2.00   Min.   :0.00  
##  1st Qu.:0     1st Qu.:1.00   1st Qu.: 2.00   1st Qu.:0.00  
##  Median :0     Median :1.00   Median : 2.00   Median :0.00  
##  Mean   :0     Mean   :0.92   Mean   : 2.96   Mean   :0.04  
##  3rd Qu.:0     3rd Qu.:1.00   3rd Qu.: 5.00   3rd Qu.:0.00  
##  Max.   :0     Max.   :1.00   Max.   : 5.00   Max.   :1.00  
##                                                             
##    STOVEFUEL          OVEN         OVENFUEL        OVENUSE     
##  Min.   :-2.00   Min.   :0.00   Min.   :-2.00   Min.   :-2.00  
##  1st Qu.:-2.00   1st Qu.:0.00   1st Qu.:-2.00   1st Qu.: 3.00  
##  Median :-2.00   Median :0.00   Median :-2.00   Median : 4.00  
##  Mean   :-1.88   Mean   :0.04   Mean   :-1.88   Mean   : 3.36  
##  3rd Qu.:-2.00   3rd Qu.:0.00   3rd Qu.:-2.00   3rd Qu.: 5.00  
##  Max.   : 1.00   Max.   :1.00   Max.   : 1.00   Max.   : 6.00  
##                                                                
##     OVENCLN         TYPECLN          MICRO         AMTMICRO    
##  Min.   :-2.00   Min.   :-2.00   Min.   :0.00   Min.   :-2.00  
##  1st Qu.: 0.00   1st Qu.:-2.00   1st Qu.:1.00   1st Qu.: 1.00  
##  Median : 0.00   Median :-2.00   Median :1.00   Median : 2.00  
##  Mean   : 0.24   Mean   :-0.72   Mean   :0.96   Mean   : 2.16  
##  3rd Qu.: 1.00   3rd Qu.: 2.00   3rd Qu.:1.00   3rd Qu.: 3.00  
##  Max.   : 1.00   Max.   : 2.00   Max.   :1.00   Max.   : 4.00  
##                                                                
##     DEFROST         OUTGRILL     OUTGRILLFUEL      TOPGRILL    STGRILA  
##  Min.   :-2.00   Min.   :0.00   Min.   :-2.00   Min.   :0   Min.   :-2  
##  1st Qu.: 0.00   1st Qu.:0.00   1st Qu.:-2.00   1st Qu.:0   1st Qu.:-2  
##  Median : 1.00   Median :1.00   Median : 2.00   Median :0   Median :-2  
##  Mean   : 0.44   Mean   :0.52   Mean   : 3.12   Mean   :0   Mean   :-2  
##  3rd Qu.: 1.00   3rd Qu.:1.00   3rd Qu.: 2.00   3rd Qu.:0   3rd Qu.:-2  
##  Max.   : 1.00   Max.   :1.00   Max.   :21.00   Max.   :0   Max.   :-2  
##                                                                         
##     TOASTER        NUMMEAL      FUELFOOD         COFFEE       NUMFRIG    
##  Min.   :0.0   Never   : 0   Min.   :-2.00   Min.   :0.0   Min.   :1.00  
##  1st Qu.:0.0   ThreeDay: 1   1st Qu.: 2.00   1st Qu.:1.0   1st Qu.:1.00  
##  Median :0.0   TwoDay  : 9   Median : 2.00   Median :1.0   Median :1.00  
##  Mean   :0.4   OneDay  :10   Mean   : 3.08   Mean   :0.8   Mean   :1.08  
##  3rd Qu.:1.0   FewWeek : 5   3rd Qu.: 5.00   3rd Qu.:1.0   3rd Qu.:1.00  
##  Max.   :1.0   OneWeek : 0   Max.   : 5.00   Max.   :1.0   Max.   :2.00  
##                LessWeek: 0                                               
##     TYPERFR1        SIZRFRI1       REFRIGT1         ICE      
##  Min.   : 1.00   Min.   :2.00   Min.   :1.00   Min.   :0.00  
##  1st Qu.:21.00   1st Qu.:3.00   1st Qu.:2.00   1st Qu.:0.00  
##  Median :22.00   Median :3.00   Median :2.00   Median :0.00  
##  Mean   :18.56   Mean   :3.36   Mean   :1.84   Mean   :0.16  
##  3rd Qu.:22.00   3rd Qu.:4.00   3rd Qu.:2.00   3rd Qu.:0.00  
##  Max.   :23.00   Max.   :4.00   Max.   :2.00   Max.   :1.00  
##                                                              
##     AGERFRI1         ESFRIG         REPLCFRI        HELPFRI     
##  Min.   : 1.00   Min.   :-9.00   Min.   :-2.00   Min.   :-2.00  
##  1st Qu.: 3.00   1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.00  
##  Median : 3.00   Median :-2.00   Median :-2.00   Median :-2.00  
##  Mean   :21.12   Mean   :-1.44   Mean   :-1.52   Mean   :-1.64  
##  3rd Qu.:41.00   3rd Qu.: 0.00   3rd Qu.:-2.00   3rd Qu.:-2.00  
##  Max.   :42.00   Max.   : 1.00   Max.   : 1.00   Max.   : 1.00  
##                                                                 
##     HELPFRIY        TYPERFR2        SIZRFRI2       REFRIGT2    
##  Min.   :-2.00   Min.   :-2.00   Min.   :-2.0   Min.   :-2.00  
##  1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.0   1st Qu.:-2.00  
##  Median :-2.00   Median :-2.00   Median :-2.0   Median :-2.00  
##  Mean   :-1.84   Mean   :-0.12   Mean   :-1.6   Mean   :-1.68  
##  3rd Qu.:-2.00   3rd Qu.:-2.00   3rd Qu.:-2.0   3rd Qu.:-2.00  
##  Max.   : 2.00   Max.   :22.00   Max.   : 3.0   Max.   : 2.00  
##                                                                
##     MONRFRI2        AGERFRI2        ESFRIG2         TYPERFR3     SIZRFRI3 
##  Min.   :-2.00   Min.   :-2.00   Min.   :-2.00   Min.   :-2   Min.   :-2  
##  1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2   1st Qu.:-2  
##  Median :-2.00   Median :-2.00   Median :-2.00   Median :-2   Median :-2  
##  Mean   :-1.68   Mean   :-0.08   Mean   :-1.88   Mean   :-2   Mean   :-2  
##  3rd Qu.:-2.00   3rd Qu.:-2.00   3rd Qu.:-2.00   3rd Qu.:-2   3rd Qu.:-2  
##  Max.   : 3.00   Max.   :41.00   Max.   : 1.00   Max.   :-2   Max.   :-2  
##                                                                           
##     REFRIGT3     MONRFRI3     AGERFRI3     ESFRIG3      SEPFREEZ  
##  Min.   :-2   Min.   :-2   Min.   :-2   Min.   :-2   Min.   :0.0  
##  1st Qu.:-2   1st Qu.:-2   1st Qu.:-2   1st Qu.:-2   1st Qu.:0.0  
##  Median :-2   Median :-2   Median :-2   Median :-2   Median :0.0  
##  Mean   :-2   Mean   :-2   Mean   :-2   Mean   :-2   Mean   :0.4  
##  3rd Qu.:-2   3rd Qu.:-2   3rd Qu.:-2   3rd Qu.:-2   3rd Qu.:1.0  
##  Max.   :-2   Max.   :-2   Max.   :-2   Max.   :-2   Max.   :1.0  
##                                                                   
##     NUMFREEZ       UPRTFRZR        SIZFREEZ        FREEZER    
##  Min.   :-2.0   Min.   :-2.00   Min.   :-2.00   Min.   :-2.0  
##  1st Qu.:-2.0   1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.0  
##  Median :-2.0   Median :-2.00   Median :-2.00   Median :-2.0  
##  Mean   :-0.8   Mean   :-0.52   Mean   :-0.52   Mean   :-0.6  
##  3rd Qu.: 1.0   3rd Qu.: 2.00   3rd Qu.: 1.00   3rd Qu.: 1.0  
##  Max.   : 1.0   Max.   : 2.00   Max.   : 3.00   Max.   : 2.0  
##                                                               
##     AGEFRZR         REPLCFRZ        HELPFRZ         HELPFRZY    UPRTFRZR2 
##  Min.   :-2.00   Min.   :-9.00   Min.   :-2.00   Min.   :-2   Min.   :-2  
##  1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2   1st Qu.:-2  
##  Median :-2.00   Median :-2.00   Median :-2.00   Median :-2   Median :-2  
##  Mean   : 6.08   Mean   :-2.08   Mean   :-1.92   Mean   :-2   Mean   :-2  
##  3rd Qu.: 3.00   3rd Qu.:-2.00   3rd Qu.:-2.00   3rd Qu.:-2   3rd Qu.:-2  
##  Max.   :42.00   Max.   : 1.00   Max.   : 0.00   Max.   :-2   Max.   :-2  
##                                                                           
##    SIZFREEZ2     FREEZER2     AGEFRZR2     DISHWASH       DWASHUSE    
##  Min.   :-2   Min.   :-2   Min.   :-2   Min.   :0.00   Min.   :-2.00  
##  1st Qu.:-2   1st Qu.:-2   1st Qu.:-2   1st Qu.:0.00   1st Qu.:-2.00  
##  Median :-2   Median :-2   Median :-2   Median :0.00   Median :-2.00  
##  Mean   :-2   Mean   :-2   Mean   :-2   Mean   :0.48   Mean   : 6.84  
##  3rd Qu.:-2   3rd Qu.:-2   3rd Qu.:-2   3rd Qu.:1.00   3rd Qu.:13.00  
##  Max.   :-2   Max.   :-2   Max.   :-2   Max.   :1.00   Max.   :30.00  
##                                                                       
##      AGEDW          ESDISHW        REPLCDW          HELPDW     
##  Min.   :-2.00   Min.   :-9.0   Min.   :-2.00   Min.   :-2.00  
##  1st Qu.:-2.00   1st Qu.:-2.0   1st Qu.:-2.00   1st Qu.:-2.00  
##  Median :-2.00   Median :-2.0   Median :-2.00   Median :-2.00  
##  Mean   : 4.64   Mean   :-1.8   Mean   :-1.44   Mean   :-1.68  
##  3rd Qu.: 3.00   3rd Qu.: 0.0   3rd Qu.:-2.00   3rd Qu.:-2.00  
##  Max.   :41.00   Max.   : 1.0   Max.   : 1.00   Max.   : 0.00  
##                                                                
##     HELPDWY      ZSTOVEN   ZSTOVENFUEL     ZSTOVE    ZSTOVEFUEL
##  Min.   :-2   Min.   :0   Min.   :0    Min.   :0   Min.   :0   
##  1st Qu.:-2   1st Qu.:0   1st Qu.:0    1st Qu.:0   1st Qu.:0   
##  Median :-2   Median :0   Median :0    Median :0   Median :0   
##  Mean   :-2   Mean   :0   Mean   :0    Mean   :0   Mean   :0   
##  3rd Qu.:-2   3rd Qu.:0   3rd Qu.:0    3rd Qu.:0   3rd Qu.:0   
##  Max.   :-2   Max.   :0   Max.   :0    Max.   :0   Max.   :0   
##                                                                
##      ZOVEN     ZOVENFUEL    ZOVENUSE    ZOVENCLN       ZTYPECLN
##  Min.   :0   Min.   :0   Min.   :0   Min.   :0.00   Min.   :0  
##  1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0.00   1st Qu.:0  
##  Median :0   Median :0   Median :0   Median :0.00   Median :0  
##  Mean   :0   Mean   :0   Mean   :0   Mean   :0.04   Mean   :0  
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0.00   3rd Qu.:0  
##  Max.   :0   Max.   :0   Max.   :0   Max.   :1.00   Max.   :0  
##                                                                
##      ZMICRO    ZAMTMICRO    ZDEFROST   ZOUTGRILL ZOUTGRILLFUEL   ZTOPGRILL
##  Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0     Min.   :0  
##  1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0     1st Qu.:0  
##  Median :0   Median :0   Median :0   Median :0   Median :0     Median :0  
##  Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0     Mean   :0  
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0     3rd Qu.:0  
##  Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0     Max.   :0  
##                                                                           
##     ZSTGRILA    ZTOASTER    ZNUMMEAL   ZFUELFOOD    ZCOFFEE     ZNUMFRIG
##  Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0  
##  1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0  
##  Median :0   Median :0   Median :0   Median :0   Median :0   Median :0  
##  Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0  
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0  
##  Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0  
##                                                                         
##    ZTYPERFR1   ZSIZRFRI1   ZREFRIGT1      ZICE     ZAGERFRI1   
##  Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0.00  
##  1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0.00  
##  Median :0   Median :0   Median :0   Median :0   Median :0.00  
##  Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0.04  
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0.00  
##  Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :1.00  
##                                                                
##    ZTYPERFR2   ZSIZRFRI2   ZREFRIGT2   ZMONRFRI2   ZAGERFRI2   ZTYPERFR3
##  Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0  
##  1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0  
##  Median :0   Median :0   Median :0   Median :0   Median :0   Median :0  
##  Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0  
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0  
##  Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0  
##                                                                         
##    ZSIZRFRI3   ZREFRIGT3   ZMONRFRI3   ZAGERFRI3   ZSEPFREEZ   ZNUMFREEZ
##  Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0  
##  1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0  
##  Median :0   Median :0   Median :0   Median :0   Median :0   Median :0  
##  Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0  
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0  
##  Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0  
##                                                                         
##    ZUPRTFRZR   ZSIZFREEZ    ZFREEZER       ZAGEFRZR      ZUPRTFRZR2
##  Min.   :0   Min.   :0   Min.   :0.00   Min.   :0.00   Min.   :0   
##  1st Qu.:0   1st Qu.:0   1st Qu.:0.00   1st Qu.:0.00   1st Qu.:0   
##  Median :0   Median :0   Median :0.00   Median :0.00   Median :0   
##  Mean   :0   Mean   :0   Mean   :0.04   Mean   :0.04   Mean   :0   
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0.00   3rd Qu.:0.00   3rd Qu.:0   
##  Max.   :0   Max.   :0   Max.   :1.00   Max.   :1.00   Max.   :0   
##                                                                    
##    ZSIZFREEZ2   ZFREEZER2   ZAGEFRZR2   ZDISHWASH   ZDWASHUSE     ZAGEDW 
##  Min.   :0    Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0  
##  1st Qu.:0    1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0  
##  Median :0    Median :0   Median :0   Median :0   Median :0   Median :0  
##  Mean   :0    Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0  
##  3rd Qu.:0    3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0  
##  Max.   :0    Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0  
##                                                                          
##     CWASHER        TOPFRONT           WASHLOAD    WASHTEMP    
##  Min.   :0.00   Min.   :-2.0   1Less      :1   Min.   :-2.00  
##  1st Qu.:1.00   1st Qu.: 1.0   2to4Loads  :9   1st Qu.: 1.00  
##  Median :1.00   Median : 1.0   5to9Loads  :7   Median : 2.00  
##  Mean   :0.76   Mean   : 0.4   10to15Loads:2   Mean   : 1.28  
##  3rd Qu.:1.00   3rd Qu.: 1.0   15PlusLoads:0   3rd Qu.: 3.00  
##  Max.   :1.00   Max.   : 2.0   NA's       :6   Max.   : 3.00  
##                                                               
##     RNSETEMP        AGECWASH        ESCWASH         REPLCCW     
##  Min.   :-2.00   Min.   :-2.00   Min.   :-9.00   Min.   :-2.00  
##  1st Qu.: 1.00   1st Qu.: 1.00   1st Qu.:-2.00   1st Qu.:-2.00  
##  Median : 2.00   Median : 2.00   Median :-2.00   Median :-2.00  
##  Mean   : 1.48   Mean   :12.16   Mean   :-1.08   Mean   :-1.16  
##  3rd Qu.: 3.00   3rd Qu.:41.00   3rd Qu.: 1.00   3rd Qu.: 1.00  
##  Max.   : 3.00   Max.   :42.00   Max.   : 1.00   Max.   : 1.00  
##                                                                 
##      HELPCW         HELPCWY     DRYER    DRYRFUEL     DRYRUSE     
##  Min.   :-2.00   Min.   :-2   FALSE: 7   NG  : 2   Min.   :-2.00  
##  1st Qu.:-2.00   1st Qu.:-2   TRUE :18   LPG : 0   1st Qu.:-2.00  
##  Median :-2.00   Median :-2              Elec:16   Median : 1.00  
##  Mean   :-1.44   Mean   :-2              NA's: 7   Mean   : 0.24  
##  3rd Qu.: 0.00   3rd Qu.:-2                        3rd Qu.: 1.00  
##  Max.   : 0.00   Max.   :-2                        Max.   : 2.00  
##                                                                   
##    AGECDRYER        TVCOLOR        TVSIZE1         TVTYPE1     
##  Min.   :-2.00   Min.   :0.00   Min.   :-2.00   Min.   :-2.00  
##  1st Qu.:-2.00   1st Qu.:1.00   1st Qu.: 2.00   1st Qu.: 1.00  
##  Median : 2.00   Median :2.00   Median : 2.00   Median : 2.00  
##  Mean   : 8.92   Mean   :2.08   Mean   : 2.12   Mean   : 1.48  
##  3rd Qu.: 3.00   3rd Qu.:3.00   3rd Qu.: 3.00   3rd Qu.: 2.00  
##  Max.   :42.00   Max.   :4.00   Max.   : 3.00   Max.   : 3.00  
##                                                                
##    CABLESAT1       COMBODVR1         DVR1         DIGITSTB1    
##  Min.   :-2.00   Min.   :-2.0   Min.   :-2.00   Min.   :-2.00  
##  1st Qu.: 0.00   1st Qu.:-2.0   1st Qu.: 0.00   1st Qu.: 0.00  
##  Median : 1.00   Median : 0.0   Median : 0.00   Median : 0.00  
##  Mean   : 0.76   Mean   :-0.8   Mean   :-0.24   Mean   : 0.12  
##  3rd Qu.: 2.00   3rd Qu.: 0.0   3rd Qu.: 0.00   3rd Qu.: 0.00  
##  Max.   : 2.00   Max.   : 1.0   Max.   : 1.00   Max.   : 1.00  
##                                                                
##     PLAYSTA1      COMBOVCRDVD1        VCR1            DVD1     
##  Min.   :-2.00   Min.   :-2.00   Min.   :-2.00   Min.   :-2.0  
##  1st Qu.: 0.00   1st Qu.: 0.00   1st Qu.: 0.00   1st Qu.: 0.0  
##  Median : 0.00   Median : 0.00   Median : 0.00   Median : 1.0  
##  Mean   : 0.16   Mean   : 0.12   Mean   : 0.04   Mean   : 0.6  
##  3rd Qu.: 0.00   3rd Qu.: 0.00   3rd Qu.: 0.00   3rd Qu.: 1.0  
##  Max.   : 1.00   Max.   : 1.00   Max.   : 1.00   Max.   : 1.0  
##                                                                
##   TVAUDIOSYS1   OTHERSTB1        TVONWD1       TVONWDWATCH1  
##  Min.   :-2   Min.   :-2.00   Min.   :-2.00   Min.   :-2.00  
##  1st Qu.: 0   1st Qu.: 0.00   1st Qu.: 2.00   1st Qu.:-2.00  
##  Median : 0   Median : 0.00   Median : 3.00   Median :-2.00  
##  Mean   : 0   Mean   :-0.04   Mean   : 2.72   Mean   :-0.84  
##  3rd Qu.: 0   3rd Qu.: 0.00   3rd Qu.: 4.00   3rd Qu.:-2.00  
##  Max.   : 1   Max.   : 1.00   Max.   : 5.00   Max.   : 4.00  
##                                                              
##     TVONWE1       TVONWEWATCH1      TVSIZE2         TVTYPE2     
##  Min.   :-2.00   Min.   :-2.00   Min.   :-2.00   Min.   :-2.00  
##  1st Qu.: 2.00   1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.00  
##  Median : 3.00   Median :-2.00   Median : 1.00   Median : 1.00  
##  Mean   : 2.88   Mean   :-1.04   Mean   : 0.52   Mean   : 0.32  
##  3rd Qu.: 4.00   3rd Qu.:-2.00   3rd Qu.: 2.00   3rd Qu.: 1.00  
##  Max.   : 5.00   Max.   : 4.00   Max.   : 3.00   Max.   : 2.00  
##                                                                 
##    CABLESAT2      COMBODVR2       DVR2         DIGITSTB2   
##  Min.   :-2.0   Min.   :-2   Min.   :-2.00   Min.   :-2.0  
##  1st Qu.:-2.0   1st Qu.:-2   1st Qu.:-2.00   1st Qu.:-2.0  
##  Median : 0.0   Median :-2   Median : 0.00   Median : 0.0  
##  Mean   : 0.2   Mean   :-1   Mean   :-0.76   Mean   :-0.4  
##  3rd Qu.: 2.0   3rd Qu.: 0   3rd Qu.: 0.00   3rd Qu.: 0.0  
##  Max.   : 2.0   Max.   : 1   Max.   : 1.00   Max.   : 1.0  
##                                                            
##     PLAYSTA2      COMBOVCRDVD2        VCR2            DVD2      
##  Min.   :-2.00   Min.   :-2.00   Min.   :-2.00   Min.   :-2.00  
##  1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.00  
##  Median : 0.00   Median : 0.00   Median : 0.00   Median : 0.00  
##  Mean   :-0.44   Mean   :-0.52   Mean   :-0.56   Mean   :-0.52  
##  3rd Qu.: 0.00   3rd Qu.: 0.00   3rd Qu.: 0.00   3rd Qu.: 0.00  
##  Max.   : 1.00   Max.   : 1.00   Max.   : 0.00   Max.   : 1.00  
##                                                                 
##   TVAUDIOSYS2      OTHERSTB2        TVONWD2       TVONWDWATCH2  
##  Min.   :-2.00   Min.   :-2.00   Min.   :-2.00   Min.   :-2.00  
##  1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.00  
##  Median : 0.00   Median : 0.00   Median : 1.00   Median :-2.00  
##  Mean   :-0.52   Mean   :-0.56   Mean   : 0.92   Mean   :-1.56  
##  3rd Qu.: 0.00   3rd Qu.: 0.00   3rd Qu.: 2.00   3rd Qu.:-2.00  
##  Max.   : 1.00   Max.   : 0.00   Max.   : 5.00   Max.   : 4.00  
##                                                                 
##     TVONWE2       TVONWEWATCH2      TVSIZE3         TVTYPE3     
##  Min.   :-2.00   Min.   :-2.00   Min.   :-2.00   Min.   :-2.00  
##  1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.00  
##  Median : 1.00   Median :-2.00   Median :-2.00   Median :-2.00  
##  Mean   : 0.84   Mean   :-1.56   Mean   :-0.96   Mean   :-0.96  
##  3rd Qu.: 2.00   3rd Qu.:-2.00   3rd Qu.: 1.00   3rd Qu.: 1.00  
##  Max.   : 5.00   Max.   : 4.00   Max.   : 3.00   Max.   : 4.00  
##                                                                 
##    CABLESAT3       COMBODVR3         DVR3         DIGITSTB3    
##  Min.   :-2.00   Min.   :-2.0   Min.   :-2.00   Min.   :-2.00  
##  1st Qu.:-2.00   1st Qu.:-2.0   1st Qu.:-2.00   1st Qu.:-2.00  
##  Median :-2.00   Median :-2.0   Median :-2.00   Median :-2.00  
##  Mean   :-1.32   Mean   :-1.8   Mean   :-1.52   Mean   :-1.36  
##  3rd Qu.: 0.00   3rd Qu.:-2.0   3rd Qu.:-2.00   3rd Qu.: 0.00  
##  Max.   : 2.00   Max.   : 1.0   Max.   : 0.00   Max.   : 1.00  
##                                                                
##     PLAYSTA3      COMBOVCRDVD3        VCR3           DVD3     
##  Min.   :-2.00   Min.   :-2.00   Min.   :-2.0   Min.   :-2.0  
##  1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.0   1st Qu.:-2.0  
##  Median :-2.00   Median :-2.00   Median :-2.0   Median :-2.0  
##  Mean   :-1.44   Mean   :-1.44   Mean   :-1.4   Mean   :-1.4  
##  3rd Qu.: 0.00   3rd Qu.: 0.00   3rd Qu.: 0.0   3rd Qu.: 0.0  
##  Max.   : 0.00   Max.   : 0.00   Max.   : 1.0   Max.   : 1.0  
##                                                               
##   TVAUDIOSYS3      OTHERSTB3        TVONWD3      TVONWDWATCH3
##  Min.   :-2.00   Min.   :-2.00   Min.   :-2.0   Min.   :-2   
##  1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.0   1st Qu.:-2   
##  Median :-2.00   Median :-2.00   Median :-2.0   Median :-2   
##  Mean   :-1.44   Mean   :-1.44   Mean   :-0.8   Mean   :-2   
##  3rd Qu.: 0.00   3rd Qu.: 0.00   3rd Qu.: 1.0   3rd Qu.:-2   
##  Max.   : 0.00   Max.   : 0.00   Max.   : 5.0   Max.   :-2   
##                                                              
##     TVONWE3       TVONWEWATCH3    COMPUTER       NUMPC     
##  Min.   :-2.00   Min.   :-2    Min.   :0.0   Min.   :0.00  
##  1st Qu.:-2.00   1st Qu.:-2    1st Qu.:0.0   1st Qu.:0.00  
##  Median :-2.00   Median :-2    Median :0.0   Median :0.00  
##  Mean   :-0.72   Mean   :-2    Mean   :0.4   Mean   :0.48  
##  3rd Qu.: 1.00   3rd Qu.:-2    3rd Qu.:1.0   3rd Qu.:1.00  
##  Max.   : 5.00   Max.   :-2    Max.   :1.0   Max.   :2.00  
##                                                            
##     PCTYPE1         MONITOR1        TIMEON1         PCONOFF1    
##  Min.   :-2.00   Min.   :-2.00   Min.   :-2.00   Min.   :-2.00  
##  1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.00  
##  Median :-2.00   Median :-2.00   Median :-2.00   Median :-2.00  
##  Mean   :-0.64   Mean   :-1.32   Mean   :-0.08   Mean   :-0.96  
##  3rd Qu.: 1.00   3rd Qu.:-2.00   3rd Qu.: 2.00   3rd Qu.: 0.00  
##  Max.   : 2.00   Max.   : 1.00   Max.   : 5.00   Max.   : 1.00  
##                                                                 
##     PCSLEEP1        PCTYPE2         MONITOR2        TIMEON2     
##  Min.   :-2.00   Min.   :-2.00   Min.   :-2.00   Min.   :-2.00  
##  1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.00  
##  Median :-2.00   Median :-2.00   Median :-2.00   Median :-2.00  
##  Mean   :-1.56   Mean   :-1.72   Mean   :-1.88   Mean   :-1.76  
##  3rd Qu.:-2.00   3rd Qu.:-2.00   3rd Qu.:-2.00   3rd Qu.:-2.00  
##  Max.   : 1.00   Max.   : 2.00   Max.   : 1.00   Max.   : 1.00  
##                                                                 
##     PCONOFF2        PCSLEEP2     PCTYPE3      MONITOR3     TIMEON3  
##  Min.   :-2.00   Min.   :-2   Min.   :-2   Min.   :-2   Min.   :-2  
##  1st Qu.:-2.00   1st Qu.:-2   1st Qu.:-2   1st Qu.:-2   1st Qu.:-2  
##  Median :-2.00   Median :-2   Median :-2   Median :-2   Median :-2  
##  Mean   :-1.76   Mean   :-2   Mean   :-2   Mean   :-2   Mean   :-2  
##  3rd Qu.:-2.00   3rd Qu.:-2   3rd Qu.:-2   3rd Qu.:-2   3rd Qu.:-2  
##  Max.   : 1.00   Max.   :-2   Max.   :-2   Max.   :-2   Max.   :-2  
##                                                                     
##     PCONOFF3     PCSLEEP3     INTERNET       INDIALUP         INDSL      
##  Min.   :-2   Min.   :-2   Min.   :-2.0   Min.   :-2.00   Min.   :-2.00  
##  1st Qu.:-2   1st Qu.:-2   1st Qu.:-2.0   1st Qu.:-2.00   1st Qu.:-2.00  
##  Median :-2   Median :-2   Median :-2.0   Median :-2.00   Median :-2.00  
##  Mean   :-2   Mean   :-2   Mean   :-0.8   Mean   :-1.16   Mean   :-1.12  
##  3rd Qu.:-2   3rd Qu.:-2   3rd Qu.: 1.0   3rd Qu.: 0.00   3rd Qu.: 0.00  
##  Max.   :-2   Max.   :-2   Max.   : 1.0   Max.   : 1.00   Max.   : 1.00  
##                                                                          
##     INCABLE         INSATEL        INWIRELESS       PCPRINT     
##  Min.   :-2.00   Min.   :-2.00   Min.   :-2.00   Min.   :-2.00  
##  1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.00  
##  Median :-2.00   Median :-2.00   Median :-2.00   Median :-2.00  
##  Mean   :-1.04   Mean   :-1.12   Mean   :-0.88   Mean   :-0.84  
##  3rd Qu.: 0.00   3rd Qu.: 0.00   3rd Qu.: 1.00   3rd Qu.: 1.00  
##  Max.   : 1.00   Max.   : 1.00   Max.   : 1.00   Max.   : 1.00  
##                                                                 
##       FAX           COPIER        WELLPUMP        DIPSTICK    
##  Min.   :0.00   Min.   :0.00   Min.   :-2.00   Min.   :-2.00  
##  1st Qu.:0.00   1st Qu.:0.00   1st Qu.:-2.00   1st Qu.:-2.00  
##  Median :0.00   Median :0.00   Median : 0.00   Median :-2.00  
##  Mean   :0.04   Mean   :0.08   Mean   :-0.32   Mean   :-1.68  
##  3rd Qu.:0.00   3rd Qu.:0.00   3rd Qu.: 0.00   3rd Qu.:-2.00  
##  Max.   :1.00   Max.   :1.00   Max.   : 1.00   Max.   : 0.00  
##                                                               
##     SWAMPCOL        AQUARIUM        STEREO        NOCORD       ANSMACH    
##  Min.   :-2.00   Min.   :0.00   Min.   :0.0   Min.   :0.0   Min.   :0.00  
##  1st Qu.:-2.00   1st Qu.:0.00   1st Qu.:0.0   1st Qu.:0.0   1st Qu.:0.00  
##  Median :-2.00   Median :0.00   Median :0.0   Median :1.0   Median :0.00  
##  Mean   :-1.52   Mean   :0.12   Mean   :0.4   Mean   :0.6   Mean   :0.48  
##  3rd Qu.:-2.00   3rd Qu.:0.00   3rd Qu.:1.0   3rd Qu.:1.0   3rd Qu.:1.00  
##  Max.   : 0.00   Max.   :1.00   Max.   :1.0   Max.   :1.0   Max.   :1.00  
##                                                                           
##     BATTOOLS       BATCHRG      CHRGPLGT       ELECDEV        ELECCHRG    
##  Min.   :0.00   Min.   :-2   Min.   :-2.0   Min.   :0.00   Min.   :-2.00  
##  1st Qu.:0.00   1st Qu.:-2   1st Qu.:-2.0   1st Qu.:1.00   1st Qu.: 1.00  
##  Median :1.00   Median : 1   Median :-2.0   Median :1.00   Median : 2.00  
##  Mean   :0.68   Mean   : 0   Mean   :-1.2   Mean   :0.96   Mean   : 1.28  
##  3rd Qu.:1.00   3rd Qu.: 2   3rd Qu.: 0.0   3rd Qu.:1.00   3rd Qu.: 2.00  
##  Max.   :2.00   Max.   : 3   Max.   : 0.0   Max.   :2.00   Max.   : 3.00  
##                                                                           
##     CHRGPLGE       ZCWASHER   ZTOPFRONT   ZWASHLOAD   ZWASHTEMP
##  Min.   :-2.0   Min.   :0   Min.   :0   Min.   :0   Min.   :0  
##  1st Qu.:-2.0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0  
##  Median : 0.0   Median :0   Median :0   Median :0   Median :0  
##  Mean   :-0.2   Mean   :0   Mean   :0   Mean   :0   Mean   :0  
##  3rd Qu.: 1.0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0  
##  Max.   : 2.0   Max.   :0   Max.   :0   Max.   :0   Max.   :0  
##                                                                
##    ZRNSETEMP      ZAGECWASH        ZDRYER    ZDRYRFUEL    ZDRYRUSE
##  Min.   :0.00   Min.   :0.00   Min.   :0   Min.   :0   Min.   :0  
##  1st Qu.:0.00   1st Qu.:0.00   1st Qu.:0   1st Qu.:0   1st Qu.:0  
##  Median :0.00   Median :0.00   Median :0   Median :0   Median :0  
##  Mean   :0.04   Mean   :0.04   Mean   :0   Mean   :0   Mean   :0  
##  3rd Qu.:0.00   3rd Qu.:0.00   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0  
##  Max.   :1.00   Max.   :1.00   Max.   :0   Max.   :0   Max.   :0  
##                                                                   
##    ZAGECDRYER      ZTVCOLOR    ZTVSIZE1    ZTVTYPE1      ZCABLESAT1
##  Min.   :0.00   Min.   :0   Min.   :0   Min.   :0.00   Min.   :0   
##  1st Qu.:0.00   1st Qu.:0   1st Qu.:0   1st Qu.:0.00   1st Qu.:0   
##  Median :0.00   Median :0   Median :0   Median :0.00   Median :0   
##  Mean   :0.04   Mean   :0   Mean   :0   Mean   :0.04   Mean   :0   
##  3rd Qu.:0.00   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0.00   3rd Qu.:0   
##  Max.   :1.00   Max.   :0   Max.   :0   Max.   :1.00   Max.   :0   
##                                                                    
##    ZCOMBODVR1     ZDVR1     ZDIGITSTB1   ZPLAYSTA1 ZCOMBOVCRDVD1
##  Min.   :0    Min.   :0   Min.   :0    Min.   :0   Min.   :0    
##  1st Qu.:0    1st Qu.:0   1st Qu.:0    1st Qu.:0   1st Qu.:0    
##  Median :0    Median :0   Median :0    Median :0   Median :0    
##  Mean   :0    Mean   :0   Mean   :0    Mean   :0   Mean   :0    
##  3rd Qu.:0    3rd Qu.:0   3rd Qu.:0    3rd Qu.:0   3rd Qu.:0    
##  Max.   :0    Max.   :0   Max.   :0    Max.   :0   Max.   :0    
##                                                                 
##      ZVCR1       ZDVD1    ZTVAUDIOSYS1   ZOTHERSTB1    ZTVONWD1
##  Min.   :0   Min.   :0   Min.   :0     Min.   :0    Min.   :0  
##  1st Qu.:0   1st Qu.:0   1st Qu.:0     1st Qu.:0    1st Qu.:0  
##  Median :0   Median :0   Median :0     Median :0    Median :0  
##  Mean   :0   Mean   :0   Mean   :0     Mean   :0    Mean   :0  
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0     3rd Qu.:0    3rd Qu.:0  
##  Max.   :0   Max.   :0   Max.   :0     Max.   :0    Max.   :0  
##                                                                
##  ZTVONWDWATCH1    ZTVONWE1 ZTVONWEWATCH1    ZTVSIZE2    ZTVTYPE2
##  Min.   :0     Min.   :0   Min.   :0     Min.   :0   Min.   :0  
##  1st Qu.:0     1st Qu.:0   1st Qu.:0     1st Qu.:0   1st Qu.:0  
##  Median :0     Median :0   Median :0     Median :0   Median :0  
##  Mean   :0     Mean   :0   Mean   :0     Mean   :0   Mean   :0  
##  3rd Qu.:0     3rd Qu.:0   3rd Qu.:0     3rd Qu.:0   3rd Qu.:0  
##  Max.   :0     Max.   :0   Max.   :0     Max.   :0   Max.   :0  
##                                                                 
##    ZCABLESAT2   ZCOMBODVR2     ZDVR2     ZDIGITSTB2   ZPLAYSTA2
##  Min.   :0    Min.   :0    Min.   :0   Min.   :0    Min.   :0  
##  1st Qu.:0    1st Qu.:0    1st Qu.:0   1st Qu.:0    1st Qu.:0  
##  Median :0    Median :0    Median :0   Median :0    Median :0  
##  Mean   :0    Mean   :0    Mean   :0   Mean   :0    Mean   :0  
##  3rd Qu.:0    3rd Qu.:0    3rd Qu.:0   3rd Qu.:0    3rd Qu.:0  
##  Max.   :0    Max.   :0    Max.   :0   Max.   :0    Max.   :0  
##                                                                
##  ZCOMBOVCRDVD2     ZVCR2       ZDVD2    ZTVAUDIOSYS2   ZOTHERSTB2
##  Min.   :0     Min.   :0   Min.   :0   Min.   :0     Min.   :0   
##  1st Qu.:0     1st Qu.:0   1st Qu.:0   1st Qu.:0     1st Qu.:0   
##  Median :0     Median :0   Median :0   Median :0     Median :0   
##  Mean   :0     Mean   :0   Mean   :0   Mean   :0     Mean   :0   
##  3rd Qu.:0     3rd Qu.:0   3rd Qu.:0   3rd Qu.:0     3rd Qu.:0   
##  Max.   :0     Max.   :0   Max.   :0   Max.   :0     Max.   :0   
##                                                                  
##     ZTVONWD2 ZTVONWDWATCH2    ZTVONWE2 ZTVONWEWATCH2    ZTVSIZE3
##  Min.   :0   Min.   :0     Min.   :0   Min.   :0     Min.   :0  
##  1st Qu.:0   1st Qu.:0     1st Qu.:0   1st Qu.:0     1st Qu.:0  
##  Median :0   Median :0     Median :0   Median :0     Median :0  
##  Mean   :0   Mean   :0     Mean   :0   Mean   :0     Mean   :0  
##  3rd Qu.:0   3rd Qu.:0     3rd Qu.:0   3rd Qu.:0     3rd Qu.:0  
##  Max.   :0   Max.   :0     Max.   :0   Max.   :0     Max.   :0  
##                                                                 
##     ZTVTYPE3   ZCABLESAT3   ZCOMBODVR3     ZDVR3     ZDIGITSTB3
##  Min.   :0   Min.   :0    Min.   :0    Min.   :0   Min.   :0   
##  1st Qu.:0   1st Qu.:0    1st Qu.:0    1st Qu.:0   1st Qu.:0   
##  Median :0   Median :0    Median :0    Median :0   Median :0   
##  Mean   :0   Mean   :0    Mean   :0    Mean   :0   Mean   :0   
##  3rd Qu.:0   3rd Qu.:0    3rd Qu.:0    3rd Qu.:0   3rd Qu.:0   
##  Max.   :0   Max.   :0    Max.   :0    Max.   :0   Max.   :0   
##                                                                
##    ZPLAYSTA3 ZCOMBOVCRDVD3     ZVCR3       ZDVD3    ZTVAUDIOSYS3
##  Min.   :0   Min.   :0     Min.   :0   Min.   :0   Min.   :0    
##  1st Qu.:0   1st Qu.:0     1st Qu.:0   1st Qu.:0   1st Qu.:0    
##  Median :0   Median :0     Median :0   Median :0   Median :0    
##  Mean   :0   Mean   :0     Mean   :0   Mean   :0   Mean   :0    
##  3rd Qu.:0   3rd Qu.:0     3rd Qu.:0   3rd Qu.:0   3rd Qu.:0    
##  Max.   :0   Max.   :0     Max.   :0   Max.   :0   Max.   :0    
##                                                                 
##    ZOTHERSTB3    ZTVONWD3 ZTVONWDWATCH3    ZTVONWE3 ZTVONWEWATCH3
##  Min.   :0    Min.   :0   Min.   :0     Min.   :0   Min.   :0    
##  1st Qu.:0    1st Qu.:0   1st Qu.:0     1st Qu.:0   1st Qu.:0    
##  Median :0    Median :0   Median :0     Median :0   Median :0    
##  Mean   :0    Mean   :0   Mean   :0     Mean   :0   Mean   :0    
##  3rd Qu.:0    3rd Qu.:0   3rd Qu.:0     3rd Qu.:0   3rd Qu.:0    
##  Max.   :0    Max.   :0   Max.   :0     Max.   :0   Max.   :0    
##                                                                  
##    ZCOMPUTER     ZNUMPC     ZPCTYPE1   ZMONITOR1    ZTIMEON1   ZPCONOFF1
##  Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0  
##  1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0  
##  Median :0   Median :0   Median :0   Median :0   Median :0   Median :0  
##  Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0  
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0  
##  Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0  
##                                                                         
##    ZPCSLEEP1    ZPCTYPE2   ZMONITOR2    ZTIMEON2   ZPCONOFF2   ZPCSLEEP2
##  Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0  
##  1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0  
##  Median :0   Median :0   Median :0   Median :0   Median :0   Median :0  
##  Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0  
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0  
##  Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0  
##                                                                         
##     ZPCTYPE3   ZMONITOR3    ZTIMEON3   ZPCONOFF3   ZPCSLEEP3   ZINTERNET
##  Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0  
##  1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0  
##  Median :0   Median :0   Median :0   Median :0   Median :0   Median :0  
##  Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0  
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0  
##  Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0  
##                                                                         
##    ZINDIALUP     ZINDSL     ZINCABLE    ZINSATEL  ZINWIRELESS    ZPCPRINT
##  Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0    Min.   :0  
##  1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0    1st Qu.:0  
##  Median :0   Median :0   Median :0   Median :0   Median :0    Median :0  
##  Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0    Mean   :0  
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0    3rd Qu.:0  
##  Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0    Max.   :0  
##                                                                          
##       ZFAX      ZCOPIER    ZWELLPUMP   ZDIPSTICK   ZSWAMPCOL   ZAQUARIUM
##  Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0  
##  1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0  
##  Median :0   Median :0   Median :0   Median :0   Median :0   Median :0  
##  Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0  
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0  
##  Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0  
##                                                                         
##     ZSTEREO     ZNOCORD     ZANSMACH   ZBATTOOLS    ZBATCHRG   ZCHRGPLGT
##  Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0  
##  1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0  
##  Median :0   Median :0   Median :0   Median :0   Median :0   Median :0  
##  Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0  
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0  
##  Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0  
##                                                                         
##     ZELECDEV   ZELECCHRG   ZCHRGPLGE    HEATHOME    DNTHEAT    EQUIPNOHEAT
##  Min.   :0   Min.   :0   Min.   :0   Min.   :1   Min.   :-2   Min.   :-2  
##  1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:1   1st Qu.:-2   1st Qu.:-2  
##  Median :0   Median :0   Median :0   Median :1   Median :-2   Median :-2  
##  Mean   :0   Mean   :0   Mean   :0   Mean   :1   Mean   :-2   Mean   :-2  
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:1   3rd Qu.:-2   3rd Qu.:-2  
##  Max.   :0   Max.   :0   Max.   :0   Max.   :1   Max.   :-2   Max.   :-2  
##                                                                           
##    FUELNOHEAT     EQUIPM        FUELHEAT      MAINTHT        EQUIPAGE    
##  Min.   :-2   Min.   :2.00   Min.   :1.0   Min.   :0.00   Min.   : 1.00  
##  1st Qu.:-2   1st Qu.:3.00   1st Qu.:1.0   1st Qu.:0.00   1st Qu.: 2.00  
##  Median :-2   Median :3.00   Median :2.0   Median :0.00   Median : 3.00  
##  Mean   :-2   Mean   :3.44   Mean   :2.4   Mean   :0.48   Mean   :15.12  
##  3rd Qu.:-2   3rd Qu.:3.00   3rd Qu.:2.0   3rd Qu.:1.00   3rd Qu.:41.00  
##  Max.   :-2   Max.   :8.00   Max.   :7.0   Max.   :1.00   Max.   :42.00  
##                                                                          
##     REPLCHT         HELPHT         HELPHTY         HEATOTH    
##  Min.   :-2.0   Min.   :-2.00   Min.   :-2.00   Min.   :0.00  
##  1st Qu.:-2.0   1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:0.00  
##  Median :-2.0   Median : 0.00   Median :-2.00   Median :0.00  
##  Mean   :-1.2   Mean   :-0.76   Mean   :-1.72   Mean   :0.12  
##  3rd Qu.: 0.0   3rd Qu.: 0.00   3rd Qu.:-2.00   3rd Qu.:0.00  
##  Max.   : 1.0   Max.   : 5.00   Max.   : 5.00   Max.   :1.00  
##                                                               
##     EQUIPAUX      REVERSE        WARMAIR     FURNFUEL      STEAMR 
##  Min.   :0.0   Min.   :0.00   Min.   :0   Min.   :-2   Min.   :0  
##  1st Qu.:0.0   1st Qu.:0.00   1st Qu.:0   1st Qu.:-2   1st Qu.:0  
##  Median :0.0   Median :0.00   Median :0   Median :-2   Median :0  
##  Mean   :0.4   Mean   :0.04   Mean   :0   Mean   :-2   Mean   :0  
##  3rd Qu.:1.0   3rd Qu.:0.00   3rd Qu.:0   3rd Qu.:-2   3rd Qu.:0  
##  Max.   :1.0   Max.   :1.00   Max.   :0   Max.   :-2   Max.   :0  
##                                                                   
##     RADFUEL      PERMELEC       PIPELESS    PIPEFUEL     ROOMHEAT
##  Min.   :-2   Min.   :0.00   Min.   :0   Min.   :-2   Min.   :0  
##  1st Qu.:-2   1st Qu.:0.00   1st Qu.:0   1st Qu.:-2   1st Qu.:0  
##  Median :-2   Median :0.00   Median :0   Median :-2   Median :0  
##  Mean   :-2   Mean   :0.08   Mean   :0   Mean   :-2   Mean   :0  
##  3rd Qu.:-2   3rd Qu.:0.00   3rd Qu.:0   3rd Qu.:-2   3rd Qu.:0  
##  Max.   :-2   Max.   :1.00   Max.   :0   Max.   :-2   Max.   :0  
##                                                                  
##     RMHTFUEL     WOODKILN        HSFUEL         CARRYEL        CARRYKER
##  Min.   :-2   Min.   :0.00   Min.   :-2.00   Min.   :0.00   Min.   :0  
##  1st Qu.:-2   1st Qu.:0.00   1st Qu.:-2.00   1st Qu.:0.00   1st Qu.:0  
##  Median :-2   Median :0.00   Median :-2.00   Median :0.00   Median :0  
##  Mean   :-2   Mean   :0.08   Mean   :-1.28   Mean   :0.16   Mean   :0  
##  3rd Qu.:-2   3rd Qu.:0.00   3rd Qu.:-2.00   3rd Qu.:0.00   3rd Qu.:0  
##  Max.   :-2   Max.   :1.00   Max.   : 7.00   Max.   :1.00   Max.   :0  
##                                                                        
##     CHIMNEY         FPFUEL         NGFPFLUE        USENGFP     
##  Min.   :0.00   Min.   :-2.00   Min.   :-2.00   Min.   :-2.00  
##  1st Qu.:0.00   1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.00  
##  Median :0.00   Median :-2.00   Median :-2.00   Median :-2.00  
##  Mean   :0.12   Mean   :-1.16   Mean   :-1.84   Mean   :-1.88  
##  3rd Qu.:0.00   3rd Qu.:-2.00   3rd Qu.:-2.00   3rd Qu.:-2.00  
##  Max.   :1.00   Max.   : 7.00   Max.   : 2.00   Max.   : 1.00  
##                                                                
##      RANGE         RNGFUEL         DIFEQUIP       DIFFUEL    
##  Min.   :0.00   Min.   :-2.00   Min.   :0.00   Min.   :-2.0  
##  1st Qu.:0.00   1st Qu.:-2.00   1st Qu.:0.00   1st Qu.:-2.0  
##  Median :0.00   Median :-2.00   Median :0.00   Median :-2.0  
##  Mean   :0.04   Mean   :-1.88   Mean   :0.04   Mean   :-1.6  
##  3rd Qu.:0.00   3rd Qu.:-2.00   3rd Qu.:0.00   3rd Qu.:-2.0  
##  Max.   :1.00   Max.   : 1.00   Max.   :1.00   Max.   : 8.0  
##                                                              
##      EQMAMT         HEATROOM       THERMAIN       NUMTHERM    
##  Min.   :-2.00   Min.   :1.00   Min.   :-2.0   Min.   :-2.00  
##  1st Qu.:-2.00   1st Qu.:4.00   1st Qu.: 1.0   1st Qu.: 1.00  
##  Median :-2.00   Median :4.00   Median : 1.0   Median : 1.00  
##  Mean   :-0.52   Mean   :4.48   Mean   : 0.8   Mean   : 0.84  
##  3rd Qu.: 1.00   3rd Qu.:5.00   3rd Qu.: 1.0   3rd Qu.: 1.00  
##  Max.   : 3.00   Max.   :9.00   Max.   : 1.0   Max.   : 2.00  
##                                                               
##     PROTHERM      AUTOHEATNITE    AUTOHEATDAY       TEMPHOME   
##  Min.   :-2.00   Min.   :-2.00   Min.   :-2.00   Min.   :65.0  
##  1st Qu.: 0.00   1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:69.0  
##  Median : 0.00   Median :-2.00   Median :-2.00   Median :71.0  
##  Mean   :-0.04   Mean   :-1.44   Mean   :-1.52   Mean   :71.6  
##  3rd Qu.: 0.00   3rd Qu.:-2.00   3rd Qu.:-2.00   3rd Qu.:73.0  
##  Max.   : 1.00   Max.   : 1.00   Max.   : 1.00   Max.   :85.0  
##                                                                
##     TEMPGONE        TEMPNITE        MOISTURE    USEMOISTURE      ZHEATHOME
##  Min.   :40.00   Min.   :46.00   Min.   :0.0   Min.   :-2.00   Min.   :0  
##  1st Qu.:65.00   1st Qu.:66.00   1st Qu.:0.0   1st Qu.:-2.00   1st Qu.:0  
##  Median :70.00   Median :70.00   Median :0.0   Median :-2.00   Median :0  
##  Mean   :66.28   Mean   :68.88   Mean   :0.2   Mean   :-1.16   Mean   :0  
##  3rd Qu.:72.00   3rd Qu.:72.00   3rd Qu.:0.0   3rd Qu.:-2.00   3rd Qu.:0  
##  Max.   :78.00   Max.   :85.00   Max.   :1.0   Max.   : 3.00   Max.   :0  
##                                                                           
##     ZDNTHEAT  ZEQUIPNOHEAT  ZFUELNOHEAT    ZEQUIPM    ZFUELHEAT
##  Min.   :0   Min.   :0     Min.   :0    Min.   :0   Min.   :0  
##  1st Qu.:0   1st Qu.:0     1st Qu.:0    1st Qu.:0   1st Qu.:0  
##  Median :0   Median :0     Median :0    Median :0   Median :0  
##  Mean   :0   Mean   :0     Mean   :0    Mean   :0   Mean   :0  
##  3rd Qu.:0   3rd Qu.:0     3rd Qu.:0    3rd Qu.:0   3rd Qu.:0  
##  Max.   :0   Max.   :0     Max.   :0    Max.   :0   Max.   :0  
##                                                                
##     ZMAINTHT   ZEQUIPAGE       ZHEATOTH   ZFURNFUEL    ZRADFUEL
##  Min.   :0   Min.   :0.00   Min.   :0   Min.   :0   Min.   :0  
##  1st Qu.:0   1st Qu.:0.00   1st Qu.:0   1st Qu.:0   1st Qu.:0  
##  Median :0   Median :0.00   Median :0   Median :0   Median :0  
##  Mean   :0   Mean   :0.16   Mean   :0   Mean   :0   Mean   :0  
##  3rd Qu.:0   3rd Qu.:0.00   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0  
##  Max.   :0   Max.   :1.00   Max.   :0   Max.   :0   Max.   :0  
##                                                                
##    ZPIPEFUEL   ZRMHTFUEL    ZHSFUEL     ZFPFUEL    ZNGFPFLUE    ZUSENGFP
##  Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0  
##  1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0  
##  Median :0   Median :0   Median :0   Median :0   Median :0   Median :0  
##  Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0  
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0  
##  Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0  
##                                                                         
##     ZRNGFUEL    ZDIFFUEL    ZEQMAMT    ZHEATROOM   ZTHERMAIN   ZNUMTHERM
##  Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0  
##  1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0  
##  Median :0   Median :0   Median :0   Median :0   Median :0   Median :0  
##  Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0  
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0  
##  Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0  
##                                                                         
##    ZPROTHERM ZAUTOHEATNITE  ZAUTOHEATDAY   ZTEMPHOME   ZTEMPGONE
##  Min.   :0   Min.   :0     Min.   :0     Min.   :0   Min.   :0  
##  1st Qu.:0   1st Qu.:0     1st Qu.:0     1st Qu.:0   1st Qu.:0  
##  Median :0   Median :0     Median :0     Median :0   Median :0  
##  Mean   :0   Mean   :0     Mean   :0     Mean   :0   Mean   :0  
##  3rd Qu.:0   3rd Qu.:0     3rd Qu.:0     3rd Qu.:0   3rd Qu.:0  
##  Max.   :0   Max.   :0     Max.   :0     Max.   :0   Max.   :0  
##                                                                 
##    ZTEMPNITE   ZMOISTURE  ZUSEMOISTURE  NUMH2ONOTNK   NUMH2OHTRS
##  Min.   :0   Min.   :0   Min.   :0     Min.   :0    Min.   :0   
##  1st Qu.:0   1st Qu.:0   1st Qu.:0     1st Qu.:0    1st Qu.:1   
##  Median :0   Median :0   Median :0     Median :0    Median :1   
##  Mean   :0   Mean   :0   Mean   :0     Mean   :0    Mean   :1   
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0     3rd Qu.:0    3rd Qu.:1   
##  Max.   :0   Max.   :0   Max.   :0     Max.   :0    Max.   :2   
##                                                                 
##     H2OTYPE1        FUELH2O        WHEATOTH        WHEATSIZ    
##  Min.   :-2.00   Min.   :-2.0   Min.   :-2.00   Min.   :-2.00  
##  1st Qu.: 1.00   1st Qu.: 1.0   1st Qu.: 0.00   1st Qu.: 2.00  
##  Median : 1.00   Median : 5.0   Median : 0.00   Median : 2.00  
##  Mean   : 0.88   Mean   : 3.2   Mean   : 0.08   Mean   : 1.88  
##  3rd Qu.: 1.00   3rd Qu.: 5.0   3rd Qu.: 0.00   3rd Qu.: 2.00  
##  Max.   : 1.00   Max.   : 5.0   Max.   : 1.00   Max.   : 3.00  
##                                                                
##     WHEATAGE        WHEATBKT         HELPWH         HELPWHY  
##  Min.   :-2.00   Min.   :-2.00   Min.   :-2.00   Min.   :-2  
##  1st Qu.: 2.00   1st Qu.: 0.00   1st Qu.:-2.00   1st Qu.:-2  
##  Median : 3.00   Median : 0.00   Median :-2.00   Median :-2  
##  Mean   :13.24   Mean   : 0.04   Mean   :-1.76   Mean   :-2  
##  3rd Qu.:41.00   3rd Qu.: 0.00   3rd Qu.:-2.00   3rd Qu.:-2  
##  Max.   :42.00   Max.   : 1.00   Max.   : 0.00   Max.   :-2  
##                                                              
##     H2OTYPE2        FUELH2O2       WHEATSIZ2      WHEATAGE2    
##  Min.   :-2.00   Min.   :-2.00   Min.   :-2.0   Min.   :-2.00  
##  1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.0   1st Qu.:-2.00  
##  Median :-2.00   Median :-2.00   Median :-2.0   Median :-2.00  
##  Mean   :-1.88   Mean   :-1.84   Mean   :-1.8   Mean   :-0.28  
##  3rd Qu.:-2.00   3rd Qu.:-2.00   3rd Qu.:-2.0   3rd Qu.:-2.00  
##  Max.   : 1.00   Max.   : 2.00   Max.   : 3.0   Max.   :41.00  
##                                                                
##   ZNUMH2OHTRS  ZNUMH2ONOTNK   ZH2OTYPE1    ZFUELH2O      ZWHEATOTH
##  Min.   :0    Min.   :0     Min.   :0   Min.   :0.00   Min.   :0  
##  1st Qu.:0    1st Qu.:0     1st Qu.:0   1st Qu.:0.00   1st Qu.:0  
##  Median :0    Median :0     Median :0   Median :0.00   Median :0  
##  Mean   :0    Mean   :0     Mean   :0   Mean   :0.04   Mean   :0  
##  3rd Qu.:0    3rd Qu.:0     3rd Qu.:0   3rd Qu.:0.00   3rd Qu.:0  
##  Max.   :0    Max.   :0     Max.   :0   Max.   :1.00   Max.   :0  
##                                                                   
##    ZWHEATSIZ      ZWHEATAGE      ZWHEATBKT      ZH2OTYPE2   ZFUELH2O2
##  Min.   :0.00   Min.   :0.00   Min.   :0.00   Min.   :0   Min.   :0  
##  1st Qu.:0.00   1st Qu.:0.00   1st Qu.:0.00   1st Qu.:0   1st Qu.:0  
##  Median :0.00   Median :0.00   Median :0.00   Median :0   Median :0  
##  Mean   :0.08   Mean   :0.24   Mean   :0.04   Mean   :0   Mean   :0  
##  3rd Qu.:0.00   3rd Qu.:0.00   3rd Qu.:0.00   3rd Qu.:0   3rd Qu.:0  
##  Max.   :1.00   Max.   :1.00   Max.   :1.00   Max.   :0   Max.   :0  
##                                                                      
##    ZWHEATSIZ2   ZWHEATAGE2    AIRCOND         DNTAC        COOLTYPENOAC  
##  Min.   :0    Min.   :0    Min.   :0.00   Min.   :-2.00   Min.   :-2.00  
##  1st Qu.:0    1st Qu.:0    1st Qu.:1.00   1st Qu.:-2.00   1st Qu.:-2.00  
##  Median :0    Median :0    Median :1.00   Median :-2.00   Median :-2.00  
##  Mean   :0    Mean   :0    Mean   :0.76   Mean   :-1.12   Mean   :-1.76  
##  3rd Qu.:0    3rd Qu.:0    3rd Qu.:1.00   3rd Qu.:-2.00   3rd Qu.:-2.00  
##  Max.   :0    Max.   :0    Max.   :1.00   Max.   : 2.00   Max.   : 1.00  
##                                                                          
##     COOLTYPE         DUCTS       CENACHP         ACOTHERS    
##  Min.   :-2.00   Min.   :-2   Min.   :-2.00   Min.   :-2.00  
##  1st Qu.: 1.00   1st Qu.:-2   1st Qu.:-2.00   1st Qu.:-2.00  
##  Median : 1.00   Median :-2   Median :-2.00   Median :-2.00  
##  Mean   : 0.64   Mean   :-2   Mean   :-1.16   Mean   :-1.16  
##  3rd Qu.: 2.00   3rd Qu.:-2   3rd Qu.: 0.00   3rd Qu.: 0.00  
##  Max.   : 2.00   Max.   :-2   Max.   : 1.00   Max.   : 1.00  
##                                                              
##     MAINTAC         AGECENAC        REPLCCAC        HELPCAC     
##  Min.   :-2.00   Min.   :-2.00   Min.   :-2.00   Min.   :-2.00  
##  1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.00  
##  Median :-2.00   Median :-2.00   Median :-2.00   Median :-2.00  
##  Mean   :-0.92   Mean   : 5.76   Mean   :-1.44   Mean   :-1.32  
##  3rd Qu.: 1.00   3rd Qu.: 1.00   3rd Qu.:-2.00   3rd Qu.: 0.00  
##  Max.   : 1.00   Max.   :42.00   Max.   : 1.00   Max.   : 3.00  
##                                                                 
##     HELPCACY        ACROOMS        USECENAC       THERMAINAC  
##  Min.   :-2.00   Min.   :-2.0   Min.   :-2.00   Min.   :-2.0  
##  1st Qu.:-2.00   1st Qu.:-2.0   1st Qu.:-2.00   1st Qu.:-2.0  
##  Median :-2.00   Median :-2.0   Median :-2.00   Median :-2.0  
##  Mean   :-1.72   Mean   : 0.8   Mean   :-0.12   Mean   :-0.8  
##  3rd Qu.:-2.00   3rd Qu.: 4.0   3rd Qu.: 3.00   3rd Qu.: 1.0  
##  Max.   : 5.00   Max.   : 8.0   Max.   : 3.00   Max.   : 1.0  
##                                                               
##    PROTHERMAC     AUTOCOOLNITE   AUTOCOOLDAY     TEMPHOMEAC   
##  Min.   :-2.00   Min.   :-2.0   Min.   :-2.0   Min.   :-2.00  
##  1st Qu.:-2.00   1st Qu.:-2.0   1st Qu.:-2.0   1st Qu.:-2.00  
##  Median :-2.00   Median :-2.0   Median :-2.0   Median :-2.00  
##  Mean   :-1.12   Mean   :-1.8   Mean   :-1.8   Mean   :25.08  
##  3rd Qu.: 0.00   3rd Qu.:-2.0   3rd Qu.:-2.0   3rd Qu.:71.00  
##  Max.   : 1.00   Max.   : 1.0   Max.   : 1.0   Max.   :78.00  
##                                                               
##    TEMPGONEAC      TEMPNITEAC       NUMBERAC        WWACAGE     
##  Min.   :-2.00   Min.   :-2.00   Min.   :-2.00   Min.   :-2.00  
##  1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.00  
##  Median :-2.00   Median :-2.00   Median :-2.00   Median :-2.00  
##  Mean   :25.56   Mean   :25.08   Mean   :-0.52   Mean   : 2.72  
##  3rd Qu.:72.00   3rd Qu.:71.00   3rd Qu.: 1.00   3rd Qu.: 2.00  
##  Max.   :78.00   Max.   :78.00   Max.   : 5.00   Max.   :42.00  
##                                                                 
##      ESWWAC        REPLCWWAC        HELPWWAC       HELPWWACY 
##  Min.   :-9.00   Min.   :-2.00   Min.   :-2.00   Min.   :-2  
##  1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2  
##  Median :-2.00   Median :-2.00   Median :-2.00   Median :-2  
##  Mean   :-1.64   Mean   :-1.64   Mean   :-1.76   Mean   :-2  
##  3rd Qu.:-2.00   3rd Qu.:-2.00   3rd Qu.:-2.00   3rd Qu.:-2  
##  Max.   : 1.00   Max.   : 1.00   Max.   : 0.00   Max.   :-2  
##                                                              
##     USEWWAC        NUMCFAN       USECFAN      TREESHAD       NOTMOIST   
##  Min.   :-2.0   Min.   :0.0   Min.   :-2   Min.   :0.00   Min.   :0.00  
##  1st Qu.:-2.0   1st Qu.:0.0   1st Qu.:-2   1st Qu.:0.00   1st Qu.:0.00  
##  Median :-2.0   Median :1.0   Median : 1   Median :1.00   Median :0.00  
##  Mean   :-0.6   Mean   :1.8   Mean   : 1   Mean   :0.56   Mean   :0.16  
##  3rd Qu.: 1.0   3rd Qu.:3.0   3rd Qu.: 3   3rd Qu.:1.00   3rd Qu.:0.00  
##  Max.   : 3.0   Max.   :6.0   Max.   : 4   Max.   :1.00   Max.   :1.00  
##                                                                         
##   USENOTMOIST       ZAIRCOND     ZDNTAC  ZCOOLTYPENOAC   ZCOOLTYPE
##  Min.   :-2.00   Min.   :0   Min.   :0   Min.   :0     Min.   :0  
##  1st Qu.:-2.00   1st Qu.:0   1st Qu.:0   1st Qu.:0     1st Qu.:0  
##  Median :-2.00   Median :0   Median :0   Median :0     Median :0  
##  Mean   :-1.48   Mean   :0   Mean   :0   Mean   :0     Mean   :0  
##  3rd Qu.:-2.00   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0     3rd Qu.:0  
##  Max.   : 2.00   Max.   :0   Max.   :0   Max.   :0     Max.   :0  
##                                                                   
##      ZDUCTS     ZCENACHP   ZACOTHERS    ZMAINTAC   ZAGECENAC   ZUSECENAC
##  Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0  
##  1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0  
##  Median :0   Median :0   Median :0   Median :0   Median :0   Median :0  
##  Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0  
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0  
##  Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0  
##                                                                         
##     ZACROOMS  ZTHERMAINAC  ZPROTHERMAC ZAUTOCOOLNITE  ZAUTOCOOLDAY
##  Min.   :0   Min.   :0    Min.   :0    Min.   :0     Min.   :0    
##  1st Qu.:0   1st Qu.:0    1st Qu.:0    1st Qu.:0     1st Qu.:0    
##  Median :0   Median :0    Median :0    Median :0     Median :0    
##  Mean   :0   Mean   :0    Mean   :0    Mean   :0     Mean   :0    
##  3rd Qu.:0   3rd Qu.:0    3rd Qu.:0    3rd Qu.:0     3rd Qu.:0    
##  Max.   :0   Max.   :0    Max.   :0    Max.   :0     Max.   :0    
##                                                                   
##   ZTEMPHOMEAC  ZTEMPGONEAC  ZTEMPNITEAC   ZNUMBERAC    ZWWACAGE
##  Min.   :0    Min.   :0    Min.   :0    Min.   :0   Min.   :0  
##  1st Qu.:0    1st Qu.:0    1st Qu.:0    1st Qu.:0   1st Qu.:0  
##  Median :0    Median :0    Median :0    Median :0   Median :0  
##  Mean   :0    Mean   :0    Mean   :0    Mean   :0   Mean   :0  
##  3rd Qu.:0    3rd Qu.:0    3rd Qu.:0    3rd Qu.:0   3rd Qu.:0  
##  Max.   :0    Max.   :0    Max.   :0    Max.   :0   Max.   :0  
##                                                                
##     ZUSEWWAC    ZNUMCFAN    ZUSECFAN      ZTREESHAD   ZNOTMOIST   
##  Min.   :0   Min.   :0   Min.   :0.00   Min.   :0   Min.   :0.00  
##  1st Qu.:0   1st Qu.:0   1st Qu.:0.00   1st Qu.:0   1st Qu.:0.00  
##  Median :0   Median :0   Median :0.00   Median :0   Median :0.00  
##  Mean   :0   Mean   :0   Mean   :0.04   Mean   :0   Mean   :0.04  
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0.00   3rd Qu.:0   3rd Qu.:0.00  
##  Max.   :0   Max.   :0   Max.   :1.00   Max.   :0   Max.   :1.00  
##                                                                   
##   ZUSENOTMOIST    HIGHCEIL       CATHCEIL        SWIMPOOL          POOL   
##  Min.   :0     Min.   :-2.0   Min.   :-2.00   Min.   :-2.00   Min.   :-2  
##  1st Qu.:0     1st Qu.:-2.0   1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2  
##  Median :0     Median : 0.0   Median :-2.00   Median :-2.00   Median :-2  
##  Mean   :0     Mean   :-0.6   Mean   :-1.64   Mean   :-1.28   Mean   :-2  
##  3rd Qu.:0     3rd Qu.: 0.0   3rd Qu.:-2.00   3rd Qu.: 0.00   3rd Qu.:-2  
##  Max.   :0     Max.   : 1.0   Max.   : 1.00   Max.   : 0.00   Max.   :-2  
##                                                                           
##     FUELPOOL   RECBATH      FUELTUB       LGT12         LGT12EE    
##  NG     : 0   FALSE:24   NG     : 0   Min.   :0.00   Min.   :-2.0  
##  LPG    : 0   TRUE : 1   LPG    : 1   1st Qu.:0.00   1st Qu.:-2.0  
##  FuelOil: 0              FuelOil: 0   Median :0.00   Median :-2.0  
##  Elec   : 0              Elec   : 0   Mean   :0.56   Mean   :-1.4  
##  Solar  : 0              Solar  : 0   3rd Qu.:0.00   3rd Qu.:-2.0  
##  Other  : 0              Other  : 0   Max.   :9.00   Max.   : 9.0  
##  NA's   :25              NA's   :24                                
##       LGT4          LGT4EE          LGT1          LGT1EE    
##  Min.   :0.00   Min.   :-2.0   Min.   :0.00   Min.   :-2.0  
##  1st Qu.:0.00   1st Qu.:-2.0   1st Qu.:0.00   1st Qu.:-2.0  
##  Median :1.00   Median : 0.0   Median :1.00   Median : 0.0  
##  Mean   :1.28   Mean   :-0.2   Mean   :1.56   Mean   : 0.2  
##  3rd Qu.:2.00   3rd Qu.: 1.0   3rd Qu.:2.00   3rd Qu.: 1.0  
##  Max.   :5.00   Max.   : 5.0   Max.   :5.00   Max.   : 5.0  
##                                                             
##    NOUTLGTNT         LGTOEE        NGASLIGHT        INSTLCFL   
##  Min.   :-2.00   Min.   :-2.00   Min.   :-2.00   Min.   :-2.0  
##  1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.0  
##  Median :-2.00   Median :-2.00   Median :-2.00   Median :-2.0  
##  Mean   :-1.08   Mean   :-1.56   Mean   :-1.68   Mean   :-0.6  
##  3rd Qu.: 0.00   3rd Qu.:-2.00   3rd Qu.:-2.00   3rd Qu.: 1.0  
##  Max.   : 2.00   Max.   : 1.00   Max.   : 0.00   Max.   : 1.0  
##                                                                
##     HELPCFL         HELPCFLY        SLDDRS        DOOR1SUM   
##  Min.   :-2.00   Min.   :-2.0   Min.   :0.00   Min.   :0.00  
##  1st Qu.:-2.00   1st Qu.:-2.0   1st Qu.:0.00   1st Qu.:0.00  
##  Median :-2.00   Median :-2.0   Median :0.00   Median :0.00  
##  Mean   :-0.92   Mean   :-1.8   Mean   :0.04   Mean   :0.04  
##  3rd Qu.: 0.00   3rd Qu.:-2.0   3rd Qu.:0.00   3rd Qu.:0.00  
##  Max.   : 5.00   Max.   : 3.0   Max.   :1.00   Max.   :1.00  
##                                                              
##     WINDOWS           TYPEGLASS     NEWGLASS       HELPWIN    
##  Min.   :20.00   SinglePane:10   Min.   :1.00   Min.   :-9.0  
##  1st Qu.:30.00   DoublePane:15   1st Qu.:1.00   1st Qu.:-2.0  
##  Median :41.00   TriplePane: 0   Median :3.00   Median :-2.0  
##  Mean   :36.96                   Mean   :2.24   Mean   :-1.4  
##  3rd Qu.:41.00                   3rd Qu.:3.00   3rd Qu.: 0.0  
##  Max.   :60.00                   Max.   :3.00   Max.   : 0.0  
##                                                               
##     HELPWINY     ADQINSUL       INSTLINS        AGEINS        HELPINS     
##  Min.   :-2   Min.   :1.00   Min.   :0.00   Min.   :-2.0   Min.   :-2.00  
##  1st Qu.:-2   1st Qu.:1.00   1st Qu.:0.00   1st Qu.:-2.0   1st Qu.:-2.00  
##  Median :-2   Median :2.00   Median :0.00   Median :-2.0   Median :-2.00  
##  Mean   :-2   Mean   :1.84   Mean   :0.24   Mean   : 2.2   Mean   :-1.92  
##  3rd Qu.:-2   3rd Qu.:3.00   3rd Qu.:0.00   3rd Qu.:-2.0   3rd Qu.:-2.00  
##  Max.   :-2   Max.   :3.00   Max.   :1.00   Max.   :42.0   Max.   : 0.00  
##                                                                           
##     HELPINSY      DRAFTY        INSTLWS         AGEWS      
##  Min.   :-2   Min.   :2.00   Min.   :0.00   Min.   :-2.00  
##  1st Qu.:-2   1st Qu.:3.00   1st Qu.:0.00   1st Qu.:-2.00  
##  Median :-2   Median :4.00   Median :0.00   Median :-2.00  
##  Mean   :-2   Mean   :3.44   Mean   :0.32   Mean   :-0.72  
##  3rd Qu.:-2   3rd Qu.:4.00   3rd Qu.:1.00   3rd Qu.: 1.00  
##  Max.   :-2   Max.   :4.00   Max.   :1.00   Max.   : 3.00  
##                                                            
##      HELPWS         HELPWSY       AUDIT       AGEAUD      HELPAUD  
##  Min.   :-2.00   Min.   :-2   Min.   :0   Min.   :-2   Min.   :-2  
##  1st Qu.:-2.00   1st Qu.:-2   1st Qu.:0   1st Qu.:-2   1st Qu.:-2  
##  Median :-2.00   Median :-2   Median :0   Median :-2   Median :-2  
##  Mean   :-1.68   Mean   :-2   Mean   :0   Mean   :-2   Mean   :-2  
##  3rd Qu.:-2.00   3rd Qu.:-2   3rd Qu.:0   3rd Qu.:-2   3rd Qu.:-2  
##  Max.   : 0.00   Max.   :-2   Max.   :0   Max.   :-2   Max.   :-2  
##                                                                    
##     HELPAUDY    ZHIGHCEIL   ZCATHCEIL   ZSWIMPOOL     ZPOOL     ZFUELPOOL
##  Min.   :-2   Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0  
##  1st Qu.:-2   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0  
##  Median :-2   Median :0   Median :0   Median :0   Median :0   Median :0  
##  Mean   :-2   Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0  
##  3rd Qu.:-2   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0  
##  Max.   :-2   Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0  
##                                                                          
##     ZRECBATH    ZFUELTUB     ZLGT12      ZLGT4       ZLGT1     ZNOUTLGTNT
##  Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0   
##  1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   
##  Median :0   Median :0   Median :0   Median :0   Median :0   Median :0   
##  Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0   
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   
##  Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0   
##                                                                          
##    ZNGASLIGHT    ZSLDDRS    ZDOOR1SUM    ZWINDOWS   ZTYPEGLASS
##  Min.   :0    Min.   :0   Min.   :0   Min.   :0   Min.   :0   
##  1st Qu.:0    1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   
##  Median :0    Median :0   Median :0   Median :0   Median :0   
##  Mean   :0    Mean   :0   Mean   :0   Mean   :0   Mean   :0   
##  3rd Qu.:0    3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   
##  Max.   :0    Max.   :0   Max.   :0   Max.   :0   Max.   :0   
##                                                               
##    ZNEWGLASS      ZADQINSUL   ZINSTLINS    ZAGEINS     ZDRAFTY 
##  Min.   :0.00   Min.   :0   Min.   :0   Min.   :0   Min.   :0  
##  1st Qu.:0.00   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0  
##  Median :0.00   Median :0   Median :0   Median :0   Median :0  
##  Mean   :0.04   Mean   :0   Mean   :0   Mean   :0   Mean   :0  
##  3rd Qu.:0.00   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0  
##  Max.   :1.00   Max.   :0   Max.   :0   Max.   :0   Max.   :0  
##                                                                
##     ZINSTLWS        ZAGEWS         ZAUDIT     ZAGEAUD      USEEL  
##  Min.   :0.00   Min.   :0.00   Min.   :0   Min.   :0   Min.   :1  
##  1st Qu.:0.00   1st Qu.:0.00   1st Qu.:0   1st Qu.:0   1st Qu.:1  
##  Median :0.00   Median :0.00   Median :0   Median :0   Median :1  
##  Mean   :0.04   Mean   :0.04   Mean   :0   Mean   :0   Mean   :1  
##  3rd Qu.:0.00   3rd Qu.:0.00   3rd Qu.:0   3rd Qu.:0   3rd Qu.:1  
##  Max.   :1.00   Max.   :1.00   Max.   :0   Max.   :0   Max.   :1  
##                                                                   
##      USENG          USELP         USEFO      USEKERO     USEWOOD    
##  Min.   :0.00   Min.   :0.0   Min.   :0   Min.   :0   Min.   :0.00  
##  1st Qu.:0.00   1st Qu.:0.0   1st Qu.:0   1st Qu.:0   1st Qu.:0.00  
##  Median :0.00   Median :1.0   Median :0   Median :0   Median :0.00  
##  Mean   :0.44   Mean   :0.6   Mean   :0   Mean   :0   Mean   :0.16  
##  3rd Qu.:1.00   3rd Qu.:1.0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0.00  
##  Max.   :1.00   Max.   :1.0   Max.   :0   Max.   :0   Max.   :1.00  
##                                                                     
##     USESOLAR        USEOTH       ELWARM      ELECAUX       ELCOOL  
##  Min.   :0.00   Min.   :0.00   FALSE:14   Min.   :0.00   FALSE: 6  
##  1st Qu.:0.00   1st Qu.:0.00   TRUE :11   1st Qu.:0.00   TRUE :19  
##  Median :0.00   Median :0.00              Median :0.00             
##  Mean   :0.04   Mean   :0.16              Mean   :0.24             
##  3rd Qu.:0.00   3rd Qu.:0.00              3rd Qu.:0.00             
##  Max.   :1.00   Max.   :1.00              Max.   :1.00             
##                                                                    
##   ELWATER     ELFOOD      ELOTHER      UGWARM       UGASAUX    
##  FALSE:11   FALSE:13   Min.   :1   Min.   :0.0   Min.   :0.00  
##  TRUE :14   TRUE :12   1st Qu.:1   1st Qu.:0.0   1st Qu.:0.00  
##                        Median :1   Median :0.0   Median :0.00  
##                        Mean   :1   Mean   :0.4   Mean   :0.08  
##                        3rd Qu.:1   3rd Qu.:1.0   3rd Qu.:0.00  
##                        Max.   :1   Max.   :1.0   Max.   :1.00  
##                                                                
##     UGWATER         UGCOOK        UGOTH          LPWARM         LPGAUX 
##  Min.   :0.00   Min.   :0.0   Min.   :0.00   Min.   :0.00   Min.   :0  
##  1st Qu.:0.00   1st Qu.:0.0   1st Qu.:0.00   1st Qu.:0.00   1st Qu.:0  
##  Median :0.00   Median :0.0   Median :0.00   Median :0.00   Median :0  
##  Mean   :0.32   Mean   :0.2   Mean   :0.08   Mean   :0.36   Mean   :0  
##  3rd Qu.:1.00   3rd Qu.:0.0   3rd Qu.:0.00   3rd Qu.:1.00   3rd Qu.:0  
##  Max.   :1.00   Max.   :1.0   Max.   :1.00   Max.   :1.00   Max.   :0  
##                                                                        
##     LPWATER         LPCOOK        LPOTHER        FOWARM     FOILAUX 
##  Min.   :0.00   Min.   :0.00   Min.   :0.0   Min.   :0   Min.   :0  
##  1st Qu.:0.00   1st Qu.:0.00   1st Qu.:0.0   1st Qu.:0   1st Qu.:0  
##  Median :0.00   Median :0.00   Median :0.0   Median :0   Median :0  
##  Mean   :0.08   Mean   :0.28   Mean   :0.4   Mean   :0   Mean   :0  
##  3rd Qu.:0.00   3rd Qu.:1.00   3rd Qu.:1.0   3rd Qu.:0   3rd Qu.:0  
##  Max.   :1.00   Max.   :1.00   Max.   :1.0   Max.   :0   Max.   :0  
##                                                                     
##     FOWATER     FOOTHER      KRWARM     KEROAUX     KRWATER     KROTHER 
##  Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0  
##  1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0  
##  Median :0   Median :0   Median :0   Median :0   Median :0   Median :0  
##  Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0  
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0  
##  Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0  
##                                                                         
##      WDWARM        WOODAUX        WDWATER     WDOTHUSE    SOLWARM    
##  Min.   :0.00   Min.   :0.00   Min.   :0   Min.   :0   Min.   :0.00  
##  1st Qu.:0.00   1st Qu.:0.00   1st Qu.:0   1st Qu.:0   1st Qu.:0.00  
##  Median :0.00   Median :0.00   Median :0   Median :0   Median :0.00  
##  Mean   :0.16   Mean   :0.12   Mean   :0   Mean   :0   Mean   :0.04  
##  3rd Qu.:0.00   3rd Qu.:0.00   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0.00  
##  Max.   :1.00   Max.   :1.00   Max.   :0   Max.   :0   Max.   :1.00  
##                                                                      
##     SOLARAUX       SOLWATER    SOLOTHER    OTHWARM     OTHERAUX
##  Min.   :0.00   Min.   :0   Min.   :0   Min.   :0   Min.   :0  
##  1st Qu.:0.00   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0  
##  Median :0.00   Median :0   Median :0   Median :0   Median :0  
##  Mean   :0.04   Mean   :0   Mean   :0   Mean   :0   Mean   :0  
##  3rd Qu.:0.00   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0  
##  Max.   :1.00   Max.   :0   Max.   :0   Max.   :0   Max.   :0  
##                                                                
##     OTHWATER    OTHCOOK      ONSITE    ONSITEGRID    PELHEAT     
##  Min.   :0   Min.   :0   Min.   :0   Min.   :-2   Min.   :-2.00  
##  1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:-2   1st Qu.:-2.00  
##  Median :0   Median :0   Median :0   Median :-2   Median :-2.00  
##  Mean   :0   Mean   :0   Mean   :0   Mean   :-2   Mean   :-0.68  
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:-2   3rd Qu.: 1.00  
##  Max.   :0   Max.   :0   Max.   :0   Max.   :-2   Max.   : 1.00  
##                                                                  
##     PELHOTWA        PELCOOK          PELAC          PELLIGHT  
##  Min.   :-2.00   Min.   :-2.00   Min.   :-2.00   Min.   :1.0  
##  1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:1.0  
##  Median : 1.00   Median :-2.00   Median :-2.00   Median :1.0  
##  Mean   :-0.32   Mean   :-0.56   Mean   :-0.64   Mean   :1.2  
##  3rd Qu.: 1.00   3rd Qu.: 1.00   3rd Qu.: 1.00   3rd Qu.:1.0  
##  Max.   : 1.00   Max.   : 1.00   Max.   : 3.00   Max.   :3.0  
##                                                               
##    OTHERWAYEL       PGASHEAT       PGASHTWA        PUGCOOK     
##  Min.   :-2.00   Min.   :-2.0   Min.   :-2.00   Min.   :-2.00  
##  1st Qu.:-2.00   1st Qu.:-2.0   1st Qu.:-2.00   1st Qu.:-2.00  
##  Median :-2.00   Median :-2.0   Median :-2.00   Median :-2.00  
##  Mean   :-1.68   Mean   :-0.6   Mean   :-0.84   Mean   :-1.32  
##  3rd Qu.:-2.00   3rd Qu.: 1.0   3rd Qu.: 1.00   3rd Qu.:-2.00  
##  Max.   : 3.00   Max.   : 3.0   Max.   : 3.00   Max.   : 3.00  
##                                                                
##      PUGOTH        OTHERWAYNG        FOPAY      OTHERWAYFO     LPGPAY     
##  Min.   :-2.00   Min.   :-2.00   Min.   :-2   Min.   :-2   Min.   :-2.00  
##  1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2   1st Qu.:-2   1st Qu.:-2.00  
##  Median :-2.00   Median :-2.00   Median :-2   Median :-2   Median :-2.00  
##  Mean   :-1.68   Mean   :-1.68   Mean   :-2   Mean   :-2   Mean   :-0.88  
##  3rd Qu.:-2.00   3rd Qu.:-2.00   3rd Qu.:-2   3rd Qu.:-2   3rd Qu.: 1.00  
##  Max.   : 3.00   Max.   : 3.00   Max.   :-2   Max.   :-2   Max.   : 2.00  
##                                                                           
##   OTHERWAYLPG    LPGDELV         KERODEL      KEROCASH     NOCRCASH 
##  Min.   :-2   Min.   :-2.00   Min.   :-2   Min.   :-2   Min.   :-2  
##  1st Qu.:-2   1st Qu.:-2.00   1st Qu.:-2   1st Qu.:-2   1st Qu.:-2  
##  Median :-2   Median :-2.00   Median :-2   Median :-2   Median :-2  
##  Mean   :-2   Mean   :-1.08   Mean   :-2   Mean   :-2   Mean   :-2  
##  3rd Qu.:-2   3rd Qu.: 1.00   3rd Qu.:-2   3rd Qu.:-2   3rd Qu.:-2  
##  Max.   :-2   Max.   : 1.00   Max.   :-2   Max.   :-2   Max.   :-2  
##                                                                     
##     NKRGALNC     WOODLOGS        WDSCRAP         WDPELLET    
##  Min.   :-2   Min.   :-2.00   Min.   :-2.00   Min.   :-2.00  
##  1st Qu.:-2   1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.00  
##  Median :-2   Median :-2.00   Median :-2.00   Median :-2.00  
##  Mean   :-2   Mean   :-1.52   Mean   :-1.68   Mean   :-1.68  
##  3rd Qu.:-2   3rd Qu.:-2.00   3rd Qu.:-2.00   3rd Qu.:-2.00  
##  Max.   :-2   Max.   : 1.00   Max.   : 0.00   Max.   : 0.00  
##                                                              
##     WDOTHER         WOODAMT         NUMCORDS        ZONSITE   ZONSITEGRID
##  Min.   :-2.00   Min.   :-2.00   Min.   :-2.00   Min.   :0   Min.   :0   
##  1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:0   1st Qu.:0   
##  Median :-2.00   Median :-2.00   Median :-2.00   Median :0   Median :0   
##  Mean   :-1.68   Mean   :-1.28   Mean   :-1.56   Mean   :0   Mean   :0   
##  3rd Qu.:-2.00   3rd Qu.:-2.00   3rd Qu.:-2.00   3rd Qu.:0   3rd Qu.:0   
##  Max.   : 0.00   Max.   : 5.00   Max.   : 9.00   Max.   :0   Max.   :0   
##                                                                          
##     ZPELHEAT   ZPELHOTWA    ZPELCOOK     ZPELAC    ZPELLIGHT  ZOTHERWAYEL
##  Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0   
##  1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   
##  Median :0   Median :0   Median :0   Median :0   Median :0   Median :0   
##  Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0   
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   
##  Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0   
##                                                                          
##    ZPGASHEAT   ZPGASHTWA       ZPUGCOOK    ZPUGOTH   ZOTHERWAYNG
##  Min.   :0   Min.   :0.00   Min.   :0   Min.   :0   Min.   :0   
##  1st Qu.:0   1st Qu.:0.00   1st Qu.:0   1st Qu.:0   1st Qu.:0   
##  Median :0   Median :0.00   Median :0   Median :0   Median :0   
##  Mean   :0   Mean   :0.04   Mean   :0   Mean   :0   Mean   :0   
##  3rd Qu.:0   3rd Qu.:0.00   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   
##  Max.   :0   Max.   :1.00   Max.   :0   Max.   :0   Max.   :0   
##                                                                 
##      ZFOPAY   ZOTHERWAYFO    ZLPGPAY   ZOTHERWAYLPG    ZKERODEL
##  Min.   :0   Min.   :0    Min.   :0   Min.   :0     Min.   :0  
##  1st Qu.:0   1st Qu.:0    1st Qu.:0   1st Qu.:0     1st Qu.:0  
##  Median :0   Median :0    Median :0   Median :0     Median :0  
##  Mean   :0   Mean   :0    Mean   :0   Mean   :0     Mean   :0  
##  3rd Qu.:0   3rd Qu.:0    3rd Qu.:0   3rd Qu.:0     3rd Qu.:0  
##  Max.   :0   Max.   :0    Max.   :0   Max.   :0     Max.   :0  
##                                                                
##    ZKEROCASH   ZNOCRCASH   ZNKRGALNC   ZWOODLOGS    ZWDSCRAP   ZWDPELLET
##  Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0  
##  1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0  
##  Median :0   Median :0   Median :0   Median :0   Median :0   Median :0  
##  Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0  
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0  
##  Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0  
##                                                                         
##     ZWDOTHER    ZWOODAMT   ZNUMCORDS    KFUELOT         HHSEX     
##  Min.   :0   Min.   :0   Min.   :0   Min.   :0.00   Min.   :1.00  
##  1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0.00   1st Qu.:1.00  
##  Median :0   Median :0   Median :0   Median :0.00   Median :2.00  
##  Mean   :0   Mean   :0   Mean   :0   Mean   :0.04   Mean   :1.52  
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0.00   3rd Qu.:2.00  
##  Max.   :0   Max.   :0   Max.   :0   Max.   :1.00   Max.   :2.00  
##                                                                   
##     EMPLOYHH        SPOUSE       SDESCENT    Householder_Race   EDUCATION
##  Min.   :0.00   Min.   :0.0   Min.   :0.00   Wt      :21      HS     :8  
##  1st Qu.:0.00   1st Qu.:0.0   1st Qu.:0.00   AfAm    : 2      NoHS   :7  
##  Median :0.00   Median :0.0   Median :0.00   NativeAm: 0      SomeCol:5  
##  Mean   :0.48   Mean   :0.4   Mean   :0.08   Asian   : 0      BA     :2  
##  3rd Qu.:1.00   3rd Qu.:1.0   3rd Qu.:0.00   Pacific : 0      MA     :2  
##  Max.   :2.00   Max.   :1.0   Max.   :1.00   Other   : 0      AA     :1  
##                                              Multi   : 2      (Other):0  
##     NHSLDMEM       HHAGE        AGEHHMEMCAT2    AGEHHMEMCAT3  
##  Min.   :1.0   Min.   :22.00   Min.   :-2.00   Min.   :-2.00  
##  1st Qu.:1.0   1st Qu.:41.00   1st Qu.:-2.00   1st Qu.:-2.00  
##  Median :1.0   Median :54.00   Median :-2.00   Median :-2.00  
##  Mean   :1.8   Mean   :55.24   Mean   : 3.08   Mean   :-0.72  
##  3rd Qu.:2.0   3rd Qu.:68.00   3rd Qu.: 9.00   3rd Qu.:-2.00  
##  Max.   :5.0   Max.   :85.00   Max.   :14.00   Max.   : 5.00  
##                                                               
##   AGEHHMEMCAT4    AGEHHMEMCAT5    AGEHHMEMCAT6  AGEHHMEMCAT7  AGEHHMEMCAT8
##  Min.   :-2.00   Min.   :-2.00   Min.   :-2    Min.   :-2    Min.   :-2   
##  1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2    1st Qu.:-2    1st Qu.:-2   
##  Median :-2.00   Median :-2.00   Median :-2    Median :-2    Median :-2   
##  Mean   :-1.64   Mean   :-1.88   Mean   :-2    Mean   :-2    Mean   :-2   
##  3rd Qu.:-2.00   3rd Qu.:-2.00   3rd Qu.:-2    3rd Qu.:-2    3rd Qu.:-2   
##  Max.   : 3.00   Max.   : 1.00   Max.   :-2    Max.   :-2    Max.   :-2   
##                                                                           
##   AGEHHMEMCAT9 AGEHHMEMCAT10 AGEHHMEMCAT11 AGEHHMEMCAT12 AGEHHMEMCAT13
##  Min.   :-2    Min.   :-2    Min.   :-2    Min.   :-2    Min.   :-2   
##  1st Qu.:-2    1st Qu.:-2    1st Qu.:-2    1st Qu.:-2    1st Qu.:-2   
##  Median :-2    Median :-2    Median :-2    Median :-2    Median :-2   
##  Mean   :-2    Mean   :-2    Mean   :-2    Mean   :-2    Mean   :-2   
##  3rd Qu.:-2    3rd Qu.:-2    3rd Qu.:-2    3rd Qu.:-2    3rd Qu.:-2   
##  Max.   :-2    Max.   :-2    Max.   :-2    Max.   :-2    Max.   :-2   
##                                                                       
##  AGEHHMEMCAT14    HBUSNESS     ATHOME        TELLWORK    TELLDAYS 
##  Min.   :-2    Min.   :0   Min.   :0.00   Min.   :0   Min.   :-2  
##  1st Qu.:-2    1st Qu.:0   1st Qu.:0.00   1st Qu.:0   1st Qu.:-2  
##  Median :-2    Median :0   Median :1.00   Median :0   Median :-2  
##  Mean   :-2    Mean   :0   Mean   :0.56   Mean   :0   Mean   :-2  
##  3rd Qu.:-2    3rd Qu.:0   3rd Qu.:1.00   3rd Qu.:0   3rd Qu.:-2  
##  Max.   :-2    Max.   :0   Max.   :1.00   Max.   :0   Max.   :-2  
##                                                                   
##     OTHWORK        WORKPAY        RETIREPY       SSINCOME       CASHBEN 
##  Min.   :0.00   Min.   :0.00   Min.   :0.00   Min.   :0.00   Min.   :0  
##  1st Qu.:0.00   1st Qu.:0.00   1st Qu.:0.00   1st Qu.:0.00   1st Qu.:0  
##  Median :0.00   Median :1.00   Median :0.00   Median :0.00   Median :0  
##  Mean   :0.04   Mean   :0.64   Mean   :0.36   Mean   :0.08   Mean   :0  
##  3rd Qu.:0.00   3rd Qu.:1.00   3rd Qu.:1.00   3rd Qu.:0.00   3rd Qu.:0  
##  Max.   :1.00   Max.   :1.00   Max.   :1.00   Max.   :1.00   Max.   :0  
##                                                                         
##     INVESTMT      RGLRPAY         MONEYPY    POVERTY100    POVERTY150  
##  Min.   :0.0   Min.   :0.00   Less15K :7   Min.   :0.0   Min.   :0.00  
##  1st Qu.:0.0   1st Qu.:0.00   Less25K :3   1st Qu.:0.0   1st Qu.:0.00  
##  Median :0.0   Median :0.00   Less65  :3   Median :0.0   Median :0.00  
##  Mean   :0.2   Mean   :0.28   Less2500:2   Mean   :0.2   Mean   :0.44  
##  3rd Qu.:0.0   3rd Qu.:1.00   Less35K :2   3rd Qu.:0.0   3rd Qu.:1.00  
##  Max.   :1.0   Max.   :1.00   Less5K  :1   Max.   :1.0   Max.   :1.00  
##                               (Other) :7                               
##      HUPROJ       RENTHELP   FOODASST      ZHHSEX      ZHHAGE    ZEMPLOYHH
##  Min.   :-2.00   FALSE:25   FALSE:23   Min.   :0   Min.   :0   Min.   :0  
##  1st Qu.:-2.00   TRUE : 0   TRUE : 2   1st Qu.:0   1st Qu.:0   1st Qu.:0  
##  Median :-2.00                         Median :0   Median :0   Median :0  
##  Mean   :-1.36                         Mean   :0   Mean   :0   Mean   :0  
##  3rd Qu.: 0.00                         3rd Qu.:0   3rd Qu.:0   3rd Qu.:0  
##  Max.   : 0.00                         Max.   :0   Max.   :0   Max.   :0  
##                                                                           
##     ZSPOUSE    ZSDESCENT ZHouseholder_Race   ZEDUCATION   ZNHSLDMEM
##  Min.   :0   Min.   :0   Min.   :0.00      Min.   :0    Min.   :0  
##  1st Qu.:0   1st Qu.:0   1st Qu.:0.00      1st Qu.:0    1st Qu.:0  
##  Median :0   Median :0   Median :0.00      Median :0    Median :0  
##  Mean   :0   Mean   :0   Mean   :0.04      Mean   :0    Mean   :0  
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0.00      3rd Qu.:0    3rd Qu.:0  
##  Max.   :0   Max.   :0   Max.   :1.00      Max.   :0    Max.   :0  
##                                                                    
##  ZAGEHHMEMCAT2 ZAGEHHMEMCAT3 ZAGEHHMEMCAT4 ZAGEHHMEMCAT5 ZAGEHHMEMCAT6
##  Min.   :0     Min.   :0     Min.   :0     Min.   :0     Min.   :0    
##  1st Qu.:0     1st Qu.:0     1st Qu.:0     1st Qu.:0     1st Qu.:0    
##  Median :0     Median :0     Median :0     Median :0     Median :0    
##  Mean   :0     Mean   :0     Mean   :0     Mean   :0     Mean   :0    
##  3rd Qu.:0     3rd Qu.:0     3rd Qu.:0     3rd Qu.:0     3rd Qu.:0    
##  Max.   :0     Max.   :0     Max.   :0     Max.   :0     Max.   :0    
##                                                                       
##  ZAGEHHMEMCAT7 ZAGEHHMEMCAT8 ZAGEHHMEMCAT9 ZAGEHHMEMCAT10 ZAGEHHMEMCAT11
##  Min.   :0     Min.   :0     Min.   :0     Min.   :0      Min.   :0     
##  1st Qu.:0     1st Qu.:0     1st Qu.:0     1st Qu.:0      1st Qu.:0     
##  Median :0     Median :0     Median :0     Median :0      Median :0     
##  Mean   :0     Mean   :0     Mean   :0     Mean   :0      Mean   :0     
##  3rd Qu.:0     3rd Qu.:0     3rd Qu.:0     3rd Qu.:0      3rd Qu.:0     
##  Max.   :0     Max.   :0     Max.   :0     Max.   :0      Max.   :0     
##                                                                         
##  ZAGEHHMEMCAT12 ZAGEHHMEMCAT13 ZAGEHHMEMCAT14   ZHBUSNESS    ZATHOME 
##  Min.   :0      Min.   :0      Min.   :0      Min.   :0   Min.   :0  
##  1st Qu.:0      1st Qu.:0      1st Qu.:0      1st Qu.:0   1st Qu.:0  
##  Median :0      Median :0      Median :0      Median :0   Median :0  
##  Mean   :0      Mean   :0      Mean   :0      Mean   :0   Mean   :0  
##  3rd Qu.:0      3rd Qu.:0      3rd Qu.:0      3rd Qu.:0   3rd Qu.:0  
##  Max.   :0      Max.   :0      Max.   :0      Max.   :0   Max.   :0  
##                                                                      
##    ZTELLWORK   ZTELLDAYS    ZOTHWORK    ZWORKPAY   ZRETIREPY   ZSSINCOME
##  Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0  
##  1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0  
##  Median :0   Median :0   Median :0   Median :0   Median :0   Median :0  
##  Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0  
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0  
##  Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0  
##                                                                         
##     ZCASHBEN   ZINVESTMT       ZRGLRPAY    ZMONEYPY       ZHUPROJ 
##  Min.   :0   Min.   :0.00   Min.   :0   Min.   :0.00   Min.   :0  
##  1st Qu.:0   1st Qu.:0.00   1st Qu.:0   1st Qu.:0.00   1st Qu.:0  
##  Median :0   Median :0.00   Median :0   Median :0.00   Median :0  
##  Mean   :0   Mean   :0.04   Mean   :0   Mean   :0.16   Mean   :0  
##  3rd Qu.:0   3rd Qu.:0.00   3rd Qu.:0   3rd Qu.:0.00   3rd Qu.:0  
##  Max.   :0   Max.   :1.00   Max.   :0   Max.   :1.00   Max.   :0  
##                                                                   
##    ZRENTHELP   ZFOODASST    TOTSQFT       TOTSQFT_EN      TOTHSQFT   
##  Min.   :0   Min.   :0   Min.   : 240   Min.   : 240   Min.   : 240  
##  1st Qu.:0   1st Qu.:0   1st Qu.: 870   1st Qu.: 870   1st Qu.: 840  
##  Median :0   Median :0   Median :1233   Median :1233   Median :1066  
##  Mean   :0   Mean   :0   Mean   :1916   Mean   :1844   Mean   :1304  
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:1927   3rd Qu.:1927   3rd Qu.:1568  
##  Max.   :0   Max.   :0   Max.   :6902   Max.   :6652   Max.   :4510  
##                                                                      
##     TOTUSQFT         TOTCSQFT        TOTUCSQFT       ZTOTSQFT  ZTOTSQFT_EN
##  Min.   :   0.0   Min.   :   0.0   Min.   :   0   Min.   :0   Min.   :0   
##  1st Qu.:   0.0   1st Qu.: 120.0   1st Qu.: 210   1st Qu.:0   1st Qu.:0   
##  Median :   0.0   Median : 566.0   Median : 423   Median :0   Median :0   
##  Mean   : 612.4   Mean   : 894.5   Mean   :1022   Mean   :0   Mean   :0   
##  3rd Qu.: 250.0   3rd Qu.:1250.0   3rd Qu.:1381   3rd Qu.:0   3rd Qu.:0   
##  Max.   :5733.0   Max.   :4156.0   Max.   :6401   Max.   :0   Max.   :0   
##                                                                           
##    ZTOTHSQFT   ZTOTUSQFT   ZTOTCSQFT   ZTOTUCSQFT      KWH       
##  Min.   :0   Min.   :0   Min.   :0   Min.   :0    Min.   : 2783  
##  1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0    1st Qu.: 6844  
##  Median :0   Median :0   Median :0   Median :0    Median : 9130  
##  Mean   :0   Mean   :0   Mean   :0   Mean   :0    Mean   :11706  
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0    3rd Qu.:17520  
##  Max.   :0   Max.   :0   Max.   :0   Max.   :0    Max.   :27417  
##                                                                  
##      KWHSPH         KWHCOL            KWHWTH         KWHRFG      
##  Min.   :   0   Min.   :   0.00   Min.   :   0   Min.   : 435.7  
##  1st Qu.:   0   1st Qu.:  99.25   1st Qu.:   0   1st Qu.: 942.6  
##  Median :   0   Median : 515.52   Median :1229   Median :1197.1  
##  Mean   :1142   Mean   :1035.19   Mean   :1450   Mean   :1327.9  
##  3rd Qu.:1742   3rd Qu.:1321.58   3rd Qu.:2522   3rd Qu.:1504.5  
##  Max.   :6344   Max.   :3961.05   Max.   :4914   Max.   :3168.4  
##                                                                  
##      KWHOTH          BTUEL          BTUELSPH        BTUELCOL      
##  Min.   : 1786   Min.   : 9496   Min.   :    0   Min.   :    0.0  
##  1st Qu.: 3623   1st Qu.:23352   1st Qu.:    0   1st Qu.:  338.7  
##  Median : 4830   Median :31152   Median :    0   Median : 1758.9  
##  Mean   : 6752   Mean   :39942   Mean   : 3895   Mean   : 3532.1  
##  3rd Qu.: 8651   3rd Qu.:59778   3rd Qu.: 5942   3rd Qu.: 4509.2  
##  Max.   :18541   Max.   :93547   Max.   :21646   Max.   :13515.1  
##                                                                   
##     BTUELWTH        BTUELRFG        BTUELOTH        DOLLAREL   
##  Min.   :    0   Min.   : 1487   Min.   : 6094   Min.   : 278  
##  1st Qu.:    0   1st Qu.: 3216   1st Qu.:12360   1st Qu.: 775  
##  Median : 4193   Median : 4084   Median :16480   Median : 935  
##  Mean   : 4946   Mean   : 4531   Mean   :23038   Mean   :1174  
##  3rd Qu.: 8607   3rd Qu.: 5133   3rd Qu.:29518   3rd Qu.:1551  
##  Max.   :16768   Max.   :10810   Max.   :63261   Max.   :2596  
##                                                                
##     DOLELSPH         DOLELCOL          DOLELWTH        DOLELRFG     
##  Min.   :  0.00   Min.   :  0.000   Min.   :  0.0   Min.   : 46.43  
##  1st Qu.:  0.00   1st Qu.:  8.314   1st Qu.:  0.0   1st Qu.:101.00  
##  Median :  0.00   Median : 61.767   Median :116.8   Median :117.27  
##  Mean   : 98.67   Mean   :106.366   Mean   :135.1   Mean   :138.57  
##  3rd Qu.:166.50   3rd Qu.:117.615   3rd Qu.:254.7   3rd Qu.:162.16  
##  Max.   :521.53   Max.   :426.869   Max.   :339.8   Max.   :338.04  
##                                                                     
##     DOLELOTH         CUFEETNG       CUFEETNGSPH    CUFEETNGWTH    
##  Min.   : 178.6   Min.   :   0.0   Min.   :   0   Min.   :  0.00  
##  1st Qu.: 386.0   1st Qu.:   0.0   1st Qu.:   0   1st Qu.:  0.00  
##  Median : 576.2   Median :   0.0   Median :   0   Median :  0.00  
##  Mean   : 695.7   Mean   : 354.2   Mean   : 250   Mean   : 77.77  
##  3rd Qu.: 786.6   3rd Qu.: 502.0   3rd Qu.: 327   3rd Qu.: 77.51  
##  Max.   :1905.0   Max.   :2131.0   Max.   :1439   Max.   :561.08  
##                                                                   
##   CUFEETNGOTH         BTUNG           BTUNGSPH         BTUNGWTH    
##  Min.   :  0.00   Min.   :     0   Min.   :     0   Min.   :    0  
##  1st Qu.:  0.00   1st Qu.:     0   1st Qu.:     0   1st Qu.:    0  
##  Median :  0.00   Median :     0   Median :     0   Median :    0  
##  Mean   : 26.43   Mean   : 36310   Mean   : 25630   Mean   : 7971  
##  3rd Qu.:  0.00   3rd Qu.: 51455   3rd Qu.: 33518   3rd Qu.: 7945  
##  Max.   :193.71   Max.   :218428   Max.   :147477   Max.   :57511  
##                                                                    
##     BTUNGOTH        DOLLARNG         DOLNGSPH         DOLNGWTH     
##  Min.   :    0   Min.   :   0.0   Min.   :   0.0   Min.   :  0.00  
##  1st Qu.:    0   1st Qu.:   0.0   1st Qu.:   0.0   1st Qu.:  0.00  
##  Median :    0   Median :   0.0   Median :   0.0   Median :  0.00  
##  Mean   : 2709   Mean   : 423.1   Mean   : 300.1   Mean   : 90.71  
##  3rd Qu.:    0   3rd Qu.: 719.0   3rd Qu.: 507.3   3rd Qu.:111.02  
##  Max.   :19856   Max.   :2152.0   Max.   :1453.0   Max.   :566.61  
##                                                                    
##     DOLNGOTH         GALLONLP      GALLONLPSPH     GALLONLPWTH    
##  Min.   :  0.00   Min.   :  0.0   Min.   :  0.0   Min.   :  0.00  
##  1st Qu.:  0.00   1st Qu.:  0.0   1st Qu.:  0.0   1st Qu.:  0.00  
##  Median :  0.00   Median :  0.0   Median :  0.0   Median :  0.00  
##  Mean   : 32.27   Mean   :206.8   Mean   :170.9   Mean   : 17.56  
##  3rd Qu.:  0.00   3rd Qu.:404.0   3rd Qu.:275.0   3rd Qu.:  0.00  
##  Max.   :208.88   Max.   :941.0   Max.   :872.1   Max.   :344.00  
##                                                                   
##   GALLONLPOTH         BTULP          BTULPSPH        BTULPWTH    
##  Min.   :  0.00   Min.   :    0   Min.   :    0   Min.   :    0  
##  1st Qu.:  0.00   1st Qu.:    0   1st Qu.:    0   1st Qu.:    0  
##  Median :  0.00   Median :    0   Median :    0   Median :    0  
##  Mean   : 18.28   Mean   :18883   Mean   :15610   Mean   : 1604  
##  3rd Qu.: 20.00   3rd Qu.:36847   3rd Qu.:25083   3rd Qu.:    0  
##  Max.   :225.00   Max.   :85942   Max.   :79644   Max.   :31435  
##                                                                  
##     BTULPOTH        DOLLARLP       DOLLPSPH         DOLLPWTH     
##  Min.   :    0   Min.   :   0   Min.   :   0.0   Min.   :  0.00  
##  1st Qu.:    0   1st Qu.:   0   1st Qu.:   0.0   1st Qu.:  0.00  
##  Median :    0   Median :   0   Median :   0.0   Median :  0.00  
##  Mean   : 1668   Mean   : 384   Mean   : 320.1   Mean   : 31.08  
##  3rd Qu.: 1859   3rd Qu.: 651   3rd Qu.: 467.0   3rd Qu.:  0.00  
##  Max.   :20574   Max.   :1898   Max.   :1759.1   Max.   :622.00  
##                                                                  
##     DOLLPOTH         GALLONFO  GALLONFOSPH  GALLONFOWTH  GALLONFOOTH
##  Min.   :  0.00   Min.   :0   Min.   :0    Min.   :0    Min.   :0   
##  1st Qu.:  0.00   1st Qu.:0   1st Qu.:0    1st Qu.:0    1st Qu.:0   
##  Median :  0.00   Median :0   Median :0    Median :0    Median :0   
##  Mean   : 32.75   Mean   :0   Mean   :0    Mean   :0    Mean   :0   
##  3rd Qu.: 35.00   3rd Qu.:0   3rd Qu.:0    3rd Qu.:0    3rd Qu.:0   
##  Max.   :368.00   Max.   :0   Max.   :0    Max.   :0    Max.   :0   
##                                                                     
##      BTUFO      BTUFOSPH    BTUFOWTH    BTUFOOTH    DOLLARFO    DOLFOSPH
##  Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0  
##  1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0  
##  Median :0   Median :0   Median :0   Median :0   Median :0   Median :0  
##  Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0  
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0  
##  Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0  
##                                                                         
##     DOLFOWTH    DOLFOOTH   GALLONKER  GALLONKERSPH  GALLONKERWTH
##  Min.   :0   Min.   :0   Min.   :0   Min.   :0     Min.   :0    
##  1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0     1st Qu.:0    
##  Median :0   Median :0   Median :0   Median :0     Median :0    
##  Mean   :0   Mean   :0   Mean   :0   Mean   :0     Mean   :0    
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0     3rd Qu.:0    
##  Max.   :0   Max.   :0   Max.   :0   Max.   :0     Max.   :0    
##                                                                 
##   GALLONKEROTH     BTUKER    BTUKERSPH   BTUKERWTH   BTUKEROTH   DOLLARKER
##  Min.   :0     Min.   :0   Min.   :0   Min.   :0   Min.   :0   Min.   :0  
##  1st Qu.:0     1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:0  
##  Median :0     Median :0   Median :0   Median :0   Median :0   Median :0  
##  Mean   :0     Mean   :0   Mean   :0   Mean   :0   Mean   :0   Mean   :0  
##  3rd Qu.:0     3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:0  
##  Max.   :0     Max.   :0   Max.   :0   Max.   :0   Max.   :0   Max.   :0  
##                                                                           
##    DOLKERSPH   DOLKERWTH   DOLKEROTH    BTUWOOD          CORDSWD    
##  Min.   :0   Min.   :0   Min.   :0   Min.   :     0   Min.   :0.00  
##  1st Qu.:0   1st Qu.:0   1st Qu.:0   1st Qu.:     0   1st Qu.:0.00  
##  Median :0   Median :0   Median :0   Median :     0   Median :0.00  
##  Mean   :0   Mean   :0   Mean   :0   Mean   :  9600   Mean   :0.48  
##  3rd Qu.:0   3rd Qu.:0   3rd Qu.:0   3rd Qu.:     0   3rd Qu.:0.00  
##  Max.   :0   Max.   :0   Max.   :0   Max.   :180000   Max.   :9.00  
##                                                                     
##     TOTALBTU       TOTALBTUSPH      TOTALBTUCOL     TOTALBTUWTH   
##  Min.   : 31152   Min.   :  4495   Min.   :    0   Min.   :    0  
##  1st Qu.: 63815   1st Qu.: 20623   1st Qu.:  339   1st Qu.: 6266  
##  Median : 75671   Median : 33518   Median : 1759   Median : 9091  
##  Mean   : 95135   Mean   : 45135   Mean   : 3532   Mean   :14521  
##  3rd Qu.:112661   3rd Qu.: 56205   3rd Qu.: 4509   3rd Qu.:17799  
##  Max.   :292813   Max.   :147477   Max.   :13515   Max.   :57511  
##                                                                   
##   TOTALBTURFG     TOTALBTUOTH       TOTALDOL     TOTALDOLSPH    
##  Min.   : 1487   Min.   : 9318   Min.   : 775   Min.   : 112.0  
##  1st Qu.: 3216   1st Qu.:16381   1st Qu.:1494   1st Qu.: 461.0  
##  Median : 4084   Median :22777   Median :1791   Median : 522.0  
##  Mean   : 4531   Mean   :27415   Mean   :1981   Mean   : 718.9  
##  3rd Qu.: 5133   3rd Qu.:29904   3rd Qu.:2168   3rd Qu.:1001.0  
##  Max.   :10810   Max.   :76701   Max.   :4392   Max.   :1759.0  
##                                                                 
##   TOTALDOLCOL     TOTALDOLWTH     TOTALDOLRFG     TOTALDOLOTH    
##  Min.   :  0.0   Min.   :  0.0   Min.   : 46.0   Min.   : 221.0  
##  1st Qu.:  8.0   1st Qu.:184.0   1st Qu.:101.0   1st Qu.: 485.0  
##  Median : 62.0   Median :241.0   Median :117.0   Median : 646.0  
##  Mean   :106.3   Mean   :256.9   Mean   :138.5   Mean   : 760.7  
##  3rd Qu.:118.0   3rd Qu.:312.0   3rd Qu.:162.0   3rd Qu.: 787.0  
##  Max.   :427.0   Max.   :622.0   Max.   :338.0   Max.   :2093.0  
##                                                                  
##     KAVALEL        PERIODEL       SCALEEL       KAVALNG    
##  Min.   :1.00   Min.   :1.00   Min.   :0.0   Min.   :-2.0  
##  1st Qu.:1.00   1st Qu.:1.00   1st Qu.:0.0   1st Qu.:-2.0  
##  Median :1.00   Median :1.00   Median :0.0   Median :-2.0  
##  Mean   :1.88   Mean   :2.68   Mean   :1.2   Mean   :-0.4  
##  3rd Qu.:3.00   3rd Qu.:5.00   3rd Qu.:3.0   3rd Qu.: 1.0  
##  Max.   :3.00   Max.   :5.00   Max.   :3.0   Max.   : 3.0  
##                                                            
##     PERIODNG        SCALENG         PERIODLP        SCALELP     
##  Min.   :-2.00   Min.   :-2.00   Min.   :-2.00   Min.   :-2.00  
##  1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.00   1st Qu.:-2.00  
##  Median :-2.00   Median :-2.00   Median :-2.00   Median :-2.00  
##  Mean   :-0.32   Mean   :-0.88   Mean   :-0.28   Mean   :-0.92  
##  3rd Qu.: 1.00   3rd Qu.: 0.00   3rd Qu.: 2.00   3rd Qu.: 0.00  
##  Max.   : 5.00   Max.   : 3.00   Max.   : 5.00   Max.   : 3.00  
##                                                                 
##     PERIODFO     SCALEFO      PERIODKR     SCALEKER  CookTopElectric
##  Min.   :-2   Min.   :-2   Min.   :-2   Min.   :-2   Mode :logical  
##  1st Qu.:-2   1st Qu.:-2   1st Qu.:-2   1st Qu.:-2   FALSE:13       
##  Median :-2   Median :-2   Median :-2   Median :-2   TRUE :12       
##  Mean   :-2   Mean   :-2   Mean   :-2   Mean   :-2   NA's :0        
##  3rd Qu.:-2   3rd Qu.:-2   3rd Qu.:-2   3rd Qu.:-2                  
##  Max.   :-2   Max.   :-2   Max.   :-2   Max.   :-2                  
##                                                                     
##  OvenElectric    ELectricCook          AgeFridge  DishwaherTrue
##  Mode :logical   Mode :logical   Less2      : 1   TRUE :13     
##  FALSE:13        FALSE:13        2to4Years  : 3   FALSE:12     
##  TRUE :12        TRUE :12        5to9Years  : 9                
##  NA's :0         NA's :0         20PlusYears: 0                
##                                  10to14Years:10                
##                                  15to19Years: 2                
##                                                                
##   Hispanic      
##  Mode :logical  
##  FALSE:23       
##  TRUE :2        
##  NA's :0        
##                 
##                 
## 
```
They are very poor.  Solution is to drop the ones with weights greater than 40K.  TODO



Looking at weather

```r
summary(RECS$HDD65)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##       0    2198    4483    4141    5913   12520
```

```r
summary(RECS$CDD65)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##       0     561    1045    1415    1897    5480
```
Nothing odd.


This is the data ME created from the HUD report on the number of complaints per 100K population


```r
HUD <- read.csv("~/Research/EnergyEthnicity/Data/HUD.csv")

#And the clean up from importing from excell
HUD$pop<-as.numeric(gsub(",","",HUD$pop))
HUD$reportablen<-as.factor(HUD$reportablen)
summary(HUD)
```

```
##         state    compltothudfhap       pop              comppop      
##  Alabama   : 1   Min.   :   4.0   Min.   :  532981   Min.   :0.4132  
##  Alaska    : 1   1st Qu.:  63.5   1st Qu.: 1654728   1st Qu.:2.1526  
##  Arizona   : 1   Median : 107.0   Median : 4287931   Median :2.8810  
##  Arkansas  : 1   Mean   : 200.2   Mean   : 5968134   Mean   :3.4185  
##  California: 1   3rd Qu.: 202.0   3rd Qu.: 6554834   3rd Qu.:4.3463  
##  Colorado  : 1   Max.   :1108.0   Max.   :36580371   Max.   :8.7306  
##  (Other)   :45                                                       
##   reportablen   reporttot     
##  1      : 5   Min.   : 1.812  
##  10     : 4   1st Qu.: 4.222  
##  14     : 4   Median : 9.258  
##  23     : 4   Mean   : 9.592  
##  27     : 4   3rd Qu.:13.504  
##  18     : 3   Max.   :20.496  
##  (Other):27
```
# Some Ideas on what matters

```r
table(RECS$UR, RECS$RENTHELP)
```

```
##        
##         FALSE TRUE
##   Rural  2416   11
##   Urban  9497  159
```

```r
table(RECS$TYPEHUQ,RECS$KOWNRENT)
```

```
##              
##                Own Rent Free
##   Mobile       431   99   11
##   SFDetached  6835  879   89
##   SFAttached   506  373   11
##   SmApartment  144  769   13
##   LgApartment  224 1681   18
```

```r
#Dump the houses that are free

boxplot(RECS$TOTSQFT_EN~RECS$REPORTABLE_DOMAIN )
```

![plot of chunk unnamed-chunk-7](figure/unnamed-chunk-7-1.png) 

```r
boxplot(RECS$TOTSQFT_EN~RECS$EDUCATION )
```

![plot of chunk unnamed-chunk-7](figure/unnamed-chunk-7-2.png) 

```r
boxplot(RECS$TOTSQFT_EN~RECS$UR )
```

![plot of chunk unnamed-chunk-7](figure/unnamed-chunk-7-3.png) 

```r
table(RECS$EDUCATION)
```

```
## 
##    None    NoHS      HS SomeCol      AA      BA      MA    Prof     PHD 
##     200    1033    3193    2701    1193    2428     957     221     157
```

```r
table(RECS$UR,RECS$Householder_Race)
```

```
##        
##           Wt AfAm NativeAm Asian Pacific Other Multi
##   Rural 2131  201       28    14       6    17    30
##   Urban 7447 1316       82   443      34   194   140
```


