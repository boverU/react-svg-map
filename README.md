# react-svg-map

A React.js component to display an interactive SVG map.

## Demo

[Take a look at the live demo!](https://victorcazanave.com/react-svg-map)

## Installation

`npm install react-svg-map`

## Usage

* Import `SVGMap` component and the map you want from `react-svg-map`.
* Optionally, import `react-svg-map/lib/index.css` if you want to apply the default styles.

```javascript
import React from 'react';
import ReactDOM from 'react-dom';
import { SVGMap, Taiwan } from 'react-svg-map';
import 'react-svg-map/lib/index.css';

class App extends React.Component {
  constructor(props) {
    super(props);
  }

  render() {
    return (
      <SVGMap map={Taiwan} />
    );
  }
}

ReactDOM.render(
  <App />,
  document.getElementById('app')
);
```

## API

| Prop | Type | Default | Description |
| ---- | ---- | ------- | ----------- |
| map | object | **required** | Describe SVG map to display. See [maps section](#maps) for more details. |
| tabIndex | string | '0' | Tabindex of each location. This property is used to set the `tabindex` HTML attribute. |
| type | string | 'none' | Type of each location: 'checkbox'/'radio'/'link'. This property is used to set the `role` HTML attribute and should match the behavior of your map. |
| onLocationMouseOver | func |  | Invoked when the user put the mouse over a location. |
| onLocationMouseOut | func |  | Invoked when the user put the mouse out of a location. |
| onLocationClick | func |  | Invoked when the user click on a location. |
| onLocationFocus | func |  | Invoked when the user focus a location (with mouse or keyboard). |
| onLocationBlur | func |  | Invoked when the user unfocus a location. |
| isLocationSelected | func |  | Executed to determine if a location is selected when using checkbox or radio behavior. This property is used to set the `aria-checked` HTML attribute. |

## Maps

### Existing maps

The component provides maps that can be imported and used directly.

#### Australia

TBA

#### France

TBA

#### Taiwan

Locations:
* Changhua County
* Chiayi City
* Chiayi County
* Hualien County
* Hsinchu City
* Hsinchu County
* Kaohsiung City
* Keelung City
* Miaoli County
* Nantou County
* New Taipei City
* Penghu County
* Pingtung County
* Taichung City
* Tainan City
* Taipei City
* Taitung County
* Taoyuan City
* Yilan County
* Yunlin County

### Custom maps

You can modify existing maps or create your own.

#### Modify a map

1. Import the map to modify.
1. Create a new object from this map.
1. Pass this new object as `map` prop of `SVGMap` component.

```javascript
import React from 'react';
import { SVGMap, Taiwan } from 'react-svg-map';

class App extends React.Component {
  constructor(props) {
    super(props);

		this.customTaiwan = {
			...Taiwan,
			label: 'Custom map label',
			locations: Taiwan.locations.map((location) => {
				// Modify each location
			})
		}
  }

  render() {
    return (
      <SVGMap map={this.customTaiwan} />
    );
  }
}
```

It is recommended to not modify the SVG properties (viewBox, path), because it may break the map's display.

#### Create a map

If you create a new map (other country, city...), feel free to share it creating a pull request to add it in `src/maps/`!
