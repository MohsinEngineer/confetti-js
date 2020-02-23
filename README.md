# 🎉 <a href="https://agezao.github.io/confetti-js" target="_blank">Confetti Generator</a> 🎉
Easily Generate random confetti with javascript and make your design look cooler

<a href="https://www.npmjs.com/package/confetti-js"><img src="https://badge.fury.io/js/confetti-js.svg"></a>

## Demo 🚀
<a href="https://agezao.github.io/confetti-js" target="_blank">Demo</a> // <a href="https://agezao.github.io/confetti-js/examples" target="_blank">Examples</a>

## Why?
Have you ever seen that cool looking confetti on landing pages and above-the-fold content? We give you the power to create the same effect for free and without the hassle of having to design or code it from scratch.

## Installing/Using
### 📲 Downloading
- Using `npm`

  ```bash
    npm install confetti-js --save
  ```

- Direct download -> [click here](https://github.com/agezao/confetti-js/archive/master.zip)

### ➕ Add scripts
- The `classic` way
  ```html
  <script src="node_modules/confetti-js/dist/index.min.js"></script>
  ```

- ES6 module

  ```javascript
  // At the component you want to use confetti
  import ConfettiGenerator from "confetti-js";
  ```

### 🤔 How to use it?
After installing the plugin(the topic above), just call-it passing your options:
#### html
```html
<canvas id="my-canvas"></canvas>
```

#### javascript
```javascript
var confettiSettings = { target: 'my-canvas' };
var confetti = new ConfettiGenerator(confettiSettings);
confetti.render();
```

### React

```jsx
React.useEffect(() => {
  const confettiSettings = { target: 'my-canvas' };
  const confetti = new ConfettiGenerator(confettiSettings);
  confetti.render();

  return () => confetti.clear();
}, []) // add the var dependencies or not
```

### Angular

```typescript
import { Component, ViewChild, ElementRef } from '@angular/core';
import ConfettiGenerator from "confetti-js";

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.sass']
})
export class AppComponent {
  @ViewChild('my-canvas', { static: false }) myCanvas: ElementRef;
  public confetti: ConfettiGenerator;
  
  constructor() {}

  ngAfterViewInit() {
    var confettiSettings = { target: this.myCanvas.nativeElement }; // Passing the canvas element itself instead of id
    this.confetti = new ConfettiGenerator(confettiSettings);
    
    console.log("Dropping confetti");
    this.confetti.render();
    setTimeout( () => {
      this.confetti.clear();
    }, 5000); // Stop confetti after 5 seconds
  }
}
```

done!

## Options

| Attribute | Description | Example value | Default value |
|---------------------------|-------------|--------------------|---------|
| *`target`* | The Id tag of the canvas that will be used | 'my-canvas' | 'confetti-holder' |
| *`max`* | The number of props(confetti) to be rendered | 11 | 80 |
| *`size`* | Prop size | 1.8 | 1 |
| *`animate`* | If the confetti should fall | false | true |
| *`respawn`* | If the confetti should be recreated after going off-screen | false | true |
| *`clock`* | The speed confetti fall | 50 | 25 |
| *`props`* | The type of props(confetti) that should be rendered. In addition to those listed in the default, there's a special "svg" type which requires further configuration and is detailed below. | ['circle', 'square'] | ['circle', 'square', 'triangle', 'line'] |
| *`colors`* | The color to be rendered on the confetti. By default, RGB format inside an array. | [[0,0,0], [255,255,255]] | [[165,104,246],[230,61,135],[0,199,228],[253,214,126]] |
| *`start_from_edge`* | Whether the confettis should fall from the top of the screen (or should move up from the bottom) | true | false |
| *`width`* | Canvas width | 960 | *window size* |
| *`height`* | Canvas height | 767 | *window height* |
| *`rotate`* | If set to `true`, SVG and squares will rotate while falling. | `true` | `false` |

### Special SVG particle type

There is an extra special partical type ("prop") which allows you to render SVGs as confetti particles. For example:

```json
{
  "props": [
    "circle",
    "square",
    { "type": "svg", "src": "site/hat.svg" }
  ]
}
```

You must specify the `type` and `src` properties. There are also a few other configuration properties available to SVG objects:


| Attribute | Description | Example value | Default value |
|---------------------------|-------------|--------------------|---------|
| *`size`* | Set the size of the SVG when it renders as a particle. | `25` | `15` |
| *`weight`* | The probability of this particle being rendered, where 1 is a regular weight, and 0.1 is uncommon. | `0.5` | `1` |

## API
Using the object generated by `new ConfettiGenerator()` is pretty easy, there're just two main methods actually.

| Method | Description |
|---------------------------|-------------|
| *`render`* | Render the confetti at the config `<canvas/>` |
| *`clear`* | Clear the `<canvas/>` where the confetti where rendered |

```javascript
var confetti = new ConfettiGenerator();
confetti.render();
//
confetti.clear();
```

## License
You can use/hack/re-distribute/do whatever you want with this for free without having to credit the author or anything. Go on, just do it.

_But if you take the time to contribute with the project it would be nice too, just saying :)_

## Thanks
Special thanks to _["Paper Matthew"](https://codepen.io/paper_matthew/pen/PNxrbK)_ on codepen for providing the starting point wich I fork to build this. You are awesome.
