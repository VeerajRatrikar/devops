c1 - create maven project - groupid=org.apache.maven.archtypes artifactid=maven-archtypes-quickstart version=1.1
create a folder JSON add student.json
google - maven repository - search for json -simple json version 1.1 - or  - search for xml- dom4j version 2.0.3
paste it in POM.XML
in src/test/java put the java file 


JAVA FILE OF XML:

package XMLDEMO.XMLDEMO;

import javax.xml.parsers.*;  
import org.w3c.dom.*;  
import java.io.*;

public class XMLProgam {
    public static void main(String[] args) throws Exception {

        Document d = DocumentBuilderFactory.newInstance()
                        .newDocumentBuilder()
                        .parse(new File("XML/student.xml"));

        NodeList n = d.getElementsByTagName("Person");

        for (int i = 0; i < n.getLength(); i++)
            System.out.println(
                ((Element)n.item(i)).getElementsByTagName("FirstName").item(0).getTextContent()
                + " " +
                ((Element)n.item(i)).getElementsByTagName("LastName").item(0).getTextContent()
            );
    }
}

------------------------------------------------------------------------------------------------------
student.xml:

<People>
    <Person>
        <FirstName>John</FirstName>
        <LastName>Doe</LastName>
    </Person>

    <Person>
        <FirstName>Jane</FirstName>
        <LastName>Smith</LastName>
    </Person>
</People>

------------------------------------------------------------------------------------------------------
Dependency:
jackson-dataformat-xml
<dependency>
    <groupId>tools.jackson.dataformat</groupId>
    <artifactId>jackson-dataformat-xml</artifactId>
    <version>3.0.3</version>
</dependency>
------------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------------



JAVA ReadJSON

package org.apache.maven.archetypes.maven_archetype_quickstart;

import java.io.FileReader;
import java.io.IOException;
import org.json.simple.JSONObject;
import org.json.simple.parser.JSONParser;
import org.json.simple.parser.ParseException;

public class ReadJSON {

    public static void main(String[] args) throws IOException, ParseException {

        JSONParser jsonparser = new JSONParser();
        FileReader reader = new FileReader(".\\JSON\\student.json");

        Object obj = jsonparser.parse(reader);
        JSONObject studentobj = (JSONObject)obj;

        String fname = (String) studentobj.get("firstname");
        String lname = (String) studentobj.get("lastname");

        System.out.println("First Name: " + fname);
        System.out.println("Last Name: " + lname);
    }
}

----------------------------------------------------------------------------------------------------------

Student.json

{
  "firstname": "John",
  "lastname": "Doe"
}

-----------------------------------------------------------------------------------------------------------

dependceies

<dependency>
    <groupId>com.googlecode.json-simple</groupId>
    <artifactId>json-simple</artifactId>
    <version>1.1.1</version>
</dependency>

----------------------------------------------------------------------------------------------------------
SQL Java file
import java.sql.*;

public class ReadSQL {
    public static void main(String[] args) {
        try {
            Connection con = DriverManager.getConnection(
                    "jdbc:mysql://localhost:3306/school", "root", "root@123");

            Statement st = con.createStatement();
            ResultSet rs = st.executeQuery("SELECT * FROM students");

            while (rs.next()) {
                System.out.println("ID: " + rs.getInt(1));
                System.out.println("Name: " + rs.getString(2));
                System.out.println("Age: " + rs.getInt(3));
            }
            con.close();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
---------------------------------------------------------------------------------------------------------
create database

CREATE DATABASE school;
USE school;

CREATE TABLE students (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    age INT
);

INSERT INTO students VALUES 
(1, 'John', 25),
(2, 'Mary', 22);
---------------------------------------------------------------------------------------------------------
dependencies

<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <version>8.0.33</version>
</dependency>
----------------------------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------------------------

c2
 - Jenkins - admin password
new item - freestyle project 
configure go to settings - plugin - slack notifications
settings - system - slack --- workspace = vvcegroup credential= add- Jenkins
 (https://my.slack.com/services/new/jenkins-ci - 
choose - #devops-demo - add integration - step 3- secret text  )
kind - secret text - paste - id -description(D) - save - credential - click on D - save
configure project in dashboard - build steps - execute batch command - java --version 
post build actions - slack notification - enable checkbox 
apply - save - build now -console output
vvcegroup.slack.com verify channel 

---------------------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------------------

A3
 - Jenkins - admin password
new item - freestyle project
configure project in dashboard - SCM - Git - url of repository (should contain one java or python file)
build steps - execute batch command - java --version
javac lab.java
java lab

or 
python --version
python lab.py 
                               
apply - save - build now -console output






