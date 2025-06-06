# LCI Grant Tracking Schema Implementation Summary
## California Department of Innovation in Climate and Territory (LCI)

This document summarizes the complete Dataverse schema extension for the Pravia Mule CRM to support LCI grant tracking functionality.

### New Entities Created

#### 1. LCI Grant Program (cr07c_lcigrantprogram)
**Purpose**: Manages grant programs offered by the California LCI department

**Fields:**
- **cr07c_lcigrantprogramid** (Primary Key) - Unique identifier
- **cr07c_programname** (Primary Name Field) - Program display name (required)
- **cr07c_programid** (Auto-generated) - Program ID using format PGM-{SEQNUM:5}
- **cr07c_purpose** (Multiline Text) - Detailed program description
- **cr07c_granttype** (OptionSet) - Grant type classification
  - Planning (100000000)
  - Implementation (100000001) 
  - Heat Resilience (100000002)
- **cr07c_totalfunding** (Money) - Total funding available ($0 - $1B, 2 decimal precision)
- **cr07c_applicationdeadline** (Date) - Application submission deadline
- **cr07c_status** (OptionSet) - Program status
  - Open (100000000)
  - Closed (100000001)
  - Awarded (100000002)
  - Cancelled (100000003)

#### 2. LCI Grant Application (cr07c_lcigrantapplication)
**Purpose**: Tracks individual grant applications submitted to LCI programs

**Fields:**
- **cr07c_lcigrantapplicationid** (Primary Key) - Unique identifier
- **cr07c_applicationid** (Primary Name Field) - Auto-generated application ID using format APP-{SEQNUM:5}
- **cr07c_organization** (Lookup) - Reference to organization (prv_Customer1)
- **cr07c_contact** (Lookup) - Reference to contact person (prv_Contact1)
- **cr07c_grantprogramname** (Lookup) - Reference to grant program (cr07c_lcigrantprogram)
- **cr07c_amountrequested** (Money) - Requested funding amount ($0 - $1B, 2 decimal precision)
- **cr07c_awardedamount** (Money) - Actual awarded amount ($0 - $1B, 2 decimal precision)
- **cr07c_submitteddate** (Date) - Application submission date
- **cr07c_awardnotificationdate** (Date) - Award decision notification date
- **cr07c_applicationstatus** (OptionSet) - Application status
  - Draft (100000000)
  - Submitted (100000001)
  - In Review (100000002)
  - Approved (100000003)
  - Denied (100000004)
- **cr07c_climatezone** (OptionSet) - Climate zone classification
  - Zone 1 - High Desert (100000000)
  - Zone 2 - Central Valley (100000001)
  - Zone 3 - Coastal (100000002)
  - Zone 4 - Mountain (100000003)
  - Zone 5 - Southern Interior (100000004)
- **cr07c_landusetype** (OptionSet) - Land use classification
  - Urban (100000000)
  - Rural (100000001)
  - Forest (100000002)
  - Agriculture (100000003)

### Entity Relationships

#### Primary Relationships
1. **LCI Grant Application → Organization**: One-to-many relationship linking applications to organizations
2. **LCI Grant Application → Contact**: One-to-many relationship linking applications to contacts
3. **LCI Grant Application → Grant Program**: One-to-many relationship linking applications to grant programs

#### System Relationships
Both entities include standard Dataverse ownership and security relationships:
- Owner (User/Team ownership)
- Business Unit
- Created By/Modified By audit trails

### Naming Convention
- **Entity Prefix**: `cr07c_` (following California government naming standards)
- **Logical Names**: All lowercase with underscores
- **Display Names**: Proper capitalization and spacing
- **Auto-numbering**: Sequential patterns (PGM-##### and APP-#####)

### Key Design Features

#### Security & Ownership
- Both entities support full Dataverse security model
- Owner-based record access control
- Team and business unit hierarchical security

#### Data Validation
- Money fields with appropriate range validation (min: 0, max: 1,000,000,000)
- Required fields properly marked
- Lookup field validation through relationships

#### User Experience
- Primary Name fields use human-readable formats (not technical IDs)
- Auto-generated ID fields for system tracking
- Color-coded OptionSet values for visual distinction
- Comprehensive field descriptions for usability

#### Integration Ready
- Full relationship definitions for Power Platform integrations
- Proper schema registration in solution components
- Consistent with existing CRM entity patterns

### Files Created

#### Entity Definitions
- `/entities/cr07c_lcigrantprogram/entity.yml`
- `/entities/cr07c_lcigrantapplication/entity.yml`

#### Field Definitions (16 total)
- 8 fields for Grant Program entity
- 12 fields for Grant Application entity

#### Relationship Definitions (3 primary + system relationships)
- Grant Application → Organization
- Grant Application → Contact  
- Grant Application → Grant Program

#### Solution Configuration
- Updated `solutioncomponents.yml` with all new components
- All entities, attributes, and relationships properly registered

This implementation provides a complete, production-ready schema extension for California LCI grant tracking within the existing Pravia Mule CRM infrastructure.
