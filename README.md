
------------------------------------------------------------------------------Table ID Sequence------------------------------------------------
CREATE SEQUENCE TABLE_SEQUENCE
    MAXVALUE 99999
    MINVALUE 1
    START WITH 1
    INCREMENT BY 1
    CYCLE
    CACHE 30;

----------------------------------------------------------------------------------------------Excel Import Infomation---------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------Table--------------------------------------------------------------------------------------------------------
CREATE TABLE EXCEL_INFO
( EXCEL_INFO_ID NUMBER(10) NOT NULL,                               
  EXCEL_INFO_NAME VARCHAR2(150) NOT NULL,                                                 
  CREATION_DATE DATE NOT NULL,                                                                    
  CREATED_BY VARCHAR2(50),                                                                           
  CODE VARCHAR2(20),
  MESSAGE VARCHAR2(200),
  ATTRIBUTE1 VARCHAR2(150),   
  CONSTRAINT EXCEL_INFO_PK PRIMARY KEY (EXCEL_INFO_ID)
);


----------------------------------------------------------------------------------------------Excel Version---------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------Table----------------------------------------------------------------------------------------------------
CREATE TABLE EXCEL_VERSION
( EXCEL_VERSION_ID NUMBER(10) NOT NULL,                               
  EXCEL_VERSION VARCHAR2(150) NOT NULL,                                                     
  CREATION_DATE DATE NOT NULL,                                                                    
  CREATED_BY VARCHAR2(50),                                                                           
  EXCEL_INFO_ID NUMBER(10) NOT NULL,                                                           
  ATTRIBUTE1 VARCHAR2(150),   
  CONSTRAINT EXCEL_VERSION_PK PRIMARY KEY (EXCEL_VERSION_ID)
);


-------------------------------------------------------------------------------------------Foundation User-----------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------Table------------------------------------------------------------------------------------------------
CREATE TABLE XX_USER
( USER_ID NUMBER(10) NOT NULL,
  USER_NAME VARCHAR2(50) NOT NULL,                                                             
  ENCRYPTED_PASSWORD VARCHAR2(200) NOT NULL,                                         
  DESCRIPTION VARCHAR2(150),                                                                        
  EMPLOYEE_NAME VARCHAR2(50),                                                                     
  ATTRIBUTE1 VARCHAR2(150),   
  ATTRIBUTE2 VARCHAR2(150),   
  ATTRIBUTE3 VARCHAR2(150),   
  CONSTRAINT XX_USER_PK PRIMARY KEY (USER_ID)
);



-------------------------------------------------------------------------------------------Employee-----------------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------Table--------------------------------------------------------------------------------------------------------
CREATE TABLE EMPLOYEE
( EMP_NO VARCHAR2(50) NOT NULL,                                                                   
  EMP_NAME VARCHAR2(50) NOT NULL,                                                               
  AKA VARCHAR2(150),                                                                                      
  DESCRIPTION VARCHAR2(150),                                                                        
  SEX VARCHAR2(10),                                                                                                                                        
  DATE_OF_BIRTH DATE,                                                                                   
  PHONE1 VARCHAR2(50),                                                                                 
  PHONE2 VARCHAR2(50),                                                                                 
  ADDRESS1 VARCHAR2(200),                                                                             
  ADDRESS2 VARCHAR2(200),                                                                             
  EMAIL_ADDRESS VARCHAR2(200),                                                                  
  CONTACT VARCHAR2(200),                                                                              
  START_DATE DATE,                                                                                         
  END_DATE DATE,                                                                                             
  ENABLE_FLAG VARCHAR2(5) DEFAULT 'Y',                                                      
  DEPT_NAME VARCHAR2(50),                                                                             
  POSITION_NAME VARCHAR2(50),                                                                      
  BANK_NO VARCHAR2(50),                                                                                
  BANK_ACCOUNT VARCHAR2(50) ,                                                                     
  BANK_DESCRIPTION VARCHAR2(150),                                                               
  ATTRIBUTE1 VARCHAR2(150),   
  ATTRIBUTE2 VARCHAR2(150),   
  ATTRIBUTE3 VARCHAR2(150),   
  ATTRIBUTE4 VARCHAR2(150),   
  ATTRIBUTE5 VARCHAR2(150),   
  ATTRIBUTE6 VARCHAR2(150),   
  CONSTRAINT EMPLOYEE_PK PRIMARY KEY (EMP_NO)
);

