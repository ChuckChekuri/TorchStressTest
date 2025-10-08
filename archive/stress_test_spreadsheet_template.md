# Stress Testing Feedback Spreadsheet

## 📊 **Google Sheets Template**

**Template Link**: [Create a new Google Sheet and copy the structure below]

### **Sheet 1: Issue Tracker**

| Timestamp | Tester ID | Group | Test Case | Device/Browser | Severity | Issue Type | Description | Steps to Reproduce | Expected Result | Actual Result | Screenshots | Status | Assigned To | Resolution |
|-----------|-----------|-------|-----------|----------------|----------|------------|-------------|-------------------|------------------|---------------|-------------|--------|-------------|------------|
| 2025-10-06 09:00:00 | Tester001 | 1 | Homepage Parallax Scrolling | Chrome 120.0.6099.109 (Mac) | Medium | Performance | Parallax scrolling stutters on scene transitions | 1. Visit homepage<br>2. Scroll slowly through scenes<br>3. Observe transitions | Smooth 60fps scrolling | Noticeable stuttering | [Link] | Open |  |  |

### **Sheet 2: Summary Dashboard**

**A1:B10 - Issue Summary**
```
Total Issues: =COUNT('Issue Tracker'!A:A)-1
Critical Issues: =COUNTIF('Issue Tracker'!F:F,"Critical")
High Issues: =COUNTIF('Issue Tracker'!F:F,"High")
Medium Issues: =COUNTIF('Issue Tracker'!F:F,"Medium")
Low Issues: =COUNTIF('Issue Tracker'!F:F,"Low")
Open Issues: =COUNTIF('Issue Tracker'!L:L,"Open")
Resolved Issues: =COUNTIF('Issue Tracker'!L:L,"Fixed")
```

**D1:E10 - Issues by Group**
```
Group 1 (Homepage): =COUNTIF('Issue Tracker'!C:C,1)
Group 2 (Auth): =COUNTIF('Issue Tracker'!C:C,2)
Group 3 (Chat): =COUNTIF('Issue Tracker'!C:C,3)
Group 4 (Blog): =COUNTIF('Issue Tracker'!C:C,4)
Group 5 (Pre-order): =COUNTIF('Issue Tracker'!C:C,5)
Group 6 (Admin): =COUNTIF('Issue Tracker'!C:C,6)
Group 7 (Mobile): =COUNTIF('Issue Tracker'!C:C,7)
Group 8 (Performance): =COUNTIF('Issue Tracker'!C:C,8)
```

### **Sheet 3: Performance Metrics**

| Metric | Target | Actual | Status | Notes |
|--------|--------|--------|--------|-------|
| Homepage Load Time | < 3s |  |  |  |
| Chat Response Time | < 5s |  |  |  |
| Payment Processing | < 10s |  |  |  |
| Concurrent Users | 100+ |  |  |  |
| Error Rate | < 1% |  |  |  |

### **Sheet 4: User Experience Scores**

| Tester ID | Group | Ease of Navigation (1-5) | Feature Satisfaction (1-5) | Overall Experience (1-5) | Comments |
|-----------|-------|--------------------------|---------------------------|--------------------------|----------|
| Tester001 | 1 |  |  |  |  |

## 📋 **Data Validation Rules**

### **Severity Dropdown**
- Critical: System breaking, no workaround
- High: Major feature broken, poor workaround
- Medium: Feature impaired but usable
- Low: Minor annoyance, cosmetic issues

### **Issue Type Dropdown**
- Bug: Functional error
- Performance: Speed/loading issues
- UI: Visual/layout problems
- UX: Usability issues
- Feature: Missing functionality

### **Status Dropdown**
- Open: Newly reported
- In Progress: Being worked on
- Fixed: Resolved
- Won't Fix: By design or low priority
- Duplicate: Already reported

## 📊 **Charts to Create**

1. **Issues by Severity** (Pie Chart)
2. **Issues by Group** (Bar Chart)
3. **Issues Over Time** (Line Chart)
4. **Resolution Timeline** (Burndown Chart)

## 🔄 **Automated Calculations**

### **Average Resolution Time**
```
=AVERAGE(IF('Issue Tracker'!L:L="Fixed", 'Issue Tracker'!A:A - [Creation Date], ""))
```

### **Issue Aging**
```
=IF('Issue Tracker'!L:L="Open", TODAY() - DATEVALUE('Issue Tracker'!A:A), "")
```

## 📤 **Export Instructions**

1. **Daily Reports**: Filter by date, export as PDF
2. **Group Reports**: Filter by group number, export as CSV
3. **Executive Summary**: Use summary dashboard, export charts
4. **Complete Archive**: Export entire spreadsheet as XLSX

## 🔗 **Sharing Settings**

- **Editor Access**: Test coordinators and developers
- **Viewer Access**: All testers (for reference)
- **Comment Access**: All team members
- **Version History**: Keep enabled for audit trail

---

## 📱 **Mobile Access**

For testers using mobile devices:
1. Use Google Sheets mobile app
2. Enable offline mode for reliability
3. Take photos directly in app for screenshots
4. Use voice-to-text for detailed descriptions

---

**Template Version**: 1.0
**Last Updated**: October 6, 2025</content>
<parameter name="filePath">/Users/chuckchekuri/projects/ai-greatness-torch-website/stress_test_spreadsheet_template.md