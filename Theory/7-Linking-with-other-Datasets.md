# Linking with other Datasets

## Overview

The key concept in Linked Data are links to data from other datasets. These links ensure that datasets are not just isolated data islands but form an interconnected web of information. Data linking denotes connecting different data from various heterogeneous data sources, creating a network that enables discovery, integration, and enhanced querying capabilities across multiple datasets.

## Inputs
- Developed ontology
- Generated RDF data

## Outputs
- Linked dataset with external connections
- Link specifications and mappings
- Interlinked data network

## Fundamental Concepts

### The Importance of Linking

**Linked Data Principles**: Tim Berners-Lee's fourth principle states "Include links to other URIs so that they can discover more things."

**Benefits of Data Linking**:
- **Discovery**: Enable finding related information across datasets
- **Integration**: Combine data from multiple sources for richer insights  
- **Validation**: Cross-reference information for accuracy verification
- **Network Effects**: Increase value as more datasets become connected
- **Interoperability**: Enable seamless data exchange and reuse

### Linking Relationships

**owl:sameAs**: Indicates two URIs refer to the same real-world entity
**Related Properties**: Various semantic relationships (broader, narrower, related, etc.)
**Domain-Specific Links**: Custom properties for specific relationship types

## Three Categories of Data Linking

### 1. Value Matching

**Definition**: Determining if two values of properties expressed in different ways are equivalent

#### Equivalence Scenarios
- **Format Differences**: Different date formats, number representations, etc.
- **Synonym Usage**: Alternative terms with same meaning
- **Language Variations**: Multi-language labels and descriptions
- **Encoding Differences**: Character encoding, case sensitivity, whitespace

#### Value Matching Techniques

##### String Similarity Measures
- **Edit Distance**: Levenshtein, Damerau-Levenshtein algorithms
- **Phonetic Matching**: Soundex, Metaphone for pronunciation similarity
- **N-gram Comparison**: Character or word-based substring analysis
- **Fuzzy Matching**: Probabilistic string matching algorithms

##### External Knowledge Resources
- **WordNet**: Lexical database for semantic relationships
- **OpenCyc**: High-level vocabulary and common-sense knowledge
- **Domain Ontologies**: Specialized vocabulary for specific fields
- **Gazetteers**: Geographic name databases and location services

##### Search-Based Similarity
- **Web Search**: Using search engines to validate entity relationships
- **Keyword Analysis**: Co-occurrence patterns in external corpora
- **Context Analysis**: Surrounding text and metadata examination

#### Important Limitations
**Value Match ≠ Instance Equivalence**: Matching property values doesn't automatically mean instances are equivalent, but provides starting point for equivalence analysis.

### 2. Individual Matching

**Definition**: Determining whether two instances from different datasets can be linked based on their complete descriptions

#### Matching Approaches

##### Aggregation-Based Matching
- **Multi-property Analysis**: Combine evidence from multiple property matches
- **Weighted Scoring**: Assign importance weights to different properties
- **Threshold-Based Decisions**: Define confidence levels for link creation
- **Machine Learning**: Train classifiers on known positive/negative examples

##### Transitivity-Based Matching
- **owl:sameAs Chains**: Follow existing equivalence relationships
- **Transitive Closure**: Compute complete equivalence networks
- **Consistency Checking**: Validate logical consistency of link networks

##### Ontology Mapping-Based Matching
- **Schema Alignment**: Map between different ontological structures
- **Class Equivalence**: Identify equivalent concepts across ontologies
- **Property Alignment**: Match similar relationships with different names
- **Structural Matching**: Compare graph patterns and constraints

#### Description-Based Analysis
**Comprehensive Profiling**: Examine all available properties and relationships
**Contextual Information**: Consider broader graph neighborhood
**Temporal Aspects**: Account for time-varying properties and relationships

### 3. Dataset Matching

**Definition**: Utilizing sets of potential individual mappings between entire datasets to solve problems with insufficient individual descriptions

