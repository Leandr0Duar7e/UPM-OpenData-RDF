# Transform Data into RDFs

## Overview

After the ontology has been developed, the data from the selected data source can be transformed into RDF format. This task is the core technical implementation phase where structured data becomes Linked Data through systematic mapping and conversion processes. The transformation requires careful consideration of serialization formats, tool selection, mapping strategies, and quality evaluation.

## Inputs
- Source data (analyzed and prepared)
- Resource naming strategy
- Developed ontology

## Outputs
- RDF data (in chosen serialization format)
- Transformation mappings
- Quality validation results

## 4-Step Transformation Process

### Step 1: Select RDF Serialization Format

**Purpose**: Choose appropriate RDF syntax for data representation and usage requirements

#### Available W3C Standard Serializations

All mentioned serializations are W3C recommendations (official standards), ensuring interoperability and tool support.

#### RDF/XML
- **Format**: XML-based serialization
- **Characteristics**: Less human-readable, XML structure
- **Best For**: Legacy systems, XML-native environments
- **Processing**: Standard XML parsers can handle structure
- **Use Cases**: Enterprise systems with XML infrastructure

**Example Structure**:
```xml
<rdf:RDF xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#"
         xmlns:ex="http://example.org/">
  <ex:Building rdf:about="http://example.org/building123">
    <ex:hasName>Office Building</ex:hasName>
  </ex:Building>
</rdf:RDF>
```

#### Turtle (Terse RDF Triple Language)
- **Format**: Compact, human-readable text format
- **Characteristics**: Easy to read and write manually
- **Processing**: Fast parsing and processing
- **Best For**: Development, debugging, small to medium datasets
- **Community**: Widely preferred by developers

**Example Structure**:
```turtle
@prefix ex: <http://example.org/> .

ex:building123 a ex:Building ;
    ex:hasName "Office Building" .
```

#### N-Triples
- **Format**: Line-based, simplest RDF format
- **Characteristics**: One triple per line, very easy to read
- **Processing**: Extremely fast parsing, simple streaming
- **Best For**: Large datasets, streaming processing, data exchange
- **Debugging**: Excellent for validation and testing

**Example Structure**:
```
<http://example.org/building123> <http://www.w3.org/1999/02/22-rdf-syntax-ns#type> <http://example.org/Building> .
<http://example.org/building123> <http://example.org/hasName> "Office Building" .
```

#### JSON-LD
- **Format**: JSON-based with linked data context
- **Characteristics**: Native JSON structure with semantic extensions
- **Best For**: Web applications, APIs, JavaScript environments
- **Integration**: Seamless integration with JSON-based systems
- **Flexibility**: Can embed in existing JSON applications

**Example Structure**:
```json
{
  "@context": {"ex": "http://example.org/"},
  "@id": "ex:building123",
  "@type": "ex:Building",
  "ex:hasName": "Office Building"
}
```

#### Selection Criteria

- **Human Readability**: Turtle > N-Triples > JSON-LD > RDF/XML
- **Processing Speed**: N-Triples > Turtle ≈ JSON-LD > RDF/XML  
- **Compactness**: Turtle > JSON-LD > RDF/XML > N-Triples
- **Tool Support**: All formats widely supported
- **Use Case Fit**: Consider target applications and user needs

### Step 2: Select Transformation Tool

**Purpose**: Choose appropriate software based on data format and transformation requirements

#### Database-to-RDF Tools

##### morph-RDB
- **Standard Compliance**: W3C R2RML specification
- **Functionality**: RDB2RDF engine with query translation support
- **Database Support**: MySQL, PostgreSQL, MonetDB
- **Features**: Direct SQL-to-SPARQL translation
- **Best For**: Relational databases requiring standard compliance

##### D2R Server  
- **Approach**: On-demand RDF instance creation
- **Features**: Declarative mapping language for ontology-database relationships
- **Output**: RDF instances from relational data
- **Integration**: Can expose databases as SPARQL endpoints
- **Best For**: Dynamic RDF generation from existing databases

