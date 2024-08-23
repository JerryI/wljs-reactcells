# React MDX cells renderer
This module renders MDX representation of WLJS Notebook cells using React and Docusaurus.

::__Warning__
This is a prototype!

## Examples
[Blog page](https://jerryi.github.io/wljs-docs/blog) of WLJS Docs

## Installation and usage
1. Clone this repo
2. Place it to `src/components/` of your Docusarurus project
3. Export to MDX your WLJS notebook using `Share button` 
4. Start your docusaurus server `npm start`

## Styles and JS libraries
It is up to you, what is to include and what is not
### Libraries
On step *3* in the modal window a list of used libraries will be shown. Remove unnecessary from the list (which is not used in your notebook) and add it to the header of your blog. One of the ways is use `headTags` property of your `docusaurus.config`

*for example*
```js
const scripts = [ //use CDN or host them locally
  "https://cdn.jsdelivr.net/gh/JerryI/wljs-interpreter@dev/src/interpreter.min.js",
  "https://cdn.jsdelivr.net/gh/JerryI/wljs-interpreter@dev/src/core.min.js",
  "https://cdn.jsdelivr.net/gh/JerryI/wljs-cells@dev/src/module.min.js",
  "https://cdn.jsdelivr.net/gh/JerryI/wljs-editor@dev/dist/kernel.min.js",
  "https://cdn.jsdelivr.net/gh/JerryI/wljs-editor@dev/src/boxes.min.js",  
  "https://cdn.jsdelivr.net/gh/JerryI/wljs-editor@dev/src/objects.min.js",
  "https://cdn.jsdelivr.net/gh/JerryI/wljs-js-support@dev/src/kernel.min.js",
  "https://cdn.jsdelivr.net/gh/JerryI/wljs-mermaid-support@dev/dist/kernel.min.js",
  "https://cdn.jsdelivr.net/gh/JerryI/wljs-sound@master/dist/kernel.min.js",  
  "https://cdn.jsdelivr.net/gh/JerryI/wljs-inputs@dev/dist/kernel.min.js",
  "https://cdn.jsdelivr.net/gh/JerryI/wljs-html-support@dev/src/kernel.min.js",
  "https://cdn.jsdelivr.net/gh/JerryI/wljs-sharedlib-d3@master/dist/kernel.min.js",
  "https://cdn.jsdelivr.net/gh/JerryI/wljs-graphics-d3@dev/dist/kernel.min.js",
  "https://cdn.jsdelivr.net/gh/JerryI/Mathematica-ThreeJS-graphics-engine@dev/dist/kernel.min.js",
].map((link) => {
  return {tagName: 'script', attributes: {
    type: 'module',
    src: link
  }}
});

...

const config = {
    ...

    headTags: scripts,
    ...
```

### Styles/CSS
It is up to a user, how to stylize the cells. WLJS cells is using TailwindCSS for styling, therefore most of classes are reusable utility classes

Here is some base styles used on the official blog page

*If you are using Tailwind, please, remove all utility classes*
<details>

```css
:root {
  --ifm-color-primary: #c4421a;
  --ifm-color-primary-dark: #4C566A;
  --ifm-color-primary-darker: #3B4252;
  --ifm-color-primary-darkest: #2E3440;
  --ifm-color-primary-light:  #B48EAD;
  --ifm-color-primary-lighter:    #5E81AC;
  --ifm-color-primary-lightest: #88C0D0;
  --ifm-color-primary-text: #242424;
  --ifm-color-primary-text-alt: #242424;
  --ifm-color-primary-button: #fffafa;
  --ifm-code-font-size: 95%;
  --docusaurus-highlighted-code-line-bg: rgba(0, 0, 0, 0.1);

  --editor-key-meta: #404740;
  --editor-key-keyword: #708;
  --editor-key-atom: #219;
  --editor-key-literal: #164;
  --editor-key-string: #a11;
  --editor-key-escape: #e40;
  --editor-key-variable: #00f;
  --editor-local-variable: #30a;
  --editor-key-type: #085;
  --editor-key-class: #167;
  --editor-special-variable: #256;
  --editor-key-property: #00c;
  --editor-key-comment: #940;
  --editor-key-invalid: #f00;
  
  --editor-outline: #696969;

  --editor-bracket-1: #5461c8;
  --editor-bracket-2: #c724b1;
  --editor-bracket-3: #e4002b;
  --editor-bracket-4: #ff6900;
  --editor-bracket-5: #978d00;
  --editor-bracket-6: #019e79;
  --editor-bracket-7: #008dc1;

  --editor-bracket-1-a: #5461c8; 
  --editor-bracket-2-a: #c724b1;
  --editor-bracket-3-a: #e4002b;
  --editor-bracket-4-a: #ff6900;
  --editor-bracket-5-a: #978d00;
  --editor-bracket-6-a: #019e79;
  --editor-bracket-7-a: #008dc1;  
}

.container table td {
  border: none;
  background-color:none;
  padding: 0.1em;
}

.container table tr {
  border: none;
  background-color:none;
  padding: 0.1em;
}

.wljscols {
  flex-direction: row;
}

@media screen and (max-width: 996px) {


  .wljscols {
    flex-direction: column;
  }
}

a {
  text-decoration: underline !important;
}


.cell-type-slide {
  background-color: hsl(191, 100%, 79%);
  color: rgba(55, 53, 47, 0.5);
}

.cell-type-slides {
  background-color: hsl(311, 100%, 79%);
  color: rgba(58, 28, 60, 0.5);
}  

.slide-number {
  bottom: 0;
  position: absolute;
  font-size: medium;
  right: 0;
  margin-right: 1em;
  margin-bottom: 0.5em;
}

:root {
  --markdown-h5: rgb(133, 0, 120);
  --markdown-h4: darkgreen;
  --markdown-h3: darkblue;  
  --markdown-h2: darkred;      
     
 }
 
 html[data-theme='dark'] {
  --markdown-h5: rgb(255, 173, 247);
  --markdown-h4: rgb(172, 255, 172);
  --markdown-h3: rgb(133, 133, 255);  
  --markdown-h2: rgb(255, 159, 159);      
 }
 
 
 .markdown>h5 {
  color: var(--markdown-h5) !important;   
 }
 
 .markdown>h4 {
  color: var(--markdown-h4) !important;   
 }
 
 .markdown>h3 {
  color: var(--markdown-h3) !important;   
 }
 
 .markdown>h2 {
  color: var(--markdown-h2) !important;   
 }

 .d3-controls {
  position: absolute;
  right: -1rem;
  padding: 0;
  opacity: 0.7;
  opacity: 0;
  cursor: pointer;
}

.frontend-view:hover .d3-controls {
  opacity: 0.6;
}

.graphics2d-controller {
  position:absolute;
  right:0;
  opacity:0;
}

.graphics2d-controller:hover {
  opacity:1;
}

.graphics3d-controller {
  position:absolute;
  right:0;
  opacity:0;
}

.graphics3d-controller:hover {
  opacity:1;
}

.dg.main {
  color:#777;
  text-shadow: none;
  border-radius: 4px;
  max-width:200px;
}


.dg.main li.cr.function {
  border-radius: 4px;
  border-bottom: none;
  margin-bottom:0.25rem;
  background-color: rgb(0 0 0 / 5%) !important;
  
}

.dg.main li.title {
  background-color: rgb(0 0 0 / 5%) !important;
  border-radius: 4px;
  border-bottom: none;
  margin-bottom:0.25rem;
  color: #777;
  text-shadow: none;
}

.dg.main .close-button.close-bottom {
  background-color: rgb(0 0 0 / 5%) !important;
  border-radius: 4px;
  border-bottom: none;
  font-weight: 500;
  color: #777;
  text-shadow: none;   
  max-width:200px; 
}

.dg.main li.cr.string {
  border-radius: 4px;
  border-bottom: none;
  margin-bottom:0.25rem;
  background-color: rgb(0 0 0 / 5%) !important; 
  color:#777;
  text-shadow: none;
}

.dg.main li.cr.boolean {
      border-radius: 4px;
  border-bottom: none;
  margin-bottom:0.25rem;
  background-color: rgb(0 0 0 / 5%) !important; 
  color:#777;
  text-shadow: none;
}


.cell-type-widget {
  display: inline-block;
  position: relative;
  border-radius: 4px;
  padding-left: 6px;
  padding-right: 6px;
  font-size: 0.75rem;
  /* line-height: 120%; */
  height:1.1rem;
  background-color: rgb(236, 236, 236);
  color: rgba(55, 53, 47, 0.5);
  opacity: 0.7;
}

.bg-d9 {
  background: #d9d9d9;
}

.bg-239 {
  background: rgb(239,239,239)
}

input::selection {
  color: #2fa1d6;
}

.sm-controls {
    font-family: system-ui;
    caret-color: auto;
}

.cgi-ico {
  position: absolute;
  width: 0.5rem;
  height: 0.5rem;
  border-radius: 999px;
  margin-right: 0.25rem;
  margin-top: 0.25rem;
  right: 0;
}

.text-gray-454 {
  --tw-text-opacity: 1;
  color: rgb(154 154 154 / var(--tw-text-opacity));
}

.bg-gray-454-half {
  --tw-text-opacity: 1;
  background: rgb(154 154 154 / 50%);
}

@media (min-width: 1024px) {
  .lg\:pl-70 {
    padding-left:16rem;
  }
}

@media (min-width: 768px) {
 .md\:pl-70 {
    padding-left: 16rem;
 }
}

@media (min-width: 768px) {
  .md\:w-70 {
    width:16rem;
  }
}

@media (min-width: 1024px) {
  .lg\:w-70 {
    width:16rem;
  }
}

.sc-b {
  scrollbar-width: 2px;
  scrollbar-color: rgba(15, 15, 15, 0.2) transparent;
}

.sc-b::-webkit-scrollbar {
  width: 2px;
  height: 2px;
}

.sc-b::-webkit-scrollbar-thumb {
  background: rgba(15, 15, 15, 0.2);
  border-radius: 5px;
}

.sc-b::-webkit-scrollbar-track {
  background-color: transparent;
}

.sc-b::-webkit-scrollbar-button {
  background-color: transparent;
  border-radius: 5px;
}


.cm-scroller::-webkit-scrollbar {
  width: 2px;
  height: 2px;
}

.cm-scroller::-webkit-scrollbar-thumb {
  background: rgba(15, 15, 15, 0.2);
  border-radius: 5px;
}

.cm-scroller::-webkit-scrollbar-track {
  background-color: transparent;
}

.cg-fix {
  height: auto;
}

.z-inf {
  z-index:110;
}

.h-titlebar {
  height: env(titlebar-area-height) !important;
}

[os="Windows"] .win\:h-titlebar {
  height: env(titlebar-area-height) !important;
}

[os="WindowsLegacy"] .owin\:h-titlebar {
  height: env(titlebar-area-height) !important;
}

[os="Windows"] .win\:sc-b {
  scrollbar-width: 2px;
  scrollbar-color: rgba(15, 15, 15, 0.2) transparent;
}

[os="Windows"] .win\:sc-b::-webkit-scrollbar {
  width: 2px;
  height: 2px;
}

[os="Windows"] .win\:sc-b::-webkit-scrollbar-thumb {
  background: rgba(15, 15, 15, 0.2);
  border-radius: 5px;
}

[os="Windows"] .win\:sc-b::-webkit-scrollbar-track {
  background-color: transparent;
}

[os="Windows"] .win\:sc-b::-webkit-scrollbar-button {
  background-color: transparent;
  border-radius: 5px;
}

[os="WindowsLegacy"] .owin\:sc-b {
  scrollbar-width: 2px;
  scrollbar-color: rgba(15, 15, 15, 0.2) transparent;
}

[os="WindowsLegacy"] .owin\:sc-b::-webkit-scrollbar {
  width: 2px;
  height: 2px;
}

[os="WindowsLegacy"] .owin\:sc-b::-webkit-scrollbar-thumb {
  background: rgba(15, 15, 15, 0.2);
  border-radius: 5px;
}

[os="WindowsLegacy"] .owin\:sc-b::-webkit-scrollbar-track {
  background-color: transparent;
}

[os="WindowsLegacy"] .owin\:sc-b::-webkit-scrollbar-button {
  background-color: transparent;
  border-radius: 5px;
}

[os="Unix"] .linux\:h-titlebar {
  height: env(titlebar-area-height) !important;
}

[os="Windows"][sidebar="hidden"] .win-zen\:pl-2 {
  padding-left: 0.5rem;
}

[os="Unix"][sidebar="hidden"] .linux-zen\:pl-2 {
  padding-left: 0.5rem;
}

[os="WindowsLegacy"][sidebar="hidden"] .owin-zen\:pl-2 {
  padding-left: 0.5rem;
}

[os="Browser"][sidebar="hidden"] .bro-zen\:pl-2 {
  padding-left: 0.5rem;
}

.ttint {
  transition: height 0.2s;
  background: #0056880f;
}

.h-fade-20 {
  mask-image: -webkit-gradient(linear, left top, left bottom, from(rgba(0,0,0,1)), to(rgba(0,0,0,0)));
  max-height: 4rem;
  overflow: hidden;
}

.frontend-view {
  display: inline-flex;
  vertical-align: sub;
  position: relative;
}

@keyframes pulse {
50% {
    opacity:.75
}
}

.frontend-view:empty::after {
width: 100%;
height: 100%;
padding: 0.20em;
padding-right:1em;
padding-left:1em;
border-radius:4px;
font-family:system-ui;
color:#444;
background: rgba(15, 15, 15, 0.2);
opacity: 0.25;
overflow: hidden;
font-size:x-small;
content: 'Loading...';
animation: pulse 2s cubic-bezier(.4,0,.6,1) infinite;
}

.cm-tooltip {
  font-family: var(--font-code-family);
  line-height:1.2;
}

.cm-focused {
  outline: none !important;
  background: var(--editor-selected-tint) !important;
  border-radius: 1px !important;
}


.cm-tooltip.cm-tooltip-autocomplete ul li {
font-family: var(--font-code-family);
}

.cm-tooltip-autocomplete.cm-tooltip{
border: 1px none #888 !important;
border-radius: 4px !important;
/* box-shadow: 0px 0px 10px #d4d4d47f !important; */
background-color: #fff !important;
}

.cm-tooltip.cm-tooltip-autocomplete > ul{
font-family: 'Hasklig' !important;
font-size: small !important;
padding: 0em;
white-space: nowrap;
overflow: hidden auto;
max-width: 700px;
max-width: min(700px, 95vw);
min-width: 250px;
max-height: 10em;
height: 100%;
list-style: none;
margin: 0;
padding: 0;
padding: 0.25rem !important;
overflow-y: hidden !important;
}

.cm-tooltip-autocomplete ul li[aria-selected] {
background: #00b5f8 !important;
color: white !important;

border-radius: 4px !important;
}

.cm-tooltip.cm-completionInfo {
position: absolute;
padding: 3px 9px;
font-size: small !important;
width: max-content;
max-width: 400px;
box-sizing: border-box;
border-radius: 4px !important;
border: 1px none #888 !important;
color: #333338;
border-radius: 4px !important;
box-shadow: 0px 0px 10px #d4d4d47f !important;
background-color: #fff !important;
}
.frame-box {
  border: 1px solid #000000;
}

sup.subscript-tail {
  line-height: normal;
  vertical-align: super;
  font-size: smaller;
  top:auto;
}

sub.subscript-tail {
line-height: normal;
vertical-align: sub;
font-size: smaller;
bottom:auto;
}

.subscript-tail {
  display: inline-block;
}

.fraction {
  display: inline-flex;
}

.matrix {
  display: inline-flex;
}

.fraction .container .enumenator {
  border-bottom:solid 1px;
}

.sqroot {
  display: inline-block;
  vertical-align: middle;
  border-top: 1px solid;
  border-left: 1px solid;
  transform: skew(-15deg);
  transform-origin: bottom left;
  margin: 0 10px;
  position: relative;
}

.sqroot:before {
  content: "";
  position: absolute;
  bottom: 0;
  height: 40%;
  width: 5px;
  left: -5px;
  border-top: 1px solid;
  border-right: 1px solid;
  transform: skew(30deg);
  transform-origin: bottom right;
}

.radicand {
  display: inline-block;
  padding-left: 0.5em;
  transform: skew(15deg);
}

.cell-type-js {
  background: #ffe846;
  color: #000000ad;
}

.cell-type-html {
  background: #b6d3ff;
  color: #0000009c;
}

.cell-type-slide {
  background-color: hsl(191, 100%, 79%);
  color: rgba(55, 53, 47, 0.5);
}

.cell-type-slides {
  background-color: hsl(311, 100%, 79%);
  color: rgba(58, 28, 60, 0.5);
}  

.cell-type-wlx {
  background-color: rgb(45 255 227 / 79%);
  color: #0000009c;
}

.cm-line {
  font-size: 15px !important;
}


.frontend-object {
  position: relative;
  font-size:small;
}

.g3d-label {
  font-size: x-small;
}

.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border-width: 0;
}

.pointer-events-none {
  pointer-events: none;
}

.pointer-events-auto {
  pointer-events: auto;
}

.visible {
  visibility: visible;
}

.fixed {
  position: fixed;
}

.absolute {
  position: absolute;
}

.relative {
  position: relative;
}

.sticky {
  position: sticky;
}

.inset-0 {
  inset: 0px;
}

.-top-6 {
  top: -1.5rem;
}

.bottom-0 {
  bottom: 0px;
}

.left-0 {
  left: 0px;
}

.right-0 {
  right: 0px;
}

.top-0 {
  top: 0px;
}

.top-6 {
  top: 1.5rem;
}

.z-0 {
  z-index: 0;
}

.z-10 {
  z-index: 10;
}

.z-40 {
  z-index: 40;
}

.z-50 {
  z-index: 50;
}

.m-4 {
  margin: 1rem;
}

.-mx-2 {
  margin-left: -0.5rem;
  margin-right: -0.5rem;
}

.mx-1 {
  margin-left: 0.25rem;
  margin-right: 0.25rem;
}

.mx-4 {
  margin-left: 1rem;
  margin-right: 1rem;
}

.mx-auto {
  margin-left: auto;
  margin-right: auto;
}

.my-1 {
  margin-top: 0.25rem;
  margin-bottom: 0.25rem;
}

.my-2 {
  margin-top: 0.5rem;
  margin-bottom: 0.5rem;
}

.my-auto {
  margin-top: auto;
  margin-bottom: auto;
}

.-ml-0 {
  margin-left: -0px;
}

.-ml-0\.5 {
  margin-left: -0.125rem;
}

.-mt-1 {
  margin-top: -0.25rem;
}

.mb-1 {
  margin-bottom: 0.25rem;
}

.mb-2 {
  margin-bottom: 0.5rem;
}

.mb-4 {
  margin-bottom: 1rem;
}

.mb-6 {
  margin-bottom: 1.5rem;
}

.mb-auto {
  margin-bottom: auto;
}

.ml-0 {
  margin-left: 0px;
}

.ml-0\.5 {
  margin-left: 0.125rem;
}

.ml-1 {
  margin-left: 0.25rem;
}

.ml-3 {
  margin-left: 0.75rem;
}

.ml-4 {
  margin-left: 1rem;
}

.ml-auto {
  margin-left: auto;
}

.mr-0 {
  margin-right: 0px;
}

.mr-0\.5 {
  margin-right: 0.125rem;
}

.mr-1 {
  margin-right: 0.25rem;
}

.mr-1\.5 {
  margin-right: 0.375rem;
}

.mr-2 {
  margin-right: 0.5rem;
}

.mr-3 {
  margin-right: 0.75rem;
}

.mr-8 {
  margin-right: 2rem;
}

.mr-auto {
  margin-right: auto;
}

.mt-0 {
  margin-top: 0px;
}

.mt-1 {
  margin-top: 0.25rem;
}

.mt-10 {
  margin-top: 2.5rem;
}

.mt-12 {
  margin-top: 3rem;
}

.mt-2 {
  margin-top: 0.5rem;
}

.mt-3 {
  margin-top: 0.75rem;
}

.mt-4 {
  margin-top: 1rem;
}

.mt-5 {
  margin-top: 1.25rem;
}

.mt-6 {
  margin-top: 1.5rem;
}

.mt-auto {
  margin-top: auto;
}

.block {
  display: block;
}

.inline-block {
  display: inline-block;
}

.inline {
  display: inline;
}

.flex {
  display: flex;
}

.inline-flex {
  display: inline-flex;
}

.hidden {
  display: none;
}

.h-1 {
  height: 0.25rem;
}

.h-1\.5 {
  height: 0.375rem;
}

.h-10 {
  height: 2.5rem;
}

.h-12 {
  height: 3rem;
}

.h-16 {
  height: 4rem;
}

.h-2 {
  height: 0.5rem;
}

.h-3 {
  height: 0.75rem;
}

.h-4 {
  height: 1rem;
}

.h-5 {
  height: 1.25rem;
}

.h-6 {
  height: 1.5rem;
}

.h-7 {
  height: 1.75rem;
}

.h-8 {
  height: 2rem;
}

.h-auto {
  height: auto;
}

.h-full {
  height: 100%;
}

.h-px {
  height: 1px;
}

.max-h-60 {
  max-height: 15rem;
}

.max-h-80 {
  max-height: 20rem;
}

.max-h-96 {
  max-height: 24rem;
}

.min-h-full {
  min-height: 100%;
}

.w-0 {
  width: 0px;
}

.w-1 {
  width: 0.25rem;
}

.w-1\.5 {
  width: 0.375rem;
}

.w-12 {
  width: 3rem;
}

.w-2 {
  width: 0.5rem;
}

.w-2\/4 {
  width: 50%;
}

.w-3 {
  width: 0.75rem;
}

.w-3\/6 {
  width: 50%;
}

.w-4 {
  width: 1rem;
}

.w-5 {
  width: 1.25rem;
}

.w-56 {
  width: 14rem;
}

.w-6 {
  width: 1.5rem;
}

.w-7 {
  width: 1.75rem;
}

.w-8 {
  width: 2rem;
}

.w-96 {
  width: 24rem;
}

.w-full {
  width: 100%;
}

.w-px {
  width: 1px;
}

.w-screen {
  width: 100vw;
}

.min-w-0 {
  min-width: 0px;
}

.max-w-2xl {
  max-width: 42rem;
}

.max-w-60 {
  max-width: 15rem;
}

.max-w-7xl {
  max-width: 80rem;
}

.max-w-full {
  max-width: 100%;
}

.max-w-lg {
  max-width: 32rem;
}

.max-w-xs {
  max-width: 20rem;
}

.flex-1 {
  flex: 1 1 0%;
}

.flex-auto {
  flex: 1 1 auto;
}

.flex-none {
  flex: none;
}

.flex-shrink-0 {
  flex-shrink: 0;
}

.shrink {
  flex-shrink: 1;
}

.shrink-0 {
  flex-shrink: 0;
}

.flex-grow {
  flex-grow: 1;
}

.grow {
  flex-grow: 1;
}

.grow-0 {
  flex-grow: 0;
}

.table-auto {
  table-layout: auto;
}

.border-spacing-x-0 {
  --tw-border-spacing-x: 0px;
  border-spacing: var(--tw-border-spacing-x) var(--tw-border-spacing-y);
}

.border-spacing-x-0\.5 {
  --tw-border-spacing-x: 0.125rem;
  border-spacing: var(--tw-border-spacing-x) var(--tw-border-spacing-y);
}

.origin-top-right {
  transform-origin: top right;
}

.translate-x-0 {
  --tw-translate-x: 0px;
  transform: translate(var(--tw-translate-x), var(--tw-translate-y)) rotate(var(--tw-rotate)) skewX(var(--tw-skew-x)) skewY(var(--tw-skew-y)) scaleX(var(--tw-scale-x)) scaleY(var(--tw-scale-y));
}

.translate-x-5 {
  --tw-translate-x: 1.25rem;
  transform: translate(var(--tw-translate-x), var(--tw-translate-y)) rotate(var(--tw-rotate)) skewX(var(--tw-skew-x)) skewY(var(--tw-skew-y)) scaleX(var(--tw-scale-x)) scaleY(var(--tw-scale-y));
}

.translate-y-0 {
  --tw-translate-y: 0px;
  transform: translate(var(--tw-translate-x), var(--tw-translate-y)) rotate(var(--tw-rotate)) skewX(var(--tw-skew-x)) skewY(var(--tw-skew-y)) scaleX(var(--tw-scale-x)) scaleY(var(--tw-scale-y));
}

.translate-y-2 {
  --tw-translate-y: 0.5rem;
  transform: translate(var(--tw-translate-x), var(--tw-translate-y)) rotate(var(--tw-rotate)) skewX(var(--tw-skew-x)) skewY(var(--tw-skew-y)) scaleX(var(--tw-scale-x)) scaleY(var(--tw-scale-y));
}

.rotate-45 {
  --tw-rotate: 45deg;
  transform: translate(var(--tw-translate-x), var(--tw-translate-y)) rotate(var(--tw-rotate)) skewX(var(--tw-skew-x)) skewY(var(--tw-skew-y)) scaleX(var(--tw-scale-x)) scaleY(var(--tw-scale-y));
}

.rotate-90 {
  --tw-rotate: 90deg;
  transform: translate(var(--tw-translate-x), var(--tw-translate-y)) rotate(var(--tw-rotate)) skewX(var(--tw-skew-x)) skewY(var(--tw-skew-y)) scaleX(var(--tw-scale-x)) scaleY(var(--tw-scale-y));
}

.transform {
  transform: translate(var(--tw-translate-x), var(--tw-translate-y)) rotate(var(--tw-rotate)) skewX(var(--tw-skew-x)) skewY(var(--tw-skew-y)) scaleX(var(--tw-scale-x)) scaleY(var(--tw-scale-y));
}

@keyframes spin {
  to {
    transform: rotate(360deg);
  }
}

.animate-spin {
  animation: spin 1s linear infinite;
}

.cursor-default {
  cursor: default;
}

.cursor-pointer {
  cursor: pointer;
}

.cursor-vertical-text {
  cursor: vertical-text;
}

.select-none {
  -webkit-user-select: none;
     -moz-user-select: none;
          user-select: none;
}

.resize-none {
  resize: none;
}

.scroll-py-2 {
  scroll-padding-top: 0.5rem;
  scroll-padding-bottom: 0.5rem;
}

.list-disc {
  list-style-type: disc;
}

.appearance-none {
  -webkit-appearance: none;
     -moz-appearance: none;
          appearance: none;
}


.flex-row {
  flex-direction: row;
}

.flex-col {
  flex-direction: column;
}

.flex-wrap-reverse {
  flex-wrap: wrap-reverse;
}

.items-start {
  align-items: flex-start;
}

.items-end {
  align-items: flex-end;
}

.items-center {
  align-items: center;
}

.justify-center {
  justify-content: center;
}

.justify-between {
  justify-content: space-between;
}


.self-start {
  align-self: flex-start;
}

.self-end {
  align-self: flex-end;
}

.overflow-hidden {
  overflow: hidden;
}

.overflow-y-auto {
  overflow-y: auto;
}

.scroll-smooth {
  scroll-behavior: smooth;
}

.truncate {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.rounded {
  border-radius: 0.25rem;
}

.rounded-full {
  border-radius: 9999px;
}

.rounded-lg {
  border-radius: 0.5rem;
}

.rounded-md {
  border-radius: 0.375rem;
}

.rounded-sm {
  border-radius: 0.125rem;
}

.rounded-xl {
  border-radius: 0.75rem;
}

.rounded-b-lg {
  border-bottom-right-radius: 0.5rem;
  border-bottom-left-radius: 0.5rem;
}

.border {
  border-width: 1px;
}

.border-0 {
  border-width: 0px;
}

.border-2 {
  border-width: 2px;
}

.border-b {
  border-bottom-width: 1px;
}

.border-l {
  border-left-width: 1px;
}

.border-r {
  border-right-width: 1px;
}

.border-t {
  border-top-width: 1px;
}

.border-gray-100 {
  --tw-border-opacity: 1;
  border-color: rgb(243 244 246 / var(--tw-border-opacity));
}

.border-gray-200 {
  --tw-border-opacity: 1;
  border-color: rgb(229 231 235 / var(--tw-border-opacity));
}

.border-gray-300 {
  --tw-border-opacity: 1;
  border-color: rgb(209 213 219 / var(--tw-border-opacity));
}

.border-transparent {
  border-color: transparent;
}

.bg-gray-100 {
  --tw-bg-opacity: 1;
  background-color: rgb(243 244 246 / var(--tw-bg-opacity));
}

.bg-gray-200 {
  --tw-bg-opacity: 1;
  background-color: rgb(229 231 235 / var(--tw-bg-opacity));
}

.bg-gray-400\/30 {
  background-color: rgb(156 163 175 / 0.3);
}

.bg-gray-50 {
  --tw-bg-opacity: 1;
  background-color: rgb(249 250 251 / var(--tw-bg-opacity));
}

.bg-gray-500 {
  --tw-bg-opacity: 1;
  background-color: rgb(107 114 128 / var(--tw-bg-opacity));
}

.bg-green-300\/50 {
  background-color: rgb(134 239 172 / 0.5);
}

.bg-green-50 {
  --tw-bg-opacity: 1;
  background-color: rgb(240 253 244 / var(--tw-bg-opacity));
}

.bg-red-100 {
  --tw-bg-opacity: 1;
  background-color: rgb(254 226 226 / var(--tw-bg-opacity));
}

.bg-red-50 {
  --tw-bg-opacity: 1;
  background-color: rgb(254 242 242 / var(--tw-bg-opacity));
}

.bg-red-600 {
  --tw-bg-opacity: 1;
  background-color: rgb(220 38 38 / var(--tw-bg-opacity));
}

.bg-teal-300 {
  --tw-bg-opacity: 1;
  background-color: rgb(94 234 212 / var(--tw-bg-opacity));
}

.bg-teal-400 {
  --tw-bg-opacity: 1;
  background-color: rgb(45 212 191 / var(--tw-bg-opacity));
}

.bg-teal-500\/15 {
  background-color: rgb(20 184 166 / 0.15);
}

.bg-teal-600 {
  --tw-bg-opacity: 1;
  background-color: rgb(13 148 136 / var(--tw-bg-opacity));
}

.bg-transparent {
  background-color: transparent;
}

.bg-white {
  --tw-bg-opacity: 1;
  background-color: rgb(255 255 255 / var(--tw-bg-opacity));
}

.bg-white\/90 {
  background-color: rgb(255 255 255 / 0.9);
}

.bg-yellow-300 {
  --tw-bg-opacity: 1;
  background-color: rgb(253 224 71 / var(--tw-bg-opacity));
}

.bg-opacity-25 {
  --tw-bg-opacity: 0.25;
}

.bg-opacity-60 {
  --tw-bg-opacity: 0.6;
}

.bg-opacity-75 {
  --tw-bg-opacity: 0.75;
}

.bg-opacity-80 {
  --tw-bg-opacity: 0.8;
}

.fill-current {
  fill: currentColor;
}

.fill-teal-600 {
  fill: #0d9488;
}

.stroke-current {
  stroke: currentColor;
}

.p-0 {
  padding: 0px;
}

.p-0\.5 {
  padding: 0.125rem;
}

.p-1 {
  padding: 0.25rem;
}

.p-2 {
  padding: 0.5rem;
}

.p-2\.5 {
  padding: 0.625rem;
}

.p-3 {
  padding: 0.75rem;
}

.p-4 {
  padding: 1rem;
}

.p-8 {
  padding: 2rem;
}

.px-0 {
  padding-left: 0px;
  padding-right: 0px;
}

.px-1 {
  padding-left: 0.25rem;
  padding-right: 0.25rem;
}

.px-2 {
  padding-left: 0.5rem;
  padding-right: 0.5rem;
}

.px-3 {
  padding-left: 0.75rem;
  padding-right: 0.75rem;
}

.px-4 {
  padding-left: 1rem;
  padding-right: 1rem;
}

.px-5 {
  padding-left: 1.25rem;
  padding-right: 1.25rem;
}

.px-6 {
  padding-left: 1.5rem;
  padding-right: 1.5rem;
}

.py-0 {
  padding-top: 0px;
  padding-bottom: 0px;
}

.py-0\.5 {
  padding-top: 0.125rem;
  padding-bottom: 0.125rem;
}

.py-1 {
  padding-top: 0.25rem;
  padding-bottom: 0.25rem;
}

.py-1\.5 {
  padding-top: 0.375rem;
  padding-bottom: 0.375rem;
}

.py-2 {
  padding-top: 0.5rem;
  padding-bottom: 0.5rem;
}

.py-3 {
  padding-top: 0.75rem;
  padding-bottom: 0.75rem;
}

.py-4 {
  padding-top: 1rem;
  padding-bottom: 1rem;
}

.py-5 {
  padding-top: 1.25rem;
  padding-bottom: 1.25rem;
}

.py-6 {
  padding-top: 1.5rem;
  padding-bottom: 1.5rem;
}

.py-8 {
  padding-top: 2rem;
  padding-bottom: 2rem;
}

.pb-0 {
  padding-bottom: 0px;
}

.pb-0\.5 {
  padding-bottom: 0.125rem;
}

.pb-1 {
  padding-bottom: 0.25rem;
}

.pb-10 {
  padding-bottom: 2.5rem;
}

.pb-2 {
  padding-bottom: 0.5rem;
}

.pb-3 {
  padding-bottom: 0.75rem;
}

.pb-4 {
  padding-bottom: 1rem;
}

.pl-0 {
  padding-left: 0px;
}

.pl-0\.5 {
  padding-left: 0.125rem;
}

.pl-1 {
  padding-left: 0.25rem;
}

.pl-2 {
  padding-left: 0.5rem;
}

.pl-20 {
  padding-left: 5rem;
}

.pl-24 {
  padding-left: 6rem;
}

.pl-3 {
  padding-left: 0.75rem;
}

.pl-5 {
  padding-left: 1.25rem;
}

.pl-7 {
  padding-left: 1.75rem;
}

.pr-0 {
  padding-right: 0px;
}

.pr-1 {
  padding-right: 0.25rem;
}

.pr-10 {
  padding-right: 2.5rem;
}

.pr-2 {
  padding-right: 0.5rem;
}

.pr-4 {
  padding-right: 1rem;
}

.pt-0 {
  padding-top: 0px;
}

.pt-0\.5 {
  padding-top: 0.125rem;
}

.pt-1 {
  padding-top: 0.25rem;
}

.pt-2 {
  padding-top: 0.5rem;
}

.pt-2\.5 {
  padding-top: 0.625rem;
}

.pt-5 {
  padding-top: 1.25rem;
}

.text-left {
  text-align: left;
}

.text-center {
  text-align: center;
}

.font-sans {
  font-family: ui-sans-serif, system-ui, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji";
}

.text-2xl {
  font-size: 1.5rem;
  line-height: 2rem;
}

.text-3xl {
  font-size: 1.875rem;
  line-height: 2.25rem;
}

.text-base {
  font-size: 1rem;
  line-height: 1.5rem;
}

.text-lg {
  font-size: 1.125rem;
  line-height: 1.75rem;
}

.text-sm {
  font-size: 0.875rem;
  line-height: 1.25rem;
}

.text-xs {
  font-size: 0.75rem;
  line-height: 1rem;
}

.font-bold {
  font-weight: 700;
}

.font-medium {
  font-weight: 500;
}

.font-semibold {
  font-weight: 600;
}

.leading-4 {
  line-height: 1rem;
}

.leading-5 {
  line-height: 1.25rem;
}

.leading-6 {
  line-height: 1.5rem;
}

.leading-7 {
  line-height: 1.75rem;
}

.leading-8 {
  line-height: 2rem;
}

.leading-tight {
  line-height: 1.25;
}

.tracking-tight {
  letter-spacing: -0.025em;
}

.text-black {
  --tw-text-opacity: 1;
  color: rgb(0 0 0 / var(--tw-text-opacity));
}

.text-blue-600 {
  --tw-text-opacity: 1;
  color: rgb(37 99 235 / var(--tw-text-opacity));
}

.text-gray-200 {
  --tw-text-opacity: 1;
  color: rgb(229 231 235 / var(--tw-text-opacity));
}

.text-gray-400 {
  --tw-text-opacity: 1;
  color: rgb(156 163 175 / var(--tw-text-opacity));
}

.text-gray-500 {
  --tw-text-opacity: 1;
  color: rgb(107 114 128 / var(--tw-text-opacity));
}

.text-gray-600 {
  --tw-text-opacity: 1;
  color: rgb(75 85 99 / var(--tw-text-opacity));
}

.text-gray-700 {
  --tw-text-opacity: 1;
  color: rgb(55 65 81 / var(--tw-text-opacity));
}

.text-gray-800 {
  --tw-text-opacity: 1;
  color: rgb(31 41 55 / var(--tw-text-opacity));
}

.text-gray-900 {
  --tw-text-opacity: 1;
  color: rgb(17 24 39 / var(--tw-text-opacity));
}

.text-green-400 {
  --tw-text-opacity: 1;
  color: rgb(74 222 128 / var(--tw-text-opacity));
}

.text-green-500 {
  --tw-text-opacity: 1;
  color: rgb(34 197 94 / var(--tw-text-opacity));
}

.text-indigo-600 {
  --tw-text-opacity: 1;
  color: rgb(79 70 229 / var(--tw-text-opacity));
}

.text-orange-600 {
  --tw-text-opacity: 1;
  color: rgb(234 88 12 / var(--tw-text-opacity));
}

.text-red-300 {
  --tw-text-opacity: 1;
  color: rgb(252 165 165 / var(--tw-text-opacity));
}

.text-red-400 {
  --tw-text-opacity: 1;
  color: rgb(248 113 113 / var(--tw-text-opacity));
}

.text-red-500 {
  --tw-text-opacity: 1;
  color: rgb(239 68 68 / var(--tw-text-opacity));
}

.text-red-600 {
  --tw-text-opacity: 1;
  color: rgb(220 38 38 / var(--tw-text-opacity));
}

.text-red-700 {
  --tw-text-opacity: 1;
  color: rgb(185 28 28 / var(--tw-text-opacity));
}

.text-red-800 {
  --tw-text-opacity: 1;
  color: rgb(153 27 27 / var(--tw-text-opacity));
}

.text-teal-500 {
  --tw-text-opacity: 1;
  color: rgb(20 184 166 / var(--tw-text-opacity));
}

.text-teal-600 {
  --tw-text-opacity: 1;
  color: rgb(13 148 136 / var(--tw-text-opacity));
}

.text-transparent {
  color: transparent;
}

.text-white {
  --tw-text-opacity: 1;
  color: rgb(255 255 255 / var(--tw-text-opacity));
}

.text-yellow-400 {
  --tw-text-opacity: 1;
  color: rgb(250 204 21 / var(--tw-text-opacity));
}

.text-opacity-40 {
  --tw-text-opacity: 0.4;
}

.opacity-0 {
  opacity: 0;
}

.opacity-100 {
  opacity: 1;
}

.shadow {
  --tw-shadow: 0 1px 3px 0 rgb(0 0 0 / 0.1), 0 1px 2px -1px rgb(0 0 0 / 0.1);
  --tw-shadow-colored: 0 1px 3px 0 var(--tw-shadow-color), 0 1px 2px -1px var(--tw-shadow-color);
  box-shadow: var(--tw-ring-offset-shadow, 0 0 #0000), var(--tw-ring-shadow, 0 0 #0000), var(--tw-shadow);
}

.shadow-2xl {
  --tw-shadow: 0 25px 50px -12px rgb(0 0 0 / 0.25);
  --tw-shadow-colored: 0 25px 50px -12px var(--tw-shadow-color);
  box-shadow: var(--tw-ring-offset-shadow, 0 0 #0000), var(--tw-ring-shadow, 0 0 #0000), var(--tw-shadow);
}

.shadow-inner {
  --tw-shadow: inset 0 2px 4px 0 rgb(0 0 0 / 0.05);
  --tw-shadow-colored: inset 0 2px 4px 0 var(--tw-shadow-color);
  box-shadow: var(--tw-ring-offset-shadow, 0 0 #0000), var(--tw-ring-shadow, 0 0 #0000), var(--tw-shadow);
}

.shadow-lg {
  --tw-shadow: 0 10px 15px -3px rgb(0 0 0 / 0.1), 0 4px 6px -4px rgb(0 0 0 / 0.1);
  --tw-shadow-colored: 0 10px 15px -3px var(--tw-shadow-color), 0 4px 6px -4px var(--tw-shadow-color);
  box-shadow: var(--tw-ring-offset-shadow, 0 0 #0000), var(--tw-ring-shadow, 0 0 #0000), var(--tw-shadow);
}

.shadow-md {
  --tw-shadow: 0 4px 6px -1px rgb(0 0 0 / 0.1), 0 2px 4px -2px rgb(0 0 0 / 0.1);
  --tw-shadow-colored: 0 4px 6px -1px var(--tw-shadow-color), 0 2px 4px -2px var(--tw-shadow-color);
  box-shadow: var(--tw-ring-offset-shadow, 0 0 #0000), var(--tw-ring-shadow, 0 0 #0000), var(--tw-shadow);
}

.shadow-sm {
  --tw-shadow: 0 1px 2px 0 rgb(0 0 0 / 0.05);
  --tw-shadow-colored: 0 1px 2px 0 var(--tw-shadow-color);
  box-shadow: var(--tw-ring-offset-shadow, 0 0 #0000), var(--tw-ring-shadow, 0 0 #0000), var(--tw-shadow);
}

.shadow-xl {
  --tw-shadow: 0 20px 25px -5px rgb(0 0 0 / 0.1), 0 8px 10px -6px rgb(0 0 0 / 0.1);
  --tw-shadow-colored: 0 20px 25px -5px var(--tw-shadow-color), 0 8px 10px -6px var(--tw-shadow-color);
  box-shadow: var(--tw-ring-offset-shadow, 0 0 #0000), var(--tw-ring-shadow, 0 0 #0000), var(--tw-shadow);
}

.outline {
  outline-style: solid;
}

.outline-1 {
  outline-width: 1px;
}

.outline-offset-0 {
  outline-offset: 0px;
}

.outline-gray-300 {
  outline-color: #d1d5db;
}

.ring-0 {
  --tw-ring-offset-shadow: var(--tw-ring-inset) 0 0 0 var(--tw-ring-offset-width) var(--tw-ring-offset-color);
  --tw-ring-shadow: var(--tw-ring-inset) 0 0 0 calc(0px + var(--tw-ring-offset-width)) var(--tw-ring-color);
  box-shadow: var(--tw-ring-offset-shadow), var(--tw-ring-shadow), var(--tw-shadow, 0 0 #0000);
}

.ring-1 {
  --tw-ring-offset-shadow: var(--tw-ring-inset) 0 0 0 var(--tw-ring-offset-width) var(--tw-ring-offset-color);
  --tw-ring-shadow: var(--tw-ring-inset) 0 0 0 calc(1px + var(--tw-ring-offset-width)) var(--tw-ring-color);
  box-shadow: var(--tw-ring-offset-shadow), var(--tw-ring-shadow), var(--tw-shadow, 0 0 #0000);
}

.ring-inset {
  --tw-ring-inset: inset;
}

.ring-black {
  --tw-ring-opacity: 1;
  --tw-ring-color: rgb(0 0 0 / var(--tw-ring-opacity));
}

.ring-gray-200 {
  --tw-ring-opacity: 1;
  --tw-ring-color: rgb(229 231 235 / var(--tw-ring-opacity));
}

.ring-gray-300 {
  --tw-ring-opacity: 1;
  --tw-ring-color: rgb(209 213 219 / var(--tw-ring-opacity));
}

.ring-gray-400 {
  --tw-ring-opacity: 1;
  --tw-ring-color: rgb(156 163 175 / var(--tw-ring-opacity));
}

.ring-green-600\/20 {
  --tw-ring-color: rgb(22 163 74 / 0.2);
}

.ring-red-600\/20 {
  --tw-ring-color: rgb(220 38 38 / 0.2);
}

.ring-opacity-5 {
  --tw-ring-opacity: 0.05;
}

.blur {
  --tw-blur: blur(8px);
  filter: var(--tw-blur) var(--tw-brightness) var(--tw-contrast) var(--tw-grayscale) var(--tw-hue-rotate) var(--tw-invert) var(--tw-saturate) var(--tw-sepia) var(--tw-drop-shadow);
}

.drop-shadow-xl {
  --tw-drop-shadow: drop-shadow(0 20px 13px rgb(0 0 0 / 0.03)) drop-shadow(0 8px 5px rgb(0 0 0 / 0.08));
  filter: var(--tw-blur) var(--tw-brightness) var(--tw-contrast) var(--tw-grayscale) var(--tw-hue-rotate) var(--tw-invert) var(--tw-saturate) var(--tw-sepia) var(--tw-drop-shadow);
}

.grayscale {
  --tw-grayscale: grayscale(100%);
  filter: var(--tw-blur) var(--tw-brightness) var(--tw-contrast) var(--tw-grayscale) var(--tw-hue-rotate) var(--tw-invert) var(--tw-saturate) var(--tw-sepia) var(--tw-drop-shadow);
}

.filter {
  filter: var(--tw-blur) var(--tw-brightness) var(--tw-contrast) var(--tw-grayscale) var(--tw-hue-rotate) var(--tw-invert) var(--tw-saturate) var(--tw-sepia) var(--tw-drop-shadow);
}

.backdrop-blur {
  --tw-backdrop-blur: blur(8px);
  -webkit-backdrop-filter: var(--tw-backdrop-blur) var(--tw-backdrop-brightness) var(--tw-backdrop-contrast) var(--tw-backdrop-grayscale) var(--tw-backdrop-hue-rotate) var(--tw-backdrop-invert) var(--tw-backdrop-opacity) var(--tw-backdrop-saturate) var(--tw-backdrop-sepia);
          backdrop-filter: var(--tw-backdrop-blur) var(--tw-backdrop-brightness) var(--tw-backdrop-contrast) var(--tw-backdrop-grayscale) var(--tw-backdrop-hue-rotate) var(--tw-backdrop-invert) var(--tw-backdrop-opacity) var(--tw-backdrop-saturate) var(--tw-backdrop-sepia);
}

.backdrop-blur-xl {
  --tw-backdrop-blur: blur(24px);
  -webkit-backdrop-filter: var(--tw-backdrop-blur) var(--tw-backdrop-brightness) var(--tw-backdrop-contrast) var(--tw-backdrop-grayscale) var(--tw-backdrop-hue-rotate) var(--tw-backdrop-invert) var(--tw-backdrop-opacity) var(--tw-backdrop-saturate) var(--tw-backdrop-sepia);
          backdrop-filter: var(--tw-backdrop-blur) var(--tw-backdrop-brightness) var(--tw-backdrop-contrast) var(--tw-backdrop-grayscale) var(--tw-backdrop-hue-rotate) var(--tw-backdrop-invert) var(--tw-backdrop-opacity) var(--tw-backdrop-saturate) var(--tw-backdrop-sepia);
}

.backdrop-filter {
  -webkit-backdrop-filter: var(--tw-backdrop-blur) var(--tw-backdrop-brightness) var(--tw-backdrop-contrast) var(--tw-backdrop-grayscale) var(--tw-backdrop-hue-rotate) var(--tw-backdrop-invert) var(--tw-backdrop-opacity) var(--tw-backdrop-saturate) var(--tw-backdrop-sepia);
          backdrop-filter: var(--tw-backdrop-blur) var(--tw-backdrop-brightness) var(--tw-backdrop-contrast) var(--tw-backdrop-grayscale) var(--tw-backdrop-hue-rotate) var(--tw-backdrop-invert) var(--tw-backdrop-opacity) var(--tw-backdrop-saturate) var(--tw-backdrop-sepia);
}

.transition {
  transition-property: color, background-color, border-color, text-decoration-color, fill, stroke, opacity, box-shadow, transform, filter, -webkit-backdrop-filter;
  transition-property: color, background-color, border-color, text-decoration-color, fill, stroke, opacity, box-shadow, transform, filter, backdrop-filter;
  transition-property: color, background-color, border-color, text-decoration-color, fill, stroke, opacity, box-shadow, transform, filter, backdrop-filter, -webkit-backdrop-filter;
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
  transition-duration: 150ms;
}

.transition-all {
  transition-property: all;
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
  transition-duration: 150ms;
}

.transition-colors {
  transition-property: color, background-color, border-color, text-decoration-color, fill, stroke;
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
  transition-duration: 150ms;
}

.transition-opacity {
  transition-property: opacity;
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
  transition-duration: 150ms;
}

.duration-100 {
  transition-duration: 100ms;
}

.duration-200 {
  transition-duration: 200ms;
}

.duration-300 {
  transition-duration: 300ms;
}

.ease-in {
  transition-timing-function: cubic-bezier(0.4, 0, 1, 1);
}

.ease-in-out {
  transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
}

.ease-linear {
  transition-timing-function: linear;
}

.ease-out {
  transition-timing-function: cubic-bezier(0, 0, 0.2, 1);
}

.placeholder\:text-gray-400::-moz-placeholder {
  --tw-text-opacity: 1;
  color: rgb(156 163 175 / var(--tw-text-opacity));
}

.placeholder\:text-gray-400::placeholder {
  --tw-text-opacity: 1;
  color: rgb(156 163 175 / var(--tw-text-opacity));
}

.focus-within\:ring-2:focus-within {
  --tw-ring-offset-shadow: var(--tw-ring-inset) 0 0 0 var(--tw-ring-offset-width) var(--tw-ring-offset-color);
  --tw-ring-shadow: var(--tw-ring-inset) 0 0 0 calc(2px + var(--tw-ring-offset-width)) var(--tw-ring-color);
  box-shadow: var(--tw-ring-offset-shadow), var(--tw-ring-shadow), var(--tw-shadow, 0 0 #0000);
}

.focus-within\:ring-indigo-600:focus-within {
  --tw-ring-opacity: 1;
  --tw-ring-color: rgb(79 70 229 / var(--tw-ring-opacity));
}

.focus-within\:ring-teal-600:focus-within {
  --tw-ring-opacity: 1;
  --tw-ring-color: rgb(13 148 136 / var(--tw-ring-opacity));
}

.hover\:rotate-90:hover {
  --tw-rotate: 90deg;
  transform: translate(var(--tw-translate-x), var(--tw-translate-y)) rotate(var(--tw-rotate)) skewX(var(--tw-skew-x)) skewY(var(--tw-skew-y)) scaleX(var(--tw-scale-x)) scaleY(var(--tw-scale-y));
}

.hover\:bg-gray-100:hover {
  --tw-bg-opacity: 1;
  background-color: rgb(243 244 246 / var(--tw-bg-opacity));
}

.hover\:bg-gray-50:hover {
  --tw-bg-opacity: 1;
  background-color: rgb(249 250 251 / var(--tw-bg-opacity));
}

.hover\:bg-red-500:hover {
  --tw-bg-opacity: 1;
  background-color: rgb(239 68 68 / var(--tw-bg-opacity));
}

.hover\:bg-sky-100:hover {
  --tw-bg-opacity: 1;
  background-color: rgb(224 242 254 / var(--tw-bg-opacity));
}

.hover\:bg-teal-400:hover {
  --tw-bg-opacity: 1;
  background-color: rgb(45 212 191 / var(--tw-bg-opacity));
}

.hover\:text-gray-500:hover {
  --tw-text-opacity: 1;
  color: rgb(107 114 128 / var(--tw-text-opacity));
}

.hover\:text-green-300:hover {
  --tw-text-opacity: 1;
  color: rgb(134 239 172 / var(--tw-text-opacity));
}

.hover\:text-red-300:hover {
  --tw-text-opacity: 1;
  color: rgb(252 165 165 / var(--tw-text-opacity));
}

.hover\:text-teal-600:hover {
  --tw-text-opacity: 1;
  color: rgb(13 148 136 / var(--tw-text-opacity));
}

.hover\:text-white:hover {
  --tw-text-opacity: 1;
  color: rgb(255 255 255 / var(--tw-text-opacity));
}

.focus\:border-blue-500:focus {
  --tw-border-opacity: 1;
  border-color: rgb(59 130 246 / var(--tw-border-opacity));
}

.focus\:bg-teal-500\/25:focus {
  background-color: rgb(20 184 166 / 0.25);
}

.focus\:outline-none:focus {
  outline: 2px solid transparent;
  outline-offset: 2px;
}

.focus\:ring-0:focus {
  --tw-ring-offset-shadow: var(--tw-ring-inset) 0 0 0 var(--tw-ring-offset-width) var(--tw-ring-offset-color);
  --tw-ring-shadow: var(--tw-ring-inset) 0 0 0 calc(0px + var(--tw-ring-offset-width)) var(--tw-ring-color);
  box-shadow: var(--tw-ring-offset-shadow), var(--tw-ring-shadow), var(--tw-shadow, 0 0 #0000);
}

.focus\:ring-2:focus {
  --tw-ring-offset-shadow: var(--tw-ring-inset) 0 0 0 var(--tw-ring-offset-width) var(--tw-ring-offset-color);
  --tw-ring-shadow: var(--tw-ring-inset) 0 0 0 calc(2px + var(--tw-ring-offset-width)) var(--tw-ring-color);
  box-shadow: var(--tw-ring-offset-shadow), var(--tw-ring-shadow), var(--tw-shadow, 0 0 #0000);
}

.focus\:ring-inset:focus {
  --tw-ring-inset: inset;
}

.focus\:ring-blue-500:focus {
  --tw-ring-opacity: 1;
  --tw-ring-color: rgb(59 130 246 / var(--tw-ring-opacity));
}

.focus\:ring-indigo-500:focus {
  --tw-ring-opacity: 1;
  --tw-ring-color: rgb(99 102 241 / var(--tw-ring-opacity));
}

.focus\:ring-indigo-600:focus {
  --tw-ring-opacity: 1;
  --tw-ring-color: rgb(79 70 229 / var(--tw-ring-opacity));
}

.focus\:ring-teal-600:focus {
  --tw-ring-opacity: 1;
  --tw-ring-color: rgb(13 148 136 / var(--tw-ring-opacity));
}

.focus\:ring-offset-2:focus {
  --tw-ring-offset-width: 2px;
}

.focus-visible\:outline:focus-visible {
  outline-style: solid;
}

.focus-visible\:outline-2:focus-visible {
  outline-width: 2px;
}

.focus-visible\:outline-offset-2:focus-visible {
  outline-offset: 2px;
}

.group:hover .group-hover\:bg-gray-300 {
  --tw-bg-opacity: 1;
  background-color: rgb(209 213 219 / var(--tw-bg-opacity));
}

.group:hover .group-hover\:text-indigo-500 {
  --tw-text-opacity: 1;
  color: rgb(99 102 241 / var(--tw-text-opacity));
}

.group:hover .group-hover\:text-white {
  --tw-text-opacity: 1;
  color: rgb(255 255 255 / var(--tw-text-opacity));
}

.group:hover .group-hover\:opacity-0 {
  opacity: 0;
}

.group:hover .group-hover\:opacity-100 {
  opacity: 1;
}


@media (min-width: 640px) {
  .sm\:mx-0 {
    margin-left: 0px;
    margin-right: 0px;
  }

  .sm\:my-8 {
    margin-top: 2rem;
    margin-bottom: 2rem;
  }

  .sm\:ml-3 {
    margin-left: 0.75rem;
  }

  .sm\:ml-4 {
    margin-left: 1rem;
  }

  .sm\:mt-0 {
    margin-top: 0px;
  }

  .sm\:mt-4 {
    margin-top: 1rem;
  }

  .sm\:flex {
    display: flex;
  }

  .sm\:h-10 {
    height: 2.5rem;
  }

  .sm\:w-10 {
    width: 2.5rem;
  }

  .sm\:w-auto {
    width: auto;
  }

  .sm\:w-full {
    width: 100%;
  }

  .sm\:max-w-lg {
    max-width: 32rem;
  }

  .sm\:translate-x-0 {
    --tw-translate-x: 0px;
    transform: translate(var(--tw-translate-x), var(--tw-translate-y)) rotate(var(--tw-rotate)) skewX(var(--tw-skew-x)) skewY(var(--tw-skew-y)) scaleX(var(--tw-scale-x)) scaleY(var(--tw-scale-y));
  }

  .sm\:translate-x-2 {
    --tw-translate-x: 0.5rem;
    transform: translate(var(--tw-translate-x), var(--tw-translate-y)) rotate(var(--tw-rotate)) skewX(var(--tw-skew-x)) skewY(var(--tw-skew-y)) scaleX(var(--tw-scale-x)) scaleY(var(--tw-scale-y));
  }

  .sm\:translate-y-0 {
    --tw-translate-y: 0px;
    transform: translate(var(--tw-translate-x), var(--tw-translate-y)) rotate(var(--tw-rotate)) skewX(var(--tw-skew-x)) skewY(var(--tw-skew-y)) scaleX(var(--tw-scale-x)) scaleY(var(--tw-scale-y));
  }

  .sm\:flex-row-reverse {
    flex-direction: row-reverse;
  }

  .sm\:flex-col {
    flex-direction: column;
  }

  .sm\:items-start {
    align-items: flex-start;
  }

  .sm\:items-end {
    align-items: flex-end;
  }

  .sm\:items-center {
    align-items: center;
  }

  .sm\:p-0 {
    padding: 0px;
  }

  .sm\:p-6 {
    padding: 1.5rem;
  }

  .sm\:px-0 {
    padding-left: 0px;
    padding-right: 0px;
  }

  .sm\:px-2 {
    padding-left: 0.5rem;
    padding-right: 0.5rem;
  }

  .sm\:px-6 {
    padding-left: 1.5rem;
    padding-right: 1.5rem;
  }

  .sm\:pr-3 {
    padding-right: 0.75rem;
  }

  .sm\:text-left {
    text-align: left;
  }

  .sm\:text-sm {
    font-size: 0.875rem;
    line-height: 1.25rem;
  }

  .sm\:text-xs {
    font-size: 0.75rem;
    line-height: 1rem;
  }

  .sm\:leading-6 {
    line-height: 1.5rem;
  }
}

@media (min-width: 768px) {
  .md\:fixed {
    position: fixed;
  }

  .md\:inset-y-0 {
    top: 0px;
    bottom: 0px;
  }

  .md\:z-50 {
    z-index: 50;
  }

  .md\:-ml-14 {
    margin-left: -3.5rem;
  }

  .md\:ml-2 {
    margin-left: 0.5rem;
  }

  .md\:ml-5 {
    margin-left: 1.25rem;
  }

  .md\:block {
    display: block;
  }

  .md\:flex {
    display: flex;
  }

  .md\:flex-col {
    flex-direction: column;
  }

  .md\:space-x-3 > :not([hidden]) ~ :not([hidden]) {
    --tw-space-x-reverse: 0;
    margin-right: calc(0.75rem * var(--tw-space-x-reverse));
    margin-left: calc(0.75rem * calc(1 - var(--tw-space-x-reverse)));
  }

  .md\:p-20 {
    padding: 5rem;
  }

  .md\:px-4 {
    padding-left: 1rem;
    padding-right: 1rem;
  }

  .md\:pl-2 {
    padding-left: 0.5rem;
  }

  .md\:pr-5 {
    padding-right: 1.25rem;
  }
}

@media (min-width: 1024px) {
  .lg\:px-8 {
    padding-left: 2rem;
    padding-right: 2rem;
  }
}

@media (prefers-color-scheme: dark) {
  .dark\:divide-gray-600 > :not([hidden]) ~ :not([hidden]) {
    --tw-divide-opacity: 1;
    border-color: rgb(75 85 99 / var(--tw-divide-opacity));
  }

  .dark\:divide-gray-700 > :not([hidden]) ~ :not([hidden]) {
    --tw-divide-opacity: 1;
    border-color: rgb(55 65 81 / var(--tw-divide-opacity));
  }

  .dark\:border-gray-500 {
    --tw-border-opacity: 1;
    border-color: rgb(107 114 128 / var(--tw-border-opacity));
  }

  .dark\:border-gray-600 {
    --tw-border-opacity: 1;
    border-color: rgb(75 85 99 / var(--tw-border-opacity));
  }

  .dark\:bg-gray-400 {
    --tw-bg-opacity: 1;
    background-color: rgb(156 163 175 / var(--tw-bg-opacity));
  }

  .dark\:bg-gray-600 {
    --tw-bg-opacity: 1;
    background-color: rgb(75 85 99 / var(--tw-bg-opacity));
  }

  .dark\:bg-gray-700 {
    --tw-bg-opacity: 1;
    background-color: rgb(55 65 81 / var(--tw-bg-opacity));
  }

  .dark\:bg-gray-800 {
    --tw-bg-opacity: 1;
    background-color: rgb(31 41 55 / var(--tw-bg-opacity));
  }

  .dark\:bg-red-800 {
    --tw-bg-opacity: 1;
    background-color: rgb(153 27 27 / var(--tw-bg-opacity));
  }

  .dark\:bg-teal-500 {
    --tw-bg-opacity: 1;
    background-color: rgb(20 184 166 / var(--tw-bg-opacity));
  }

  .dark\:bg-opacity-75 {
    --tw-bg-opacity: 0.75;
  }

  .dark\:text-blue-300 {
    --tw-text-opacity: 1;
    color: rgb(147 197 253 / var(--tw-text-opacity));
  }

  .dark\:text-gray-300 {
    --tw-text-opacity: 1;
    color: rgb(209 213 219 / var(--tw-text-opacity));
  }

  .dark\:text-gray-400 {
    --tw-text-opacity: 1;
    color: rgb(156 163 175 / var(--tw-text-opacity));
  }

  .dark\:text-gray-500 {
    --tw-text-opacity: 1;
    color: rgb(107 114 128 / var(--tw-text-opacity));
  }

  .dark\:text-gray-600 {
    --tw-text-opacity: 1;
    color: rgb(75 85 99 / var(--tw-text-opacity));
  }

  .dark\:text-gray-800 {
    --tw-text-opacity: 1;
    color: rgb(31 41 55 / var(--tw-text-opacity));
  }

  .dark\:text-red-200 {
    --tw-text-opacity: 1;
    color: rgb(254 202 202 / var(--tw-text-opacity));
  }

  .dark\:text-red-300 {
    --tw-text-opacity: 1;
    color: rgb(252 165 165 / var(--tw-text-opacity));
  }

  .dark\:text-white {
    --tw-text-opacity: 1;
    color: rgb(255 255 255 / var(--tw-text-opacity));
  }

  .dark\:placeholder-gray-400::-moz-placeholder {
    --tw-placeholder-opacity: 1;
    color: rgb(156 163 175 / var(--tw-placeholder-opacity));
  }

  .dark\:placeholder-gray-400::placeholder {
    --tw-placeholder-opacity: 1;
    color: rgb(156 163 175 / var(--tw-placeholder-opacity));
  }

  .dark\:outline-gray-700 {
    outline-color: #374151;
  }

  .dark\:ring-gray-500 {
    --tw-ring-opacity: 1;
    --tw-ring-color: rgb(107 114 128 / var(--tw-ring-opacity));
  }

  .dark\:ring-gray-600 {
    --tw-ring-opacity: 1;
    --tw-ring-color: rgb(75 85 99 / var(--tw-ring-opacity));
  }

  .dark\:ring-gray-700 {
    --tw-ring-opacity: 1;
    --tw-ring-color: rgb(55 65 81 / var(--tw-ring-opacity));
  }

  .dark\:ring-gray-800 {
    --tw-ring-opacity: 1;
    --tw-ring-color: rgb(31 41 55 / var(--tw-ring-opacity));
  }

  .dark\:contrast-75 {
    --tw-contrast: contrast(.75);
    filter: var(--tw-blur) var(--tw-brightness) var(--tw-contrast) var(--tw-grayscale) var(--tw-hue-rotate) var(--tw-invert) var(--tw-saturate) var(--tw-sepia) var(--tw-drop-shadow);
  }

  .dark\:invert {
    --tw-invert: invert(100%);
    filter: var(--tw-blur) var(--tw-brightness) var(--tw-contrast) var(--tw-grayscale) var(--tw-hue-rotate) var(--tw-invert) var(--tw-saturate) var(--tw-sepia) var(--tw-drop-shadow);
  }

  .dark\:hover\:bg-gray-200:hover {
    --tw-bg-opacity: 1;
    background-color: rgb(229 231 235 / var(--tw-bg-opacity));
  }

  .dark\:hover\:bg-gray-700:hover {
    --tw-bg-opacity: 1;
    background-color: rgb(55 65 81 / var(--tw-bg-opacity));
  }

  .dark\:hover\:text-white:hover {
    --tw-text-opacity: 1;
    color: rgb(255 255 255 / var(--tw-text-opacity));
  }

}
```

</details>

