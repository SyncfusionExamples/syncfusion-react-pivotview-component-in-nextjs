# 📊 Getting Started — React Pivot Table Component (Syncfusion EJ2) + Next.js

[![License](https://img.shields.io/badge/license-SEE%20LICENSE%20IN%20license-blue.svg)](https://www.syncfusion.com/content/downloads/syncfusion_license.pdf)
[![Nextjs](https://img.shields.io/badge/Nextjs-16.1.6-blue.svg)](https://nextjs.org/)
[![Last Updated](https://img.shields.io/github/last-commit/SyncfusionExamples/syncfusion-react-pivotview-component-in-nextjs.svg)](https://github.com/SyncfusionExamples/syncfusion-react-pivotview-component-in-nextjs/commits)
[![Syncfusion Version](https://img.shields.io/badge/Syncfusion%20EJ2-LTS-green.svg)](https://www.syncfusion.com/react-components/)
[![Node.js](https://img.shields.io/badge/Node.js-LTS-green.svg)](https://nodejs.org/)
[![npm](https://img.shields.io/badge/npm-v10%2B-blue.svg)](https://www.npmjs.com/)

A small Next.js sample showcasing how to integrate the Syncfusion React Pivot Table (PivotView) component with the Next.js App Router. This repo demonstrates a client-side `app/page.tsx` usage, sample datasource and theme imports so you can run the demo locally in minutes. 🚀

## 🔍 Quick overview

- What: Example Next.js app that integrates the Syncfusion React Pivot Table (`@syncfusion/ej2-react-pivotview`).
- Why: Shows how to use Syncfusion interactive components with the Next.js App Router (client components + CSS imports).
- Who: Frontend developers building data-visualization dashboards using React + Next.js.

## ✨ Key Features

| Feature | Description | Benefit |
|---------|-------------|---------|
| 🎯 **Field List Interface** | Dynamically add, remove, and rearrange data fields at runtime | Empowers end-users to customize reports without code modifications |
| 📊 **Flexible Data Binding** | Supports relational data binding with hierarchical structures | Handle complex multi-dimensional business data |
| 🧮 **Calculated Fields** | Create custom formulas combining multiple data fields | Advanced data analysis and business metric computation |
| 💱 **Data Formatting** | Display values in currency, percentages, and custom formats | Professional presentation of numerical data |
| ↕️ **Multi-Level Sorting** | Sort by multiple fields with ascending/descending control | Enhanced data exploration and trend analysis |
| 🔗 **Advanced Filtering** | Filter by single or multiple criteria across all dimensions | Focused data analysis and drill-down exploration |
| 📱 **Responsive Design** | Adapts seamlessly to desktop, tablet, and mobile screens | Universal accessibility across all devices |
| 📤 **Export Functionality** | Export pivot table data to Excel and PDF formats | Generate shareable reports and archives |
| 🎨 **Theme Support** | Multiple Tailwind and Bootstrap themes available | Consistent branding and visual customization |
| ⚡ **Performance Optimized** | Efficient rendering with virtual scrolling | Handle large datasets without performance degradation |


## ✅ Highlights

- Ready-to-run demo with sample `pivotData`.
- Uses Syncfusion module injection (`CalculatedField`, `FieldList`).
- Shows theme / CSS imports to `app/globals.css` for consistent styling.

## 🔧 Prerequisites

- Node.js 18 LTS or later
- npm (or yarn)

## 🚀 Quick start

Clone, install and run the app locally:

```bash
git clone https://github.com/SyncfusionExamples/syncfusion-react-pivotview-component-in-nextjs
cd syncfusion-react-pivotview-component-in-nextjs
npm install
npm run dev
```

Open http://localhost:3000 to view the running sample.

---

## 📁 What’s included

- `app/datasource.tsx` — sample `pivotData` used by the demo.
- `app/page.tsx` — client component mounting `PivotViewComponent` and injecting services.
- `app/globals.css` — recommended place to add Syncfusion theme CSS imports.

## 🔌 How this sample was prepared (key steps)

1. Install the Syncfusion PivotView package:

```bash
npm install @syncfusion/ej2-react-pivotview --save
```

2. Import Syncfusion theme CSS into `app/globals.css` (example Tailwind3 theme imports):

```css
@import '../node_modules/@syncfusion/ej2-base/styles/tailwind3.css';
@import '../node_modules/@syncfusion/ej2-buttons/styles/tailwind3.css';
@import '../node_modules/@syncfusion/ej2-dropdowns/styles/tailwind3.css';
@import '../node_modules/@syncfusion/ej2-grids/styles/tailwind3.css';
@import '../node_modules/@syncfusion/ej2-inputs/styles/tailwind3.css';
@import '../node_modules/@syncfusion/ej2-lists/styles/tailwind3.css';
@import '../node_modules/@syncfusion/ej2-navigations/styles/tailwind3.css';
@import '../node_modules/@syncfusion/ej2-popups/styles/tailwind3.css';
@import '../node_modules/@syncfusion/ej2-splitbuttons/styles/tailwind3.css';
@import '../node_modules/@syncfusion/ej2-calendars/styles/tailwind3.css';
@import '../node_modules/@syncfusion/ej2-react-pivotview/styles/tailwind3.css';
/* add other component CSS as needed */
```

3. Make `app/page.tsx` a client component and mount `PivotViewComponent`:

```tsx
'use client'
import { CalculatedField, FieldList, Inject, PivotViewComponent } from '@syncfusion/ej2-react-pivotview';
import { DataSourceSettingsModel } from '@syncfusion/ej2-pivotview/src/model/datasourcesettings-model';
import { pivotData } from './datasource';

export default function Home() {
	const dataSourceSettings: DataSourceSettingsModel = {
		columns: [{ name: 'Year', caption: 'Production Year' }, { name: 'Quarter' }],
		dataSource: pivotData as any[],
		expandAll: false,
		filters: [],
		drilledMembers: [{ name: 'Country', items: ['Germany'] }],
		formatSettings: [{ name: 'Amount', format: 'C0' }],
		rows: [{ name: 'Country' }, { name: 'Products' }],
		values: [{ name: 'Sold', caption: 'Units Sold' }, { name: 'Amount', caption: 'Sold Amount' }]
	};

	return (
		<>
			<h2>Syncfusion React Pivot Table Component</h2>
			<PivotViewComponent id='PivotView' height={350} dataSourceSettings={dataSourceSettings} allowCalculatedField={true} showFieldList={true}><Inject services={[CalculatedField, FieldList]} />
			</PivotViewComponent>
		</>
	)
}
```

4. Provide sample `pivotData` in `app/datasource.tsx` (array of objects) — the demo ships with this file.

---

## ⚙️ Configuration & customization

- Theme: Swap the Tailwind3 CSS imports to a different Syncfusion theme file if you prefer (e.g., `fabric.css`, `material.css`).
- Localization: Use Syncfusion localization utilities if needed.
- Lazy-loading: Consider dynamic imports for PivotView if server-side rendering is used elsewhere.

## 🧩 Files structure (important files)

- `app/datasource.tsx` — sample data
- `app/page.tsx` — demo page (client component)
- `app/globals.css` — place to import Syncfusion themes
- `next.config.js`, `package.json`, `tsconfig.json` — project configs

---

## 🛠 Troubleshooting

- If components don’t style correctly, ensure the theme CSS is imported into `app/globals.css` and there are no conflicting global rules.
- If interactive features fail, verify `app/page.tsx` includes `'use client'` at the top.

---

## 🤝 Contributing

We welcome contributions! Here's how you can help:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/amazing-feature`)
3. **Commit** your changes (`git commit -m 'Add amazing feature'`)
4. **Push** to the branch (`git push origin feature/amazing-feature`)
5. **Open** a Pull Request

---

## 📜 License & Support

### License

This project is licensed under the **Syncfusion Community License**. See the [Syncfusion License](https://www.syncfusion.com/content/downloads/syncfusion_license.pdf) for details.

### Support & Resources

- 📚 **Official Documentation:** [Syncfusion React PivotView](https://ej2.syncfusion.com/react/documentation/pivotview/nextjs-getting-started)
- 🎬 **Video Tutorials:** [Syncfusion YouTube Channel](https://www.youtube.com/c/SyncfusionInc)
- 💬 **Support Forum:** [Syncfusion Support](https://www.syncfusion.com/forums/react-js2)
- 🐛 **Report Issues:** [GitHub Issues](https://github.com/SyncfusionExamples/syncfusion-react-pivotview-component-in-nextjs/issues)
- 📧 **Contact Us:** support@syncfusion.com

### Additional Resources

- 🔗 [Syncfusion React Components](https://www.syncfusion.com/react-components/)
- 📖 [Syncfusion Community](https://www.syncfusion.com/forums/react-js2)
- 🎯 [Demo Sample](https://ej2.syncfusion.com/nextjs/demos/tailwind3/pivot-table/overview)

---

## ⚡ Performance Tips

- ✅ Use **virtual scrolling** for large datasets (1000+ rows)
- ✅ Enable **lazy loading** for remote data sources
- ✅ Optimize **format settings** to reduce rendering overhead
- ✅ Use **filter and drill-down** to reduce data volume displayed
- ✅ Consider **server-side aggregation** for very large datasets

---