##### TopBraid Composer
- **Approach**: Commercial comprehensive RDF platform
- **Features**: Database row-to-instance conversion
- **Integration**: Full ontology development and data management
- **Support**: Professional support and advanced features
- **Best For**: Enterprise environments with complex requirements

#### Stream-to-RDF Tools

##### morph-streams
- **Capability**: Real-time RDF generation from data streams
- **Features**: Stream querying and continuous RDF output
- **Use Cases**: IoT sensors, social media feeds, real-time monitoring
- **Performance**: Optimized for high-throughput streaming data

##### D2R Server (Stream Mode)
- **Approach**: Two-stage process (stream → database → RDF)
- **Process**: Store streaming data in database, then generate RDF
- **Benefits**: Leverages existing D2R capabilities for streams
- **Use Cases**: When stream persistence is required

#### XML-to-RDF Tools

##### XML2RDF
- **Specialization**: Direct XML file to RDF ontology instance conversion
- **Features**: Handles complex XML structures and namespaces
- **Configuration**: Flexible mapping rules for XML elements

##### TopBraid Composer
- **XML Support**: Comprehensive XML-to-RDF conversion
- **Integration**: Part of broader RDF development platform
- **Flexibility**: Custom transformation rules and mappings

##### LODRefine
- **Base**: Extended version of OpenRefine for Linked Data
- **Features**: Interactive data cleaning and RDF transformation
- **Formats**: XML, spreadsheets, CSV, and various other formats
- **Community**: Active open-source community and extensions

#### Spreadsheet-to-RDF Tools

##### OpenRefine (with RDF Extension)
- **Popularity**: Widely used in Linked Data community
- **Features**: Interactive mapping interface, data cleaning capabilities
- **Flexibility**: Handles complex transformations and data quality issues
- **Learning Curve**: User-friendly GUI with extensive documentation

##### Excel2rdf
- **Type**: Java-based command-line utility
- **Target**: Direct Excel-to-RDF conversion
- **Automation**: Suitable for batch processing and automated workflows
- **Simplicity**: Straightforward conversion without complex mapping

##### RDF123
- **Platform**: Open-source web-based tool
- **Support**: CSV files and Google Spreadsheets
- **Service**: Public web service for transformation tasks
- **Accessibility**: No local installation required

##### XLWrap
- **Specialty**: Excel and OpenDocument spreadsheet transformation
- **Flexibility**: Local files or remote HTTP access
- **Configuration**: XML-based mapping configuration
- **Features**: Advanced spreadsheet structure handling

#### Tool Selection Criteria

**Data Format Compatibility**:
- Match tool capabilities to source data format
- Consider data volume and complexity
- Evaluate preprocessing requirements

**Transformation Complexity**:
- Simple mappings: Basic tools (Excel2rdf, RDF123)
- Complex transformations: Advanced tools (OpenRefine, TopBraid Composer)
- Real-time processing: Streaming tools (morph-streams)

**Technical Environment**:
- GUI vs. command-line preferences
- Integration with existing systems
- Maintenance and support requirements

### Step 3: Execute Data Transformation

**Purpose**: Apply chosen tool to generate RDF according to ontology and naming strategy

#### Mapping Process

##### Ontology-Data Alignment
- **Class Mapping**: Map data entities to ontology classes
- **Property Mapping**: Connect data attributes to ontology properties
- **Instance Generation**: Create unique URIs following naming strategy
- **Value Transformation**: Convert data values to appropriate RDF literals

##### URI Generation Strategy
- **Naming Conformance**: Follow established resource naming strategy
- **Uniqueness**: Ensure unique identifiers for all instances
- **Consistency**: Apply uniform patterns across all data
- **Persistence**: Generate stable, long-term URIs

#### Tool-Specific Implementation

**Note**: Concrete implementation steps vary significantly between tools. Each tool has unique interfaces, configuration methods, and workflow processes.

**Common Workflow Elements**:
1. **Data Import**: Load source data into transformation environment
2. **Schema Analysis**: Review data structure and identify mappings
3. **Mapping Configuration**: Define relationships between data and ontology
4. **Transformation Rules**: Specify conversion logic and URI patterns
5. **Preview and Testing**: Validate mappings with sample data
6. **Batch Processing**: Execute full transformation
7. **Output Generation**: Produce RDF in chosen serialization format