-------------------------------------------------------------------------------------------Department---------------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------Table--------------------------------------------------------------------------------------------------------

CREATE TABLE DEPARTMENT
( DEPT_NO VARCHAR2(50) NOT NULL,                                                                 
  DEPT_NAME VARCHAR2(50) NOT NULL,                                                             
  DESCRIPTION VARCHAR2(150),                                                                        
  DEPT_LEADER VARCHAR2(50),                                                                         
  DEPT_PARENT_NAME VARCHAR2(50) ,
  ATTRIBUTE1 VARCHAR2(150),   
  CONSTRAINT DEPARTMENT_PK PRIMARY KEY (DEPT_NO)
);

-------------------------------------------------------------------------------------------Position------------------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------Table--------------------------------------------------------------------------------------------------------
CREATE TABLE POSITION
( POSITION_NAME VARCHAR2(50) NOT NULL,                                                      
  DESCRIPTION VARCHAR2(150),                                                                        
  ATTRIBUTE1 VARCHAR2(150),   
  CONSTRAINT POSITION_PK PRIMARY KEY (POSITION_NAME)
);

----------------------------------------------------------------------------------------------Salary------------------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------Table--------------------------------------------------------------------------------------------------------
CREATE TABLE SALARY
( SAL_NO VARCHAR2(50) NOT NULL,                                                                  
  SAL_NAME VARCHAR2(50) NOT NULL,                                                               
  DESCRIPTION VARCHAR2(150),                                                                        
  SAL_SIGN VARCHAR2(10) NOT NULL,                                                                 
  CYCLE_NAME VARCHAR2(50) NOT NULL,                                                           
  SAL_TAX VARCHAR2(10),                                                                                 
  RATIO NUMBER(10),                                                                                                                                            
  ATTRIBUTE1 VARCHAR2(150),   
  ATTRIBUTE2 VARCHAR2(150),   
  CONSTRAINT SALARY_PK PRIMARY KEY (SAL_NO)
);

---------------------------------------------------------------------------------------------Salary Cycle--------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------Table--------------------------------------------------------------------------------------------------------
CREATE TABLE SAL_CYCLE
( CYCLE_NAME VARCHAR2(50) NOT NULL,                                                            
  DESCRIPTION VARCHAR2(150),                                                                       
  DAYS NUMBER(10),                                                                                          
  ATTRIBUTE1 VARCHAR2(150),   
  CONSTRAINT SAL_CYCLE_PK PRIMARY KEY (CYCLE_NAME)
);

----------------------------------------------------------------------------------------------Employee Salary---------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------Table--------------------------------------------------------------------------------------------------------
CREATE TABLE EMP_SAL
( EMP_SAL_NO VARCHAR2(50) NOT NULL,                                                           
  EMP_SAL_NAME VARCHAR2(50) NOT NULL,                                                     
  DESCRIPTION VARCHAR2(150),                                                                       
  EMP_SAL_SIGN VARCHAR2(10) NOT NULL,                                                        
  CYCLE_NAME VARCHAR2(50) NOT NULL,                                                            
  EMP_SAL_TAX VARCHAR2(10),                                                                       
  AMOUNT NUMBER(20) ,                                                                                    
  EMP_NAME VARCHAR2(50)   NOT NULL,
  ATTRIBUTE1 VARCHAR2(150),   
  ATTRIBUTE2 VARCHAR2(150),   
  CONSTRAINT EMP_SAL_PK PRIMARY KEY (EMP_SAL_NO)
);
COMMIT;

----------------------------------------------------------------------------------------------Employee Calendar---------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------Table--------------------------------------------------------------------------------------------------------
CREATE TABLE EMP_SCHEDULE
( EMP_SCHEDULE_NAME VARCHAR2(50) NOT NULL,                                             
  EMP_NAME VARCHAR2(50) NOT NULL,                                                               
  DESCRIPTION VARCHAR2(150),                                                                         
  VACATION_NAME VARCHAR2(50) NOT NULL,                                                      
  SCHEDULE_START_DATE DATE,
  SCHEDULE_END_DATE DATE,
  ATTRIBUTE1 VARCHAR2(150),   
  ATTRIBUTE2 VARCHAR2(150)
);