#### Holistic Analysis Approaches
- **Network-Level Analysis**: Examine entire dataset structures and patterns
- **Repository Networks**: Leverage publicly available linked data cloud
- **Statistical Correlation**: Identify systematic relationship patterns
- **Community Detection**: Find clusters of related entities across datasets

#### Addressing Information Gaps
**Incomplete Descriptions**: Compensate for missing individual information
**Collective Intelligence**: Use dataset-wide evidence for individual decisions  
**Cross-Validation**: Verify linkage decisions using multiple datasets
**Probabilistic Models**: Handle uncertainty in matching decisions

## 4-Step Data Linking Process

### Step 1: Identify Linkable Classes

**Purpose**: Determine which types of entities in your dataset can potentially be linked to external datasets

#### Class Selection Criteria
- **External Relevance**: Classes likely to have counterparts in other datasets
- **Rich Descriptions**: Entities with sufficient identifying information
- **Standard Types**: Common entity types (Person, Place, Organization, etc.)
- **Domain Importance**: Critical entities for your application domain

#### Common Linkable Entity Types
- **Geographic Entities**: Cities, countries, landmarks, addresses
- **People**: Authors, historical figures, public personalities
- **Organizations**: Companies, institutions, government agencies  
- **Concepts**: Abstract concepts, categories, classifications
- **Products**: Commercial products, publications, artworks
- **Events**: Historical events, conferences, incidents

#### Analysis Methodology
1. **Ontology Review**: Examine classes in your developed ontology
2. **Instance Analysis**: Assess available identifying information for instances
3. **External Survey**: Research potential target datasets for each class
4. **Linking Potential**: Evaluate likelihood of successful matches

### Step 2: Identify Target Datasets

**Purpose**: Find external datasets containing instances of the previously identified classes

#### Dataset Discovery Strategies

##### Major Linked Data Hubs
- **DBpedia**: Structured content from Wikipedia
- **Wikidata**: Collaborative knowledge base
- **GeoNames**: Geographical database
- **VIAF**: Virtual International Authority File (persons/organizations)
- **LinkedGeoData**: Geographic data from OpenStreetMap

##### Domain-Specific Resources
- **Scientific Data**: Research datasets, publication databases
- **Government Data**: Open government data portals
- **Industry Data**: Sector-specific databases and registries
- **Cultural Heritage**: Museum, library, and archive datasets

##### Dataset Evaluation Criteria
- **Coverage**: Scope and completeness for your entity types
- **Quality**: Data accuracy and maintenance standards  
- **Accessibility**: Availability and usage terms
- **Update Frequency**: Currency and maintenance activity
- **Link Density**: Existing connections to other datasets

#### Research Methodology
1. **LOD Cloud Survey**: Examine Linked Open Data cloud diagrams
2. **Registry Search**: Use dataset registries and catalogs
3. **Domain Research**: Identify authoritative sources in your field
4. **Community Consultation**: Engage with domain expert communities

### Step 3: Select Linking Tools

**Purpose**: Choose appropriate software tools based on dataset characteristics and matching requirements

#### Manual vs. Automated Approaches

##### Manual Linking
**Appropriate When**:
- Small number of instances to link
- High precision requirements
- Complex domain-specific rules
- One-time linking projects

**Process**:
- Expert review of candidate matches
- Manual validation of automated suggestions
- Domain knowledge application for edge cases

##### Automated Tool Selection
**Considerations**:
- **Dataset Size**: Volume of instances to process
- **Matching Complexity**: Simple similarity vs. complex rules
- **Performance Requirements**: Processing speed and scalability
- **Integration Needs**: Workflow and system compatibility

#### Tool Categories and Capabilities

##### Comprehensive Matching Systems
**LN2R (Logical and Numerical Reasoning)**
- **Architecture**: Dual engine approach (logical + numerical)
- **Capabilities**: All three matching categories supported
- **Methodology**: Ontology axiom exploitation with similarity analysis
- **Strengths**: Principled logical foundation with practical similarity measures

##### Similarity-Based Tools
**Silk Framework**
- **Approach**: Configurable similarity measures and aggregation
- **Input Method**: SPARQL endpoint integration
- **Capabilities**: Value matching and individual matching
- **Features**: Link maintenance and validation capabilities
- **Configuration**: User-defined similarity metrics and thresholds

