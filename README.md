import {Component} from 'react'

import './index.css'

class Stopwatch extends Component { state = { isTimerRunning: false, timeElapsedInSeconds: 0, }

componentWillUnmount() { clearInterval(this.timeInterval) }

onResetTimer = () => { clearInterval(this.timeInterval) this.setState({isTimerRunning: false, timeElapsedInSeconds: 0}) }

onStopTimer = () => { clearInterval(this.timeInterval) this.setState({isTimerRunning: false}) }

updateTime = () => { this.setState(prevState => ({ timeElapsedInSeconds: prevState.timeElapsedInSeconds + 1, })) }

onStartTimer = () => { this.timeInterval = setInterval(this.updateTime, 1000) this.setState({isTimerRunning: true}) }

renderSeconds = () => { const {timeElapsedInSeconds} = this.state const seconds = Math.floor(timeElapsedInSeconds % 60)

    if (seconds < 10) {
      return `0${seconds}`
    }
    return seconds

}

renderMinutes = () => { const {timeElapsedInSeconds} = this.state const minutes = Math.floor(timeElapsedInSeconds / 60)

    if (minutes < 10) {
      return `0${minutes}`
    }
    return minutes

}

render() { const {isTimerRunning} = this.state const time = `${this.renderMinutes()}:${this.renderSeconds()}`

    return (
      <div className="app-container">
        <div className="stopwatch-container">
          <h1 className="stopwatch">Stopwatch</h1>
          <div className="timer-container">
            <div className="timer">
              <img
                className="timer-image"
                src="https://assets.ccbp.in/frontend/react-js/stopwatch-timer.png"
                alt="stopwatch"
              />
              <p className="timer-text">Timer</p>
            </div>
            <h1 className="stopwatch-timer">{time}</h1>
            <div className="timer-buttons">
              <button
                type="button"
                className="start-button button"
                onClick={this.onStartTimer}
                disabled={isTimerRunning}
              >
                Start
              </button>
              <button
                type="button"
                className="stop-button button"
                onClick={this.onStopTimer}
              >
                Stop
              </button>
              <button
                type="button"
                className="reset-button button"
                onClick={this.onResetTimer}
              >
                Reset
              </button>
            </div>
          </div>
        </div>
      </div>
    )

} }

export default StopwatchIn this project, let's fix the **Stopwatch** by applying the concepts we have learned till now.

### Refer to the image below:

<br/>
<div style="text-align: center;">
    <img src="https://assets.ccbp.in/frontend/content/react-js/stopwatch-output-v2.gif" alt="stopwatch output" style="max-width:70%;box-shadow:0 2.8px 2.2px rgba(0, 0, 0, 0.12)">
</div>
<br/>

### Set Up Instructions

<details>
<summary>Click to view</summary>

- Download dependencies by running `npm install`
- Start up the app using `npm start`
</details>

### Completion Instructions

<details>
<summary>Functionality to be fixed</summary>
<br/>

Fix the given code to have the following functionality

- When the **Start** button is clicked, then the Stopwatch should start running
- When the **Stop** button is clicked, then the Stopwatch should stop running
- When the **Reset** button is clicked, then the Stopwatch should be reset to zero

</details>

### Quick Tips

<details>
<summary>Click to view</summary>
<br>

- There are `10` bugs to be fixed to achieve the functionality and the UI that is expected

</details>

> ### _Things to Keep in Mind_
>
> - All components you implement should go in the `src/components` directory.
> - Don't change the component folder names as those are the files being imported into the tests.
> - **Do not remove the pre-filled code**
> - Want to quickly review some of the concepts you’ve been learning? Take a look at the Cheat Sheets.
