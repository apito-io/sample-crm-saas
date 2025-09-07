# CRM SaaS Sample Data

This folder contains realistic multi-tenant sample data for the CRM SaaS template:

## Hospital-Based Multi-Tenancy Structure

```
data/
├── organization/       # 5 tenant hospitals
│   ├── [uuid].json     # Individual organization files
│   └── relation.json   # Organization relationships
├── contact/           # 30 patient/contact records
│   ├── [uuid].json     # Individual contact files
│   └── relation.json   # Contact relationships
└── deal/              # 20 deals/opportunities
    ├── [uuid].json     # Individual deal files
    └── relation.json   # Deal relationships
```

## SaaS Multi-Tenancy Features

### Hospital-Based Isolation
- **5 Hospital Organizations**: Different healthcare providers and specialties
- **Tenant Filtering**: All data properly isolated by organization_id (hospital_id)
- **Cross-Hospital Security**: Complete data separation for HIPAA compliance

### Sample Hospital Organizations
1. **General Medical Center** - Comprehensive healthcare services
2. **Pediatric Specialty Hospital** - Children's healthcare focus
3. **Cardiac Care Institute** - Heart and vascular specialties
4. **Orthopedic Treatment Center** - Bone and joint care
5. **Mental Health Services** - Psychiatric and counseling services

## Sample Data Features

### Organizations (5 records - Tenant Model: Hospital)
- Complete hospital profiles with medical specializations
- Various sizes: Community Hospital, Medical Center, Specialty Clinic
- Location and contact information
- Status tracking and accreditation details
- Tenant isolation boundaries for healthcare compliance

### Contacts (30 records)
- Patient and contact management within hospitals
- Personal information with privacy compliance
- Medical record numbers and patient identifiers
- Contact preferences and communication methods
- Hospital association isolation for data privacy
- Lead source tracking and patient acquisition

### Deals (20 records)
- Healthcare service opportunities and treatment plans
- Deal stages: Lead, Qualified, Proposal, Negotiation, Closed Won, Closed Lost
- Service values and treatment cost estimations
- Expected close dates and treatment timelines
- Hospital-based deal isolation for financial tracking
- Service type categorization (Treatment, Consultation, Surgery, etc.)

## Relationship Format

### Organization Relations (Tenant - Hospital)
```json
{
  "organization-uuid": {
    "contact": {
      "relation_type": "has_many",
      "ids": ["contact-uuid-1", "contact-uuid-2"]
    },
    "deal": {
      "relation_type": "has_many", 
      "ids": ["deal-uuid-1", "deal-uuid-2"]
    }
  }
}
```

### Contact Relations
```json
{
  "contact-uuid": {
    "organization": {
      "relation_type": "has_one",
      "id": "organization-uuid"        // Hospital isolation
    },
    "deal": {
      "relation_type": "has_many",
      "ids": ["deal-uuid-1", "deal-uuid-2"]
    }
  }
}
```

### Deal Relations
```json
{
  "deal-uuid": {
    "organization": {
      "relation_type": "has_one",
      "id": "organization-uuid"        // Hospital isolation
    },
    "contact": {
      "relation_type": "has_one",
      "id": "contact-uuid"            // Patient association
    }
  }
}
```

## Healthcare Multi-Tenant Patterns

### HIPAA Compliance
- Patient data isolated by hospital organization
- Secure tenant boundaries for healthcare privacy
- Cross-hospital queries automatically filtered
- Medical record protection and access controls

### Healthcare CRM Workflows
- Patient acquisition and lead management
- Treatment opportunity tracking
- Service delivery pipeline management
- Revenue cycle management per hospital

### Hospital Operations
- Patient relationship management
- Treatment planning and scheduling
- Insurance and billing coordination
- Medical staff and resource allocation

## Healthcare Use Cases

### Patient Journey Management
- **Lead Stage**: Initial patient inquiry or referral
- **Qualified Stage**: Medical assessment and insurance verification
- **Proposal Stage**: Treatment plan and cost estimation
- **Negotiation Stage**: Insurance authorization and scheduling
- **Closed Won**: Treatment completed successfully
- **Closed Lost**: Patient declined or transferred to another provider

### Service Types Demonstrated
- **Emergency Services**: Acute care and trauma treatment
- **Surgical Procedures**: Planned operations and interventions
- **Specialist Consultations**: Expert medical opinions
- **Diagnostic Services**: Testing and imaging procedures
- **Rehabilitation Services**: Recovery and therapy programs

## Data Generation

This healthcare SaaS data was generated using the Apito Data Generator with multi-tenant support:

```bash
# Regenerate multi-tenant healthcare data
./apito-gen

# Verify hospital isolation (HIPAA compliance)
grep -r "organization_id" *.json
```

## Statistics

- **Total Files**: 58
- **Hospital Organizations**: 5 tenant entities (HIPAA isolation boundaries)
- **Patient Contacts**: 30 with healthcare-specific data
- **Medical Deals**: 20 treatment opportunities and service records
- **Relationships**: 100% tenant isolation maintained for compliance
- **UUID Format**: All files use UUID v4 naming for medical record security
- **SaaS Architecture**: Proper multi-tenant healthcare data separation

## Import Instructions

### Via Apito Dashboard
1. Create new SaaS project with hospital tenant model
2. Import schema.json with healthcare multi-tenant configuration
3. Upload data folder maintaining hospital isolation for HIPAA compliance
4. Configure healthcare workflows and patient management

### Via Apito CLI
```bash
apito import schema.json --saas --tenant-model=hospital
apito import data/ --preserve-tenant-structure --healthcare-compliance
```

## Use Cases Demonstrated

- **Healthcare CRM**: Multi-hospital patient relationship management
- **Medical Practice Management**: Treatment planning and patient care coordination
- **Hospital Operations**: Multi-location healthcare service delivery
- **Patient Acquisition**: Lead management for healthcare services
- **Revenue Cycle Management**: Financial tracking per hospital organization
- **HIPAA Compliance**: Secure multi-tenant patient data isolation

## Compliance Features

- **Data Isolation**: Complete patient record separation by hospital
- **Access Controls**: Organization-based data access restrictions
- **Audit Trails**: Patient interaction and treatment tracking
- **Privacy Protection**: Secure multi-tenant patient information handling

---

**Note**: This demonstrates comprehensive healthcare CRM SaaS architecture with hospital-based multi-tenancy, patient relationship management, and HIPAA-compliant data isolation suitable for healthcare providers, medical practices, and hospital networks. All patient data is properly isolated for healthcare privacy compliance.
