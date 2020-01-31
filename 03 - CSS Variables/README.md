# 03 - CSS Variables
## Recap

#### CSS Variables
- Declare a custom property on the :root pseudo-class and use it where needed throughout the document to reduce repetition
```
:root {
  --base: #BADA55;
  --spacing: 20px;
  --blur: 10px;
}
```
```
img {
  background: var(--base);
  padding: var(--spacing);
  filter: blur(var(--blur));
}
```

#### Set a CSS Variable's Value Using JavaScript
- Use `setProperty` on `documentElement`'s `style` property:
```
document.documentElement.style.setProperty(`--${this.name}`, this.value + suffix);
```

#### Data Attribute and Dataset
- `data-*` allows us to store extra information on standard, semantic HTML elements without other hacks
```
<input id="blur" type="range" name="blur" min="0" max="25" value="10" data-sizing="px">
```
- Here we store the suffix "px" in the data-sizing attribute
- We use it to set CSS Variable's value that has a "px" suffix
```
function handleUpdate() {
  console.log(this.dataset.sizing);
  const suffix = this.dataset.sizing || ''
  document.documentElement.style.setProperty(`--${this.name}`, this.value + suffix);
}
```


#### Events
- `change` event is fired for `<input>`, `<select>`, and `<textarea>` elements when an alteration to the element's value is commited by the user
- `mousemove`event is fired at an element when a pointing device (usually a mouse) is moved while the cursor's hotspot is inside it





css variables
chaining query selector for nested elements
array vs node list
change and mousemouse event listeners
data attribute - it's something you make up by prefixing with data-
dataset -> takes everything that has data- on that element and puts it together in an object
document.documentelement