# Define Resource Naming Strategy

## Overview

Resources are one of the key concepts in Linked Data, and choosing the right strategy for naming them is of high importance. The global identification system on the Web is the URI, and it is considered a best practice to identify resources using URIs. This task establishes clear, consistent, and persistent naming conventions for all resources in your Linked Data.

## Inputs
- Data schema
- Analyzed data structure

## Outputs
- Complete resource naming strategy
- URI patterns and conventions
- Content negotiation approach

## Fundamental Concepts

### URI Importance in Linked Data

URIs serve dual purposes in Linked Data:
1. **Identifying real-world entities** that exist outside the Web
2. **Identifying web documents** that contain descriptions of those entities

**Critical Distinction**: A clear separation must exist between:
- The identifier for a web document describing an entity
- The identifier for the entity itself

**Example**: A web page describing an energy company might be `http://www.energycompany.com/about`, but this URI cannot also identify the company itself.

### URI Structure Components

An HTTP URI consists of three main parts:

1. **Protocol**: Usually HTTP (`http://` or `https://`)
2. **Domain**: Processed by Domain Name Servers (e.g., `www.energycompany.com`)
3. **Path Structure**: Processed by the web server (e.g., `/about/energyCompany`)

### Content Negotiation

Content negotiation allows web clients and servers to communicate effectively, enabling clients to request specific representations of resources (HTML, RDF, etc.) and servers to return appropriate representations.

## URI Types and Approaches

### 1. Hash URIs (#)

