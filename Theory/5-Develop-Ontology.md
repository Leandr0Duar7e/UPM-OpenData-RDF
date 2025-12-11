# Develop Ontology

## Overview

Ontologies represent formal representations of knowledge about a specific domain and are the cornerstone of the Linked Data initiative. They serve as formal models for representing data on the Web by describing concepts in a domain and the relationships between them. This task involves creating or extending ontologies that will structure and define the semantic framework for your Linked Data.

## Inputs
- Data schema
- Analyzed data structure
- Resource naming strategy

## Outputs
- Complete ontology
- Formal knowledge model
- Class and property definitions

## Fundamental Concepts

### Ontology Components

Ontologies contain different components that define their complexity and scope:

- **Classes**: Define types of entities in the domain
- **Properties**: Define relationships between classes and data values
- **Instances**: Specific examples of classes
- **Axioms**: Logical constraints and rules

### Ontology Types

#### Lightweight Ontologies
- **Components**: Classes, properties, and instances only
- **Complexity**: Simpler structure and implementation
- **Use Case**: Most Linked Data applications, especially data-driven development
- **Advantages**: Easier to develop, maintain, and understand

#### Heavyweight Ontologies  
- **Components**: All components including complex axioms and rules
- **Complexity**: Rich logical constraints and inference capabilities
- **Use Case**: Applications requiring complex reasoning and validation
- **Advantages**: Higher expressivity and logical consistency

### Implementation Standards

**Recommended Languages**:
- **OWL (Web Ontology Language)**: W3C standard, most widely used
- **RDF-S (RDF Schema)**: Simpler alternative for basic ontologies
- **Standard Compliance**: Ensures interoperability and tool support

## Development Methodologies

### 1. Data-Driven Development
**Approach**: Start from available data and extract ontological concepts
**Best For**: Existing data sources that need semantic representation
**Advantages**: Grounded in real-world data, practical applicability

### 2. Competency Question-Driven Development
**Approach**: Start from questions the ontology should be able to answer
**Best For**: Requirements-driven development with clear use cases
**Example Methodology**: NeOn methodology for systematic development

## 8-Step Development Process

### Step 1: Define Requirements

**Purpose**: Establish clear objectives and constraints for ontology development

**Requirements Categories**:
- **Usage Purpose**: Intended applications and use cases
- **Domain Coverage**: Scope and boundaries of knowledge representation  
- **Technical Specifications**: Implementation language, complexity level
- **Integration Needs**: Compatibility with existing systems and ontologies

**Documentation**: Create formal requirement specification document

### Step 2: Extract Terms

**Process Overview**:
1. **Identify Core Concepts**: Extract basic concepts from data source and schema
2. **Find Relationships**: Identify connections between concepts
3. **Include Synonyms**: Use online services (synonyms.com, thesaurus.com) for term expansion
4. **Categorize Terms**: Organize into classes, properties, and instances

**Term Categories**:

#### Classes (Concept Types)
- **Definition**: Categories of entities in the domain
- **Examples**: Dwelling, Building, Energy, Measurement
- **Synonyms**: Include alternative terms (residence, habitat for dwelling)

#### Properties (Relationships)
- **Object Properties**: Relate classes to other classes
- **Data Type Properties**: Relate classes to literal values (strings, numbers, dates)
- **Examples**: hasIdentifier, locatedIn, measuredAt

#### Instances (Specific Examples)
- **Definition**: Concrete examples of classes
- **Examples**: Kilowatt-hour, Cubic meter, Specific buildings or locations

### Step 3: Search Existing Ontologies

**Principle**: Ontology reuse is a fundamental best practice

**Search Strategy**:
1. **Keyword-based Search**: Use extracted terms including synonyms
2. **Multiple Tools**: Employ various search engines and catalogs
3. **Filter Results**: Handle large result sets (hundreds of ontologies for common terms)
4. **Quality Assessment**: Evaluate ontology maturity and adoption

