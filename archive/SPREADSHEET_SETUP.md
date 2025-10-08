# 📊 Testing Event Spreadsheet Setup Guide

## 🎯 **Overview**
This guide explains how to create the Google Sheet for the AI Greatness Torch testing event with dropdown menus, data validation, and automated features.

## 📋 **Sheet Structure**

### **Sheet 1: Issue Tracker** (Main data collection)
### **Sheet 2: Group Assignments** (Lookup sheet for tester assignments)
### **Sheet 3: Dashboard** (Automated summaries and reports)

---

## 🛠 **Step-by-Step Setup Instructions**

### **1. Create New Google Sheet**
1. Go to [sheets.google.com](https://sheets.google.com)
2. Click "Blank" to create a new spreadsheet
3. Rename the spreadsheet: "AI Greatness Torch - Testing Event [Date]"

### **2. Set Up Sheet Tabs**
1. Rename "Sheet1" to "Issue Tracker"
2. Add new sheet: "Group Assignments"
3. Add new sheet: "Dashboard"

---

## 📝 **Sheet 1: Issue Tracker Setup**

### **Column Headers** (Row 1)
```
A1: S. No
B1: Tester Name
C1: Group
D1: Test Case/Feature
E1: Device/Browser
F1: Description
G1: Steps to Reproduce
H1: Expected Result
I1: Actual Result
J1: Screen Shot 
K1: Status
```

### **Data Validation Setup**

#### **Column C: Group** (Dropdown)
1. Select column C (C2:C1000)
2. Go to Data → Data Validation
3. Criteria: "List of items"
4. Enter: `1-Homepage/Navigation,2-Authentication,3-AI Chat,4-Blog/Pre-Order`
5. Check "Show dropdown list in cell"

#### **Column D: Feature** (Dropdown - depends on Group)
1. Select column D (D2:D1000)
2. Go to Data → Data Validation
3. Criteria: "List from a range"
4. Enter range: `=INDIRECT("Features_" & C2)` (this will reference named ranges based on group)

#### **Column E: Severity** (Dropdown)
1. Select column E (E2:E1000)
2. Go to Data → Data Validation
3. Criteria: "List of items"
4. Enter: `Critical,High,Medium,Low`

#### **Column F: Issue Type** (Dropdown)
1. Select column F (F2:F1000)
2. Go to Data → Data Validation
3. Criteria: "List of items"
4. Enter: `Functionality,Performance,UI/UX,Security,Data,Other`

#### **Column K: Device/Browser** (Dropdown)
1. Select column K (K2:K1000)
2. Go to Data → Data Validation
3. Criteria: "List of items"
4. Enter: `Chrome Desktop,Firefox Desktop,Safari Desktop,Edge Desktop,Chrome Mobile,Safari Mobile,Other`

#### **Column L: Status** (Dropdown)
1. Select column L (L2:L1000)
2. Go to Data → Data Validation
3. Criteria: "List of items"
4. Enter: `Open,In Review,Confirmed,Fixed,Duplicate,Invalid`

#### **Column M: Lead Review** (Dropdown)
1. Select column M (M2:M1000)
2. Go to Data → Data Validation
3. Criteria: "List of items"
4. Enter: `Pending,Validated,Needs More Info,Rejected`

### **Named Ranges for Features** (Required for dependent dropdowns)

#### **Features_Group1** (Homepage/Navigation)
1. In a separate area (e.g., columns O:P), create:
   ```
   O1: Features_Group1
   O2: Parallax Scrolling
   O3: Navigation Menu
   O4: Mobile Responsiveness
   O5: Page Loading
   O6: Interactive Elements
   O7: Cross-browser Compatibility
   ```
2. Select O2:O7 → Data → Named ranges → "Features_Group1"

#### **Features_Group2** (Authentication)
```
Features_Group2:
- User Registration
- User Login
- Password Reset (if available)
- Session Management
- Role-based Access
- Account Settings
- Logout Functionality
```

#### **Features_Group3** (AI Chat)
```
Features_Group3:
- Chat Interface
- AI Response Quality
- Response Time
- Conversation Persistence
- Error Handling
- Mobile Chat Experience
- Message History
```

#### **Features_Group4** (Blog/Pre-Order)
```
Features_Group4:
- Blog Article Display
- Comment System
- Pre-order Form
- Payment Processing
- Order Confirmation
- Blog Search/Filter
- Admin Blog Management
```

### **Automatic Timestamps**
1. Select column A (A2:A1000)
2. Enter formula in A2: `=IF(B2<>"", IF(A2="", NOW(), A2), "")`
3. Copy formula down the column

### **Conditional Formatting**
1. **Critical Issues**: Format row red if E2="Critical"
2. **High Issues**: Format row orange if E2="High"
3. **Open Status**: Format row yellow if L2="Open"

---

## 👥 **Sheet 2: Group Assignments Setup**

### **Column Headers** (Row 1)
```
A1: Group Number
B1: Group Name
C1: Lead Name
D1: Tester Names
E1: Tester Count
```

### **Sample Data**
```
A2: 1    B2: Homepage/Navigation    C2: Shikha Bhandari    D2: (testers add names here)    E2: =COUNTA(SPLIT(D2, ", "))
A3: 2    B3: Authentication         C3: Sai Kolluri        D3: (testers add names here)    E3: =COUNTA(SPLIT(D3, ", "))
A4: 3    B4: AI Chat                C4: Srini Jhasthy      D4: (testers add names here)    E4: =COUNTA(SPLIT(D4, ", "))
A5: 4    B5: Blog/Pre-Order         C5: Alok Sharan        D5: (testers add names here)    E5: =COUNTA(SPLIT(D5, ", "))
```

### **Instructions for Testers** (Add below the table)
```
F1: Instructions for Testers:
F2: 1. Find your preferred group above
F3: 2. Add your name to the "Tester Names" column
F4: 3. Separate multiple names with commas
F5: 4. Introduce yourself to your group lead
F6: 5. The tester count will update automatically
```

---

## 📊 **Sheet 3: Dashboard Setup**

### **Issue Summary Section** (A1:B10)
```
A1: Issue Summary
A2: Total Issues
A3: Critical Issues
A4: High Issues
A5: Medium Issues
A6: Low Issues
A7: Open Issues
A8: In Review Issues
A9: Fixed Issues
A10: Completion Rate

B2: =COUNT('Issue Tracker'!A:A)-1
B3: =COUNTIF('Issue Tracker'!E:E,"Critical")
B4: =COUNTIF('Issue Tracker'!E:E,"High")
B5: =COUNTIF('Issue Tracker'!E:E,"Medium")
B6: =COUNTIF('Issue Tracker'!E:E,"Low")
B7: =COUNTIF('Issue Tracker'!L:L,"Open")
B8: =COUNTIF('Issue Tracker'!L:L,"In Review")
B9: =COUNTIF('Issue Tracker'!L:L,"Fixed")
B10: =IFERROR(B9/B2,"No issues yet")
```

### **Issues by Group Section** (D1:E6)
```
D1: Issues by Group
D2: Group 1 (Homepage)
D3: Group 2 (Auth)
D4: Group 3 (Chat)
D5: Group 4 (Blog/Pre-Order)
D6: Total

E2: =COUNTIF('Issue Tracker'!C:C,"1-Homepage/Navigation")
E3: =COUNTIF('Issue Tracker'!C:C,"2-Authentication")
E4: =COUNTIF('Issue Tracker'!C:C,"3-AI Chat")
E5: =COUNTIF('Issue Tracker'!C:C,"4-Blog/Pre-Order")
E6: =SUM(E2:E5)
```

### **Lead Progress Section** (G1:H6)
```
G1: Lead Progress
G2: Shikha Bhandari (Group 1)
G3: Sai Kolluri (Group 2)
G4: Srini Jhasthy (Group 3)
G5: Alok Sharan (Group 4)
G6: Overall Progress

H2: ='Group Assignments'!E2
H3: ='Group Assignments'!E3
H4: ='Group Assignments'!E4
H5: ='Group Assignments'!E5
H6: =SUM(H2:H5)
```

### **Charts Section** (Starting at J1)
1. **Pie Chart**: Issue severity distribution (use B3:B6)
2. **Bar Chart**: Issues by group (use D2:E5)
3. **Line Chart**: Status distribution (use B7:B9)

---

## 🔧 **Advanced Features**

### **Data Validation with Custom Formulas**
For more complex validation, you can use custom formulas in data validation rules.

### **Protected Ranges**
1. Protect the header rows and formulas
2. Allow anyone to edit data entry rows
3. Protect the dashboard from accidental edits

### **Conditional Formatting Rules**
- Highlight rows based on severity
- Color-code based on status
- Flag issues that need lead review

---

## 📤 **Sharing Instructions**

### **Make Sheet Publicly Accessible**
1. Click "Share" button
2. Change permissions to "Anyone with the link can edit"
3. Copy the share link for the event

### **Pre-Event Checklist**
- [ ] All dropdown menus working
- [ ] Named ranges created
- [ ] Formulas calculating correctly
- [ ] Conditional formatting applied
- [ ] Charts displaying properly
- [ ] Sheet shared with edit permissions
- [ ] Backup copy created

---

## 🆘 **Troubleshooting**

### **Common Issues**
- **Dropdowns not showing**: Check data validation ranges
- **Formulas not working**: Verify sheet names and cell references
- **Named ranges missing**: Recreate named ranges
- **Sharing problems**: Ensure "Anyone with link can edit"

### **Quick Fixes**
- Refresh the page if formulas aren't updating
- Check that sheet names match exactly (case-sensitive)
- Verify that named ranges include all required cells

---

*Spreadsheet Setup Guide Version: 1.0 | Last Updated: October 7, 2025*</content>
<parameter name="filePath">/Users/chuckchekuri/projects/ai-greatness-torch-website/docs/stress-test/SPREADSHEET_SETUP.md