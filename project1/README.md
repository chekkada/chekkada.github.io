# WAPH-Web Application Programming and Hacking

## Instructor: Dr. Phu Phung

**Name**: Durga Srija Chekka

**Email**: chekkada@mail.uc.edu

**Short-bio**: Durga Srija Chekka has keen interests in cloud computing and Machine learning.

![Srija'sHeadshot](images/SrijaHeadshot.jpeg)

## Repository Information

Respository's URL: [git@github.com:chekkada/waph-chekkada.git](git@github.com:chekkada/waph-chekkada.git)

This is a private repository for Durga Srija Chekka to store all code from the course. The organization of this repository is as follows.

# Individual Project 1 – Front-end Web Development with a Professional Profile Website on github.io cloud service

## Overview and Requirements 

For Individual Project 1, I created a professional profile webpage and hosted it on GitHub Pages. The website showcases my resume, talents, and experiences while also adding numerous technical functionalities such as the joke API, digital clock, analog clock, show my email address, weather API, and flag counter. The primary goals of this project were to improve my front-end web programming skills and gain actual experience deploying websites with GitHub Pages.

The link to access my website is: [https://chekkada.github.io/project1/index.html](https://chekkada.github.io/project1/index.html).

The link to access Individual Project-1 is: [https://github.com/chekkada/chekkada.github.io](https://github.com/chekkada/chekkada.github.io).

## General Requirements

### Personal Website on Github.io

Using the name {chekkada.github.io}, I established a new public repository. developed a personal GitHub Pages website with my resume, contact details, educational background, experiences, projects, certificates, and talents.

The link to access my website is: [https://chekkada.github.io/project1/index.html](https://chekkada.github.io/project1/index.html).

![Portfolio Website](images/Portfolio1.png)

### "Web Application Programming and Hacking" course and related hands-on projects on waph.html file

In order to introduce the "Web Application Programming and Hacking" course and its associated practical projects, I made a new page on my repository called waph.html. I provide summaries of Lab0, Lab1, Lab2, Hackathon 1, and Individual Project 1 in this. 

The link to access waph.html is: [https://chekkada.github.io/waph.html](https://chekkada.github.io/waph.html).

This page link is accessible from the personal website as shown in below screenshot:

![waph.html page link on website](images/waph-html1.png)

![waph.html page](images/waph-html2.png)

## Non-technical requirements

### Bootstrap Template

I have downloaded a bootstrap template from the website `https://bootstrapmade.com/` 

I modified the template to meet my requirements and the assignments provided by the instructor.

### Page Tracker

In order to track website visits and engagement, I included Flag Counter as a page tracker. 

from the two websites that are provided. {https://flagcounter.com/} is my choice. I used the website to produce a key, which I then included into my code. The integrated flag counter is accessible on the homepage of my website.

Code for integrating Flag Counter:

```html
<div style="text-align:left;">
    <a href="https://info.flagcounter.com/szVl"><img
        src="https://s11.flagcounter.com/count2/szVl/bg_FFFFFF/txt_000000/border_000000/columns_2/maxflags_10/viewers_0/labels_1/pageviews_1/flags_0/percent_0/"
        alt="Flag Counter" border="0"></a>
</div>
```

![Flag Counter](images/page_tracker.png)



## Technical requirements

### A digital clock; An analog clock; show/hide your email:

Similar to lab 2, i implemented an analog and digital clock that display the current time using JavaScript. I also included code that  reveal or hide the email address based on user interaction.

Source Code for digital clock:
```JS
function displayTime() {
          document.getElementById('digital-clock').innerHTML = "current time:" + new Date();
        }
        setInterval(displayTime, 500);
```

Source Code for Analog clock:
```JS
var canvas = document.getElementById("analog-clock");
        var ctx = canvas.getContext("2d");
        var radius = canvas.height / 2;
        ctx.translate(radius, radius);
        radius = radius * 0.90
        setInterval(drawClock, 1000);

        function drawClock() {
          drawFace(ctx, radius);
          drawNumbers(ctx, radius);
          drawTime(ctx, radius);
        }
```

Source Code for show/hide your email:

```JS
 function showhideEmail() {
            if (shown) {
                document.getElementById("email").innerHTML = "Show my email";
                shown = false;
            } else {
                var myemail =
                    "<a href='mailto:chekkada" +
                    "@" +
                    "ucmail.uc.edu'>chekkada" +
                    "@" +
                    "ucmail.uc.edu</a>";
                document.getElementById("email").innerHTML = myemail;
                shown = true;
            }
        }
```

Screenshot Showing Digital clock, Analog Clock, Show/hide your email:

![Digital clock, Analog Clock](images/clock.png)


### One more Functionality of my choice

Combining jQuery with the SweetAlert2 Library for Popup Alerts
html
Source code :
```JS
<script src="https://code.jquery.com/jquery-3.6.4.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/sweetalert2@10"></script>
```
 ```JS
    $(document).ready(function() {
      $("#showAlertBtn").click(function() {
        showAlert();
      });

      function showAlert() {
        Swal.fire({
          title: 'Hello!',
          text: 'This is a popup alert using SweetAlert2 and jQuery.',
          icon: 'success',
          confirmButtonText: 'OK'
        });
      }
    });
 ```
![Alert](images/alert.png)

### Joke API

Integrated the jokeAPI to fetch a new joke every minute and display it on the website.

Source code for Joke API:

```JS
$(document).ready(function () {
            $.get("https://v2.jokeapi.dev/joke/Programming?type=single", function (result) {
                console.log("From jokeAPI: " + JSON.stringify(result));
                $("#response").html("A programming joke of the day: " + encodeInput(result.joke));
            });
        });

        function encodeInput(input) {
            return input;
```
![Joke API ](images/jokeAPI.png)

### Weather API

Integrated the Weatherbit API to fetch current weather information for Cincinnati and display it on the website.

```JS

$(document).ready(function () {
var apiKey = '33ea3b7afa564085948b067ce5c9f0bb'; // Replace 'YOUR_API_KEY' with your actual API key from Weatherbit
 
$.get("https://api.weatherbit.io/v2.0/current", {
key: apiKey,
city: 'Cincinnati' // Example city, you can change it to any city you want
})
.done(function (data) {
if (data && data.data && data.data.length > 0) {
var weatherData = data.data[0];
var temperature = weatherData.temp;
var description = weatherData.weather.description;
var iconCode = weatherData.weather.icon;
 
var iconUrl = "https://www.weatherbit.io/static/img/icons/" + iconCode + ".png";
 
// Display weather information on the webpage
$("#weather-icon").attr("src", iconUrl);
$("#weather-details").html("<p>Temperature: " + temperature + "°C</p>" +
"<p>Description: " + description + "</p>");
} else {
$("#weather-info").html("<p>Unable to fetch weather data.</p>");
}
})
.fail(function () {
$("#weather-info").html("<p>Error occurred while fetching weather data.</p>");
});
});

```

![ weather API](images/weather.png)

### Javascript Cookies

JavaScript cookies were used to remember the client's visit and show customized messages according to the client's recurring or first-time status. When a user visits for the first time, it says "Welcome to my homepage!" and when they return, it says "Welcome back! (Last visit time and date) was when you last visited.

```JS
// Function to set or retrieve the value of a cookie
function setCookie(name, value, days) {
var expires = "";
if (days) {
  var date = new Date();
  date.setTime(date.getTime() + (days * 24 * 60 * 60 * 1000));
  expires = "; expires=" + date.toUTCString();
}
document.cookie = name + "=" + (value || "") + expires + "; path=/";
}

function getCookie(name) {
var nameEQ = name + "=";
var ca = document.cookie.split(';');
for (var i = 0; i < ca.length; i++) {
  var c = ca[i];
  while (c.charAt(0) === ' ') c = c.substring(1, c.length);
  if (c.indexOf(nameEQ) === 0) return c.substring(nameEQ.length, c.length);
}
return null;
}

// Function to check if it's the first-time visit
    function checkFirstVisit() {
      var isFirstVisit = getCookie("firstVisit");
      if (!isFirstVisit) {
        // Display welcome message for the first-time visit
        alert("Welcome to my homepage!");
        // Set the cookie to remember the visit for 365 days
        setCookie("firstVisit", "true", 365);
      } else {
        // Display welcome back message for returning visitors
        var lastVisit = getCookie("lastVisit");
        alert("Welcome back! Your last visit was " + lastVisit);
      }
      // Set the cookie for the current visit
      setCookie("lastVisit", new Date(), 365);
    }

    // Call the function to check for the first-time visit
    checkFirstVisit();
  </script>

      <script>
    // Function to check if it's the first-time visit
    function checkFirstVisit() {
      // Check if "firstVisit" key exists in localStorage
      if (!localStorage.getItem("firstVisit")) {
        // Display welcome message for the first-time visit
        alert("Welcome to my homepage!");
        // Set the "firstVisit" key in localStorage to remember the visit
        localStorage.setItem("firstVisit", true);
      }
    }

    // Call the function to check for the first-time visit
    checkFirstVisit();

```
![Revisit](images/cookies_time.png)
![Fisrt visit](images/wlcomecookie.png)
