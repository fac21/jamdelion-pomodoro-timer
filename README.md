# FAC Pre-course: Week 4
## Consolidating the pre-course work! :sweat_smile:

### Task :star:

This week we had to make a [Pomodoro](https://en.wikipedia.org/wiki/Pomodoro_Technique) timer, featuring: 

- A “work” timer that counts down to zero (usually from 25 minutes)
- A “break” timer that counts down to zero (usually from 5 minutes)
- Buttons to start a session, pause the timer, or cancel the session and restart.

#### Stretch goals

* [ ] Customisable lengths of time for work/break
* [ ] Play an alarm sound to make it obvious the time is up

## My work process (rough notes)

1. Initialised the html file first, and used the console to try and figure out some functionality.
1. I wrote an `initialiseTimer` function, which involved some maths, like modulo and the `Math.round` and `Math.floor` methods to countdown the minutes.
1. I added some basic html elements and decided to use `innerHTML` to display and change the time.
1. Wrote the `decrementByOne` function
1. Tried adding event listener to start button to run "decrementbyone" function every second
1. Used `setTimeout` to kick off the next timer after the requisite time period.
1. Made two timers, a work timer and play timer, and made function "start next timer", to try and not have too much logic in one place. 
1. Had a go at the stretch goal of using inputs to the timer. I wanted the countdown to also be happening inside the input box. **There were lots of handy attributes for placeholder values and min/max values** :raised-hands:
1. Tried to get the style to change based on the page "listening" to whether the workState variable had changed - turned out that this wasn't really possible (after chasing a checkbox hack down a long rabbit hole... :rabbit:). 
1. Eventually wrote a new function that changed the body style and the workState variable in the same function. :relieved:

### Handy tricks :sparkle: 
Lots of console logging for when it doesn't work:

``` javascript
start.addEventListener("click", () => {
            console.log(timer);
            setInterval(() => {
                timer = decrementByOne(timer);
            }, 1000)
            console.log(timer);
```

### Problems encountered 

-  The timer was able to be stopped, but not restarted.
- - The countdownTimer was out of scope. 
:bulb: Solved by defining in a bunch of variables at the top of file. 

- Timer goes into negative numbers
:bulb: Add extra if loop in `decrementByOne` to catch this case. 

- Funky things were happening when I tried to initialise a new timer inside the startTimeout function --> think there was just one timer at this point (it was decrementing by 2 seconds at a time)

- Originally, I had "if work is 0", then start other timer but realised I needed a variable to keep hold of what time period we were in. (work state). 

### What I learned :muscle: 

:bulb: To get `clearInterval` to work, I had to move the `setInterval` into its own variable (since it returns the id of the timer).
``` javascript
let countdownTimer = setInterval(() => {
        countdown.innerHTML = decrementByOne(countdown.innerHTML);
    }, 1000);
``` 
instead of:
``` javascript
        // start.addEventListener("click", () => {
        //     setInterval(() => {
        //         countdown.innerHTML = decrementByOne(countdown.innerHTML);
        //     }, 1000)
        // });
```

:bulb: You can use `.querySelector()` on elements other than `Document` (to access childnodes).

:bulb: There's no such thing as an event listener for variable states. 

:bulb: `addEventListener("change", ...)` only works on checkboxes for when the *user* has changed the checkbox, not for if the JS changes it. 

### Questions 

:question: How can I easily see other people's code **in action** from GitHub? Is it only possible if the code is deployed somewhere? (or if clone and run it locally?)







