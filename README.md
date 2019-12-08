# utl-keep-orginal-SAS-table-but-mask-excel-output
Keep orginal SAS table but mask excel output
    Keep original SAS table but mask excel output                                              
                                                                                               
    Excel materializes the formaated value and does not keep the underlying value              
                                                                                               
    github                                                                                     
    https://tinyurl.com/u8d7mpd                                                                
    https://github.com/rogerjdeangelis/utl-keep-orginal-SAS-table-but-mask-excel-output        
                                                                                               
    *_                   _                                                                     
    (_)_ __  _ __  _   _| |_                                                                   
    | | '_ \| '_ \| | | | __|                                                                  
    | | | | | |_) | |_| | |_                                                                   
    |_|_| |_| .__/ \__,_|\__|                                                                  
            |_|                                                                                
    ;                                                                                          
                                                                                               
                                                                                               
    proc format;                                                                               
      value $nam2mis                                                                           
        'Alice'="REDACT"                                                                       
        other=[$8.]                                                                            
    ;run;quit;                                                                                 
                                                                                               
                                                                                               
    SASHELP.CLASS total obs=19                                                                 
                                                                                               
    Obs    NAME       SEX    AGE    HEIGHT    WEIGHT                                           
                                                                                               
      1    Alfred      M      14     69.0      112.5                                           
      2    Alice       F      13     56.5       84.0                                           
      3    Barbara     F      13     65.3       98.0                                           
      4    Carol       F      14     62.8      102.5                                           
     ...                                                                                       
                                                                                               
    *            _               _                                                             
      ___  _   _| |_ _ __  _   _| |_                                                           
     / _ \| | | | __| '_ \| | | | __|                                                          
    | (_) | |_| | |_| |_) | |_| | |_                                                           
     \___/ \__,_|\__| .__/ \__,_|\__|                                                          
                    |_|                                                                        
    ;                                                                                          
                                                                                               
    d:/xls/class_miss.xlsx                                                                     
                                                                                               
      NAME      SEX    AGE    HEIGHT    WEIGHT                                                 
                                                                                               
     Alfred      M      14     69.0      112.5                                                 
     ======                                                                                    
     REDACT      F      13     56.5       84.0  * name redacted                                
     ======                                     * value still in input table                   
     Barbara     F      13     65.3       98.0                                                 
     Carol       F      14     62.8      102.5                                                 
                                                                                               
    *                                                                                          
     _ __  _ __ ___   ___ ___  ___ ___                                                         
    | '_ \| '__/ _ \ / __/ _ \/ __/ __|                                                        
    | |_) | | | (_) | (_|  __/\__ \__ \                                                        
    | .__/|_|  \___/ \___\___||___/___/                                                        
    |_|                                                                                        
    ;                                                                                          
                                                                                               
                                                                                               
    ods excel file="d:/xls/class_miss.xlsx";                                                   
                                                                                               
    proc print data=sashelp.class(obs=4);                                                      
    format name $nam2mis.;                                                                     
    run;quit;                                                                                  
                                                                                               
    ods excel close;                                                                           
                                                                                               
                                                                                               
                                                                                               
