### **SQL Queries**





##### Queries for creating index



&#x20;CREATE INDEX idx\_department ON public.hr\_data ("Department");

&#x20;CREATE INDEX idx\_jobrole ON public.hr\_data ("JobRole");

&#x20;CREATE INDEX idx\_attrition ON public.hr\_data ("Attrition");

&#x20;CREATE INDEX idx\_overtime ON public.hr\_data ("OverTime");



##### Queries for Calculate the attrition rate



&#x20;SELECT

&#x20;    ROUND(

&#x20;        100.0 \* SUM(CASE WHEN "Attrition" = True THEN 1 ELSE 0 END)

&#x20;         / COUNT(\*), 2

&#x20;    ) AS AttritionRate



&#x20;    FROM hr\_data;







##### Queries for Department-wise Employee Count





SELECT

&#x20;       "Department",

&#x20;        COUNT(\*) AS EmployeeCount

FROM hr\_data

GROUP BY "Department"

ORDER BY EmployeeCount DESC;



##### Queries for Reason for Attrition by Job Role



SELECT

&#x20;   "JobRole",



&#x20;   COUNT(\*) AS TotalEmployees,



&#x20;   SUM(

&#x20;       CASE

&#x20;           WHEN "Attrition" = TRUE THEN 1

&#x20;           ELSE 0

&#x20;       END

&#x20;   ) AS AttritionCount,



&#x20;   ROUND(

&#x20;       100.0 \*

&#x20;       SUM(

&#x20;           CASE

&#x20;               WHEN "Attrition" = TRUE THEN 1

&#x20;               ELSE 0

&#x20;           END

&#x20;       ) / COUNT(\*),

&#x20;       2

&#x20;   ) AS AttritionRate



FROM hr\_data



GROUP BY "JobRole"



ORDER BY AttritionRate DESC;





##### Queries for Attrition by OverTime vs Attrition



SELECT

&#x20;      "OverTime",

&#x20;      COUNT(\*) AS TotalEmployees,

&#x20;      SUM (CASE WHEN "Attrition" = True THEN 1 ELSE 0 END)

&#x20;       AS AttritionCount,

&#x20;     ROUND(

&#x20;           100.0 \* SUM(CASE WHEN "Attrition" = True THEN 1 ELSE 0 END)

&#x20;            / COUNT(\*), 2) AS AttritionRate

FROM hr\_data

GROUP BY "OverTime"

ORDER BY "OverTime" DESC;





##### \-- Queries of Attrition by WorkLifeBalance vs Attrition --



SELECT

&#x20;   "WorkLifeBalance",



&#x20;   COUNT(\*) AS TotalEmployees,



&#x20;   ROUND(

&#x20;       100.0 \*

&#x20;       SUM(

&#x20;           CASE

&#x20;               WHEN "Attrition" = TRUE THEN 1

&#x20;               ELSE 0

&#x20;           END

&#x20;       ) / COUNT(\*),

&#x20;       2

&#x20;   ) AS AttritionRate



FROM hr\_data



GROUP BY "WorkLifeBalance"



ORDER BY "WorkLifeBalance";

##### 

##### \--Queries of Attrition by JobRole vs Attrition --



SELECT

&#x20;   "JobRole",

&#x20;   COUNT(\*) AS TotalEmployees,

&#x20;   SUM(CASE WHEN "Attrition" = True THEN 1 ELSE 0 END)

&#x20;    AS AttritionCount,

&#x20;   ROUND(

&#x20;       100.0 \* SUM(CASE WHEN "Attrition" = True THEN 1 ELSE 0 END)

&#x20;        / COUNT(\*),

&#x20;       2

&#x20;   ) AS AttritionRate

FROM hr\_data

GROUP BY "JobRole"

ORDER BY AttritionRate DESC;



##### \--Queries of Attrition by Job Satisfaction vs Attrition --



SELECT

&#x20;   "JobSatisfaction",

&#x20;   COUNT(\*) AS TotalEmployees,

&#x20;   SUM(CASE WHEN "Attrition" = True THEN 1 ELSE 0 END)

&#x20;    AS AttritionCount,

&#x20;   ROUND(

&#x20;       100.0 \* SUM(CASE WHEN "Attrition" = True THEN 1 ELSE 0 END)

&#x20;        / COUNT(\*),

&#x20;       2

&#x20;   ) AS AttritionRate

FROM hr\_data

GROUP BY "JobSatisfaction"

ORDER BY "JobSatisfaction" DESC;





#### \--Queries of Attrition by Department vs Attrition --



SELECT

&#x20;   "Department",

&#x20;   COUNT(\*) AS TotalEmployees,

&#x20;   SUM(CASE WHEN "Attrition" = True THEN 1 ELSE 0 END)

&#x20;    AS AttritionCount,

&#x20;   ROUND(

&#x20;       100.0 \* SUM(CASE WHEN "Attrition" = True THEN 1 ELSE 0 END)