#### Data Quality Considerations

##### Data Cleaning
- **Preprocessing**: Clean inconsistent or malformed data before transformation
- **Validation**: Check data integrity and completeness
- **Standardization**: Normalize formats, units, and representations
- **Filtering**: Remove invalid or unnecessary data elements

##### Transformation Validation
- **Mapping Verification**: Ensure all intended data is transformed
- **URI Consistency**: Validate naming strategy implementation
- **Property Completeness**: Check all required properties are populated
- **Type Accuracy**: Verify correct class instantiation

### Step 4: Evaluate RDF Dataset

**Purpose**: Ensure quality, completeness, and usability of generated RDF data

#### Evaluation Dimensions

##### 1. Syntax Validation
- **RDF Syntax**: Verify valid RDF structure and syntax
- **Serialization**: Ensure proper format compliance
- **Parsing**: Test with multiple RDF parsers
- **Tools**: W3C RDF Validator, parser-specific validators

##### 2. Completeness Evaluation
- **Property Coverage**: Check for missing values in required properties
- **Data Completeness**: Verify all source data is represented
- **Relationship Integrity**: Ensure all connections are preserved
- **Instance Coverage**: Confirm all entities are transformed

##### 3. Licensing Evaluation
**Machine-Processable Licensing**:
- Embedded license metadata in RDF
- Standard license property usage (Dublin Core)
- Programmatically accessible licensing information

**Human-Readable Licensing**:
- Clear license statements in documentation
- Accessible license text and terms
- User-friendly license descriptions

##### 4. Accuracy Evaluation
- **Data Type Compliance**: Verify literals match expected data types
- **Range Validation**: Check property values are within expected ranges
- **Format Consistency**: Ensure consistent representation patterns
- **Semantic Accuracy**: Validate meaning preservation from source data

##### 5. Conciseness Evaluation
**Redundancy Detection**:
- Identify duplicate objects with different URIs
- Check for equivalent instances with same meaning
- Detect unnecessary data repetition

**Duplicate Prevention**:
- Eliminate duplicate entries and redundant triples
- Consolidate equivalent resources
- Optimize data representation efficiency

##### 6. Representational Consistency
- **Ontology Compliance**: Verify use of established ontologies
- **Standard Conformance**: Check adherence to community standards
- **Pattern Consistency**: Ensure uniform modeling approaches
- **Vocabulary Reuse**: Validate appropriate existing vocabulary usage

##### 7. Understandability Evaluation
- **Human-Readable Labels**: Include rdfs:label properties
- **Descriptive Comments**: Add rdfs:comment for complex concepts
- **Documentation**: Provide clear metadata and descriptions
- **Accessibility**: Ensure data can be understood by intended users

##### 8. Versatility Evaluation
- **Multi-language Support**: Include labels and descriptions in multiple languages
- **Cultural Adaptation**: Consider regional and cultural variations
- **Internationalization**: Support Unicode and international standards
- **Accessibility**: Accommodate diverse user communities

##### 9. Usage Evaluation
- **Query Capability**: Test with representative SPARQL queries
- **Information Retrieval**: Verify ability to answer intended questions
- **Application Fitness**: Ensure data meets application requirements
- **Performance**: Evaluate query response times and efficiency

#### Evaluation Tools

##### Syntax and Structure Validation
- **W3C RDF Validator**: Official syntax validation service
- **RDF Parser Tools**: Various language-specific parsers
- **Triple Store Import**: Test loading into RDF databases

##### Quality Assessment Tools
- **Databugger**: SPARQL-based data quality validation
- **Custom Validators**: Domain-specific quality checking tools
- **Automated Testing**: Script-based validation procedures

## Practical Examples

### Energy Consumption Transformation (BECA Project)

#### Implementation Overview
- **Source Format**: Excel spreadsheet with energy consumption data
- **Target Serialization**: Turtle (for human readability)
- **Tool Selection**: OpenRefine with RDF extension
- **Domain**: Social housing energy management

