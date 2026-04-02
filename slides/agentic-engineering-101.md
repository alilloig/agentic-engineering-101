---
marp: true
paginate: true
footer: "Sui"
---

<!--
  AGENTIC ENGINEERING 101 — Single-session deck (40 min)
  Theme: Sui Dark
  Render: marp agentic-engineering-101.md --html
-->

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');

/* === BASE — DARK THEME (default) === */
section {
  background: #000000;
  color: #8B8B8B;
  font-family: 'Inter', 'SF Pro Display', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  font-size: 22px;
  font-weight: 400;
  line-height: 1.5;
  padding: 60px;
  width: 1280px;
  height: 720px;
  position: relative;
}

section h1 { color: #FFFFFF; font-size: 42px; font-weight: 700; line-height: 1.15; margin: 0 0 16px 0; letter-spacing: -0.02em; }
section h2 { color: #FFFFFF; font-size: 32px; font-weight: 600; line-height: 1.25; margin: 0 0 12px 0; }
section h3 { color: #FFFFFF; font-size: 24px; font-weight: 600; line-height: 1.3; margin: 0 0 8px 0; }
section h4 { color: #8B8B8B; font-size: 20px; font-weight: 500; line-height: 1.4; margin: 0 0 8px 0; }
section p { margin: 0 0 12px 0; }
section strong { color: #FFFFFF; font-weight: 600; }
section em { color: #4DA2FF; font-style: normal; }
section a { color: #4DA2FF; text-decoration: none; }
section code { background: #1A1A1A; color: #4DA2FF; padding: 2px 6px; border-radius: 4px; font-size: 0.9em; }
section pre { background: #0A0A0A; border: 1px solid #3A3A3A; border-radius: 8px; padding: 20px; margin: 12px 0; }
section pre code { background: transparent; padding: 0; }
section ul, section ol { margin: 0 0 12px 0; padding-left: 24px; }
section li { margin-bottom: 6px; }
section li::marker { color: #4DA2FF; }
section blockquote { border-left: 3px solid #4DA2FF; padding-left: 16px; margin: 12px 0; color: #AAAAAA; }
section table { width: 100%; border-collapse: collapse; margin: 12px 0; }
section th { color: #FFFFFF; background: #000000; font-weight: 600; text-align: left; padding: 10px 16px; border-bottom: 2px solid #4DA2FF; }
section td { padding: 8px 16px; border-bottom: 1px solid #1A1A1A; background: #000000; }
section hr { border: none; border-top: 1px dashed #3A3A3A; margin: 24px 0; }

/* Pagination */
section::after { color: #FFFFFF; font-size: 12px; font-weight: 600; background: #4DA2FF; border-radius: 2px; padding: 2px 8px; }

/* Footer & Header */
section footer { color: #8B8B8B; font-size: 14px; position: absolute; bottom: 24px; left: 60px; }
section footer::before { content: ''; display: inline-block; width: 14px; height: 18px; background: url("data:image/svg+xml,%3Csvg width='300' height='384' viewBox='0 0 300 384' fill='none' xmlns='http://www.w3.org/2000/svg'%3E %3Cpath fill-rule='evenodd' clip-rule='evenodd' d='M240.057 159.914C255.698 179.553 265.052 204.39 265.052 231.407C265.052 258.424 255.414 284.019 239.362 303.768L237.971 305.475L237.608 303.31C237.292 301.477 236.929 299.613 236.502 297.749C228.46 262.421 202.265 232.134 159.148 207.597C130.029 191.071 113.361 171.195 108.985 148.586C106.157 133.972 108.258 119.294 112.318 106.717C116.379 94.1569 122.414 83.6187 127.549 77.2831L144.328 56.7754C147.267 53.1731 152.781 53.1731 155.719 56.7754L240.073 159.914H240.057ZM266.584 139.422L154.155 1.96703C152.007 -0.655678 147.993 -0.655678 145.845 1.96703L33.4316 139.422L33.0683 139.881C12.3868 165.555 0 198.181 0 233.698C0 316.408 67.1635 383.461 150 383.461C232.837 383.461 300 316.408 300 233.698C300 198.181 287.613 165.555 266.932 139.896L266.568 139.438L266.584 139.422ZM60.3381 159.472L70.3866 147.164L70.6868 149.439C70.9237 151.24 71.2239 153.041 71.5715 154.858C78.0809 189.001 101.322 217.456 140.173 239.496C173.952 258.724 193.622 280.828 199.278 305.064C201.648 315.176 202.059 325.129 201.032 333.835L200.969 334.372L200.479 334.609C185.233 342.05 168.09 346.237 149.984 346.237C86.4546 346.237 34.9484 294.826 34.9484 231.391C34.9484 204.153 44.4439 179.142 60.3065 159.44L60.3381 159.472Z' fill='%234DA2FF'/%3E %3C/svg%3E") no-repeat center/contain; margin-right: 5px; vertical-align: middle; }
section header { color: #4DA2FF; font-size: 14px; font-weight: 500; position: absolute; top: 24px; right: 60px; }

/* === WHITE / LIGHT THEME === */
section.white, section.light { background: #FFFFFF; color: #6B6B6B; }
section.white h1, section.light h1 { color: #000000; }
section.white h2, section.light h2 { color: #000000; }
section.white h3, section.light h3 { color: #000000; }
section.white h4, section.light h4 { color: #6B6B6B; }
section.white strong, section.light strong { color: #000000; }
section.white em, section.light em { color: #4DA2FF; font-style: normal; }
section.white code, section.light code { background: #F0F0F0; color: #4DA2FF; }
section.white pre, section.light pre { background: #F5F5F5; border: 1px solid #E0E0E0; }
section.white th, section.light th { color: #000000; background: #FFFFFF; border-bottom: 2px solid #4DA2FF; }
section.white td, section.light td { background: #FFFFFF; border-bottom: 1px solid #E8E8E8; }
section.white hr, section.light hr { border-top: 1px dashed #D0D0D0; }
section.white footer, section.light footer { color: #6B6B6B; }
section.white::after, section.light::after { color: #4DA2FF; background: rgba(77,162,255,0.08); }
section.white .col, section.light .col { border-top-color: #D0D0D0; }
section.white .card, section.light .card { background: #F5F5F5; border-color: #E8E8E8; }
section.white .card h4, section.light .card h4 { color: #000000; }
section.white .stat, section.light .stat { color: #000000; }
section.white .stat-large, section.light .stat-large { color: #000000; }
section.white .stat-label, section.light .stat-label { color: #6B6B6B; }

/* === GRID SYSTEM === */
section .grid { display: grid; gap: 24px; width: 100%; height: auto; }
section .col { display: flex; flex-direction: column; border-top: 1px dashed #3A3A3A; padding-top: 16px; }
section .col h3 { margin-bottom: 8px; }
section .col p { font-size: 18px; margin: 0; }

/* Category label */
section .category { display: inline-flex; align-items: center; gap: 6px; font-size: 11px; font-weight: 600; letter-spacing: 0.08em; text-transform: uppercase; color: #8B8B8B; font-family: 'Inter', monospace; margin-bottom: 8px; }
section .category::before { content: ''; display: inline-block; width: 8px; height: 8px; background: #4DA2FF; flex-shrink: 0; }
section.white .category, section.light .category { color: #6B6B6B; }

/* Droplet icon marker variant — use class="col icon-marker" */
section .col.icon-marker h3::before { content: ''; width: 20px; height: 20px; background: none; margin-right: 8px; background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none'%3E%3Cpath d='M12 2C12 2 5 10 5 14.5C5 18.09 8.13 21 12 21C15.87 21 19 18.09 19 14.5C19 10 12 2 12 2Z' stroke='%234DA2FF' stroke-width='1.5' fill='none'/%3E%3Cpath d='M12 18C14.21 18 16 16.21 16 14C16 11 12 6 12 6C12 6 8 11 8 14C8 16.21 9.79 18 12 18Z' stroke='%234DA2FF' stroke-width='1' fill='none'/%3E%3C/svg%3E"); background-size: contain; background-repeat: no-repeat; }

/* Stats */
section .stat { color: #FFFFFF; font-size: 48px; font-weight: 700; line-height: 1; margin-bottom: 4px; }
section .stat-label { color: #8B8B8B; font-size: 16px; }
section .stat-large { color: #FFFFFF; font-size: 72px; font-weight: 700; line-height: 1; margin-bottom: 8px; }

/* Cards */
section .card { background: #0A0A0A; border: 1px solid #1A1A1A; border-radius: 8px; padding: 16px 20px; margin-bottom: 8px; }
section .card h4 { color: #FFFFFF; margin: 0 0 4px 0; }
section .card p { margin: 0; font-size: 16px; }

/* Icon container */
section .icon { width: 48px; height: 48px; margin-bottom: 12px; }
section .icon img { width: 100%; height: 100%; object-fit: contain; }

/* === LAYOUT: lead === */
section.lead { display: flex; flex-direction: column; justify-content: flex-end; padding-bottom: 80px; }
section.lead h1 { font-size: 64px; font-weight: 700; margin-bottom: 16px; letter-spacing: -0.03em; }
section.lead p { font-size: 24px; color: #8B8B8B; max-width: 70%; }
section.white.lead p, section.light.lead p { color: #6B6B6B; }

/* === LAYOUT: cover-gradient === */
section.cover-gradient { display: flex; flex-direction: column; justify-content: flex-start; padding-top: 60px; color: #FFFFFF; }
section.cover-gradient h1 { font-size: 56px; font-weight: 700; color: #FFFFFF; letter-spacing: -0.03em; margin-bottom: 16px; position: relative; z-index: 1; }
section.cover-gradient p { font-size: 22px; color: rgba(255,255,255,0.85); max-width: 60%; position: relative; z-index: 1; }
section.cover-gradient footer { display: none; }
section.cover-gradient::after { display: block !important; content: '' !important; position: absolute; bottom: 40px; right: 60px; width: 140px; height: 55px; background: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 220 80'%3E%3Cg transform='translate(0,2) scale(0.19)'%3E%3Cpath fill-rule='evenodd' clip-rule='evenodd' d='M240.057 159.914C255.698 179.553 265.052 204.39 265.052 231.407C265.052 258.424 255.414 284.019 239.362 303.768L237.971 305.475L237.608 303.31C237.292 301.477 236.929 299.613 236.502 297.749C228.46 262.421 202.265 232.134 159.148 207.597C130.029 191.071 113.361 171.195 108.985 148.586C106.157 133.972 108.258 119.294 112.318 106.717C116.379 94.1569 122.414 83.6187 127.549 77.2831L144.328 56.7754C147.267 53.1731 152.781 53.1731 155.719 56.7754L240.073 159.914H240.057ZM266.584 139.422L154.155 1.96703C152.007-0.655678 147.993-0.655678 145.845 1.96703L33.4316 139.422L33.0683 139.881C12.3868 165.555 0 198.181 0 233.698C0 316.408 67.1635 383.461 150 383.461C232.837 383.461 300 316.408 300 233.698C300 198.181 287.613 165.555 266.932 139.896L266.568 139.438L266.584 139.422ZM60.3381 159.472L70.3866 147.164L70.6868 149.439C70.9237 151.24 71.2239 153.041 71.5715 154.858C78.0809 189.001 101.322 217.456 140.173 239.496C173.952 258.724 193.622 280.828 199.278 305.064C201.648 315.176 202.059 325.129 201.032 333.835L200.969 334.372L200.479 334.609C185.233 342.05 168.09 346.237 149.984 346.237C86.4546 346.237 34.9484 294.826 34.9484 231.391C34.9484 204.153 44.4439 179.142 60.3065 159.44L60.3381 159.472Z' fill='white'/%3E%3C/g%3E%3Ctext x='72' y='57' font-family='Inter,sans-serif' font-size='52' font-weight='400' fill='white'%3ESui%3C/text%3E%3C/svg%3E") no-repeat center/contain; color: transparent; font-size: 0; padding: 0; border-radius: 0; z-index: 1; }

/* === LAYOUT: cover-stripes === */
section.cover-stripes { display: flex; flex-direction: column; justify-content: flex-start; padding-top: 60px; color: #FFFFFF; }
section.cover-stripes h1 { font-size: 56px; font-weight: 700; color: #FFFFFF; letter-spacing: -0.03em; margin-bottom: 16px; position: relative; z-index: 1; }
section.cover-stripes p { font-size: 22px; color: rgba(255,255,255,0.85); max-width: 60%; position: relative; z-index: 1; }
section.cover-stripes footer { display: none; }
section.cover-stripes::after { display: block !important; content: '' !important; position: absolute; bottom: 40px; right: 60px; width: 140px; height: 55px; background: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 220 80'%3E%3Cg transform='translate(0,2) scale(0.19)'%3E%3Cpath fill-rule='evenodd' clip-rule='evenodd' d='M240.057 159.914C255.698 179.553 265.052 204.39 265.052 231.407C265.052 258.424 255.414 284.019 239.362 303.768L237.971 305.475L237.608 303.31C237.292 301.477 236.929 299.613 236.502 297.749C228.46 262.421 202.265 232.134 159.148 207.597C130.029 191.071 113.361 171.195 108.985 148.586C106.157 133.972 108.258 119.294 112.318 106.717C116.379 94.1569 122.414 83.6187 127.549 77.2831L144.328 56.7754C147.267 53.1731 152.781 53.1731 155.719 56.7754L240.073 159.914H240.057ZM266.584 139.422L154.155 1.96703C152.007-0.655678 147.993-0.655678 145.845 1.96703L33.4316 139.422L33.0683 139.881C12.3868 165.555 0 198.181 0 233.698C0 316.408 67.1635 383.461 150 383.461C232.837 383.461 300 316.408 300 233.698C300 198.181 287.613 165.555 266.932 139.896L266.568 139.438L266.584 139.422ZM60.3381 159.472L70.3866 147.164L70.6868 149.439C70.9237 151.24 71.2239 153.041 71.5715 154.858C78.0809 189.001 101.322 217.456 140.173 239.496C173.952 258.724 193.622 280.828 199.278 305.064C201.648 315.176 202.059 325.129 201.032 333.835L200.969 334.372L200.479 334.609C185.233 342.05 168.09 346.237 149.984 346.237C86.4546 346.237 34.9484 294.826 34.9484 231.391C34.9484 204.153 44.4439 179.142 60.3065 159.44L60.3381 159.472Z' fill='white'/%3E%3C/g%3E%3Ctext x='72' y='57' font-family='Inter,sans-serif' font-size='52' font-weight='400' fill='white'%3ESui%3C/text%3E%3C/svg%3E") no-repeat center/contain; color: transparent; font-size: 0; padding: 0; border-radius: 0; z-index: 1; }

/* === LAYOUT: section-break (decorative filler — title hidden) === */
section.section-break { display: flex; flex-direction: column; justify-content: center; align-items: center; text-align: center; }
section.section-break h1 { display: none; }
section.section-break footer, section.section-break::after { display: none; }

/* === LAYOUT: chapter — topic/section intro, title top-left === */
section.chapter { display: flex; flex-direction: column; justify-content: flex-start; align-items: flex-start; padding-top: 60px; color: #FFFFFF; }
section.chapter h1 { font-size: 48px; font-weight: 700; color: #FFFFFF; letter-spacing: -0.02em; position: relative; z-index: 1; }
section.chapter p { font-size: 22px; color: rgba(255,255,255,0.85); max-width: 60%; position: relative; z-index: 1; }
section.chapter footer, section.chapter::after { display: none; }

/* === LAYOUT: quote === */
section.quote { display: flex; flex-direction: column; justify-content: center; align-items: center; text-align: center; padding: 80px 120px; }
section.quote p { font-size: 36px; font-weight: 500; color: #FFFFFF; line-height: 1.4; max-width: 900px; position: relative; z-index: 1; }
section.quote footer, section.quote::after { display: none; }
section.white.quote p, section.light.quote p { color: #000000; }

/* === LAYOUT: toc === */
section.toc { display: grid; grid-template-columns: 1fr 1fr; gap: 0; padding: 0; }
section.toc .toc-left { display: flex; flex-direction: column; justify-content: center; align-items: center; padding: 60px; position: relative; overflow: hidden; }
section.toc .toc-left h1 { font-size: 56px; font-weight: 700; color: #FFFFFF; position: relative; z-index: 1; }
section.toc .toc-right { display: flex; flex-direction: column; justify-content: center; padding: 60px; }
section.toc .toc-item { display: flex; align-items: baseline; gap: 16px; padding: 12px 0; font-size: 22px; font-weight: 600; }
section.toc .toc-item .toc-num { font-size: 18px; font-weight: 700; color: #8B8B8B; min-width: 30px; }
section.toc .toc-item .toc-label { color: #FFFFFF; font-weight: 600; }
section.white.toc .toc-item .toc-label, section.light.toc .toc-item .toc-label { color: #000000; }

/* === LAYOUT: content === */
section.content { display: flex; flex-direction: column; justify-content: flex-start; align-items: flex-start; }
section.content h1 { font-size: 42px; margin-bottom: 16px; }
section.content p { max-width: 45%; font-size: 20px; }

/* === COLUMN LAYOUTS === */
section.cols-4 .grid { grid-template-columns: repeat(4, 1fr); margin-top: 24px; }
section.cols-3 .grid { grid-template-columns: repeat(3, 1fr); margin-top: 24px; }
section.cols-2-center { text-align: center; }
section.cols-2-center h1 { text-align: center; width: 100%; }
section.cols-2-center .grid { grid-template-columns: repeat(2, 1fr); margin-top: 24px; text-align: center; }
section.cols-2-center .col { align-items: center; }

section.grid-2x2 { text-align: center; }
section.grid-2x2 h1 { text-align: center; width: 100%; }
section.grid-2x2 .grid { grid-template-columns: repeat(2, 1fr); grid-template-rows: repeat(2, auto); margin-top: 24px; text-align: center; }
section.grid-2x2 .col { align-items: center; }

section.cols-4-minimal .grid { grid-template-columns: repeat(4, 1fr); margin-top: 40px; }
section.cols-4-minimal .col { padding-top: 24px; }
section.cols-4-minimal .col p { display: none; }

section.fullbleed { padding: 0; }
section.fullbleed img { width: 100%; height: 100%; object-fit: cover; }

section.cols-4-icon .grid { grid-template-columns: repeat(4, 1fr); margin-top: 24px; }
section.cols-4-icon .col h3::before { display: none; }

/* === STATS LAYOUTS === */
section.cols-4-stats .grid { grid-template-columns: repeat(4, 1fr); margin-top: 24px; }
section.cols-4-stats .col { text-align: left; border-top: 1px dashed #3A3A3A; padding-top: 16px; }
section.cols-4-stats .stat { font-size: 48px; color: #FFFFFF; }
section.cols-4-stats .stat-label { font-size: 18px; color: #8B8B8B; }
section.white.cols-4-stats .col, section.light.cols-4-stats .col { border-top-color: #D0D0D0; }
section.white.cols-4-stats .stat, section.light.cols-4-stats .stat { color: #000000; }

section.stats-side { display: grid; grid-template-columns: 1fr 1fr; gap: 40px; align-items: center; }
section.stats-side .content { display: flex; flex-direction: column; }
section.stats-side .stats { display: flex; flex-direction: column; gap: 24px; }
section.stats-side .stat-row { border-top: 1px dashed #3A3A3A; padding-top: 16px; }
section.white.stats-side .stat-row, section.light.stats-side .stat-row { border-top-color: #D0D0D0; }

section.stats-left { display: flex; flex-direction: column; justify-content: center; }
section.stats-left .grid { grid-template-columns: 1fr; gap: 8px; max-width: 50%; }
section.stats-left .col { border-top: 1px dashed #3A3A3A; padding-top: 16px; }
section.stats-left .stat-large { font-size: 80px; color: #FFFFFF; }
section.stats-left .stat-label { font-size: 20px; color: #8B8B8B; margin-top: 4px; }
section.white.stats-left .stat-large, section.light.stats-left .stat-large { color: #000000; }
section.white.stats-left .col, section.light.stats-left .col { border-top-color: #D0D0D0; }

/* === SPLIT/LIST LAYOUTS === */
section.split-right { display: flex; flex-direction: column; align-items: flex-end; justify-content: flex-start; text-align: left; }
section.split-right h1, section.split-right p { max-width: 55%; }

section.list-right { display: grid; grid-template-columns: 1fr 1fr; gap: 40px; align-items: start; }
section.list-right .content { display: flex; flex-direction: column; justify-content: center; height: 100%; }
section.list-right .cards { display: flex; flex-direction: column; gap: 8px; }

/* === SPLIT-IMAGE === */
section.split-image { display: grid; grid-template-columns: 1fr 1fr; gap: 0; padding: 0; }
section.split-image .content { display: flex; flex-direction: column; justify-content: flex-start; padding: 60px; }
section.split-image .images { display: grid; grid-template-columns: 1fr; grid-template-rows: 1fr 1fr; gap: 0; }
section.split-image .images img { width: 100%; height: 100%; object-fit: cover; }

/* === SPLIT-IMAGE-LEFT === */
section.split-image-left { display: grid; grid-template-columns: 1fr 1fr; gap: 0; padding: 0; }
section.split-image-left .images { display: grid; grid-template-columns: 1fr; grid-template-rows: 1fr 1fr; gap: 0; }
section.split-image-left .images img { width: 100%; height: 100%; object-fit: cover; }
section.split-image-left .content { display: flex; flex-direction: column; justify-content: flex-start; padding: 60px; }

/* === PRODUCT GRIDS === */
section.grid-products .grid { grid-template-columns: repeat(4, 1fr); grid-template-rows: repeat(2, auto); gap: 16px; margin-top: 24px; }
section.grid-products .col { border-top: none; padding-top: 12px; text-align: center; align-items: center; }
section.grid-products .col h3::before { display: none; }
section.grid-products .icon { width: 56px; height: 56px; margin: 0 auto 8px auto; }

section.grid-images .grid { grid-template-columns: repeat(4, 1fr); grid-template-rows: repeat(2, 1fr); gap: 12px; margin-top: 24px; height: calc(100% - 100px); }
section.grid-images .col { border-top: none; padding-top: 0; background: #0A0A0A; border-radius: 8px; overflow: hidden; }
section.grid-images .col img { width: 100%; height: 100%; object-fit: cover; }
section.white.grid-images .col, section.light.grid-images .col { background: #F0F0F0; }

/* === PRODUCT HERO SLIDES === */
section.product-seal, section.product-deepbook, section.product-walrus, section.product-suins, section.product-sui, section.product-mysticeti, section.product-nautilus, section.product-passkey, section.product-zklogin, section.product-move { display: flex; flex-direction: column; align-items: center; justify-content: center; text-align: center; overflow: hidden; }
section.product-seal::before, section.product-deepbook::before, section.product-walrus::before, section.product-suins::before, section.product-sui::before, section.product-mysticeti::before, section.product-nautilus::before, section.product-passkey::before, section.product-zklogin::before, section.product-move::before { position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%); font-size: 160px; font-weight: 700; color: rgba(255,255,255,0.06); text-transform: capitalize; white-space: nowrap; pointer-events: none; z-index: 0; }
section.product-seal::before { content: 'Seal'; }
section.product-deepbook::before { content: 'Deepbook'; }
section.product-walrus::before { content: 'Walrus'; }
section.product-suins::before { content: 'SuiNS'; }
section.product-sui::before { content: 'Sui'; font-size: 220px; }
section.product-mysticeti::before { content: 'Mysticeti'; }
section.product-nautilus::before { content: 'Nautilus'; }
section.product-passkey::before { content: 'Passkey'; }
section.product-zklogin::before { content: 'zkLogin'; }
section.product-move::before { content: 'Move'; font-size: 200px; }
section.product-seal > *, section.product-deepbook > *, section.product-walrus > *, section.product-suins > *, section.product-sui > *, section.product-mysticeti > *, section.product-nautilus > *, section.product-passkey > *, section.product-zklogin > *, section.product-move > * { position: relative; z-index: 1; }
section.product-seal h1, section.product-deepbook h1, section.product-walrus h1, section.product-suins h1, section.product-sui h1, section.product-mysticeti h1, section.product-nautilus h1, section.product-passkey h1, section.product-zklogin h1, section.product-move h1 { font-size: 56px; margin-top: 16px; }

/* === PRODUCT CONTENT SLIDES === */
section.product-seal-content, section.product-deepbook-content, section.product-walrus-content, section.product-suins-content, section.product-sui-content, section.product-mysticeti-content, section.product-nautilus-content, section.product-passkey-content, section.product-zklogin-content, section.product-move-content { display: grid; grid-template-columns: 1fr 1fr; gap: 40px; align-items: center; }
section.product-seal-content h1, section.product-deepbook-content h1, section.product-walrus-content h1, section.product-suins-content h1, section.product-sui-content h1, section.product-mysticeti-content h1, section.product-nautilus-content h1, section.product-passkey-content h1, section.product-zklogin-content h1, section.product-move-content h1 { font-size: 64px; letter-spacing: -0.03em; }
section.product-seal-content .content, section.product-deepbook-content .content, section.product-walrus-content .content, section.product-suins-content .content, section.product-sui-content .content, section.product-mysticeti-content .content, section.product-nautilus-content .content, section.product-passkey-content .content, section.product-zklogin-content .content, section.product-move-content .content { display: flex; flex-direction: column; }
section.product-seal-content .illustration, section.product-deepbook-content .illustration, section.product-walrus-content .illustration, section.product-suins-content .illustration, section.product-sui-content .illustration, section.product-mysticeti-content .illustration, section.product-nautilus-content .illustration, section.product-passkey-content .illustration, section.product-zklogin-content .illustration, section.product-move-content .illustration { display: flex; align-items: center; justify-content: center; }
section.product-seal-content .illustration img, section.product-deepbook-content .illustration img, section.product-walrus-content .illustration img, section.product-suins-content .illustration img, section.product-sui-content .illustration img, section.product-mysticeti-content .illustration img, section.product-nautilus-content .illustration img, section.product-passkey-content .illustration img, section.product-zklogin-content .illustration img, section.product-move-content .illustration img { max-width: 100%; max-height: 400px; object-fit: contain; }

/* Utility */
section .no-border { border-top: none !important; padding-top: 0 !important; }
section .accent { color: #4DA2FF; }
section .badge { display: inline-block; background: rgba(77,162,255,0.15); color: #4DA2FF; padding: 4px 12px; border-radius: 16px; font-size: 14px; font-weight: 500; }
</style>

<!-- _class: cover-gradient -->
<!-- _paginate: false -->

![bg](assets/images/sui-cover.png)

# Agentic Engineering 101

Agentic development from first principles

---

<!-- _class: toc -->
<!-- _paginate: false -->

<div class="toc-left" style="background: url('assets/images/sui-cover.png') center/cover;">

# Agenda

</div>
<div class="toc-right">

<div class="toc-item"><span class="toc-num">01</span><span class="toc-label">ML Basics for Agentic Development</span></div>
<div class="toc-item"><span class="toc-num">02</span><span class="toc-label">Installation</span></div>
<div class="toc-item"><span class="toc-num">03</span><span class="toc-label">Basic Usage</span></div>
<div class="toc-item"><span class="toc-num">04</span><span class="toc-label">Day 0 Setup</span></div>
<div class="toc-item"><span class="toc-num">05</span><span class="toc-label">Expanding Claude Code</span></div>

</div>

---

<!-- SECTION 1: ML BASICS -->

<!-- _class: chapter -->
<!-- _paginate: false -->

![bg](assets/images/sui-cover.png)

# 01 — ML Basics for Agentic Development

---

<!-- _class: cols-2-center -->

# Tokens Explained

<div class="grid">
<div class="col">

<span class="category">WHAT THEY ARE</span>

### Subword Chunks

LLMs don't read words or characters -- they process *tokens*, subword pieces. "unhappiness" becomes three tokens; "the" is always one.

</div>
<div class="col">

<span class="category">WHY IT MATTERS</span>

### Everything Is Budgeted

Every prompt, file read, tool response, and reply is measured in tokens against a finite context window.

</div>
</div>

---

# Token Counting

The practical heuristic for estimating token usage:

- **1 token** ~ 4 characters of English text
- **1 token** ~ 0.75 words
- **1,000 words** ~ 1,300 tokens
- Every prompt, file read, and tool result counts against your limit

You are always budgeting. The context window is the total token budget for a conversation.

---

<!-- _class: cols-2-center -->

# Transformer Architecture

<div class="grid">
<div class="col">

<span class="category">ARCHITECTURE</span>

### Decoder-Only

Claude uses a decoder-only transformer -- it processes the entire conversation and predicts the next token, repeatedly, until the response is complete.

</div>
<div class="col">

<span class="category">KEY INNOVATION</span>

### Self-Attention

The mechanism that lets the model decide which parts of its input are most relevant to each other. This is what gives the model its apparent understanding.

</div>
</div>

---

# Why Transformers Matter

Self-attention is what makes Claude useful as a coding agent:

- Holds CLAUDE.md instructions, file contents, tool results, and your message -- *all at once*
- Computes which pieces are relevant to the current decision
- But attention is not free -- more tokens means weaker focus on any single detail
- This is the fundamental tension you manage in every Claude Code session

---

# Context Windows

The total number of tokens a model can process in a single conversation -- input and output combined.

- **Working memory**: everything the model knows must fit inside the window
- Once full, oldest content is dropped or summarized
- No background recall -- if it's not in the window, it doesn't exist
- Agentic loops compound cost: each think-act-observe cycle adds to the total

---

<!-- _class: cols-3 -->

# Claude Model Comparison

<div class="grid">
<div class="col">

<span class="category">FLAGSHIP</span>

### Opus 4.6

- *1M tokens* context
- 128k output
- $5 / $25 per MTok
- May 2025 cutoff

</div>
<div class="col">

<span class="category">BALANCED</span>

### Sonnet 4.6

- *1M tokens* context
- 64k output
- $3 / $15 per MTok
- Aug 2025 cutoff

</div>
<div class="col">

<span class="category">FAST</span>

### Haiku 4.5

- *200k tokens* context
- 64k output
- $1 / $5 per MTok
- Feb 2025 cutoff

</div>
</div>

---

# The 1M Token Window

Opus 4.6 and Sonnet 4.6 support 1M tokens natively -- a 5x increase over previous models.

- **750,000 words** in a single conversation
- Hold an entire medium-sized codebase at once
- Longer agentic sessions before context pressure forces a reset
- Work across more files without losing track of earlier reads

Previous-generation models (Opus 4.5, 4.1, 4.0) were limited to 200k tokens.

---

<!-- _class: cols-3 -->

# Context Rot

<div class="grid">
<div class="col">

<span class="category">WHAT IT IS</span>

### Quality Degradation

Output quality degrades as the context fills. Attention must spread across all tokens -- early instructions get diluted by intermediate results.

</div>
<div class="col">

<span class="category">SYMPTOMS</span>

### How to Spot It

Vague outputs, forgotten instructions, repetition, confidently wrong details blended from noisy context.

</div>
<div class="col">

<span class="category">MITIGATION</span>

### How to Fight It

**Compaction** -- auto-summarize history. **Scoping** -- read only what you need. **Fresh sessions** -- start over for long tasks.

</div>
</div>

---

<!-- SECTION 2: INSTALLATION -->

<!-- _class: chapter -->
<!-- _paginate: false -->

![bg](assets/images/sui-cover.png)

# 02 — Installation

---

# CLI Prerequisites

Before installing Claude Code, ensure you have:

- **OS**: macOS 13.0+, Windows 10 1809+, or Ubuntu 20.04+ / Debian 10+
- **RAM**: 4 GB minimum
- **Shell**: Bash, Zsh, PowerShell, or CMD
- **Windows**: Install Git for Windows first
- **Account**: Paid Claude plan (Pro, Max, Teams, or Enterprise)

> Node.js is no longer required. The current install methods are native binaries.

---

<!-- _class: cols-3 -->

# Three Install Methods

<div class="grid">
<div class="col">

<span class="category">RECOMMENDED</span>

### Native Install

```
curl -fsSL \
  https://claude.ai/install.sh \
  | bash
```

Auto-updates in background. No dependencies.

</div>
<div class="col">

<span class="category">ALTERNATIVE</span>

### Homebrew

```
brew install --cask \
  claude-code
```

Does not auto-update. Run `brew upgrade` periodically.

</div>
<div class="col">

<span class="category">DEPRECATED</span>

### npm

```
npm install -g \
  @anthropic-ai/claude-code
```

Slower, requires Node.js 18+. Migrate to native binary.

</div>
</div>

---

# Verify Your Installation

Two commands to confirm everything works:

```bash
claude --version
# Expected: 2.1.85 (Claude Code) or newer

claude doctor
# Diagnoses auth, auto-updates, and system config
```

Then start Claude Code in any project:

```bash
cd your-project && claude
```

You will be prompted to authenticate in your browser on first launch.

---

<!-- _class: cols-2-center -->

# Desktop App

<div class="grid">
<div class="col">

<span class="category">INSTALL</span>

### macOS (Intel + Apple Silicon)

Download the `.dmg` from claude.ai, drag to Applications, and launch. Sign in with your Claude account.

</div>
<div class="col">

<span class="category">FEATURES</span>

### Same Engine, Visual Interface

Review diffs visually, run multiple sessions side by side, schedule tasks, kick off cloud sessions. Shares CLAUDE.md and settings with CLI.

</div>
</div>

---

<!-- _class: cols-3 -->

# Chrome Extension

<div class="grid">
<div class="col">

<span class="category">INSTALL</span>

### Add to Chrome

Search "Claude in Chrome" in the Chrome Web Store. Click Add to Chrome. Works with Chrome and Edge.

</div>
<div class="col">

<span class="category">CONNECT</span>

### Enable in CLI

```bash
claude --chrome
```

Or run `/chrome` in an existing session.

</div>
<div class="col">

<span class="category">CAPABILITIES</span>

### What It Unlocks

Live debugging, web app testing, authenticated site access, data extraction, browser task automation.

</div>
</div>

---

# Verification Checklist

Before moving on, confirm all three surfaces:

| Surface | Check | Expected Result |
|---------|-------|-----------------|
| **CLI** | `claude --version` | Version number displayed |
| **Desktop** | Open app, sign in | Code tab loads |
| **Chrome** | `claude --chrome` then `/chrome` | Connection status OK |

If any step fails: run `claude doctor` or consult the troubleshooting guide.

---

<!-- SECTION 3: BASIC USAGE -->

<!-- _class: chapter -->
<!-- _paginate: false -->

![bg](assets/images/sui-cover.png)

# 03 — Basic Usage

---

# Context in Practice

Every interaction consumes tokens from your context budget:

- **Prompts** you send
- **Tool definitions** loaded each turn
- **File contents** Claude reads
- **Tool results** from bash, grep, etc.
- **Conversation history** accumulated over turns

Claude Code operates on models with up to 1M tokens -- which sounds enormous until a few large files and a long conversation fill it up.

---

<!-- _class: cols-3 -->

# Five Prompting Tips

<div class="grid">
<div class="col">

<span class="category">TIP 1-2</span>

### Lead with Intent

"Add validation to the signup form" beats a long preamble.

### Be Specific

"Fix the test in `auth.test.ts`" beats "fix the tests."

</div>
<div class="col">

<span class="category">TIP 3-4</span>

### Skip Filler

"Please kindly help me with" wastes tokens. Just state the task.

### One Task per Prompt

Compound requests increase drift. Break them up or use plan mode.

</div>
<div class="col">

<span class="category">TIP 5</span>

### Reference Files Directly

Mention the file path rather than describing where it might be.

Every token in your prompt is one less token for code and reasoning.

</div>
</div>

---

<!-- _class: cols-2-center -->

# CLAUDE.md Explained

<div class="grid">
<div class="col">

<span class="category">PURPOSE</span>

### Persistent Instructions

A markdown file read at the start of every session. Tells Claude what this project is and how you want things done.

</div>
<div class="col">

<span class="category">CONTENTS</span>

### What Goes In It

Project structure, coding conventions, build commands, architectural decisions, workflow constraints. Keep under 200 lines.

</div>
</div>

---

<!-- _class: cols-3 -->

# CLAUDE.md Scopes

<div class="grid">
<div class="col">

<span class="category">SHARED</span>

### Project

`./CLAUDE.md` or `./.claude/CLAUDE.md`

Committed to source control. Project-specific standards the whole team follows.

</div>
<div class="col">

<span class="category">PERSONAL</span>

### User

`~/.claude/CLAUDE.md`

Your personal preferences across all projects on your machine.

</div>
<div class="col">

<span class="category">ENFORCED</span>

### Managed

System-level, set by IT.

Organization-wide instructions that cannot be overridden. Highest precedence.

</div>
</div>

---

# Settings Configuration

Four scopes with strict precedence (highest to lowest):

| Scope | Location | Shared? | Purpose |
|-------|----------|---------|---------|
| **Managed** | System-level (MDM) | By IT | Org-wide policies, cannot override |
| **Local** | `.claude/settings.local.json` | No | Machine-specific overrides |
| **Project** | `.claude/settings.json` | Yes | Team-shared repo settings |
| **User** | `~/.claude/settings.json` | No | Personal defaults |

Use `settings.local.json` for machine-specific overrides -- it is automatically gitignored.

---

<!-- _class: cols-3 -->

# Key Settings to Know

<div class="grid">
<div class="col">

<span class="category">SECURITY</span>

### permissions

Allow or deny tools and commands.

E.g., `Bash(npm run test *)` in the `allow` list.

</div>
<div class="col">

<span class="category">ENVIRONMENT</span>

### env

Environment variables applied every session.

E.g., `CLAUDE_AUTOCOMPACT_PCT_OVERRIDE`.

</div>
<div class="col">

<span class="category">QUALITY</span>

### effortLevel

`"low"`, `"medium"`, or `"high"` -- persists across sessions.

Supported on Opus 4.6 and Sonnet 4.6.

</div>
</div>

---

# Five Best Practices

1. **Start every new task in plan mode** -- prevents more wasted work than anything else
2. **Keep CLAUDE.md under 200 lines** -- split with imports or `.claude/rules/`
3. **Be explicit about boundaries** -- "Do not modify files outside `src/`"
4. **Use `/compact` when context gets heavy** -- summarizes history, re-reads CLAUDE.md
5. **Commit `.claude/settings.json` and CLAUDE.md** -- they are team resources

---

<!-- _class: cols-2-center -->

# /init and Plan Mode

<div class="grid">
<div class="col">

<span class="category">BOOTSTRAP</span>

### /init

Analyzes your codebase and generates a starter CLAUDE.md. If one exists, suggests improvements. A bootstrap, not a finished product.

</div>
<div class="col">

<span class="category">WORKFLOW</span>

### Plan Mode

Claude reads and proposes but does not edit. Review, give feedback, then execute. Cycle with `Shift+Tab` or start with `--permission-mode plan`.

</div>
</div>

---

# Plan -> Review -> Execute

**Always use plan mode when doing something new.**

This is the single most important workflow habit in Claude Code.

Without it, Claude jumps straight into editing. Wrong approach means wasted tokens and changes to undo. Plan mode costs almost nothing and catches misalignment before damage is done.

Use for: new features, unfamiliar code, complex debugging. Skip only for trivial tasks.

---

<!-- _class: cols-4 -->

# Permission Modes

<div class="grid">
<div class="col">

<span class="category">DEFAULT</span>

### default

Prompts for every edit and command. Safest while learning.

</div>
<div class="col">

<span class="category">BALANCED</span>

### acceptEdits

Auto-approves edits, prompts for shell commands. Best for daily work.

</div>
<div class="col">

<span class="category">SMART</span>

### auto

Classifier auto-approves safe ops, prompts for risky ones. Team plans only.

</div>
<div class="col">

<span class="category">LOCKED</span>

### dontAsk

Auto-denies everything not in allowlist. For CI and locked-down envs.

</div>
</div>

---

<!-- SECTION 4: DAY 0 SETUP -->

<!-- _class: chapter -->
<!-- _paginate: false -->

![bg](assets/images/sui-cover.png)

# 04 — Day 0 Setup

---

# Why Day 0 Matters

Before writing any code, spend ten minutes installing plugins that shape how Claude works for you.

- The marketplace has 100+ entries -- choosing the right starting set matters
- Three plugins are complementary -- install all of them
- They cover planning, analysis, and memory -- the gaps Claude cannot fill alone
- Everything else is either optional or already covered by these three

---

<!-- _class: cols-3 -->

# Three Essential Plugins

<div class="grid">
<div class="col">

<span class="category">233K+ INSTALLS</span>

### Superpowers

Composable skills framework. Planning, TDD, debugging, brainstorming, code review, skill authoring. **Install first.**

</div>
<div class="col">

<span class="category">55K+ INSTALLS</span>

### Claude Code Setup

Analyzes your codebase and recommends automations -- hooks, skills, MCPs, subagents -- tailored to your stack.

</div>
<div class="col">

<span class="category">92K+ INSTALLS</span>

### Claude MD Management

Audits and improves CLAUDE.md files. `/revise-claude-md` captures session learnings as reviewable diffs.

</div>
</div>

---

# Superpowers Deep Dive

Superpowers imposes discipline through structured methodologies:

- **TDD**: Strict red-green-refactor cycles -- tests must fail before implementation
- **Debugging**: Root cause investigation required before any fix is attempted
- **Brainstorming**: Socratic sessions that refine requirements -- hard gate prevents coding until design is approved
- **Planning**: `/writing-plans` and `/execute-plan` for structured implementation

Substantially replaces several standalone plugins (Commit Commands, Code Review, others).

---

# Covered by Superpowers

These plugins provide functionality that Superpowers partially or fully covers:

| Plugin | Installs | Overlap |
|--------|----------|---------|
| Commit Commands | 86k+ | `finishing-a-development-branch` covers commit/push/PR |
| Code Review | 169k+ | `requesting-code-review` provides single-agent review |
| Code Simplifier | 140k+ | No direct equivalent |
| Security Guidance | 87k+ | No direct equivalent |
| Learning Output Style | 23k+ | `brainstorming` partially overlaps |

---

# Standalone Highlights

Plugins worth knowing about even if Superpowers covers part of their function:

- **Code Review** (169k+) -- launches *5 parallel agents* for deeper analysis vs Superpowers' single-agent approach
- **Code Simplifier** (140k+) -- autonomous clarity and maintainability refinement with no Superpowers equivalent
- **Security Guidance** (87k+) -- pre-tool hook scanning for injection, XSS, and unsafe patterns with no Superpowers equivalent

Install separately only if you need their specific capabilities beyond what Superpowers provides.

---

<!-- SECTION 5: EXPANDING CLAUDE CODE -->

<!-- _class: chapter -->
<!-- _paginate: false -->

![bg](assets/images/sui-cover.png)

# 05 — Expanding Claude Code

---

<!-- _class: cols-2-center -->

# Skills and AGENTS.md

<div class="grid">
<div class="col">

<span class="category">SKILLS</span>

### SKILL.md Files

YAML frontmatter + prose instructions. No compiled code. Lives in `.claude/skills/`, `~/.claude/skills/`, or inside plugins.

Invoke with `/skill-name` or let Claude auto-match from description.

</div>
<div class="col">

<span class="category">AGENTS.md</span>

### Agent Role Catalog

Convention for cataloging reusable agent roles -- system prompts, model preferences, constraints. A cast list for team-based workflows.

Requires `CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS=1`.

</div>
</div>

---

# Built-in Skill Examples

Skills that ship with Claude Code or common plugins:

| Skill | What It Does |
|-------|-------------|
| `/batch` | Parallel large-scale changes across worktrees |
| `/claude-api` | Building apps with the Anthropic SDK |
| `/debug` | Session log analysis for troubleshooting |
| `/loop` | Recurring prompt execution on an interval |
| `/simplify` | Three parallel agents review recent changes |

`disable-model-invocation: true` restricts a skill to manual-only invocation, keeping context lean.

---

<!-- _class: cols-3 -->

# Hooks Explained

<div class="grid">
<div class="col">

<span class="category">EVENTS</span>

### 25+ Lifecycle Points

SessionStart, UserPromptSubmit, PreToolUse, PostToolUse, Stop, PreCompact, Notification, SessionEnd, and more.

</div>
<div class="col">

<span class="category">HANDLERS</span>

### Four Types

**Command** (shell script), **HTTP** (POST to URL), **Prompt** (LLM yes/no), **Agent** (subagent with tools).

</div>
<div class="col">

<span class="category">CONFIGURE</span>

### settings.json

Define under `hooks` key: event + optional `matcher` regex + handler(s). E.g., block `rm -rf` via PreToolUse.

</div>
</div>

---

<!-- _class: cols-2-center -->

# Plugins and Marketplace

<div class="grid">
<div class="col">

<span class="category">WHAT THEY ARE</span>

### Bundled Packages

Skills, commands, hooks, agents, and MCP servers in a single installable unit. Namespace prefix prevents conflicts.

</div>
<div class="col">

<span class="category">ANATOMY</span>

### Plugin Structure

`.claude-plugin/plugin.json` manifest plus `skills/`, `commands/`, `agents/`, `hooks/`, and `.mcp.json` directories.

</div>
</div>

---

<!-- _class: cols-3 -->

# MCPs: USB-C for AI

<div class="grid">
<div class="col">

<span class="category">STANDARD</span>

### Open Protocol

MCP connects AI tools to external data and services. Built once, works everywhere -- Claude Code, VS Code, Cursor, ChatGPT.

</div>
<div class="col">

<span class="category">TRANSPORTS</span>

### stdio and HTTP

**stdio** for local processes, **HTTP** for remote services. Legacy SSE is deprecated. Configure via `claude mcp add` or `.mcp.json`.

</div>
<div class="col">

<span class="category">INTEGRATIONS</span>

### Common Servers

Chrome DevTools (live debugging), Linear and Notion (project management), custom API wrappers. Plugins can bundle MCP servers.

</div>
</div>

---

<!-- _class: cols-4 -->

# Context Window Impact

<div class="grid">
<div class="col">

<span class="category">LIGHTWEIGHT</span>

### Skills

Descriptions load ~2% of window. Full content only on invocation.

</div>
<div class="col">

<span class="category">MINIMAL</span>

### Hooks

Run externally. Minimal context impact unless they inject messages.

</div>
<div class="col">

<span class="category">ADDITIVE</span>

### MCP Tools

Definitions added every turn. 5 servers x 20 tools adds up fast.

</div>
<div class="col">

<span class="category">COMBINED</span>

### Plugins

All layers at once. Enable what you need, disable what you don't.

</div>
</div>

---

<!-- CLOSING -->

<!-- _class: quote -->
<!-- _paginate: false -->

![bg](assets/images/sui-cover.png)

Tokens are your budget. Attention is your scarcest resource. Every file read, tool call, and conversation turn is a spending decision. Build with that constraint, not against it.

---

<!-- _class: lead -->
<!-- _paginate: false -->

# Go Build Something

Agentic Engineering 101 -- Agentic development from first principles
