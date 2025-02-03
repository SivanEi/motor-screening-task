# motor-screening-task
Motor Screening Task
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>jsPsych MOT Task</title>

    <!-- Load jsPsych library -->
    <script src="https://cdn.jsdelivr.net/npm/jspsych@6.3.1/dist/jspsych.min.js"></script>
    <link href="https://cdn.jsdelivr.net/npm/jspsych@6.3.1/dist/css/jspsych.css" rel="stylesheet">

    <!-- Load jsPsych plugins for the task -->
    <script src="https://cdn.jsdelivr.net/npm/jspsych@6.3.1/plugins/jspsych-html-keyboard-response.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/jspsych@6.3.1/plugins/jspsych-survey-text.js"></script>
</head>
<body>

    <script>
        // Define jsPsych experiment timeline
        var timeline = [];

        // Simple trial: Display a message
        var trial1 = {
            type: "html-keyboard-response",
            stimulus: "<p>Press any key to start the task!</p>"
        };
        timeline.push(trial1);

        // Define the MOT task
        var mot_task = {
            type: 'html-keyboard-response',
            stimulus: '<p>Look at the screen. Press any key when you see the target.</p>',
            choices: ['space'],
            prompt: '<p>Press the space bar when you see the target appear!</p>',
            data: {
                task: 'mot'
            }
        };
        timeline.push(mot_task); // Add the MOT task to the timeline

        // Define a trial to collect participant information
        var survey_trial = {
            type: "survey-text",
            questions: [
                {prompt: "What is your name?", name: 'name'},
                {prompt: "What is your age?", name: 'age'}
            ]
        };
        timeline.push(survey_trial);

        // Initialize jsPsych and run the experiment
        var experiment = new jsPsych.init({
            timeline: timeline,
            on_finish: function() {
                jsPsych.data.displayData(); // Show the results after the experiment is completed
            }
        });
    </script>

</body>
</html>
