# HTML Tables: Usage, Anatomy & Best Practices

> [!ABSTRACT] Quick Summary
> HTML tables are designed **strictly for displaying tabular data** (statistics, pricing models, comparison matrixes, schedules). They should **never** be used to layout web pages—modern CSS tools like **Flexbox** and **Grid** handle page layouts today.

---

## 1. When to Use (and Avoid) Tables

| Use HTML Tables For 🟢           | Do NOT Use HTML Tables For 🔴          |
| :------------------------------- | :------------------------------------- |
| Multi-column structured data     | Web page layouts or grid positioning   |
| Financial reports and statistics | Form alignment or UI component layouts |
| Comparison charts and schedules  | Styling decorative elements            |

> [!WARNING] Why Avoid Tables for Page Layouts?
> Back in the 1990s, developers used `<table>` tags to position elements because CSS layout tools didn't exist yet. Today, this practice:
> - **Destroys Accessibility:** Screen readers misinterpret the page layout as data relationships.
> - **Breaks Responsiveness:** Tables are notoriously difficult to make fluid on mobile screens.
> - **Creates Code Bloat:** Generates unnecessary nested elements.

---

## 2. Table Hierarchy & Element Structure

HTML tables follow a strict semantic tree structure:

```text
<table> (Root Container)
├── <thead> (Header Section)
│   └── <tr> (Table Row)
│       └── <th> (Header Cell)
├── <tbody> (Body Section / Data)
│   └── <tr> (Table Row)
│       ├── <th> (Row Label - optional)
│       └── <td> (Data Cell)
└── <tfoot> (Footer Section / Meta & Summaries)
    └── <tr> (Table Row)
        └── <td> / <th>
```

### Element Breakdown
* `<table>`: The wrapper for the entire table structure.
* `<thead>`: Groups the heading content at the top of the table.
* `<tbody>`: Encloses the main data content rows.
* `<tfoot>`: Encloses footer notes, totals, or publication metadata.
* `<tr>` *(Table Row)*: Defines a horizontal row of cells.
* `<th>` *(Table Header)*: Defines a header cell (bold and centered by default; holds labels).
* `<td>` *(Table Data)*: Defines a standard data cell holding values.

---

## 3. Practical Code Examples

### A. Minimal Boilerplate Template

```html
<table>
  <thead>
    <tr>
      <th scope="col">Header Column 1</th>
      <th scope="col">Header Column 2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Row 1 Label</th>
      <td>Row 1 Data</td>
    </tr>
    <tr>
      <th scope="row">Row 2 Label</th>
      <td>Row 2 Data</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <td colspan="2">Footer metadata or copyright note.</td>
    </tr>
  </tfoot>
</table>
```

---

### B. Real-World Example: U.S. Bureau of Labor Statistics

```html
<table id="quickfacts">
  <thead>
    <tr>
      <!-- colspan="2" makes this cell span across 2 columns -->
      <th colspan="2">Quick Facts: Software Developers, Quality Assurance Analysts, and Testers</th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <th scope="row">2023 Median Pay</th>
      <td>
        $130,160 per year
        <br>$62.58 per hour
      </td>
    </tr>
    <tr>
      <th scope="row">Typical Entry-Level Education</th>
      <td>Bachelor's degree</td>
    </tr>
    <tr>
      <th scope="row">Work Experience in a Related Occupation</th>
      <td>None</td>
    </tr>
    <tr>
      <th scope="row">On-the-job Training</th>
      <td>None</td>
    </tr>
    <tr>
      <th scope="row">Number of Jobs, 2022</th>
      <td>1,795,300</td>
    </tr>
    <tr>
      <th scope="row">Job Outlook, 2022-32</th>
      <td>25% (Much faster than average)</td>
    </tr>
    <tr>
      <th scope="row">Employment Change, 2022-32</th>
      <td>451,200</td>
    </tr>
  </tbody>

  <tfoot>
    <tr>
      <td colspan="2">Source: U.S. Bureau of Labor Statistics</td>
    </tr>
  </tfoot>
</table>
```

---

## 4. Key Developer Insights & Best Practices

> [!TIP] Pro Tip 1: Semantic Tables vs. `<div>` Tag Soup
> Some developers try to build tables using `<div>` elements styled with CSS grid. **Avoid this when dealing with real tabular data!** Native `<table>` elements carry built-in accessibility semantics that tell screen readers how rows and columns relate to one another.

> [!TIP] Pro Tip 2: Use the `scope` Attribute for Accessibility
> Always specify `scope="col"` or `scope="row"` on `<th>` elements:
> - `<th scope="col">`: Tells screen readers this header applies to the whole column below it.
> - `<th scope="row">`: Tells screen readers this header applies to the horizontal row next to it.

> [!TIP] Pro Tip 3: Making Tables Mobile Responsive
> Native HTML tables don't shrink gracefully on small screens. The standard practice is to wrap the table in a container `div` and use CSS overflow:
> ```html
> <div style="overflow-x: auto;">
>   <table> ... </table>
> </div>
> ```