&#x20;        / COUNT(\*),

&#x20;       2

&#x20;   ) AS AttritionRate

FROM hr\_data

GROUP BY "Department"

ORDER BY AttritionRate DESC;







##### \--Queries of Correlation between Monthly Income and Attrition --



SELECT

&#x20;         CASE

&#x20;         WHEN "MonthlyIncome" BETWEEN 40000 AND 70000 THEN 'MEDIUM INCOME'

&#x20;         WHEN "MonthlyIncome" < 40000 THEN 'LOW INCOME'

&#x20;         ELSE 'HIGH INCOME'

&#x20;     END AS IncomeBracket,

ROUND(100.0 \* SUM(CASE WHEN "Attrition" = True THEN 1 ELSE 0 END) / COUNT(\*), 2) AS AttritionRate

FROM hr\_data

GROUP BY IncomeBracket

ORDER BY IncomeBracket ;





#### Not this one

&#x20;



SELECT



&#x20;      MIN ("MonthlyIncome") AS MinIncome,

&#x20;      MAX ("MonthlyIncome") AS MaxIncome,

&#x20;      AVG ("MonthlyIncome") AS AvgIncome

FROM hr\_data;







##### \--Queries for Correlation between MonthlyIncome and Attrition Using Quartiles --



SELECT

&#x20;

&#x20;     percentile\_cont(0.25) WITHIN GROUP (ORDER BY "MonthlyIncome") AS Q1,

&#x20;     percentile\_cont(0.50) WITHIN GROUP (ORDER BY "MonthlyIncome") AS Q2,

&#x20;     percentile\_cont(0.75) WITHIN GROUP (ORDER BY "MonthlyIncome") AS Q3

FROM hr\_data;



\-- Creating View for hr\_data Analysis --



CREATE OR REPLACE VIEW hr\_data\_analysis AS

SELECT

&#x20;    "EmployeeID",

&#x20;    "Age",

&#x20;    "Gender",

&#x20;    "JobRole",

&#x20;    "Attrition",

&#x20;    "WorkLifeBalance",

&#x20;    "OverTime",

&#x20;    "MonthlyIncome",

&#x20;    "JobSatisfaction",

&#x20;    "Department",

&#x20;    "DateOfJoining",

&#x20;    "YearsAtCompany",

&#x20;    "PerformanceRating"

FROM hr\_data;



SELECT \*

FROM hr\_data\_analysis

ORDER BY "EmployeeID" ASC

LIMIT 10;



SELECT "EmployeeID"

FROM hr\_data

LIMIT 10;





##### Python Code for Data Cleaning  



pd.set\_option('display.max\_columns', None)



profile=pd.DataFrame({                                                                                                                  

&#x20;   "Column": **df\_db**.columns,                  

&#x20;   "DataType": **df\_db**.dtypes,

&#x20;   "NullCount": **df\_db**.isnull().sum(),

&#x20;   "UniqueCount": **df\_db**.nunique(),

&#x20;   "DuplicatedCount": **df\_db**.duplicated().sum()

})



profile.sort\_values(by="UniqueCount", ascending=True)



\[ Why **df\_db** because we Bring all data from the PostgreSQL table hr\_data into a Pandas DataFrame.]







##### Merge data from staging to production 

##### 

from sqlalchemy import text



columns = df\_db.columns.tolist()

update\_columns = \[col for col in columns if col != "EmployeeID"]



update\_set = ", ".join(

&#x20;   \[f'"{col}" = EXCLUDED."{col}"' for col in update\_columns]

)



merge\_query = f"""

INSERT INTO public.hr\_data

SELECT \*

FROM public.hr\_data\_staging

ON CONFLICT ("EmployeeID")

DO UPDATE SET

{update\_set};

"""



with engine.begin() as conn:

&#x20;   conn.execute(text(merge\_query))



print("Production merge completed successfully!") 



##### **Main focus on SQL query if you have to merge data or table**



##### Python code for Income Quartile



df\_db\["IncomeQuartile"] = pd.qcut(

&#x20;   df\_db\["MonthlyIncome"],

&#x20;   q=4,

&#x20;   labels=\[

&#x20;       "Q1 - Bottom 25%",

&#x20;       "Q2 - 25% to 50%",

&#x20;       "Q3 - 50% to 75%",

&#x20;       "Q4 - Top 25%"

&#x20;   ]

)



result = (

&#x20;   df\_db.groupby("IncomeQuartile", observed=False)

&#x20;   .agg(

&#x20;       TotalEmployees=("EmployeeID", "count"),

&#x20;       AttritionCount=("Attrition", "sum")

&#x20;   )

)



result\["AttritionRate"] = round(

&#x20;   result\["AttritionCount"] \* 100 / result\["TotalEmployees"],

&#x20;   2

)



result = result.sort\_values(

&#x20;   by="AttritionRate",

&#x20;   ascending=False

)



print(result)



&#x20;          

