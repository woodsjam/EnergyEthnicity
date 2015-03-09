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

#END on LINE 240









#Starting again from the bottom
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
#MONEYPY row 789 in category then make cont.
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
#RENTHELP
FOODASST
```

```
## Error in eval(expr, envir, enclos): object 'FOODASST' not found
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



# Restrict to primary and not seasonal 
```
Checkign out the weight variable

```r
summary(RECS$NWEIGHT)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##   476.1  6297.0  7971.0  9403.0 11330.0 95780.0
```
Looks like it is the number of equivelent HH in population style.

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