##### Optimization-Focused Systems  
**LIMES (Link Discovery Framework)**
- **Innovation**: Optimization techniques to minimize comparisons
- **Interfaces**: Web service and graphical user interface
- **Configuration**: XML-based rule specification
- **Limitation**: Focuses on value matching only
- **Performance**: Optimized for large-scale dataset processing

##### Specialized Approaches
**LD mapper**
- **Technology**: Prolog-based implementation
- **Algorithm**: Similarity aggregation with user configuration
- **Support**: Value matching and individual matching
- **Strengths**: Logic programming flexibility for complex rules

**RDF-AI (RDF Automatic Interlinking)**
- **Output**: owl:sameAs relationship generation
- **Configuration**: XML specification for matching parameters
- **Scope**: All three matching categories supported
- **Parameters**: Dataset structure and technique specification

**Serimi (Semantic Relation Discovery)**
- **Methodology**: Two-phase approach
- **Phase 1**: Information retrieval for candidate selection
- **Phase 2**: Algorithmic analysis of candidate descriptions
- **Capabilities**: Value matching and dataset matching

### Step 4: Execute Linking Process

**Purpose**: Apply selected tools to generate links between your dataset and external sources

#### Tool Configuration

##### Parameter Specification
- **Similarity Thresholds**: Minimum confidence levels for link creation
- **Matching Rules**: Specific algorithms and weightings for different properties
- **Dataset Endpoints**: SPARQL endpoints or data access configuration
- **Output Formats**: Link serialization and integration specifications

##### Quality Control Settings
- **Validation Rules**: Constraints to ensure link quality
- **Review Processes**: Human validation for ambiguous cases
- **Conflict Resolution**: Handling contradictory evidence
- **Performance Monitoring**: Tracking success rates and errors

#### Execution Workflow

1. **Preprocessing**: Prepare datasets and configure access methods
2. **Candidate Generation**: Identify potential matching instances
3. **Similarity Computation**: Apply configured matching algorithms
4. **Link Validation**: Apply quality filters and validation rules
5. **Output Generation**: Create and serialize discovered links
6. **Integration**: Incorporate links into your dataset
7. **Documentation**: Record linking decisions and metadata

## Practical Examples

### Energy Consumption Linking (BECA Project)

#### Linking Context
- **Source Dataset**: BECA energy consumption data
- **Target Dataset**: DBpedia (Wikipedia structured content)
- **Linkable Class**: City (schema.org vocabulary)
- **Specific Instance**: Torino (all pilot sites located in this city)

#### Step-by-Step Implementation

**Step 1: Class Identification**
- **Analysis**: Reviewed BECA ontology for externally linkable concepts
- **Result**: Identified City class as primary linking candidate
- **Rationale**: Geographic entities commonly available in external datasets

**Step 2: Target Dataset Selection**
- **Choice**: DBpedia selected as target dataset
- **Justification**: Comprehensive geographic coverage, high data quality
- **Content**: Structured Wikipedia content including detailed city information

**Step 3: Approach Selection**  
- **Method**: Manual linking chosen
- **Rationale**: Single instance (Torino) made automated tools unnecessary
- **Efficiency**: Simple manual verification more appropriate than tool setup

**Step 4: Link Creation**
- **Source URI**: `http://smartcity.linkeddata.es/BECA/resource/City#Torino`
- **Target URI**: `http://dbpedia.org/page/Turin`  
- **Relationship**: `owl:sameAs` property
- **Validation**: Verified geographic and administrative equivalence

#### Linking Results
**Benefits Achieved**:
- **Enhanced Descriptions**: Access to comprehensive city information from DBpedia
- **Contextual Enrichment**: Historical, demographic, and geographic data integration
- **Discovery**: Enable finding related energy data through city connections
- **Validation**: Cross-reference location information for accuracy

### Building Information Linking (IFC/BIM)

#### Complex Linking Requirements