**Structure**: Contains a fragment separated by a hash character (#)
**Example**: `http://www.energycompany.com/about#energyCompany`

**Characteristics**:
- Fragment part is stripped when requesting from server
- Cannot be retrieved directly
- Ideal for identifying non-document resources
- Suitable for smaller datasets

**Content Negotiation**: Fragment is processed client-side after document retrieval

### 2. Slash URIs (303 URIs)

**Structure**: Uses 303 redirection to document location
**Example**: `http://www.energycompany.com/about/energyCompany`

**Content Negotiation Options**:

#### Option A: Forwarding to One Generic Document
- 303 redirection points to single document
- Document returns appropriate description using content negotiation
- Client specifies desired format in request

#### Option B: Forwarding to Different Documents  
- 303 redirection with content negotiation
- Points to specific document with desired representation
- Multiple documents contain different representations

**Characteristics**:
- Better for larger datasets
- More flexible content negotiation
- Requires server-side 303 redirection setup

## Development Process

### Step 1: Choose URI Form and Content Negotiation

**Decision Points**:
- **Hash URIs**: Suitable for smaller datasets, simpler server setup
- **Slash URIs**: Better for larger datasets, more flexible content negotiation

**Content Negotiation Selection** (for Slash URIs):
- Generic document approach vs. multiple document approach
- Consider server capabilities and maintenance requirements

### Step 2: Choose Domain

**Domain Selection Criteria**:
- **Ownership**: Use domain under your control
- **Persistence**: Ensure long-term domain availability
- **Alternative**: Use PURL (Persistent Uniform Resource Locator) service for third-party management

### Step 3: Choose Path Structure

**Path Strategy Components**:
- **Base Path**: Define server folder structure (e.g., `/about`, `/data`)
- **Resource Categories**: Separate paths for different resource types
- **Hierarchical Structure**: Reflect logical organization

**Example Structure**:
```
http://example.com/
├── ontology/     (ontology definitions)
├── resource/     (data instances)
└── vocabulary/   (shared vocabularies)
```

### Step 4: Define Patterns for Classes, Properties, and Instances

**Pattern Elements**:
- **Ontology Classes**: Include ontology name and class name
- **Properties**: Include ontology context and property name  
- **Instances**: Include class context and unique identifier

## Best Practices and Guidelines

### 1. Unambiguity
- **One URI = One Resource**: Each URI should identify exactly one item
- **No Dual Purpose**: Avoid using same URI for web page and real-world object
- **Clear Semantics**: URI structure should reflect resource relationships

### 2. Persistence
- **Avoid Changeable Elements**: No state information, session IDs, or temporary values
- **Stable Structure**: Design for long-term maintenance
- **Impact Consideration**: Changes affect dependent applications
- **PURL Alternative**: Use PURL service for additional persistence layer

### 3. Domain Control
- **Own Your Domain**: Use domains under your direct control
- **Backup Plan**: Consider PURL service for institutional changes
- **DNS Stability**: Ensure reliable DNS management

### 4. Ontology-Instance Separation

**Ontology Model URIs**:
- Pattern: `{baseURI}/ontology/{ontologyName}#{className}`
- Purpose: Define classes, properties, and relationships

**Instance URIs**:
- Pattern: `{baseURI}/resource/{className}#{identifier}`
- Purpose: Identify specific data instances

### 5. Human Readability
- **Descriptive Names**: Use meaningful, understandable terms
- **Consistent Conventions**: Apply uniform naming patterns
- **Avoid Cryptic Codes**: Prefer readable identifiers over numeric IDs when possible

## Established Guidelines and Standards

### Recommended References
- **Cool URIs** (Sauermann and Cyganiak, 2008)
- **UK Public Sector Design Guidelines** (UK Cabinet Office, 2010)  
- **Ten Rules for Persistent URIs** (Semantic Interoperability Community, 2012)
- **Linked Data Patterns** (Dodds and Davis, 2012)

## Practical Examples

### Energy Consumption Example (BECA Project)

**Strategy Decisions**:
- **URI Type**: Hash URIs (small dataset size)
- **Domain**: `http://smartcity.linkeddata.es/` (UPM controlled)
- **Project Path**: `/BECA/` (clear project identification)

**URI Patterns**:

#### Ontology Classes
```
Pattern: http://smartcity.linkeddata.es/BECA/ontology/{ontologyName}#{className}
Example: http://smartcity.linkeddata.es/BECA/ontology/ResidenceOntology#Dwelling
```

#### Ontology Properties  
```
Pattern: http://smartcity.linkeddata.es/BECA/ontology/{ontologyName}#{propertyName}
Example: http://smartcity.linkeddata.es/BECA/ontology/ResidenceOntology#hasId
```

#### Data Instances
```
Pattern: http://smartcity.linkeddata.es/BECA/resource/{className}#{identifier}
Example: http://smartcity.linkeddata.es/BECA/resource/Dwelling#347fns7ebcuwdb
```

**Rationale**:
- Small dataset size suitable for hash URIs
- Clear organizational hierarchy
- UPM domain control ensures persistence
- Human-readable structure aids understanding

### Building Information Example (IFC/BIM)

**Strategy Considerations**:
- **Existing Framework**: IFC data already has sound data modeling approach
- **Automatic Conversion**: META-model level EXPRESS to OWL conversion available
- **Scale Considerations**: Large data volumes require different approach

**Recommended Approach**:

#### IFC Ontology (Schema)
```
URI Type: Hash URIs
Access: Web-accessible ontology definitions
Structure: Based on existing IFC-EXPRESS standards
```

#### IFC Instances (Data)
```
URI Type: Slash URIs (due to data volume)
Domain: Any suitable domain for publication
Identifier Strategy: 
  - Uniquely identifiable elements: Use global unique identifier
  - Resource elements: Anonymous individuals (blank nodes)
```

**Special Considerations**:
- **Naming Conflicts**: When publishing multiple IFC datasets under same domain
- **Anonymous Individuals**: Node IDs may need modification for uniqueness
- **Existing Tools**: Leverage LinkedBuildingData.net mapping approaches

**Available Mapping Strategies**:
- Multiple OWL configurations (OWL 1, OWL 2)
- Different reasoning profiles (DL, EL, Full, RL)
- Established conversion tools and methodologies

## Implementation Checklist

### Pre-Implementation
- [ ] Choose URI type (Hash vs Slash)
- [ ] Select or secure appropriate domain
- [ ] Design path structure hierarchy
- [ ] Define pattern templates for all resource types
- [ ] Plan content negotiation approach

### Domain and Infrastructure
- [ ] Verify domain ownership and control
- [ ] Set up DNS and web server configuration
- [ ] Implement 303 redirection (if using Slash URIs)
- [ ] Configure content negotiation
- [ ] Plan backup and persistence strategy

### Pattern Definition
- [ ] Create URI templates for ontology classes
- [ ] Define property naming conventions  
- [ ] Establish instance identifier patterns
- [ ] Document human-readable guidelines
- [ ] Test pattern consistency across use cases

### Documentation and Governance
- [ ] Document complete naming strategy
- [ ] Create governance procedures for changes
- [ ] Establish quality control processes
- [ ] Plan versioning strategy if needed
- [ ] Train team members on conventions

## Common Pitfalls and Solutions

### Pitfall: Changing URI Patterns
**Problem**: Modifying URI structure after publication breaks existing links
**Solution**: Design for stability from the start; use PURL for additional layer

### Pitfall: Ambiguous Resource Identity
**Problem**: Same URI used for both document and real-world entity
**Solution**: Clear separation between entity URIs and document URIs

### Pitfall: Non-Persistent Domains
**Problem**: Loss of domain control breaks all published URIs
**Solution**: Use institutional domains or PURL service; plan for succession

### Pitfall: Complex, Unreadable URIs
**Problem**: Cryptic identifiers reduce human usability
**Solution**: Balance machine processing with human readability

### Pitfall: Inconsistent Patterns
**Problem**: Ad-hoc URI creation leads to maintenance difficulties
**Solution**: Establish clear templates and governance processes