#### Step-by-Step Process

**1. Serialization Selection**:
- **Choice**: Turtle format
- **Rationale**: Small dataset size, human readability priority
- **Benefits**: Easy debugging and validation during development

**2. Tool Selection**:
- **Choice**: OpenRefine with RDF extension
- **Rationale**: User-friendly interface, community support, Excel compatibility
- **Advantages**: Interactive mapping, data cleaning capabilities

**3. Transformation Execution**:

##### Phase A: Data Import
- Import Excel spreadsheet into OpenRefine working environment
- Configure import options (worksheet selection, row exclusions)
- Review data structure and identify transformation targets

##### Phase B: Mapping Configuration
- Use RDF extension to create ontology mappings
- Define URI patterns for each resource type following naming strategy
- Specify property mappings between columns and ontology properties
- Configure data type conversions and value transformations

##### Phase C: Data Manipulation (Optional)
- Add calculated columns based on existing data
- Transform existing cell values using pattern matching
- Clean and standardize data values for consistency
- Handle missing or invalid data entries

##### Phase D: RDF Generation
- Execute transformation using configured mappings
- Select Turtle as output serialization format
- Generate RDF file with all transformed data

##### Phase E: Data Cleaning
- Remove unwanted elements (e.g., table headers converted as data)
- Validate URI generation and property assignments
- Ensure data quality and completeness

**4. Quality Evaluation**:

##### SPARQL Query Testing
**Test Environment**: Virtuoso triple store
**Methodology**: Import generated RDF and execute representative queries

**Query 1: Residences by Building and Occupancy**
```sparql
# Select residences in building "108" with 3 persons
SELECT ?residence WHERE {
  ?residence a :Residence ;
             :inBuilding "108" ;
             :numberOfPersons 3 .
}
```

**Query 2: Consumption Data by Tenancy**
```sparql
# Select cold water consumption for specific tenancy
SELECT ?consumption ?value ?time WHERE {
  ?tenancy :identifier "M3600100011" .
  ?consumption a :ColdWaterConsumption ;
               :forTenancy ?tenancy ;
               :hasValue ?value ;
               :atTime ?time .
}
```

**Query 3: Temporal Consumption Analysis**
```sparql
# Select all consumption types with time periods
SELECT ?consumption ?type ?value ?period WHERE {
  ?tenancy :identifier "M3600100011" .
  ?consumption :forTenancy ?tenancy ;
               a ?type ;
               :hasValue ?value ;
               :duringPeriod ?period .
}
```

##### Validation Results
- **Query Accuracy**: All queries returned expected results matching original Excel data
- **Syntax Validation**: RDF successfully imported into Virtuoso (confirming valid syntax)
- **Data Completeness**: All relevant data from spreadsheet represented in RDF
- **Performance**: Acceptable query response times for dataset size

### Building Information Transformation (IFC/BIM)

#### Implementation Overview
- **Source Format**: IFC (Industry Foundation Classes) files
- **Transformation Approach**: Automated EXPRESS-to-OWL mapping
- **Complexity**: Large-scale data with complex relationships
- **Domain**: Architecture, engineering, construction

#### Transformation Strategy

##### IFC-to-RDF Mapping Process
1. **Schema Mapping**: Convert EXPRESS schema to OWL ontology
2. **Data Import**: Load IFC file data according to chosen OWL profile
3. **Instance Generation**: Create RDF instances from IFC objects
4. **Relationship Mapping**: Transform IFC relationships to RDF properties
5. **Export**: Generate RDF in appropriate serialization format

##### Data Filtering Considerations
**Privacy and Confidentiality**:
- Filter out confidential information before transformation
- Use predefined filters for sensitive data categories
- Edit IFC data in BIM tools to remove restricted content

**Performance Optimization**:
- Subset large IFC datasets based on use case requirements
- Focus on specific building systems or project phases
- Balance completeness with processing efficiency

##### Quality Control Integration
**Pre-transformation Validation**:
- Verify IFC data quality and completeness
- Check constraint compliance with original IFC schema
- Validate no additional knowledge requirements exist

