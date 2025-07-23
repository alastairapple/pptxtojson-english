Here's the translated README for the PPTX to JSON Converter:
🎨 PPTX to JSON Converter
A JavaScript library that runs in the browser and converts .pptx files to readable JSON data.
> The main differences from other PPTX file parsing tools:
>  * Runs directly in the browser.
>  * The parsing result is readable JSON data, not just XML file content directly translated to hard-to-understand JSON.
> 
Online Demo: https://pipipi-pikachu.github.io/pptxtojson/
🎯 Important Notes
⚒️ Use Cases
This repository was created for the project PPTist, to provide a reference example for its "import .pptx file" feature. However, currently, there are still style differences between the parsed PPT information and the source file.
But if you only need to extract text content, media resource information, structural information, etc., from a PPT file, or if you don't have extremely high requirements for layout/style accuracy, then pptxtojson might be helpful to you.
📏 Length Unit
In the output JSON, all numerical length values are in pt (points).
> Note: In version 0.x, all output length values were in px (pixels).
> 
🔨 Installation
npm install pptxtojson

💿 Usage
Browser
<input type="file" accept="application/vnd.openxmlformats-officedocument.presentationml.presentation"/>

import { parse } from 'pptxtojson'

document.querySelector('input').addEventListener('change', evt => {
	const file = evt.target.files[0]
	
	const reader = new FileReader()
	reader.onload = async e => {
		const json = await parse(e.target.result)
		console.log(json)
	}
	reader.readAsArrayBuffer(file)
})

Output Example
{
	"slides": [
		{
			"fill": {
				"type": "color",
				"value": "#FF0000"
			},
			"elements": [
				{
					"left":	0,
					"top": 0,
					"width": 72,
					"height":	72,
					"borderColor": "#1F4E79",
					"borderWidth": 1,
					"borderType": "solid",
					"borderStrokeDasharray": 0,
					"fill": {
						"type": "color",
						"value": "#FF0000"
					},
					"content": "<p style=\"text-align: center;\"><span style=\"font-size: 18pt;font-family: Calibri;\">TEST</span></p>",
					"isFlipV": false,
					"isFlipH": false,
					"rotate": 0,
					"vAlign": "mid",
					"name": "Rectangle 1",
					"type": "shape",
					"shapType": "rect"
				},
				// more...
			],
			"layoutElements": [
				// more...
			],
			"note": "Speaker notes content..."
		},
		// more...
	],
	"themeColors": ['#4472C4', '#ED7D31', '#A5A5A5', '#FFC000', '#5B9BD5', '#70AD47'],
	"size": {
		"width": 960,
		"height": 540
	}
}

📕 Full Feature Support
Slide Theme Colors themeColors
Slide Size size
 * Slide width width
 * Slide height height
Slide Pages slides
Page Background Fill (Color, Image, Gradient) fill
Page Notes note
Page Elements elements / Master Slide Elements layoutElements
Text
 * Type type='text'
 * Horizontal coordinate left
 * Vertical coordinate top
 * Width width
 * Height height
 * Border color borderColor
 * Border width borderWidth
 * Border type (solid, dot, dash) borderType
 * Non-solid border style borderStrokeDasharray
 * Shadow shadow
 * Fill (color, image, gradient) fill
 * Content text (HTML rich text) content
 * Vertical flip isFlipV
 * Horizontal flip isFlipH
 * Rotation angle rotate
 * Vertical alignment vAlign
 * Whether it's vertical text isVertical
 * Element name name
Image
 * Type type='image'
 * Horizontal coordinate left
 * Vertical coordinate top
 * Width width
 * Height height
 * Border color borderColor
 * Border width borderWidth
 * Border type (solid, dot, dash) borderType
 * Non-solid border style borderStrokeDasharray
 * Crop shape geom
 * Crop area rect
 * Image URL (base64) src
 * Rotation angle rotate
Shape
 * Type type='shape'
 * Horizontal coordinate left
 * Vertical coordinate top
 * Width width
 * Height height
 * Border color borderColor
 * Border width borderWidth
 * Border type (solid, dot, dash) borderType
 * Non-solid border style borderStrokeDasharray
 * Shadow shadow
 * Fill (color, image, gradient) fill
 * Content text (HTML rich text) content
 * Vertical flip isFlipV
 * Horizontal flip isFlipH
 * Rotation angle rotate
 * Shape type shapType
 * Vertical alignment vAlign
 * Shape path path
 * Element name name
Table
 * Type type='table'
 * Horizontal coordinate left
 * Vertical coordinate top
 * Width width
 * Height height
 * Borders (4 sides) borders
 * Table data data
 * Row heights rowHeights
 * Column widths colWidths
Chart
 * Type type='chart'
 * Horizontal coordinate left
 * Vertical coordinate top
 * Width width
 * Height height
 * Chart data data
 * Chart theme colors colors
 * Chart type chartType
 * Bar chart direction barDir
 * Whether to include data markers marker
 * Donut chart hole size holeSize
 * Grouping mode grouping
 * Chart style style
Video
 * Type type='video'
 * Horizontal coordinate left
 * Vertical coordinate top
 * Width width
 * Height height
 * Video blob blob
 * Video source src
Audio
 * Type type='audio'
 * Horizontal coordinate left
 * Vertical coordinate top
 * Width width
 * Height height
 * Audio blob blob
Equation
 * Type type='math'
 * Horizontal coordinate left
 * Vertical coordinate top
 * Width width
 * Height height
 * Equation image picBase64
 * LaTeX expression (only common structures supported) latex
 * Text (exists when text and equations are mixed) text
SmartArt
 * Type type='diagram'
 * Horizontal coordinate left
 * Vertical coordinate top
 * Width width
 * Height height
 * Collection of child elements elements
Multi-element Group
 * Type type='group'
 * Horizontal coordinate left
 * Vertical coordinate top
 * Width width
 * Height height
 * Collection of child elements elements
For more types, please refer to 👇
https://github.com/pipipi-pikachu/pptxtojson/blob/master/dist/index.d.ts
🙏 Thanks
This repository heavily references the implementations of PPTX2HTML and PPTXjs.
> The difference from them is: PPTX2HTML and PPTXjs convert PPT files into runnable HTML pages, while pptxtojson converts PPT files into clean JSON data, with significant optimizations and additions to the original (including code quality and the completeness and accuracy of extracted information).
> 
📄 Open Source License
MIT License | Copyright © 2020-PRESENT pipipi-pikachu
(https://github.com/pipipi-pikachu)