**Domain Characteristics**:
- **Engineering Knowledge**: Requires sophisticated technical understanding
- **Rule Complexity**: Manual setup of intricate linking rules needed
- **Dataset Specificity**: Rules may be limited to specific building projects
- **Data Transformations**: Often requires coordinate conversions and data combination

#### Linking Scenarios

##### Design Phase Integration
**Library and Catalog Linking**:
- **Purpose**: Connect BIM elements to standard component libraries
- **Examples**: HESMOS and ISES project implementations
- **Benefits**: Default settings assignment and standardization
- **Challenges**: Maintaining currency with evolving standards

##### Monitoring Phase Integration  
**Sensor Data Linking**:
- **Data Types**: Temperature, humidity, energy consumption, air flow rate
- **Integration**: Combine static BIM data with dynamic sensor measurements
- **Applications**: Building performance analysis and optimization
- **Technical Requirements**: Spatial and temporal data alignment

#### Implementation Challenges

##### Data Conversion Requirements
**Coordinate System Transformation**:
- **Need**: Convert between different spatial reference systems
- **Example**: Postal addresses ↔ geographic coordinates
- **Complexity**: Multiple coordinate systems and projection methods
- **Validation**: Accuracy verification across transformation processes

##### Structural Modifications
**Data Preparation for Linking**:
- **Wall Example**: Split partially exterior walls into interior/exterior segments
- **Purpose**: Enable separate linking with weather data vs. occupant behavior
- **Impact**: Requires modification of original BIM data structure
- **Documentation**: Track changes for audit and maintenance purposes

##### Linking Rule Limitations
**Constraints and Challenges**:
- **Naming Convention Dependency**: Rules limited to specific building projects
- **Information Gaps**: Missing or imprecise data preventing rule definition
- **Manual Fallback**: Individual assignment required when rules insufficient
- **Scalability**: Time-consuming and error-prone manual processes
- **Tool Support**: Need for filtering and assistance capabilities

#### Best Practices for BIM Linking

##### Rule Generalization
- **Reusability**: Design rules applicable across multiple BIM datasets
- **Parameterization**: Create configurable rules for different contexts
- **Standardization**: Follow industry conventions where possible
- **Documentation**: Maintain clear rule specifications and rationale

##### Quality Assurance
- **Validation Protocols**: Systematic verification of linking results
- **Error Handling**: Robust processes for handling exceptions and conflicts
- **Performance Monitoring**: Track linking accuracy and efficiency metrics
- **Expert Review**: Domain expert validation for critical links

## Advanced Linking Strategies

### Multi-Step Linking Workflows

#### Progressive Refinement
1. **Initial Automated Matching**: High-confidence automatic links
2. **Semi-Automatic Review**: Human validation of medium-confidence candidates  
3. **Manual Expert Review**: Domain expert analysis of complex cases
4. **Iterative Improvement**: Refine rules based on validation outcomes

#### Confidence-Based Processing
- **High Confidence**: Automatic acceptance with minimal review
- **Medium Confidence**: Queue for expert validation
- **Low Confidence**: Manual analysis or rejection
- **Threshold Adjustment**: Dynamic tuning based on accuracy feedback

### Cross-Dataset Validation

#### Consistency Checking
- **Multiple Sources**: Verify links using several external datasets
- **Conflict Resolution**: Handle contradictory information systematically
- **Consensus Building**: Weight evidence from multiple authoritative sources
- **Quality Metrics**: Measure agreement levels across sources

#### Link Network Analysis
- **Graph Properties**: Analyze structural characteristics of link networks
- **Community Detection**: Identify clusters of highly connected entities
- **Anomaly Detection**: Find unusual patterns indicating potential errors
- **Network Evolution**: Track changes in link patterns over time

### Domain-Specific Considerations

#### Geographic Data Linking
- **Spatial Hierarchies**: Handle administrative and geographic containment
- **Temporal Changes**: Account for boundary and name changes over time
- **Coordinate Systems**: Manage different spatial reference systems
- **Scale Differences**: Link across different levels of geographic detail

#### Temporal Data Linking
- **Time Period Alignment**: Handle different temporal granularities
- **Historical Changes**: Account for entity evolution over time
- **Event Correlation**: Link related events across different datasets
- **Temporal Validation**: Verify chronological consistency

