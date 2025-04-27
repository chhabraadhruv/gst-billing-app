# GST Billing Application for Linux
## Installation and Usage Guide

This guide will help you set up and use the GST Billing Application, a desktop tool for creating and managing GST-compliant invoices in India.

## Prerequisites

- Linux operating system (Ubuntu, Debian, Fedora, etc.)
- Node.js 16.x or higher
- npm 7.x or higher

## Installation

### 1. Clone or download the repository

```bash
git clone https://github.com/yourusername/gst-billing-app.git
# or download and extract the zip file
cd gst-billing-app
```

### 2. Install dependencies

```bash
npm install
```

### 3. Run the application

```bash
npm start
```

### 4. Build a distributable package (optional)

```bash
npm run package
```

This will create a distributable package in the `dist` folder.

## Configuration

When you first launch the application, you should configure your company details:

1. Click on the "Settings" tab
2. Fill in your company details:
   - Company Name
   - GSTIN (GST Identification Number)
   - Address
   - Phone
   - Email
   - Default Jurisdiction
3. Click "Save Settings"

## Creating Invoices

### 1. Navigate to the "Create Invoice" tab

The application automatically loads with this tab open.

### 2. Fill in Invoice Details

- Invoice No. (automatically generated)
- Date (defaults to current date)
- Place of Supply (State and State Code)
- Transport (optional)
- Vehicle No. (optional)
- Reverse Charge (if applicable)

### 3. Add Customer Details

- Customer Name
- GSTIN
- Address

### 4. Add Items

Each invoice requires at least one item. For each item, enter:
- Description
- HSN/SAC Code
- Quantity
- Unit (Pcs, Kg, Ltr, Mtr)
- Price per unit

Click "Add Item" to add more items.

### 5. Set Tax Details

- Select the appropriate GST rate (0%, 5%, 12%, 18%, 28%)
- Check "Interstate Supply" if the customer is from a different state
- The application will automatically calculate CGST & SGST or IGST based on this selection

### 6. Save and Generate PDF

- Click "Save Invoice" to save the invoice to the database
- Click "Generate PDF" to create a printable PDF invoice

## Managing Invoices

### View Invoices

Navigate to the "View Invoices" tab to see all saved invoices. From here you can:
- View invoice details
- Print/generate PDF of existing invoices

## Tax Calculation Logic

- For intrastate supplies (within the same state):
  - CGST = (Tax Rate ÷ 2)% of taxable amount
  - SGST = (Tax Rate ÷ 2)% of taxable amount
  - IGST = Not applicable

- For interstate supplies (between different states):
  - CGST/SGST = Not applicable
  - IGST = (Tax Rate)% of taxable amount

## Data Storage

The application stores all data locally in the following files:

- `invoices.db`: All invoice data
- `customers.db`: Customer information
- `products.db`: Product catalog

These files are located in the application's user data directory.

## Additional Features

- **Auto-calculation**: The application automatically calculates amounts, taxes, and totals
- **Amount in Words**: Automatically converts the invoice amount to words
- **Multiple Units**: Support for different units of measurement
- **PDF Generation**: Creates professional, print-ready invoices

## Troubleshooting

### Common Issues

1. **Missing dependencies**: Ensure you have all required dependencies installed
   ```bash
   npm install
   ```

2. **Permission issues**: If you encounter permission errors, try running with elevated privileges
   ```bash
   sudo npm start
   ```

3. **PDF generation fails**: Make sure you have write permissions to the selected output directory

### Reporting Bugs

If you encounter any issues, please report them by creating an issue on the GitHub repository.

## Future Enhancements

- Customer database management
- Product catalog management
- Reports and analytics
- Data backup and restore
- Multiple currency support
- Invoice customization
