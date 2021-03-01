# jamdelion-pomodoro-timer
A pomodoro timer written in vanilla JS for FAC21's pre-course.



<!-- work timer counts to 0 from 25 minutes -->
<!-- break timer that counts to 0 from 5 minutes -->
<!-- start/stop/cancel buttons -->

<!-- stretch: alarm sound -->
<!-- stretch: customisable time lengths -->

**ROUGH NOTES FOR README:**

Initialised a html file
Used the console to try and figure out the functionality
write "initialise timer" function - involved some maths, like modulo and the Math.round and Math.floor methods.

added some basic html elements - buttons and timer class (00:00 inner html)
assign elements to DOM variables - now timer is initialised with 25 on start. 

decrement by one function

try adding event listener to start button to run "decrementbyone" function every second

lots of console logging for when it doesn't work 
start.addEventListener("click", () => {
            console.log(timer);
            setInterval(() => {
                timer = decrementByOne(timer);
            }, 1000)
            console.log(timer);

to get clearInterval to work, had to move the setInterval into its own variable (since it returns the id of the timer).
        let countdownTimer = setInterval(() => {
                countdown.innerHTML = decrementByOne(countdown.innerHTML);
            }, 1000);

instead of
        // start.addEventListener("click", () => {
        //     setInterval(() => {
        //         countdown.innerHTML = decrementByOne(countdown.innerHTML);
        //     }, 1000)
        // });

could stop the timer but then not restart it - countdownTimer out of scope. Solved by defining in a bunch of variables at the top of file. 

Goes into negative numbers - add extra if loop

Use setTimeout to kick off a new thing after the requisite time period

Funky things happening when tried to initialise a new timer inside the startTimeout function --> think there was just one timer at this point (it was decrementing by 2 seconds at a time)

function startTimeout() {
            let timeUntilChange = getTimePeriod(countdown.innerHTML);
            let timeout = setTimeout(() => {
                console.log("Timeout");
                countdown.innerHTML = initialiseTimer(timer, 0.1);
                countdownTimerId = startTimer();
                timeoutId = startTimeout();
            }, timeUntilChange);
            return timeout;
        }

Made two timers, a work timer and play timer, and invented fictional function "start next timer", to try and not have too much logic in one place. 

originally had "if work is 0", then start other timer but realised I needed a variable to keep hold of what time period we were in. (work state)

How to easily see other people's code in action from github?

Turn into inputs (lots of handy attributes for placeholder values and min/max values)

learnt = can do queryselector on elements other than document (e.g. to access childnodes. )

tried stuff with checkboxes to get style to change -- need to track variable but no such thing as an event listener for variable state. 
Checkbox hack? But only works for user inputs. 
Eventually wrote new function that changed body style and variable in same function.