#### Scientific Data Linking
- **Identifier Systems**: Leverage DOIs, ORCIDs, and other persistent identifiers
- **Citation Networks**: Utilize publication and citation relationships
- **Experimental Context**: Link related experiments and methodologies
- **Reproducibility**: Enable verification through linked experimental data

## Quality Assurance and Validation

### Link Quality Metrics

#### Precision and Recall
- **Precision**: Proportion of created links that are correct
- **Recall**: Proportion of correct links that are discovered
- **F-measure**: Harmonic mean of precision and recall
- **Coverage**: Percentage of linkable instances successfully linked

#### Consistency Measures
- **Logical Consistency**: Verify no contradictory owl:sameAs chains
- **Type Consistency**: Ensure linked instances have compatible types
- **Property Consistency**: Check for contradictory property values
- **Temporal Consistency**: Validate time-related constraints

### Validation Methodologies

#### Manual Validation
- **Sampling Strategy**: Representative sample selection for manual review
- **Expert Panels**: Domain expert evaluation of link quality
- **Cross-Validation**: Multiple reviewer assessment for reliability
- **Feedback Integration**: Incorporate manual corrections into automated processes

#### Automated Validation
- **Rule-Based Checking**: Logical constraints and business rules
- **Statistical Analysis**: Outlier detection and pattern analysis
- **Cross-Reference**: Validation against multiple external sources  
- **Historical Validation**: Comparison with previous linking results

## Tools and Resources

### Data Linking Tools

#### Comprehensive Frameworks
- **LN2R**: https://sourcesup.renater.fr/projects/ln2r-lt/
- **RDF-AI**: https://code.google.com/p/rdfai/
- **Serimi**: https://github.com/samuraraujo/SERIMI-RDF-Interlinking/

#### Specialized Tools
- **Silk**: http://sourceforge.net/projects/silk2/
- **LIMES**: http://lod2.eu/Project/LIMES.html
- **LD mapper**: http://sourceforge.net/p/motools/code/HEAD/tree/

### Target Datasets

#### General Knowledge Bases
- **DBpedia**: http://dbpedia.org/
- **Wikidata**: https://www.wikidata.org/
- **YAGO**: https://yago-knowledge.org/

#### Domain-Specific Resources
- **GeoNames**: http://www.geonames.org/
- **VIAF**: https://viaf.org/
- **LinkedGeoData**: http://linkedgeodata.org/

### Validation and Quality Tools
- **Link Validation Services**: Various online validation tools
- **SPARQL Endpoints**: For querying and validating linked data
- **Graph Analysis Tools**: NetworkX, Gephi for link network analysis

### Standards and Guidelines
- **W3C Linking Guidelines**: Best practices for creating links
- **LOD Principles**: Linked Open Data community standards
- **Domain Standards**: Field-specific linking conventions and practices

## Best Practices and Recommendations

### Planning and Strategy
- **Start Simple**: Begin with high-confidence, straightforward links
- **Incremental Approach**: Gradually increase complexity and scope
- **Quality over Quantity**: Prioritize link accuracy over coverage
- **Documentation**: Maintain detailed records of linking decisions and processes

### Technical Implementation  
- **Threshold Tuning**: Carefully calibrate similarity thresholds
- **Performance Optimization**: Monitor and optimize processing efficiency
- **Error Handling**: Robust exception handling and recovery procedures
- **Scalability Planning**: Design for future data growth and complexity

### Quality Management
- **Continuous Monitoring**: Ongoing assessment of link quality and accuracy
- **Feedback Loops**: Incorporate validation results into process improvement
- **Expert Involvement**: Engage domain experts for validation and rule refinement
- **Version Control**: Track changes to linking rules and configurations

### Community Engagement
- **Standard Adoption**: Use established vocabularies and linking patterns
- **Community Contribution**: Share successful linking strategies and rules
- **Collaboration**: Partner with other organizations for mutual linking benefits
- **Knowledge Sharing**: Contribute to best practices and methodological development