**Search Tools**:
- **Swoogle**: General ontology search engine
- **Watson**: Semantic web search for ontologies
- **LOV (Linked Open Vocabularies)**: Curated vocabulary catalog
- **Google**: General web search with specific filters
- **Domain Catalogs**: Specialized collections (e.g., Smart Cities catalog)

**Search Optimization Tips**:
- Add "ontology" to search terms for better context
- Use filetype:owl to find OWL files specifically
- Example: "residence ontology" or "residence filetype:owl"

### Step 4: Select Existing Ontologies

**Selection Criteria**:

#### Semantic Relevance
- **Contextual Match**: Class/property semantics align with intended use
- **Domain Appropriateness**: Ontology fits the application domain

#### Completeness
- **Property Coverage**: Classes have relevant properties for the terms
- **Relationship Richness**: Adequate connections between concepts

#### Quality and Adoption
- **Wide Acceptance**: Ontology is widely used and recognized
- **Maintenance**: Active development and community support
- **Documentation**: Clear specifications and usage examples

**Well-known Ontologies for Common Concepts**:
- **Schema.org**: General web semantics, widely adopted
- **Dublin Core**: Metadata properties (identifier, title, etc.)
- **DOLCE/DUL**: Upper-level ontology for time and events
- **SSN (Semantic Sensor Network)**: Observations and measurements
- **RDFS**: Basic schema properties (comment, label, etc.)

### Step 5: Draft Initial Conceptualization

**Integration Process**:

#### Class Reuse Decisions
- **Direct Reuse**: Use existing classes that match extracted terms
- **Superclass Relationships**: Leverage existing classes as parent classes
- **Namespace Integration**: Maintain original ontology namespaces

#### Property Reuse Decisions
- **Relationship Mapping**: Match extracted terms to existing properties
- **Domain/Range Consistency**: Ensure property usage aligns with definitions
- **Cross-Ontology Properties**: Combine properties from multiple sources

#### Initial Model Creation
- **Conceptual Diagram**: Visual representation of integrated concepts
- **Namespace Management**: Track reused ontology prefixes and URIs
- **Completeness Assessment**: Identify gaps requiring new definitions

### Step 6: Complete Conceptualization

**Gap Analysis and Extension**:

#### New Classes
- **Creation Criteria**: Only when existing ontologies lack needed concepts
- **Term Alignment**: Must relate to originally extracted terms
- **Hierarchy Integration**: Fit within existing class structures

#### New Properties
- **Domain Classes**: Can connect to new or reused classes
- **Range Specification**: Define appropriate value types or classes
- **Relationship Semantics**: Clear meaning and usage context

**Design Principles**:
- **Minimalism**: Create only what's necessary
- **Consistency**: Follow patterns from reused ontologies
- **Extensibility**: Design for future expansion needs

### Step 7: Implement Ontology

**Technical Implementation**:

#### URI Conformance
- **Naming Strategy**: Follow established resource naming conventions
- **Domain Consistency**: Use appropriate base URIs
- **Pattern Application**: Apply class and property URI patterns

#### Tool Selection
**Development Tools**:
- **Protégé**: Most popular, rich feature set, plugin ecosystem
- **WebProtégé**: Browser-based collaborative development
- **NeOn Toolkit**: Methodology-oriented development environment
- **TopBraid Composer**: Commercial tool with advanced features

#### Implementation Standards
- **OWL Profiles**: Choose appropriate OWL variant (DL, EL, QL, RL)
- **Syntax Format**: Select serialization (RDF/XML, Turtle, Manchester)
- **Validation**: Ensure syntactic correctness throughout development

### Step 8: Evaluate Ontology

**Six Evaluation Dimensions**:

#### 1. Human Understanding
- **Documentation Quality**: Comprehensive annotations and examples
- **Code Clarity**: Readable class and property names
- **Conceptual Coherence**: Logical organization and structure

#### 2. Logical Consistency
- **Inconsistency Detection**: No logical contradictions
- **Satisfiability**: All classes can have instances
- **Reasoner Validation**: Use automated consistency checking

