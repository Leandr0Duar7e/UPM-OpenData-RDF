# Analyze License and Data

## Overview

Before proceeding with data transformation, it is crucial to understand both the legal framework governing data usage and the structure of the data itself. This phase consists of two critical tasks: analyzing licensing conditions and examining the data source structure.

---

## Task 1: Analyze Licensing of the Data Source

### Inputs
- Data source
- Retrieved data

### Outputs
- License information
- Legal usage rights and restrictions

### Description

Licenses declared for a dataset specify the legal terms under which data can be used and exploited. In the absence of specific contracts, generic licenses specify which actions can be executed on a dataset, provided certain conditions are satisfied.

Understanding licensing is essential to prevent legal conflicts and ensure compliant data usage. This can be challenging because:
- The same dataset may appear in different locations with different licenses
- There are no legal prescriptions for how licenses should be declared
- No common standard practices exist for license declaration

### Process Steps

#### 1. Identify the Authoritative Dataset Publisher
Prior knowledge of the rightsholder is essential to assess whether data has been published by (or on behalf of) the rightsholder or an authorized distributor.

#### 2. Find the Applicable License
Once the authoritative publisher is identified, check these locations for license information:

**a. Web Page Hosting the Data**
- Look for licensing text in HTML footers
- Check for well-known icons (e.g., Creative Commons)
- Review separate license pages linked from the main page

**b. Dataset Metadata**
- For RDF data: Check VoID/DCAT descriptions
- Look for structured licensing information
- Common elements: DublinCore license, DublinCore rights, XHTML license

**c. Inspect the Dataset Directly**
- Comments in XML format
- Explicit DublinCore labels within data
- Simple textual notes embedded in files

**d. Contact the Dataset Publisher**
- When above steps are insufficient
- When doubts exist about applicable license
- For clarification of complex licensing terms

#### 3. Read and Evaluate License Terms
- Review license text (usually concise and understandable)
- Verify intended uses match waived rights in the license
- Ensure required conditions can be satisfied
- Confirm the resource can be used for your purposes

### Defining Licenses for Publication

When publishing data without existing licenses, follow these steps:

#### 1. Determine Publishing Rights
**If you are the data creator:**
- You are the rightsholder if data is not based on other parties' data
- You can freely publish the data

**If you are not the data creator:**
- Permission from other parties is needed
- Check if original data permits derivative works
- Obtain specific permissions when required

#### 2. Choose the Right License
**As rightsholder:**
- Any license can be chosen

**Using data from other parties:**
- Respect restrictions from original licenses
- Choose compatible licensing terms
- Select well-known licenses for easier consumer understanding

#### 3. Choose License Publication Method
**For Human Visibility:**
- Use easily recognizable placeholders
- Place in prominent, accessible locations

**For Machine Visibility:**
- Use DublinCore license elements (recommended)
- Implement RDFa in HTML when applicable
- Reference license within dataset if necessary

### Alternatives

- **Automated License Discovery**: Generally not reliable for this sensitive task
- **Access Control Systems**: May use pay-per-access models with specific policies (uncommon)
- **Permission-based Access**: Obtain rights by requesting permission or paying fees

### Best Practices

- **Consistency**: Perform license analysis on all available copies and formats
- **Single Source**: Have the same person/group conduct all analyses
- **Compatibility**: Ensure license compatibility when integrating multiple datasets
- **Documentation**: Keep detailed records of licensing decisions and sources

### Practical Examples

#### Energy Consumption Case (BECA Project)
1. **Rightsholder Identification**: ATC Torino (Agenzia Territoriale per la Cassa della Provincia di Torino)
2. **License Status**: No associated license; dataset not published
3. **Data Classification**: Not public data
4. **Result**: All rights reserved for generated RDF data; Dublin Core license element used for specification

#### Building Information Case (AEC Industry)
- **Complex Ownership**: Multiple authorship and creative architectural designs create substantial legal questions
- **Key Stakeholders**: Building owner and building users must grant permission
- **Industry Challenge**: Low readiness to publish due to:
  - Uncertainty about consequences of public availability
  - Lack of clear business case or return on investment
- **Example**: HESMOS project showcases not publicly available due to legal restrictions

---

## Task 2: Analyze Data Source

### Inputs
- Access to data source
- Retrieved data

### Outputs
- Data characteristics and content analysis
- Data schema (extracted or existing)

### Description

Once licensing permits data use, analyze the data source to gain insight into its content, structure, and organization. This analysis provides the foundation for ontology development and data transformation.

### Process Steps

