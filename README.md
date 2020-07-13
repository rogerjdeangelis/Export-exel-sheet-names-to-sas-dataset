# Export-exel-sheet-names-to-sas-dataset
Export exel sheet names to sas dataset
    Export exel sheet names to sas dataset                                                                    
                                                                                                              
    Win 10 64bit, SAS 64bit 9.4M6, MS Excel 64bit, and SAS classic editor                                     
                                                                                                              
    gihub                                                                                                     
    https://github.com/rogerjdeangelis/Export-exel-sheet-names-to-sas-dataset                                 
                                                                                                              
    SAS Forum                                                                                                 
    https://tinyurl.com/y7co5jrz                                                                              
    https://communities.sas.com/t5/SAS-Programming/How-to-pull-in-Excel-sheet-names/m-p/668691                
                                                                                                              
    /*                   _                                                                                    
    (_)_ __  _ __  _   _| |_                                                                                  
    | | `_ \| `_ \| | | | __|                                                                                 
    | | | | | |_) | |_| | |_                                                                                  
    |_|_| |_| .__/ \__,_|\__|                                                                                 
            |_|                                                                                               
    */                                                                                                        
    * create two excel tabs;                                                                                  
                                                                                                              
    libname xel "d:/xls/onetwo.xlsx";                                                                         
    data xel.one xel.two;                                                                                     
       set sashelp.class;                                                                                     
    run;quit;                                                                                                 
    libname xel clear;                                                                                        
    /*           _               _                                                                            
      ___  _   _| |_ _ __  _   _| |_                                                                          
     / _ \| | | | __| `_ \| | | | __|                                                                         
    | (_) | |_| | |_| |_) | |_| | |_                                                                          
     \___/ \__,_|\__| .__/ \__,_|\__|                                                                         
                    |_|                                                                                       
    */                                                                                                        
                                                                                                              
     WORK.DIR                                                                                                 
                                                                                                              
      NUM    NAME    MEMTYPE    OBS    VARS    LABEL    DBMSTYPE                                              
                                                                                                              
       1     one      DATA       .      5                TABLE    * sas created named range                   
       2     one$     DATA       .      5                TABLE    * tab name                                  
                                                                                                              
       3     two      DATA       .      5                TABLE                                                
       4     two$     DATA       .      5                TABLE                                                
                                                                                                              
    The CONTENTS Procedure                                                                                    
                                                                                                              
                Directory                                                                                     
                                                                                                              
    Libref         XEL                                                                                        
    Engine         EXCEL                                                                                      
    Physical Name  d:/xls/onetwo.xlsx                                                                         
    User           Admin                                                                                      
                                                                                                              
                                                                                                              
                                                DBMS                                                          
             Member  Obs, Entries               Member                                                        
    #  Name  Type     or Indexes   Vars  Label  Type                                                          
                                                                                                              
    1  one   DATA         .         5           TABLE                                                         
    2  one$  DATA         .         5           TABLE                                                         
    3  two   DATA         .         5           TABLE                                                         
    4  two$  DATA         .         5           TABLE                                                         
                                                                                                              
                                                                                                              
    /*                                                                                                        
     _ __  _ __ ___   ___ ___  ___ ___                                                                        
    | `_ \| `__/ _ \ / __/ _ \/ __/ __|                                                                       
    | |_) | | | (_) | (_|  __/\__ \__ \                                                                       
    | .__/|_|  \___/ \___\___||___/___/                                                                       
    |_|                                                                                                       
    */                                                                                                        
                                                                                                              
    * get tabnames;                                                                                           
    libname xel "d:/xls/onetwo.xlsx";                                                                         
    ods output members=dir;                                                                                   
    ods trace on;                                                                                             
    proc contents data=xel._all_;                                                                             
    run;quit;                                                                                                 
    ods trace off;                                                                                            
    libname xel clear;                                                                                        
                                                                                                              
    proc print data=dir;                                                                                      
    run;quit;                                                                                                 
                                                                                                              
                                                                                                              