#### 3. Modeling Issues
- **Language Primitives**: Correct use of OWL constructs
- **Design Patterns**: Follow established ontological patterns
- **Best Practices**: Adherence to community guidelines

#### 4. Language Specification Compliance
- **Syntax Correctness**: Valid OWL/RDF syntax
- **Profile Conformance**: Meets chosen OWL profile requirements
- **Standard Compatibility**: Follows W3C specifications

#### 5. Real World Representation
- **Domain Accuracy**: Correctly models intended domain
- **Expert Validation**: Review by domain experts
- **Use Case Coverage**: Supports intended applications

#### 6. Semantic Applications Fitness
- **Tool Compatibility**: Works with target software systems
- **Performance**: Acceptable reasoning and query performance
- **Integration**: Compatible with existing system architectures

**Evaluation Tools**:
- **OWL Validator**: W3C syntax validation service
- **OOPS! Pitfall Scanner**: Automated quality assessment
- **Reasoners**: HermiT, Fact++, Pellet for consistency checking
- **Protégé Plugins**: Integrated evaluation within development environment

## Practical Examples

### Energy Consumption Ontology (BECA Project)

**Development Context**:
- **Data Source**: Excel spreadsheet with energy consumption data
- **Domain**: Social housing energy management
- **Approach**: Data-driven methodology
- **Target Language**: OWL 2 DL

#### Step-by-Step Implementation

**1. Requirements Definition**:
- Adopt existing concepts and design patterns where possible
- Implement in OWL 2 DL for standardization
- Support energy consumption data representation

**2. Term Extraction**:

| Category | Terms and Synonyms |
|----------|-------------------|
| **Classes** | Dwelling (residence, habitat), city, building, evaluation group, tenancy (occupancy), pilot, heating degree days, hot water, cold water, heating (heat), energy, consumption (utilization), unit of measurement, month (time) |
| **Properties** | Service setup, evaluation identifier, building identifier, building name (name), pilot name, service setup name, tenant identifier, comment, dwelling identifier, change of tenancy, vacancy of dwelling, number of persons living, size of dwelling, night setback, ventilation system, participated in focus group, value |
| **Instances** | Kilowatt hour (kWh), cubic meter (cbm), square meter (sqm), thermal unit |

**3. Ontology Search and Selection**:

Selected ontologies with rationale:
- **Schema.org**: Residence and City classes (widely accepted vocabulary)
- **gbBuilding Information Ontology (BIO)**: Additional building properties
- **Energy Resource Ontology (ERO)**: UsefulEnergy class and Heat instance
- **SSN (Semantic Sensor Network)**: Observation, SensorOutput, ObservationValue
- **DOLCE/DUL**: TimeInterval class for temporal relationships
- **Dublin Core**: identifier and title properties
- **Ontology of units of Measure (OM)**: Complete unit class and instance coverage

**4. Namespace Management**:

| Ontology | Prefix | URI |
|----------|--------|-----|
| gbBuilding Information | bio | https://www.auto.tuwien.ac.at/downloads/thinkhome/ontology/gbBuildingOntology.owl# |
| DOLCE+DnS Ultralite | dul | http://www.loa-cnr.it/ontologies/DUL.owl# |
| Dublin Core | dc | http://purl.org/dc/terms/ |
| Energy Resource Ontology | ero | https://www.auto.tuwien.ac.at/downloads/thinkhome/ontology/EnergyResourceOntology.owl# |
| Ontology of units of Measure | om | http://www.wurvoc.org/vocabularies/om-1.8/ |
| Schema.org | schema | http://schema.org/ |
| Semantic Sensor Network | ssn | http://purl.oclc.org/NET/ssnx/ssn# |

**5. Implementation Results**:
- **Final Ontology**: Available at http://smartcity.linkeddata.es/BECA/ontology/EnergyConsumption.owl
- **Implementation Tool**: Protégé
- **Validation**: OOPS! pitfall scanner with iterative error correction
- **Quality**: Heavyweight ontology (axioms added for quality improvement)

### Building Information Ontology (IFC/BIM)

