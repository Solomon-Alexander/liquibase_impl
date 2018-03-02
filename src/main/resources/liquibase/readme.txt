# Run Liquibase in Command Line
# Migrate
liquibase --classpath=C:/Data/Dialog/m2/oracle/ojdbc/1.4/ojdbc-1.4.jar --driver=oracle.jdbc.driver.OracleDriver --changeLogFile=C:/Data/Dialog/workspace/lassi/src/main/resources/liquibase/db-changelog-1.0.xml --url="jdbc:oracle:thin:@54.153.240.235:1531:LVMAPDEV" --username=mapdata_dev --password=password#14570 migrate

#Update
liquibase --classpath=C:/Data/Dialog/m2/oracle/ojdbc/1.4/ojdbc-1.4.jar --driver=oracle.jdbc.driver.OracleDriver --changeLogFile=C:/Data/Dialog/workspace/lassi/src/main/resources/liquibase/db-changelog-1.0.xml --url="jdbc:oracle:thin:@54.153.240.235:1531:LVMAPDEV" --username=mapdata_dev --password=password#14570 update

# Input the liquibase.properties file 
liquibase  --defaultsFile=C:/Data/Dialog/workspace/lassi/src/main/resources/liquibase/liquibase.properties \
           --classpath=C:/Data/Dialog/m2/oracle/ojdbc/1.4/ojdbc-1.4.jar  \
           --changeLogFile=C:/Data/Dialog/workspace/lassi/src/main/resources/liquibase/db-changelog-1.0.xml   \
           update
		   
#Migrate/Update DB using Liquibase in Maven
mvn liquibase:update
mvn liquibase:migrate (deprecated)

#Rollback DB using Liquibase in Maven
Here, we define how many changesets we need to be rolled back. If we define it to be one, the last changeset execute will be rolled back:

a) Based on changed sets
1) mvn liquibase:rollback -Dliquibase.rollbackCount=1
Rollback the last change set
2) mvn liquibase:rollback -Dliquibase.rollbackCount=2
Rollback the last but one change set
3) mvn liquibase:rollback -Dliquibase.rollbackCount=3
If there are only 3 change sets, all three will be rolled back

b) Based on Date	
mvn liquibase:rollback "-Dliquibase.rollbackDate=Jun 03, 2017"

c) Based on Tag
mvn liquibase:rollback -Dliquibase.rollbackTag=1.0     