**Post-transformation Evaluation**:
- Standard RDF quality evaluation procedures
- BIM-specific validation for domain accuracy
- Performance testing with expected query loads

## Best Practices and Guidelines

### Tool Selection Strategy

#### Evaluate Requirements First
- **Data Volume**: Small datasets vs. enterprise-scale data
- **Update Frequency**: One-time conversion vs. ongoing transformation
- **Complexity**: Simple mappings vs. complex business logic
- **Integration**: Standalone tools vs. platform integration

#### Consider Total Cost of Ownership
- **Initial Setup**: Tool acquisition and installation costs
- **Learning Curve**: Training and skill development requirements
- **Maintenance**: Ongoing support and update needs
- **Scalability**: Growth accommodation and performance scaling

#### Test with Representative Data
- **Pilot Projects**: Start with small, representative datasets
- **Quality Assessment**: Evaluate output quality and accuracy
- **Performance Testing**: Measure processing speed and resource usage
- **User Experience**: Assess tool usability and workflow efficiency

### Quality Assurance Framework

#### Multi-Stage Validation
1. **Pre-transformation**: Source data quality and consistency
2. **During Transformation**: Mapping accuracy and completeness
3. **Post-transformation**: RDF quality and usability
4. **Deployment**: Production readiness and performance

#### Automated Testing Integration
- **Continuous Validation**: Integrate quality checks into transformation pipelines
- **Regression Testing**: Ensure consistent quality across updates
- **Performance Monitoring**: Track transformation efficiency over time
- **Error Detection**: Automated identification and reporting of issues

#### Documentation and Traceability
- **Transformation Documentation**: Record all mapping decisions and rationale
- **Version Control**: Track changes to mappings and configurations
- **Audit Trails**: Maintain records of data lineage and transformations
- **Quality Metrics**: Establish and monitor quality indicators

### Common Pitfalls and Solutions

#### Pitfall: Inadequate Planning
**Problem**: Starting transformation without proper analysis and tool evaluation
**Solution**: Invest time in requirements analysis and tool comparison before implementation

#### Pitfall: Poor Data Quality
**Problem**: Transforming dirty or inconsistent source data
**Solution**: Implement comprehensive data cleaning and validation procedures

#### Pitfall: Insufficient Testing
**Problem**: Deploying RDF without adequate quality evaluation
**Solution**: Establish comprehensive testing framework with representative queries

#### Pitfall: Scalability Oversight
**Problem**: Choosing tools that don't scale with data growth
**Solution**: Consider future data volumes and performance requirements in tool selection

## Tools and Resources

### Transformation Tools

#### Database Tools
- **morph-RDB**: http://mayor2.dia.fi.upm.es/oeg-upm/index.php/en/technologies/315-morph-rdb
- **D2R Server**: http://d2rq.org/d2r-server
- **TopBraid Composer**: www.topbraidcomposer.com

#### Streaming Data Tools
- **morph-streams**: https://github.com/jpcik/morph-streams

#### XML Processing Tools
- **XML2RDF**: http://rhizomik.net/html/redefer/
- **LODRefine**: http://code.zemanta.com/sparkica/index.html

#### Spreadsheet Tools
- **OpenRefine**: http://openrefine.org/index.html
- **Excel2rdf**: https://github.com/waqarini/Excel2rdf
- **RDF123**: http://rdf123.umbc.edu/
- **XLWrap**: http://xlwrap.sourceforge.net/

### Validation Tools
- **W3C RDF Validator**: http://www.w3.org/RDF/Validator/
- **Databugger**: http://databugger.aksw.org:8080/rdfunit/

### Triple Stores for Testing
- **Virtuoso**: http://virtuoso.openlinksw.com/
- **Apache Jena**: Open-source RDF framework
- **GraphDB**: Commercial RDF database
- **Blazegraph**: Open-source RDF database

### Standards and Documentation
- **RDF 1.1 Primer**: http://www.w3.org/TR/rdf11-primer/
- **W3C RDF Specifications**: Complete RDF standard documentation
- **R2RML**: W3C standard for relational database to RDF mapping
- **JSON-LD Specification**: W3C standard for JSON-based linked data
