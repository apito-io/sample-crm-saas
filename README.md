# CRM SaaS - Apito Engine Template

🏢 **A complete Customer Relationship Management SaaS platform with multi-tenant organization support**

[![Apito Engine](https://img.shields.io/badge/Apito-Engine-blue?style=flat&logo=graphql)](https://apito.io)
[![Project Type](https://img.shields.io/badge/Project%20Type-SaaS-red?style=flat)](#project-type)
[![Tenant Model](https://img.shields.io/badge/Tenant%20Model-Organization-purple?style=flat)](#multi-tenancy)
[![Models](https://img.shields.io/badge/Models-3-orange?style=flat)](#data-models)
[![Sample Data](https://img.shields.io/badge/Sample%20Data-58%20Files-purple?style=flat)](#sample-data)

## 🚀 Quick Start

1. **Import Schema**: Use `schema.json` to set up your Apito Engine project
2. **Configure Multi-tenancy**: Reference `config.yml` for SaaS setup
3. **Load Sample Data**: Import the `data/` folder for realistic examples
4. **Set Up Organizations**: Configure tenant isolation
5. **Customize**: Add additional CRM features as needed

## 📋 Project Overview

### **Project Type**
- **SaaS Project** (Multi-tenant)
- **Tenant Model**: Organization
- **Difficulty Level**: Intermediate  
- **Category**: Customer Relationship Management

### **Key Features**
- ✅ Multi-tenant organization support
- ✅ Customer contact management
- ✅ Deal pipeline tracking
- ✅ Organization-based data isolation
- ✅ Complete SaaS infrastructure
- ✅ Relationship tracking
- ✅ Complete sample data with relationships
- ✅ UUID-based data files

## 🏗️ Data Models

This template includes **3 models** with **organization-based multi-tenancy**:

### **🏢 Organization Model** (Tenant)
Multi-tenant organization entity that isolates all data.

**Fields:**
- `name` (text) - Organization name
- `slug` (text) - URL-friendly identifier  
- `description` (multiline) - Organization description
- `website` (text) - Company website
- `industry` (list) - Business industry
- `size` (list) - Company size category
- `created_at` (date) - Registration date
- `status` (list) - Active, Suspended, Inactive

**Relations:**
- `has_many` Contacts
- `has_many` Deals

### **👤 Contact Model**
Customer contact management within organizations.

**Fields:**
- `first_name` (text) - Contact first name
- `last_name` (text) - Contact last name
- `email` (text) - Contact email address
- `phone` (text) - Phone number
- `job_title` (text) - Professional title
- `company` (text) - Company name
- `address` (object) - Contact address with street, city, state, country
- `social_profiles` (object) - LinkedIn, Twitter, etc.
- `lead_source` (list) - Website, Referral, Cold Call, etc.
- `status` (list) - Lead, Prospect, Customer, Inactive
- `created_at` (date) - First contact date
- `organization_id` (relation) - Tenant organization

**Relations:**
- `belongs_to` Organization (tenant isolation)
- `has_many` Deals

### **💰 Deal Model**
Sales opportunity and pipeline management.

**Fields:**
- `title` (text) - Deal title/name
- `description` (multiline) - Deal description
- `value` (number) - Deal value/amount
- `currency` (list) - USD, EUR, GBP, etc.
- `stage` (list) - Prospect, Qualified, Proposal, Negotiation, Closed Won, Closed Lost
- `probability` (number) - Close probability percentage
- `expected_close_date` (date) - Anticipated close date
- `actual_close_date` (date) - Actual close date
- `source` (list) - Inbound, Outbound, Partner, etc.
- `created_at` (date) - Deal creation date
- `contact_id` (relation) - Primary contact
- `organization_id` (relation) - Tenant organization

**Relations:**
- `belongs_to` Organization (tenant isolation)
- `belongs_to` Contact (primary contact)

## 🔒 Multi-Tenancy

This SaaS template implements **organization-based multi-tenancy**:

### **Tenant Isolation**
- Each organization sees only their own data
- Automatic tenant-based filtering on all queries
- Secure data separation at the database level

### **Organization Structure**
```
Organization (Tenant)
├── Contacts (Customer database)
├── Deals (Sales pipeline)
└── Users (Team members)
```

### **Access Control**
- Organization-scoped permissions
- Role-based access within organizations
- Tenant admin capabilities

## 📊 Sample Data

The template includes **58 sample data files** with realistic CRM content:

### **Data Structure**
```
data/
├── organization/   # 5 organizations (tenants)
│   ├── [uuid].json # Individual org files
│   └── relation.json
├── contact/        # 30 contacts
│   ├── [uuid].json # Individual contact files  
│   └── relation.json
└── deal/           # 20 deals
    ├── [uuid].json # Individual deal files
    └── relation.json
```

## 🎯 Use Cases

Perfect for building:
- **SaaS CRM Platforms** - Multi-tenant customer management
- **Sales Pipeline Tools** - Deal tracking and forecasting
- **Customer Databases** - Contact and company management
- **Lead Management** - Lead capture and nurturing
- **B2B SaaS Products** - Organization-based applications

## 📦 Installation

### **Option 1: Apito Engine Dashboard**
1. Create new SaaS project in Apito Dashboard
2. Import `schema.json` 
3. Configure organization tenant model
4. Load sample data from `data/` folder
5. Set up multi-tenant access controls

### **Option 2: Apito CLI**
```bash
# Clone this repository
git clone https://github.com/apito-io/sample-crm-saas

# Import schema with SaaS configuration
apito import schema.json --saas --tenant-model=organization

# Load sample data  
apito import data/
```

## 🏢 SaaS Configuration

```yaml
project_type: "saas"
tenant_model: "organization"
```

## 🙋‍♂️ Support

- **Documentation**: [Apito Engine Docs](https://docs.apito.io)
- **SaaS Guide**: [Multi-tenant Setup](https://docs.apito.io/saas)
- **Issues**: [GitHub Issues](https://github.com/apito-io/sample-crm-saas/issues)
- **Email**: support@apito.io

---

**Built with ❤️ using [Apito Engine](https://apito.io)**