#### 1. Analyze the Data Content
Examine data characteristics including:
- **Data Types**: Identify present data categories
- **Value Ranges**: Understand numeric and categorical ranges
- **Data Quality**: Assess completeness and accuracy
- **Temporal Aspects**: Identify time-based patterns or periods
- **Relationships**: Understand connections between data elements

#### 2. Obtain or Extract Data Schema
**If Schema Exists:**
- Review existing schema documentation
- Verify schema completeness against actual data
- Complete schema if necessary using data analysis results

**If Schema Does Not Exist:**
- Extract schema directly from data structure
- Document domain concepts and relationships
- Use standard modeling languages (e.g., UML) for representation

### Data Types and Handling

#### Structured Data
- **Formats**: CSV, XML, SQL databases, JSON
- **Advantages**: Easier to analyze and reuse
- **Resource Requirements**: Less demanding processing
- **Common Sources**: Spreadsheets, databases, APIs

#### Unstructured Data
- **Formats**: Plain text, PDFs, natural language documents
- **Challenges**: Requires deeper analysis
- **Processing**: More difficult to reuse and transform
- **Considerations**: May need text processing or extraction tools

### Best Practices

- **Schema Documentation**: Provide clear, unambiguous schema information
- **Standard Languages**: Use recognized modeling languages (UML) for schema representation
- **Data Quality**: Document data quality issues and limitations
- **Completeness**: Identify and handle missing or incomplete data

### Practical Examples

#### Energy Consumption Data Analysis (BECA Project)
**Data Structure:**
- **Format**: Excel files with multiple sheets
- **Content**: Energy consumption data (heating, cold water, hot water)
- **Geographic Scope**: Social housing pilot sites in Torino
- **Identifiers**: Sites, buildings, dwellings, tenancies, evaluation groups (integer values)
- **Descriptive Data**: Pilot names, building names, setup types (string values)
- **Temporal Coverage**: January 2011 to October 2013
- **Measurements**: Decimal consumption values per tenancy per month

**Dwelling Characteristics:**
- Tenancy change indicators (0/1 values)
- Change date ranges (from/to dates)
- Number of persons per dwelling
- Dwelling size (square meters)
- Technical details (mechanical ventilation systems)

**Data Quality Issues:**
- Empty sheets and columns present
- Incomplete entries in some tables
- Combined heating and hot water measurements in some cases

**Schema Extraction:**
- Based on Excel spreadsheet table structure
- Relationships between dwelling, tenancy, and consumption tables
- Temporal relationships for time-series consumption data

#### Building Information Data Analysis (IFC/BIM)
**Data Structure:**
- **Format**: IFC (Industry Foundation Classes) according to EXPRESS (ISO 10303-11)
- **Modeling Language**: EXPRESS - extended entity relationship model
- **Features**: Inheritance, constraints, rules, typing, cardinality, functions
- **Standard Basis**: Common understanding within AEC industry

**Key Characteristics:**
- **Well-defined Structure**: Publicly available data structure definitions
- **Extensibility**: Supports proprietary content additions
- **Data Filtering**: Main task is limiting data scope and focus
- **Privacy Handling**: May require data anonymization
- **Domain Coverage**: Architecture, engineering, construction, facilities management

**Analysis Considerations:**
- **Proprietary Data**: May not be suitable for Linked Data publication
- **Tool-specific Settings**: Often define application-specific configurations
- **Use Case Focus**: Filter data based on specific information needs
- **Privacy Requirements**: Remove or anonymize sensitive information

### Tools and Techniques

#### For Structured Data Analysis
- **Spreadsheet Software**: Excel, LibreOffice Calc for tabular data
- **Database Tools**: SQL clients for database analysis
- **Statistical Software**: R, Python pandas for data profiling
- **Data Profiling Tools**: Specialized tools for data quality assessment

#### For Schema Extraction
- **Modeling Tools**: UML editors, ER diagram tools
- **Database Reverse Engineering**: Tools to extract schemas from databases
- **Documentation Generators**: Tools to create schema documentation
- **Standard Converters**: Tools to convert between schema formats

### Common Challenges and Solutions

#### Data Quality Issues
- **Missing Values**: Document and decide on handling strategy
- **Inconsistent Formats**: Standardize data representation
- **Duplicate Records**: Identify and resolve duplication strategy
- **Outliers**: Assess whether outliers are errors or valid extreme values

#### Schema Complexity
- **Large Schemas**: Break down into manageable components
- **Multiple Relationships**: Map relationship types and cardinalities
- **Temporal Aspects**: Document time-dependent schema elements
- **Domain Specificity**: Engage domain experts for validation
