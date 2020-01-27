# 01 - Drum Kit
## Recap

#### data-key Attribute
- Each letter of keyboard when pressed corresponds to a keyCode property (represnted as number)
- It is used in both <div> tag for visually represented button and <audio> tag
- data-key sets the mapping for buttons and audios and gets the keyCode via keydown event

#### Event Listeners
- `keydown` event on `window` is fired when a key is pressed and calls `playsound` function
- `window` is the global object in a brower, or the root object of the DOM. `document` stands for DOM 
```
 window.addEventListener('keydown', playSound);
```
- `transitionend` event is listened to on every `key` class which calls the `removeTransition` function
- `transitionend` event is fired when a CSS transition has completed, in this case the border of our button when a sound is played

#### Toggle Styles
- Add a class to an item (this way you can add css styling when key is pressed)
```
document.querySelector(`.key[data-key="${e.keyCode}"]`).classList.add('playing');
```
- Remove a class to undo the css styling by listening for the `transitionend` event
- In our case, we only removed event with `transform` property and added a condition to skip others, but any one of them can be chosen (choose one with longest transition time)
```
  function removeTransition(e) {
    if (e.propertyName !== 'transform') return;
    console.log(e)
    this.classList.remove('playing');
  }
```

#### forEach and Arrow Function
- Created an array of all the keys
- Iterated over each key and added an event listener
- Can't simply add event listener to `keys` because it's a node list
```
const keys = Array.from(document.querySelectorAll('.keys'));
keys.forEach(key => key.addEventListener('transitionend', removeTransition));
```

#### Audio Element
- The `<audio>` element is used to embed sound content in documents
```
<audio data-key="65" src="sounds/clap.wav"></audio>
```
- Audio `play()` method used to play audio
- Audio `currentTime` property used to reset audio to its beginning to allow audio to be pressed for play repeatedly

```
function playSound(e) {
  const sound = document.querySelector(`audio[data-key="${e.keyCode}"]`);
  if (!sound) return;
  sound.currentTime = 0;
  sound.play();
  document.querySelector(`.key[data-key="${e.keyCode}"]`).classList.add('playing');
}
```

#### Other Bits
- Template literal is used to use reference to javascript variable `e.keyCode` to dynamically select audio tag based on keydown event's keyCode.
```
const sound = document.querySelector(`audio[data-key="${e.keyCode}"]`);
```
- `querySelector() returns first Eleent within the document that matches the specified selector, or group of selectors. If no matches are found, null is returned
```
element = document.querySelector(selectors);
```
- Attribute selector matches elements based on presence or value of a given attribute
