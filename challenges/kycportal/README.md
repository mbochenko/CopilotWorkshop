# Develop a KYC/Document Verification Portal

## 1. Problem Description

Build a **KYC (Know Your Customer) Document Verification Portal** for financial institutions to collect, verify, and manage customer identity documents. The system must handle sensitive customer data securely while providing a smooth user experience for document submission and verification workflow.

### Core Requirements:
- **Frontend**: Secure interface for document upload and verification status tracking
- **Backend**: RESTful API (.NET Core, Python Flask, or Node.js Express) for document processing
- **Document Upload**: Support multiple document types (ID, Passport, Proof of Address, etc.)
- **Verification Workflow**: Multi-step verification process with status tracking
- **Security**: Data encryption, secure file storage, access controls
- **Compliance**: Audit trail for regulatory compliance (GDPR, AML, etc.)

### User Stories:
1. As a customer, I can create a new KYC application
2. As a customer, I can upload identity documents (ID card, passport, driver's license)
3. As a customer, I can upload proof of address documents
4. As a customer, I can track the verification status of my application
5. As a compliance officer, I can review submitted documents
6. As a compliance officer, I can approve or reject KYC applications with reasons
7. As a compliance officer, I can view audit logs of all verification actions
8. As a system admin, I can configure required document types per country/region

## 2. Hints

### Technical Implementation Hints:
- **Document Storage**: 
  - Use secure blob storage (Azure Blob, AWS S3, or local encrypted storage)
  - Generate unique filenames (UUID) to prevent conflicts
  - Store files separately from metadata in database
- **Supported Document Types**: 
  - Government ID (Passport, National ID, Driver's License)
  - Proof of Address (Utility Bill, Bank Statement, Tax Document)
  - Selfie/Photo for face matching
- **File Validation**:
  - Max file size: 5-10 MB per document
  - Allowed formats: PDF, JPG, PNG
  - Virus scanning (if possible)
  - Image quality checks
- **Verification Workflow States**:
  1. **Draft** - Customer started application
  2. **Submitted** - All documents uploaded
  3. **Under Review** - Compliance officer reviewing
  4. **Approved** - KYC verified
  5. **Rejected** - KYC failed verification
  6. **More Info Needed** - Additional documents required

### Quick Start Tips:
- Start with basic file upload functionality
- Implement document type validation early
- Use file upload libraries (multer for Node.js, Flask-Upload for Python)
- Create a simple status dashboard before complex workflows
- Mock the verification process initially (auto-approve after 5 seconds)
- Use sample documents for testing (create fake IDs for testing purposes)
- Implement basic security (authentication) before file upload

### Security Considerations:
- **Authentication**: Require login before document upload
- **Authorization**: Users can only view their own applications
- **Encryption**: Encrypt files at rest and in transit (HTTPS)
- **Data Sanitization**: Validate all inputs to prevent XSS/SQL injection
- **Audit Logging**: Log all access and modification events
- **PII Protection**: Redact sensitive data in logs
- **Session Management**: Implement secure session handling with timeouts

### Agent Mode Note:
If you are using the Agent mode and notice that the agent is working in the wrong directory, try to add the following line to your prompt:
```markdown
Work in the directory backend. When run terminal remember to change the right directory, for example: `cd challenges/kycportal/backend && <command>`.
```
Change the directory to `frontend` when working on the frontend part.

## 3. Time Needed

**Estimated Duration: 90-120 minutes**

### Time Breakdown:
- **Setup & Planning** (15-20 minutes): Project structure, dependencies, security planning
- **Backend API** (30-40 minutes): 
  - File upload endpoints
  - Document metadata storage
  - Verification workflow logic
  - Audit logging
- **Frontend UI** (30-40 minutes):
  - Document upload forms
  - Application status dashboard
  - Verification officer interface
  - File preview functionality
- **Security & Testing** (15-20 minutes): 
  - Authentication implementation
  - Security testing
  - File validation testing

## 4. Extra Features (Bonus Challenges)

Quick additions for teams that finish early:

### Easy Additions (10-15 minutes each):
- **Document Preview**: Display uploaded documents before submission
- **Email Notifications**: Send emails on status changes
- **Document Expiry**: Track document expiration dates
- **Application Notes**: Allow officers to add review notes

### Medium Additions (15-25 minutes each):
- **OCR Integration**: Extract text from ID documents automatically
- **Face Matching**: Compare selfie with ID photo (using ML libraries)
- **Document Templates**: Pre-approved document checklist per country
- **Bulk Upload**: Allow multiple files in one upload
- **Advanced Search**: Filter applications by status, date, applicant name
- **Export Reports**: Generate CSV/PDF reports of applications

### Advanced Additions (25-40 minutes each):
- **Real-Time Verification**: Integrate with third-party identity verification APIs
- **Blockchain Audit Trail**: Immutable verification record on blockchain
- **Multi-Factor Authentication**: Add 2FA for compliance officers
- **Risk Scoring**: Automatic risk assessment based on document quality
- **Video KYC**: Live video verification session
- **API Integration**: Connect to government ID verification services
- **Compliance Dashboard**: Analytics on verification times, rejection rates

### Why Perfect for Advanced Challenge:
- **Real-World Problem**: Critical for fintech, banking, crypto exchanges
- **Security Focus**: Learn secure file handling and data protection
- **Complex Workflow**: Multi-step process with different user roles
- **Compliance Aspects**: Understand regulatory requirements
- **File Handling**: Practice upload, storage, and retrieval
- **Role-Based Access**: Implement customer vs. officer views

### Success Criteria:
- ✅ Users can create KYC applications
- ✅ Multiple document types can be uploaded securely
- ✅ File validation prevents invalid uploads
- ✅ Application status workflow is functional
- ✅ Compliance officers can review and approve/reject applications
- ✅ Audit trail logs all actions
- ✅ Basic authentication and authorization implemented
- ✅ Files are stored securely with encryption
- ✅ UI shows clear upload progress and status

### Testing Checklist:
- ✅ Upload valid documents (PDF, JPG, PNG)
- ✅ Test file size limits (try uploading 20MB file)
- ✅ Test invalid file types (try .exe, .zip)
- ✅ Verify authentication - unauthorized users cannot upload
- ✅ Test authorization - users cannot view others' applications
- ✅ Test complete workflow from submission to approval
- ✅ Verify audit logs capture all actions
- ✅ Test error handling (network errors, file corruption)
- ✅ Verify encrypted file storage
- ✅ Test on mobile devices

### Data Model Example:

```typescript
// KYC Application
{
  id: string;
  customerId: string;
  status: 'draft' | 'submitted' | 'under_review' | 'approved' | 'rejected' | 'more_info_needed';
  createdAt: Date;
  submittedAt?: Date;
  reviewedAt?: Date;
  reviewedBy?: string;
  rejectionReason?: string;
  documents: Document[];
  auditLog: AuditEntry[];
}

// Document
{
  id: string;
  applicationId: string;
  documentType: 'passport' | 'national_id' | 'drivers_license' | 'proof_of_address' | 'selfie';
  fileName: string;
  fileSize: number;
  mimeType: string;
  storageUrl: string;
  uploadedAt: Date;
  expiryDate?: Date;
  verified: boolean;
}

// Audit Entry
{
  id: string;
  applicationId: string;
  action: string;
  performedBy: string;
  timestamp: Date;
  details: object;
  ipAddress: string;
}
```

This challenge combines security, compliance, file handling, and complex workflows - perfect for understanding enterprise-grade application development with strict regulatory requirements!

## 5. Additional Resources

### Security & Compliance:
- [OWASP File Upload Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/File_Upload_Cheat_Sheet.html)
- [GDPR Compliance Guide](https://gdpr.eu/)
- [PCI DSS Standards](https://www.pcisecuritystandards.org/)

### Document Verification APIs:
- [Onfido](https://onfido.com/) - Identity verification
- [Jumio](https://www.jumio.com/) - KYC automation
- [Stripe Identity](https://stripe.com/identity) - ID verification

### File Upload Libraries:
- Node.js: [Multer](https://github.com/expressjs/multer)
- Python: [Flask-Uploads](https://flask-uploads.readthedocs.io/)
- .NET: [Built-in IFormFile](https://docs.microsoft.com/en-us/aspnet/core/mvc/models/file-uploads)