**Development Context**:
- **Existing Standard**: IFC (Industry Foundation Classes) with EXPRESS modeling
- **Challenge**: Convert EXPRESS schema to OWL representation
- **Approach**: Automated mapping with configuration options

**Available Mapping Tools**:

#### NIST OntoSTEP Converter
- **Integration**: Protégé plugin
- **Output**: OWL 1 DL representation
- **Use Case**: Desktop ontology development

#### IFC2X3 (University of Ghent)  
- **Output**: OWL 1 Full representation
- **Features**: Complete IFC coverage with full expressivity

#### Linked Building Data Initiative
**Multiple OWL Configurations**:
- OWL 1 DL (two configurations)
- OWL 2 EL (two configurations)  
- OWL 2 Full (one configuration)
- OWL 2 RL (two configurations)

**Mapping Considerations**:
- **Knowledge Loss**: Some EXPRESS concepts lack OWL equivalents
- **Automatic Process**: No additional domain knowledge encoding
- **Customization Needs**: May require use-case specific simplification
- **Element Types**: 
  - Uniquely identifiable elements: Use global unique identifiers
  - Resource elements: Anonymous individuals (blank nodes)

## Best Practices and Tips

### Development Guidelines

#### Terminology and Naming
- **Expand Abbreviations**: Use full terms rather than acronyms
- **Follow Conventions**: Adhere to lexical conventions (Semantic Interoperability Community guidelines)
- **Avoid Redundancy**: Don't create classes/properties just to use specific terms for existing concepts
- **Standard Languages**: Implement in RDF-S or OWL for maximum compatibility

#### Search and Reuse Strategy
- **Exhaustive Search**: Multiple tools and synonym variations
- **Quality over Quantity**: Focus on well-established, widely-used ontologies
- **Context-Aware Selection**: Choose ontologies that fit domain and use case
- **Integration Planning**: Consider namespace management and compatibility

#### Implementation Quality
- **Iterative Evaluation**: Regular quality checks throughout development
- **Expert Validation**: Domain expert review for accuracy
- **Tool-Assisted Quality**: Use automated scanners and reasoners
- **Documentation**: Comprehensive annotations and usage examples

### Common Pitfalls and Solutions

#### Pitfall: Over-Engineering
**Problem**: Creating overly complex ontologies for simple use cases
**Solution**: Start with lightweight ontologies; add complexity only when needed

#### Pitfall: Insufficient Reuse
**Problem**: Recreating concepts that exist in established ontologies
**Solution**: Comprehensive ontology search and systematic reuse evaluation

#### Pitfall: Inconsistent Modeling
**Problem**: Mixed modeling approaches and inconsistent patterns
**Solution**: Follow established design patterns and maintain consistency

#### Pitfall: Poor Quality Control
**Problem**: Logical inconsistencies and modeling errors
**Solution**: Use multiple evaluation tools and iterative refinement

## Tools and Resources

### Ontology Search Tools
- **Swoogle**: http://swoogle.umbc.edu/
- **Watson**: http://watson.kmi.open.ac.uk/
- **LOV**: http://lov.okfn.org/dataset/lov/
- **Smart Cities Catalog**: http://smartcity.linkeddata.es/

### Development Tools  
- **Protégé**: Industry standard with rich plugin ecosystem
- **WebProtégé**: Collaborative web-based development
- **NeOn Toolkit**: Methodology-oriented development environment
- **TopBraid Composer**: Commercial solution with advanced features

### Validation and Evaluation Tools
- **OWL Validator**: http://mowl-power.cs.man.ac.uk:8080/validator/
- **OOPS! Pitfall Scanner**: http://www.oeg-upm.net/oops
- **Reasoners**: HermiT, Fact++, Pellet, Hermit
- **Protégé Integration**: Built-in reasoner plugins and validation

### Online Resources
- **Synonym Services**: synonyms.com, thesaurus.com
- **W3C Standards**: OWL and RDF specifications
- **Community Guidelines**: Semantic Interoperability Community resources
- **Domain Vocabularies**: Industry-specific ontology collections
