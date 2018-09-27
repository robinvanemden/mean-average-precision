# mean-average-precision

For explanation about mAP, please read https://github.com/Cartucho/mAP

## install

```
npm install mean-average-precision
```

## prediction format

Every prediction/ground truth objects should look like 
<class_name> <confidence> <left> <top> <right> <bottom>
```
{
	label: "car",
	left: 22,
	top: 34,
	right: 231,
	bottom: 78,
}
```

## example

```
const mAP = require('mean-average-precision')
const groundTruths = [{
			filename: "image1.jpg",
			label: "car",
			left: 22,
			top: 34,
			right: 231,
			bottom: 78,
		},{
			filename: "image1.jpg",
			label: "pedestrian",
			left: 22,
			top: 34,
			right: 231,
			bottom: 78,
	}];

const predictions = [{
		filename: 'image1.jpg',
		confidence: 0.9,
		label: 'car',
		left: 25,
		top: 38,
		right: 201,
		bottom: 90
	}, {
		filename: 'image1.jpg',
		label: 'pedestrian',
		confidence: 0.7,
		left: 32,
		top: 39,
		right: 452,
		bottom: 92
	}, {
		filename: 'image1.jpg',
		confidence: 0.5,
		label: 'car',
		left: 541,
		top: 42,
		right: 621,
		bottom: 94
	}];
	
	
mAP({
	groundTruths,
	predictions
});

// returns 0.5
```