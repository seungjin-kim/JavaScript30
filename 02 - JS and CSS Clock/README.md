# 02 - JS AND CSS CLOCK
## Recap

- HTML DOM style Property

#### Initialize Pointer Positions
`transform-origin: 100%;`
- Allows pointer to rotate on its right most point
`transform: rotate(90deg);`
- The hands start horizontally but we want them pointing up and down at 12 o'clock position
`transition: all 0.05s;`
- When the hand rotates, 10, 20, 30, etc degrees, we want to show that transition and not jus the hand move to the new degree immediately
`transition-timing-function: cubic-bezier(0, 2.5, 0.58, 1);`
- This gives the Snappy Tik-tok effect of the hands 
- Combined with the fast 0.05s transition speed, it gives the snappy animation

#### Get Time
`setInterval(setDate, 1000);`
- `setInterval` function calls the setDate function at the interval specified to implement the rotating of the hands in accordance to current time
`const now = new Date();`
- The `Date` object provides `.getSeconds()`, `getMinutes()`, and `getHours()` methods
`const secondsDegrees = ((seconds / 60) * 360) + 90;`
- Like this, you can calculate the angles of the hands by using percentages
`secondHand.style.transform = `rotate(${secondsDegrees}deg)`;`
- The HTML DOM style property is used to set style of an element using CSS properties

#### Glitch At 12 O'Clock
- When the hands reach the 12 position, the hand transforms from 0 to 90 degrees all the way backwards
- The solution to this is when the hand reaches 90 degrees, take off the transition using an if statement and reapply it back

```
if (secondsDegrees === 90) {
  secondHand.style.transition = 'all 0s';
}
else {
  secondHand.style.transition = 'all 0.05s';
}
```
