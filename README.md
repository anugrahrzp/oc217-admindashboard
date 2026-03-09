# OC217 SEBI-Compliant Terminal Procurement Prototype

Interactive HTML prototype for Razorpay's OC217 (SEBI-compliant UPI) terminal procurement workflow.

## Overview

This prototype demonstrates the complete workflow for BankingOps agents to configure OC217 terminals for SEBI-regulated merchants. OC217 terminals require validated UPI handles (@valid) as per SEBI circular requirements.

## Features

### 1. New Instrument Request Modal
- **Merchant ID**: Enter merchant ID(s)
- **Payment Method**: Select payment method (UPI, Card, etc.)
- **Feature Selection**: Choose OC217 for SEBI-compliant UPI
- **Bank Selection**: Dropdown to select bank (HDFC, ICICI, Axis)
- **Bank-Specific Fields**: Dynamic form fields based on selected bank

### 2. Bank-Specific Requirements
- **HDFC Bank**: VPA (@validhdfc) + Settlement Account + IFSC
- **ICICI Bank**: VPA (@validicici) + ICICI MID (required) + Settlement Account (optional) + IFSC
- **Axis Bank**: VPA (@validaxis) + Settlement Account + IFSC

### 3. Merchant Configuration
- Merchant search and verification
- SEBI registration validation
- Terminal type selection (One-Time, Autopay, Both)

### 4. Review & Submission
- Complete review of all configurations
- Maker-checker workflow
- QC approval process

## How to Use

1. Open `admin-dashboard-prototype.html` in a web browser
2. Click "New Instrument Request" button
3. Fill in:
   - Merchant ID (e.g., M12345)
   - Payment Method: UPI
   - Feature: OC217 (SEBI-Compliant UPI)
   - Select Bank from dropdown
   - Fill bank-specific fields that appear
4. Click "Add Request"
5. Follow the workflow through merchant verification → terminal type → review → QC

## Technical Details

- **File**: Single-page HTML prototype
- **Technologies**: HTML5, CSS3, Vanilla JavaScript
- **Responsive**: Optimized for desktop/admin dashboard use
- **No Dependencies**: Pure HTML/CSS/JS, no frameworks required

## Validation Rules

### VPA Validation
- Must end with bank-specific handle:
  - HDFC: `@validhdfc`
  - ICICI: `@validicici`
  - Axis: `@validaxis`

### IFSC Validation
- Must start with bank-specific prefix:
  - HDFC: `HDFC`
  - ICICI: `ICIC`
  - Axis: `UTIB`
- 11 characters total

### Account Number
- Required for HDFC and Axis banks
- Optional for ICICI (can use MID instead)
- 9-18 digits

### ICICI MID
- Required only for ICICI Bank
- 15-digit merchant identifier

## Workflow Screens

1. **Dashboard** - Main entry point with "New Instrument Request" button
2. **Merchant Verification** - Search and verify merchant details
3. **Terminal Type Selection** - Choose UPI One-Time, Autopay, or Both
4. **Bank Configuration** - _(Skipped - data collected in modal)_
5. **Review & Submit** - Final review before QC submission
6. **QC Review** - Quality check approval/rejection
7. **Success** - Confirmation and tracking

## Use Cases

- **Primary**: OC217 terminal procurement for SEBI-regulated merchants
- **Secondary**: Template for other feature-specific terminal requests

## Notes

- Each bank generates a separate IIR (Internal Instrument Request)
- Maker-checker workflow: BankingOps Agent creates → QC Lead approves
- Settlement types: DS (Direct Settlement) vs Non-DS

## Version History

- **v1.0** - Initial multi-bank sequential configuration
- **v2.0** - Dropdown-based bank selection with inline field configuration

---

**Last Updated**: March 2026
**Owner**: Terminal & Routing POD, Razorpay Payments Platform
