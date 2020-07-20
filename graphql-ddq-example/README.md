# GraphQL Dynamic Data Query - DyDaQ

**It is a Demo Application developed for a Sample Hospital Management System**

Database Design
![Database Design](../images/ErDiagram.PNG)

#### Steps to Start the application
Start the application please run the Main App: [SampleProjectHospitalManagement.java](src/main/java/com/americanexpress/dydaq/graphql/ddq/dynamicquery/demoproj/SampleProjectHospitalManagement.java) as Spring Boot Application and then follow the below steps : 
1. Once Application is started, open url [http://localhost:8449/dydaqgraphqlddq/gui](http://localhost:8449/dydaqgraphqlddq/gui) in your browser to load GraphQL playground GUI.
2. And add the url http://localhost:8449/dydaqgraphqlddq/graphql (the rest endpoint which will be serving all your GraphQl request) in the inner placeholder as shown in the below image.
3. Add any valid query in the left pane.
4. Hit the button to execute the query.

Please refer to below diagram :

![Execute Query](../images/appUI.PNG)

For viewing the schema details,click **DOCS** button hanging on right side.**SCHEMA** is not working due to some known bugs in **GrahQL Playground**

Below are some valid Queries which you can try out : 

1.  { fetchHospitalWithSurgeonSpeciality(HospitalId:1001) {name surgeon { fullName docSpeciality { experience } }}}
2.  { fetchHospitalWithSurgeonSpeciality(HospitalId:1001) { surgeon { fullName docSpeciality { experience } }}}
3.  { fetchHospitalWithSurgeonSpecialityTwoQuerys(HospitalId:1001) {name surgeon { fullName docSpeciality { experience } }}}
4.  { listSurgeonWithOrderByContactNo {fullName contactNo}}
5.  { hospitalWithMaxEmployee {hospitalId name noOfEmployees city contactNo}}
6.  { countHospitalByCity{city hospitalCount}}  

You can check the code implementation for different Query Builder below :
1.  [SimpleQueryBuilder](src/main/java/com/americanexpress/dydaq/graphql/ddq/dynamicquery/demoproj/resolver/SimpleQueryResolver.java)
2.  [JoinQueryBuilder](src/main/java/com/americanexpress/dydaq/graphql/ddq/dynamicquery/demoproj/resolver/JoinQueryResolver.java) 
3.  [NativeQueryBuilder](src/main/java/com/americanexpress/dydaq/graphql/ddq/dynamicquery/demoproj/resolver/NativeQueryTestResolver.java)

#### Buld your own application
While developing your own DyDaQ enabled application,follow the below steps to build the POM : 
1.  Build the jar of DyDaQ.
2.  Use the POM provided in this module(graphql-ddq-example) and make following modifications to it : 
    - Remove parent tag completely.
    - Update resources directory inside <build> tag depending upon your project structure.
2.  Update the dependency of DyDaQ core and DyDaQ plugin from the DyDaQ jar built into your project's POM. 