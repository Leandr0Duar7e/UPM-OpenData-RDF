# Select and Obtain Data Sources

## Overview

The first two steps of the Linked Data generation process involve identifying appropriate data sources and securing access to them. These foundational tasks ensure that you have the necessary data inputs to begin the transformation process.

## Task 1: Select Data Source

### Inputs
- Organizational requirements
- Use case specifications

### Outputs
- Identified data source(s)

### Description

The first step of the Linked Data generation process is selecting the data source that will be transformed into Linked Data. This selection depends on the specific needs of the organization and the expected value to be obtained.

### Process Steps

1. **Define Requirements for Data Source Selection**
   - Identify the intended use of the generated Linked Data
   - Specify target users (individuals or organizations)
   - Determine domain relevance and scope
   - Consider technical constraints and capabilities

2. **Select Data Sources for Transformation**
   - Evaluate available data sources against requirements
   - Choose one or several data sources for transformation
   - Consider data quality, accessibility, and licensing

### Selection Criteria

When selecting data sources, consider these key requirements:

- **Domain Relevance**: Data should contain information relevant to your domain (e.g., energy-related information)
- **Availability**: Data must be accessible and obtainable
- **Format**: Prefer machine-processable formats (Excel, CSV, XML) - more structured data is better
- **Documentation**: Data model and documentation should be available when possible
- **Scope**: Data can come from single or multiple sources
- **Linkability**: Data should be easily linkable with real-world entities (e.g., locations)
- **Legal Clarity**: Clear licensing and access policies should exist
- **Real-world Relevance**: Data should come from actual scenarios, not synthetic examples

### Alternatives

- **Internal Data Sources**: Most commonly, selected data sources are owned by the organization
- **External Data Sources**: Organizations may extend their data with external sources not owned by them

### Practical Examples

#### Energy Consumption Case
The BECA (Balanced European Conservation Approach) project provides an excellent example:
- **Domain**: European ICT PSP project reducing energy consumption in social housing
- **Coverage**: Multiple energy forms (electricity, gas, heating) plus water usage
- **Geographic Scope**: Multiple pilot sites across Europe (Örebro, Darmstadt, Havirov, Manresa, Torino, Ruse, Belgrade)
- **Format**: Excel spreadsheets with energy consumption data
- **Integration**: Data feeds into eeMeasure tool for consistent energy saving calculations

#### Building Information Case
Building lifecycle data offers rich transformation opportunities:
- **Domain**: Architecture, Engineering, Construction, and Facilities Management (AEC/FM)
- **Methodology**: Building Information Modelling (BIM) approach
- **Standard**: Industry Foundation Classes (IFC) developed by buildingSMART (ISO standard)
- **Lifecycle Coverage**: Design, construction, operation, demolition, and recycling phases
- **Collaboration**: Supports multi-disciplinary data sharing and coordination

---

## Task 2: Obtain Access to Data Source

### Inputs
- Selected data source(s)

### Outputs
- Technical access to data source
- Retrieved data

### Description

Once a data source is selected, you must obtain both technical means to retrieve the data and legal rights to use it. This task focuses on the technical access aspects, while legal rights are addressed in the next phase.

### Access Scenarios

- **Internal Data**: Organization-owned data sources are typically accessible without obstacles
- **Public Domain Data**: Publicly available data can be accessed straightforwardly
- **Restricted Data**: Some data sources require permission and credentials for access

### Process Steps for Restricted Data

1. **Identify Contact Person**
   - Research data ownership and management
   - Find appropriate person or department responsible for data access
   - Gather contact information and preferred communication methods

2. **Request Access to Data Source**
   - Submit formal access request
   - Provide justification for data use
   - Negotiate terms and conditions if necessary

3. **Retrieve Data from Source**
   - Follow provided access procedures
   - Download or connect to data source
   - Verify data integrity and completeness

### Data Access Methods

Choose the appropriate access method based on your technical requirements:

- **File-based Access**: Direct access to files containing the data
- **API Access**: Programming interface access (library API or web service)
- **Database Access**: Direct connection to database systems
- **Stream Access**: Real-time data from streams (sensor networks, social media feeds)

### Technical Considerations

#### For Standard File Formats
- **Excel/CSV Files**: Most common for structured tabular data
- **XML Files**: Structured hierarchical data with schema definitions
- **Database Exports**: SQL dumps or direct database connections
- **Specialized Formats**: Domain-specific formats (e.g., IFC for building data)

#### For API Access
- **RESTful Web Services**: HTTP-based APIs with standard methods
- **SOAP Services**: XML-based protocol for structured information exchange
- **Proprietary APIs**: Vendor-specific interfaces with custom protocols
- **Standardized Interfaces**: Industry-standard APIs (e.g., ISO 10303-22 for CAD data)

### Practical Examples

#### Energy Consumption Access
For the BECA project example:
1. **Contact Identification**: Partners from READY4SmartCities who participate in BECA identified data managers
2. **Access Request**: Formal request sent to identified data controllers
3. **Data Retrieval**: Data provided as Excel spreadsheet for local analysis

#### Building Information Access
For BIM/IFC data:
- **Standard Access**: IFC files stored according to ISO 10303-21 (STEP physical file format)
- **Tool Support**: Compatible with all major AEC-CAD tools
- **Lifecycle Management**: Different data managers for different building phases:
  - Design phase: Project manager typically responsible
  - Operation phase: Facilities manager or building owner
- **Data Volume**: Can reach hundreds of megabytes even for small buildings
- **Format Versatility**: Multiple access methods available (files, proprietary APIs, standardized interfaces)

### Best Practices

- **Document Access Procedures**: Keep detailed records of how data was obtained
- **Verify Data Integrity**: Ensure retrieved data matches expected format and content
- **Establish Update Mechanisms**: For dynamic data, set up procedures for regular updates
- **Maintain Relationships**: Build good relationships with data providers for ongoing access
- **Plan for Scale**: Consider data volume and bandwidth requirements for large datasets
