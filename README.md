# Data Mapper - Java Library for JSON and XML Parsing

[![License](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)

Data Mapper is a powerful Java library that offers a comprehensive solution for parsing, transforming, and mapping JSON or XML files to Java beans, driven by a given set of rules. It is designed to simplify the process of data manipulation and conversion in your Java projects.
<br><br> With the latest version, Data Mapper introduces a new feature that allows seamless transformation of one Java bean to another type. Now, you can effortlessly convert your Java beans between different classes, making it even more versatile and adaptable to various data processing scenarios.

## Features
- Effortlessly parse JSON and XML files into Java beans.
- Seamlessly transform JSON and XML strings into Java beans.
- Preview the transformed JSON or XML as a string.
- Flexibly transform one Java bean type into another using specified rules.
- Transform data using custom rules to match specific requirements.
- Exceptionally fast and lightweight for optimal performance.

## Installation

To use Data Mapper in your project, include the following dependency:

```xml
<dependency>
    <groupId>org.perfios</groupId>
    <artifactId>data-mapper</artifactId>
    <version>1.0.0</version>
</dependency>
```
## Methods exposed
### 1. `transformFile`
Transforms a JSON or XML file according to specified rules and returns an instance of the desired class type. <br>The overloaded version of this method accepts JSON or XML along with the rules as `File` type to perform the same.
#### Prameters expected
<table style="border: none; width: 100%; padding: 0; margin: 0;">
  <tr>
    <td><b><i>inputPath</i></b><br> The path to the input file (JSON or XML) to be transformed.</td>
    <td><b><i>rulesPath</i></b><br> The path to the rules file containing transformation rules.</td>
    <td rowspan="2"><b><i>className</i></b><br> The desired class type to be returned after transformation.</td>
  </tr>
  <tr>
    <td><b><i>input</i></b><br> The input JSON or XML file to be transformed.</td>
    <td><b><i>rules</i></b><br> The rules file containing transformation rules.</td>
  </tr>
</table>

#### Returns
An instance of the desired class type, representing the transformed data.

#### Usage
```java
import org.perfios.DataMapper;
import org.perfios.DataMapperImpl;

public class Usage
{
	public static void main(String[] args) {
		// Create an instance of the DataMapper interface
        DataMapper dataMapper = new DataMapperImpl();

        // Specify the paths to the input JSON file and the rules file
        String inputPath = "/path/to/input.json";
        String rulesPath = "/path/to/rules.txt";
        
        // Define the desired Java bean class (Employee in this case)
        Class<Employee> desiredClass = Employee.class;

        // Transform the JSON file using the specified rules and class type
        Employee transformedEmployee = dataMapper.transformFile(inputPath, rulesPath, desiredClass);
	}
}
```

### 2. `transformString`
Transforms a JSON or XML string according to specified rules and returns an instance of the desired class type.
#### Prameters expected
<table style="border: none; width: 100%; padding: 0; margin: 0;">
  <tr>
    <td><b><i>inputString</i></b><br>  The JSON or XML string to be transformed.</td>
    <td><b><i>rulesString</i></b><br> The string containing transformation rules.</td>
    <td><b><i>className</i></b><br> The desired class type to be returned after transformation.</td>
  </tr>
  
</table>

#### Returns
An instance of the desired class type, representing the transformed data.

#### Usage
```java
import org.perfios.DataMapper;
import org.perfios.DataMapperImpl;

public class Usage
{
	public static void main(String[] args) {
		// Create an instance of the DataMapper interface
        DataMapper dataMapper = new DataMapperImpl();

        // Specify the paths to the input JSON file and the rules file
        String inputPath = "/path/to/input.json";
        String rulesPath = "/path/to/rules.txt";
        
        // Read the contents of the input JSON file and rules file into strings
        String inputString = new String(Files.readAllBytes(Paths.get(inputPath.getAbsolutePath())));
        String rulesString = new String(Files.readAllBytes(Paths.get(rulesPath.getAbsolutePath())));
       
        
        // Define the desired Java bean class (Employee in this case)
        Class<Employee> desiredClass = Employee.class;

        // Transform the JSON file using the specified rules and class type
        Employee transformedEmployee = dataMapper.transformString(inputString, rulesString, desiredClass);
	}
}
```

### 3. `transformBean`
Transforms an input Java Bean according to specified rules and returns another Java bean of the desired type. <br>The overloaded version of this method accepts the transformation rules as `File` type to perform the same.
#### Prameters expected
<table style="border: none; width: 100%; padding: 0; margin: 0;">
  <tr>
    <td rowspan="2"><b><i>inputBean</i></b><br>The input Java bean to be transformed.</td>
    <td><b><i>rulesString</i></b><br> The rules string containing transformation rules.</td>
    <td rowspan="2"><b><i>className</i></b><br> The desired class type to be returned after transformation.</td>
  </tr>
  <tr>
    <td><b><i>rules</i></b><br> The rules file containing transformation rules.</td>
  </tr>
</table>

#### Returns
An instance of the desired class type, representing the transformed data.

#### Usage
```java
import org.perfios.DataMapper;
import org.perfios.DataMapperImpl;

public class Usage
{
	public static void main(String[] args) {
		// Create an instance of the DataMapper interface
        DataMapper dataMapper = new DataMapperImpl();

        // Specify the paths to the input Java bean and the rules file
        EmployeeTypeA inputBean = new EmployeeTypeA("emp_id","emp_name","emp_salary");
        File rules= new File("/path/to/rules.txt");
        
        // Define the desired Java bean class (Employee in this case)
        Class<EmployeeTypeB> desiredClass = EmployeeTypeB.class;

        // Transform the JSON file using the specified rules and class type
        EmployeeTypeB transformedEmployee = dataMapper.transformFile(inputBean, rules, desiredClass);
	}
}
```

### 4. `getTransformedString`
Transforms an input JSON or XML string according to specified rules and returns a string representing the transformed input in the desired extension format. <br>The overloaded version of this method accepts JSON or XML along with the rules as `File` type to perform the same.
#### Prameters expected
<table style="border: none; width: 100%; padding: 0; margin: 0;">
  <tr>
    <td><b><i>input</i></b><br>The input JSON or XML string to be transformed.</td>
    <td><b><i>rules</i></b><br> The rules string containing transformation rules.</td>
    <td rowspan="2"><b><i>ext</i></b><br> The extension indicating the format of the input file (JSON or XML).</td>
  </tr>
  <tr>
    <td><b><i>input</i></b><br>The input JSON or XML file to be transformed.</td>
    <td><b><i>rules</i></b><br> The rules file containing transformation rules.</td>
  </tr>
</table>

#### Returns
A string representing the transformed JSON or XML input in the desired extension format.

#### Usage
```java
import org.perfios.DataMapper;
import org.perfios.DataMapperImpl;

public class Usage
{
	public static void main(String[] args) {
		// Create an instance of the DataMapper interface
        DataMapper dataMapper = new DataMapperImpl();

        //Create File objects of input file and rules file using their respective paths
        File input = new File("/path/to/input.json");
        File rules = new File("/path/to/rules.txt");

        // Transform the JSON file using the specified rules and desired output type
        String transformedEmployee = dataMapper.getTransformedString(input, rules, DataMapperImpl.Extension.XML);
	}
}
```
## Contact
If you have any questions or feedback, feel free to reach out to us via [e-mail](mailto:nithinsudarsan740@gmail.com) .