CREATE TABLE EMP_ACTUAL
( EMP_ACTUAL_NAME VARCHAR2(50) NOT NULL,                                                
  EMP_NAME VARCHAR2(50) NOT NULL,                                                               
  DESCRIPTION VARCHAR2(150),                                                                         
  VACATION_NAME VARCHAR2(50) NOT NULL,                                                      
  ACTUAL_START_DATE DATE,
  ACTUAL_END_DATE DATE,
  ATTRIBUTE1 VARCHAR2(150),   
  ATTRIBUTE2 VARCHAR2(150)
);

----------------------------------------------------------------------------------------------Vacation---------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------Table--------------------------------------------------------------------------------------------------------
CREATE TABLE VACATION
( VACATION_NAME VARCHAR2(50) NOT NULL,                                                     
  DESCRIPTION VARCHAR2(150),                                                                        
  ATTRIBUTE1 VARCHAR2(150),   
  CONSTRAINT VACATION_PK PRIMARY KEY (VACATION_NAME)
);

---------------------------------------------------------------------------------------Employee Bank Transaction------------------------
CREATE TABLE EMP_BANK_TRANSACTION
( TRANSACTION_ID NUMBER(15) NOT NULL,
  EMP_BANK_NO VARCHAR2(50),                                                     --銀行代號
  EMP_BANK_ACCOUNT VARCHAR2(50) NOT NULL,                                       --銀行帳號
  DESCRIPTION VARCHAR2(150),                                                    --摘要
  EMP_NAME VARCHAR2(50) NOT NULL,                                               --員工
  TRANSACTION_DATE DATE,                                                        --轉帳日
  AMOUNT NUMBER(15),                                                            --轉帳金額
  ATTRIBUTE1 VARCHAR2(150),   
  ATTRIBUTE2 VARCHAR2(150),   
  CONSTRAINT EMP_BANK_TRANSACTION_PK PRIMARY KEY (TRANSACTION_ID)
);



---------------------------------------------------------------------------------------AUTHORITY---------------------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------Frame_Authority----------------------------------------------------------------------------------------------------
CREATE TABLE FRAME_AUTHORITY
( FRAME_NO VARCHAR2(50) ,                              
  DESCRIPTION VARCHAR2(150) NOT NULL,            
  ENABLE_FLAG VARCHAR2(2) DEFAULT 'Y',                                                                                                   
  ATTRIBUTE1 VARCHAR2(150),   
  CONSTRAINT FRAME_AUTHORITY_PK PRIMARY KEY (FRAME_NO)
);

---------------------------------------------------------------------------------------Employee User Authority -------------------------------------------------------------------------------------
CREATE TABLE USER_AUTHORITY
( USER_AU_ID NUMBER(15) ,
  USER_ID NUMBER(10) NOT NULL,                                                 
  FRAME_NO VARCHAR2(50) NOT NULL,                                       
  ENABLE_FLAG VARCHAR2(2) DEFAULT 'Y',                                                                                                   
  ATTRIBUTE1 VARCHAR2(150),   
  CONSTRAINT USER_AUTHORITY_PK PRIMARY KEY (USER_AU_ID)
);



----------------------------------------------------------------------------------------------Employee Period Salary---------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------Table--------------------------------------------------------------------------------------------------------
CREATE TABLE EMP_PERIOD_SAL
( EMP_PERIOD_SAL_NO VARCHAR2(50) NOT NULL,                                                            
  EMP_PERIOD_SAL_NAME VARCHAR2(50) NOT NULL,                                                        
  DESCRIPTION VARCHAR2(150),                                                                         
  EMP_PERIOD_SAL_SIGN VARCHAR2(10) NOT NULL,                                                         
  CYCLE_NAME VARCHAR2(50) NOT NULL,                                                             
  EMP_PERIOD_SAL_TAX VARCHAR2(10),                                                                         
  AMOUNT NUMBER(20) ,                                                                                    
  EMP_NAME VARCHAR2(50)   NOT NULL,
  START_DATE DATE NOT NULL,
  END_DATE DATE NOT NULL,
  TRANSACTION_DATE DATE NOT NULL,
  ATTRIBUTE1 VARCHAR2(150),   
  ATTRIBUTE2 VARCHAR2(150),   
  CONSTRAINT EMP_PERIOD_SAL_PK PRIMARY KEY (EMP_PERIOD_SAL_NO)
);
