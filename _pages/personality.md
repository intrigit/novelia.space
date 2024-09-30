---
layout: default
title: personality
nav: true
nav_order: 2
permalink: /personality/
---

{% assign table_cell_style = "style='width: 40%'" %}
{% assign nospace_style = "style='padding-top: 0rem; padding-bottom: 0rem; padding: 0rem; margin-top: 0rem;'" %}

<style>
  table {
    margin-top: 1rem;
  }
  th, td {
    border-bottom: 1px solid #dee2e6;
  }
  .dot {
    height: 1rem;
    width: 1rem;
    background-color: var(--global-theme-color);
    border-radius: 50%;
    display: inline-block;
    opacity: 0.5;
  }
  .dot-their { background-color: var(--blue); }

  .text {
    color: var(--global-theme-color);
    opacity: 0.8;
  }
  .text-their { color: var(--blue); }

  .slider {
    appearance: none;
    width: 100%;
    height: 0.5rem;
    border-radius: 0.5rem;  
    background: #cccccc;
    outline: none;
    opacity: 0.5;
  }
  .slider::-webkit-slider-thumb {
    -webkit-appearance: none;
    appearance: none;
    width: 1rem;
    height: 1rem;
    border-radius: 50%; 
    background: var(--global-theme-color);
  }
  .slider::-moz-range-thumb {
    width: 1rem;
    height: 1rem;
    border-radius: 50%;
    background: var(--global-theme-color);
  }

  .slider-their {}
  .slider-their::-webkit-slider-thumb {
    background: var(--blue);
  }
  .slider-their::-moz-range-thumb {
    background: var(--blue);
  }
</style>

<header class="post-header">
  <h1 class="post-title">Personality Test</h1>
</header>

<p>Thank you for participating in
<span title="An Interiors Iridescence project that helps me track my personality and understand the not-self. You know too much.">my personality test</span>!</p>

<p>If you intend to evaluate your own personality, please select "Evaluate yourself";
if you are invited by another person to evaluate their personality, please select "Evaluate another person";</p>

<table class="table">
  <tr>
    <td {{ table_cell_style }}>Context action</td>
    <td>
      <form id="purpose" action="" method="">
      Evaluate yourself <input type="radio" name="purpose-radio" value="your" onclick="onClick()" />&emsp;
      Evaluate another person <input type="radio" name="purpose-radio" value="their" onclick="onClick()" />&emsp;
      <span class="h-resume" style="display: none;">Resume your last evaluation</span> <input class="h-resume" type="radio" name="purpose-radio" value="purpose-resume" onclick="loadAnswersFromStorage()" style="display: none;" />&emsp;
      </form>
    </td>
  </tr>
</table>

<div id="purpose-evaluate" style="display: none;">

<p>Please allow me to guide you through the process.
It usually takes you 15-30 minutes to complete this survey.</p>
<!-- You can hover over the text with <span title="Good job!">question marks<sup>?</sup></span> for hints. -->

<div id="purpose-evaluate-your" style="display: none;">

<p>A nice thing with this test is that you can evaluate another person side-by-side and compare the results. Evaluating yourself and another person at the same time can increase the objectivity of your answers.</p>

<p>If you want to evaluate another person as well, please check the following box.</p>

<table class="table">
  <tr>
    <td {{ table_cell_style }}>Evaluate another person as well</td>
    <td>
      <input type="checkbox" id="checkbox-show-their" onclick="onClick()">
    </td>
  </tr>
</table>

</div>

<div id="purpose-evaluate-their" style="display: none;">

<p>A nice thing with this test is that you can evaluate yourself side-by-side and compare the results. Evaluating yourself and another person at the same time can increase the objectivity of your answers.</p>

<p>If you want to evaluate yourself as well, please check the following box.</p>

<table class="table">
  <tr>
    <td {{ table_cell_style }}>Evaluate yourself as well</td>
    <td>
      <input type="checkbox" id="checkbox-show-your" onclick="onClick()">
    </td>
  </tr>
</table>

</div>

<p>Before beginning, please tell me some basic information regarding you and/or the other person.
<!-- The nickname doesn't need to be your real name, so long as I can recognize you by it. -->
Age and gender info will be used to better situate you among your peers.</p>

<p>The email fields are optional. If you provide your email, a copy of your evaluation results, both regarding yourself and/or the other person, will be sent to your mailbox. If the other person's email is provided, they will receive a copy of your evaluation result of them, but they will not receive anything about your evaluation of yourself.</p>
<!-- <p>To be able to retrieve your results later, please keep a note of which email you use.</p> -->

<table class="table">
  <tr id="your-tr-age" class="h-your-only" style="display: none;">
    <td {{ table_cell_style }}>Your age*</td>
    <td>
      <input type="text" id="age" name="age" size="2" placeholder="e.g., 17">
    </td>
  </tr>
  <tr id="their-tr-age" class="h-their-only" style="display: none;">
    <td {{ table_cell_style }}>Their age*</td>
    <td>
      <input type="text" id="their-age" name="their-age" size="2" placeholder="e.g., 17">
    </td>
  </tr>
  <tr id="your-tr-gender" class="h-your-only" style="display: none;">
    <td>Your gender*</td>
    <td>
      Male <input type="radio" name="gender-radio" value="m" />&ensp;
      Female <input type="radio" name="gender-radio" value="f" />&ensp;
    </td>
  </tr>
  <tr id="their-tr-gender" class="h-their-only" style="display: none;">
    <td>Their gender*</td>
    <td>
      Male <input type="radio" name="their-gender-radio" value="m" />&ensp;
      Female <input type="radio" name="their-gender-radio" value="f" />&ensp;
    </td>
  </tr>
  <tr id="your-tr-email">
    <td>Your email</td>
    <td>
      <input type="text" id="email" name="email" placeholder="e.g., my@example.com">
    </td>
  </tr>
  <tr id="their-tr-email" class="h-their-only" style="display: none;">
    <td>Their email</td>
    <td>
      <input type="text" id="their-email" name="their-email" placeholder="e.g., their@example.com">
    </td>
  </tr>
</table>

<p class="h-their-only" style="display: none;"> You can also optionally fill in an adjective that best describes the other person. The adjective can be in any language you like, and will be included in the email sent to them.</p>

<table class="table">
  <tr id="their-tr-adjective" class="h-their-only" style="display: none;">
    <td>Use one adjective to describe the other person</td>
    <td>
      <input type="text" id="their-adjective" name="their-adjective" placeholder="e.g., passionate">
    </td>
  </tr>
</table>

<p>Now, let me introduce what you need to do in the test.
This test consists of 61 multiple choice questions for you to answer.
An example question is provided below.
For each question, a statement is displayed on the left, and your goal is to choose your level of agreement with the statement:</p>

<p><u>1 = Strongly disagree&emsp;2 = Disagree&emsp;3 = Neutral&emsp;4 = Agree&emsp;5 = Strongly agree</u></p>

<p>This example question will not affect your final results.</p>

<table class="table">
  <tr>
    <td colspan="2" {{ nospace_style }}>
      <table width="100%" {{ nospace_style }}>
        <tr class="h-your-only" style="display: none;">
          <td {{ table_cell_style }}>
            <span id="your-form-header-example">0. You&emsp;are a happy person<br/></span>
          </td>
          <td>
            <form id="your-form-example" action="" method="">
              {%for i in (1..5) %}
              {{ i }} <input type="radio" name="your-radio-example" value="{{ i }}" />&ensp;
            {%endfor %}
            <!-- (<span title="The subject of evaluation. 'you' means that you need to decide whether you are a good person yourself.">you<sup>?</sup></span>) -->
            </form>
          </td>
        </tr>
        <tr class="h-their-only" style="display: none;">
          <td {{ table_cell_style }}>
            <span id="their-form-header-example">0. They&ensp;are a happy person</span>
          </td>
          <td>
            <form id="their-form-example" action="" method="">
              {%for i in (1..5) %}
              {{ i }} <input type="radio" name="their-radio-example" value="{{ i }}" />&ensp;
            {%endfor %}
            <!-- (<span title="The subject of evaluation. 'they' means that you need to decide whether 'they', the person you are evaluating, are a happy person.">they<sup>?</sup></span>) -->
            </form>
          </td>
        </tr>
      </table>
    </td>
  </tr>
</table>

<p>You are now ready! By continuing, you consent to my collection of anonymized data for personal analysis. The collected data will not be disclosed to any third party.</p>

<table class="table" id="table" style="display: none;">
  <tr>
    <th {{ table_cell_style }}>Question</th>
    <th>Your Level of Agreement</th>
  </tr>
  {%for item in site.data.bigfive.questions %}
  {% assign index0 = forloop.index0 %}
  <tr>
    <td colspan="2" {{ nospace_style }}>
      <table width="100%" {{ nospace_style }}>
        <tr class="h-your-only" style="display: none;">
          <td {{ table_cell_style }}>
            <span id="your-form-header-{{ index0 }}">{{ forloop.index }}. You&emsp;{{ item }}<br/></span>
          </td>
          <td>
            <form id="your-form-{{ index0 }}" action="" method="">
              {%for i in (1..5) %}
                {{ i }} <input type="radio" name="your-radio-{{ index0 }}" value="{{ i }}" onclick="saveAnswersToStorage()" />&ensp;
              {%endfor %}
            </form>
          </td>
        </tr>
        <tr class="h-their-only" style="display: none;">
          <td {{ table_cell_style }}>
            <span id="their-form-header-{{ index0 }}">{{ forloop.index }}. They&ensp;{{ item }}</span>
          </td>
          <td>
            <form id="their-form-{{ index0 }}" action="" method="">
              {%for i in (1..5) %}
                {{ i }} <input type="radio" name="their-radio-{{ index0 }}" value="{{ i }}" onclick="saveAnswersToStorage()" />&ensp;
              {%endfor %}
            </form>
          </td>
        </tr>
      </table>
    </td>
  </tr>
  {%endfor %}
</table>

<p>Now, you may want to review your answers. If you are done, please click the button below.</p>

<table class="table">
  <tr>
    <td {{ table_cell_style }}>Submit the answer</td>
    <td>
      <button id="btn-submit" onclick="onSubmit()">Submit!</button>
    </td>
  </tr>
</table>

<p id="output">After you submit, the results will be displayed below.</p>

<table class="table" id="table-result" style="display: none;">
  <tr>
    <th>Aspect</th>
    <th colspan="3" class="text-center">
      <span class="dot h-your-only" style="display: none;"></span>&ensp;<span class="h-your-only" style="display: none;">Your result&emsp;</span>
      <span class="dot dot-their h-their-only" style="display: none;"></span>&ensp;<span class="h-their-only" style="display: none;">Their result</span>
    </th>
    <th width="50%">Interpretation</th>
  </tr>
  {%for i in (0..4) %}
  <tr>
    <td rowspan="2" class="text-center" style="vertical-align: middle;">{{ site.data.bigfive.aspects[i] }}</td>
    <td colspan="4">{{ site.data.bigfive.aspects_desc[i] }}</td>
  </tr>
  <tr>
    <td class="text-right">{{ site.data.bigfive.aspects_l[i] }}</td>
    <td class="text-center">
      <input type="range" min="0" max="100" value="50" class="slider h-your-only" id="your-aspect-{{ i }}" disabled=true style="display: none;">
      <input type="range" min="0" max="100" value="50" class="slider slider-their h-their-only" id="their-aspect-{{ i }}" disabled=true style="display: none;">
    </td>
    <td>{{ site.data.bigfive.aspects_r[i] }}</td>
    <td>
      <div id="your-aspect-interp-{{ i }}" class="text h-your-only" style="display: none;"></div>
      <div id="their-aspect-interp-{{ i }}" class="text-their h-their-only" style="display: none;"></div>
    </td>
  </tr>
  {%endfor %}
</table>
<hr>

<p><u>Credits</u></p>

<p>Soto, C. J., & John, O. P. (2017). The next Big Five Inventory (BFI-2): Developing and assessing a hierarchical model with 15 facets to enhance bandwidth, fidelity, and predictive power. Journal of Personality and Social Psychology, 113, 117-143.</p>

<p>Potter, J. (2017). Big Five Personality Test. Out of Service. Available at: <a href="https://www.outofservice.com/bigfive/">https://www.outofservice.com/bigfive/</a> [Accessed 15 July. 2023].</p>

<p>and lastly, you.</p>

<script>
  const numQuestions = {%for item in site.data.bigfive.questions %} {{ forloop.length }} {% break %} {% endfor %};
  const queryString = window.location.search;
  const urlParams = new URLSearchParams(queryString);
  if (urlParams.has('theiremail')) {
    document.getElementById('their-email').value = urlParams.get('theiremail');
  }
  showClassIf("h-resume", localStorage.getItem("apkg") !== null);

  function matchAll(regex, s) {
    const res = []
    let m;
    do {
      m = regex.exec(s);
      if (m) {
        res.push(m[1]);
      }
    } while (m);
    return res;
  }

  function highlight(elemId) {
    console.log("highlighting " + elemId);
    document.getElementById(elemId).scrollIntoView({ behavior: "smooth", block: "end" });
    const elem = $("#" + elemId);
    elem.css({ backgroundColor: '#ff8888' }); // TODO: color animation
    setTimeout(function () { document.getElementById(elemId).style.backgroundColor = null; }, 2000);
  }

  function highlightIf(elemId, If) {
    if (If) {
      highlight(elemId);
      return true;
    }
    return false;
  }

  function showElementIf(elemId, If) {
    // TODO: animate element display
    if (If) document.getElementById(elemId).style.display = null;
    else document.getElementById(elemId).style.display = "none";
  }

  function showClassIf(className, If) {
    let elements = document.getElementsByClassName(className);
    for(let i = 0; i < elements.length; i++) {
      if (If) elements[i].style.display = null;
      else elements[i].style.display = "none";
    }
  }

  function isYour() {
    const purposeRadio = document.querySelector('input[name=purpose-radio]:checked');
    const isPurposeEvaluateYour = purposeRadio.value == "your";
    const isCheckboxShowYouChecked = document.getElementById("checkbox-show-your").checked;
    return isPurposeEvaluateYour || isCheckboxShowYouChecked;
  }

  function isTheir() {
    const purposeRadio = document.querySelector('input[name=purpose-radio]:checked');
    const isPurposeEvaluateTheir = purposeRadio.value == "their";
    const isCheckboxShowTheirChecked = document.getElementById("checkbox-show-their").checked;
    return isPurposeEvaluateTheir || isCheckboxShowTheirChecked;
  }

  function collectAnswers() {
    const email = document.getElementById('email').value;
    const theirEmail = document.getElementById('their-email').value;
    const age = document.getElementById('age').value;
    const theirAge = document.getElementById('their-age').value;
    const theirAdjective = document.getElementById('their-adjective').value;
    let gender = null;
    let theirGender = null;
    const genderRadio = document.querySelector('input[name=gender-radio]:checked');
    if (genderRadio != null) {
      gender = genderRadio.value;
    }
    const theirGenderRadio = document.querySelector('input[name=their-gender-radio]:checked');
    if (theirGenderRadio != null) {
      theirGender = theirGenderRadio.value;
    }

    // construct the answers
    const apkg = {
      time: Date.now(),
      version: "2023.5.26",
      isYour: isYour(),
      isTheir: isTheir(),
      email: email,
      theirEmail: theirEmail,
      age: age,
      theirAge: theirAge,
      gender: gender,
      theirGender: theirGender,
      theirAdjective: theirAdjective,
      answers: []
    };
    if (apkg.isYour) {
      const answer = {
        type: 0,
        choices: [],
      };
      for (let i = 0; i < numQuestions; i++) {
        const yourRadio = document.querySelector('input[name=' + "your-radio-" + i + ']:checked');
        if (yourRadio != null) answer.choices.push(yourRadio.value);
        else answer.choices.push(null);
      }
      apkg.answers.push(answer);
    }
    if (apkg.isTheir) {
      const answer = {
        type: 1,
        choices: [],
      };
      for (let i = 0; i < numQuestions; i++) {
        const theirRadio = document.querySelector('input[name=' + "their-radio-" + i + ']:checked');
        if (theirRadio != null) answer.choices.push(theirRadio.value);
        else answer.choices.push(null);
      }
      apkg.answers.push(answer);
    }
    return apkg;
  }

  function checkApkg(apkg) {
    if (highlightIf("purpose", !apkg.isYour && !apkg.isTheir)) return false;
    if (highlightIf("your-tr-email", apkg.email != '' && matchAll(/^[\w-\.]+@([\w-]+\.)+[\w-]{2,4}$/g, apkg.email).length == 0)) return false;
    if (highlightIf("their-tr-email", apkg.theirEmail != '' && matchAll(/^[\w-\.]+@([\w-]+\.)+[\w-]{2,4}$/g, apkg.theirEmail).length == 0)) return false;
    if (highlightIf("your-tr-age", apkg.age == '' || isNaN(apkg.age))) return false; // age does not translate to a number
    if (highlightIf("their-tr-age", apkg.isTheir && (apkg.theirAge == '' || isNaN(apkg.theirAge)))) return false;
    if (highlightIf("your-tr-gender", apkg.gender == null)) return false;
    if (highlightIf("their-tr-gender", apkg.isTheir && apkg.theirGender == null)) return false;
    for (let answer of apkg.answers) {
      for (let i = 0; i < answer.choices.length; i++) {
      if (highlightIf("your-form-" + i, answer.choices[i] == null && answer.type == 0)) return false;
      if (highlightIf("their-form-" + i, answer.choices[i] == null && answer.type == 1)) return false;
      }
    }
    return true;
  }

  async function uploadApkg(apkg) {
    // communicate with the answer server
    const response = await fetch('https://personality.novelia.workers.dev/submit', {
      method: 'POST',
      headers: {
        'Accept': 'text/html,application/xhtml+xml,application/xml;q=0.9',
        'Content-Type': 'application/json;charset=UTF-8',
        'Token': '9b2b74e8-6720-4260-84f2-d278bdfd6987'
      },
      body: JSON.stringify(apkg)
    });
    const enc = new TextDecoder("utf-8");
    const body = enc.decode(await response.arrayBuffer());
    return body;
  }

  function removeAnswersFromStorage() {
    const apkg = JSON.parse(localStorage.getItem("apkg"));
    localStorage.setItem("apkg-old", JSON.stringify(apkg));
    localStorage.removeItem("apkg");
  }

  function saveAnswersToStorage(apkg) {
    const apkg_old = JSON.parse(localStorage.getItem("apkg"));
    localStorage.setItem("apkg-old", JSON.stringify(apkg_old));
    localStorage.setItem("apkg", JSON.stringify(apkg));
  }

  function loadAnswersFromStorage() {
    function selectRadio(radioName, value) {
      Array.from(document.querySelectorAll('[name="' + radioName + '"]')).forEach((element, index) => {
        if (value == element.value) element.checked = true;
        else element.checked = false;
      });
    }

    const apkg = JSON.parse(localStorage.getItem("apkg"));
    
    document.getElementById('email').value = apkg.email;
    document.getElementById('their-email').value = apkg.theirEmail;
    document.getElementById('age').value = apkg.age;
    document.getElementById('their-age').value = apkg.theirAge;
    document.getElementById('their-adjective').value = apkg.theirAdjective;
    selectRadio("gender-radio", apkg.gender);
    selectRadio("their-gender-radio", apkg.theirGender);

    for (let i = 0; i < apkg.answers.length; i++) {
      for (let j = 0; j < numQuestions; j++) {
        if (apkg.answers[i].type == 0) {
          selectRadio("your-radio-" + j, "" + apkg.answers[i].choices[j]);
        }
        else if (apkg.answers[i].type == 1) {
          selectRadio("their-radio-" + j, "" + apkg.answers[i].choices[j]);
        }
      }
    }

    document.getElementById("checkbox-show-your").checked = apkg.isYour;
    document.getElementById("checkbox-show-their").checked = apkg.isTheir;
    if (apkg.isYour) {
      selectRadio("purpose-radio", "your");
    }
    if (apkg.isTheir) {
      selectRadio("purpose-radio", "their");
    }
    showClassIf("h-resume", false);
    onClick();
  }

  function checkResponse(response, apkg) {
    try {
      response = JSON.parse(response);
      // check against apkg for correctness
      if (apkg.isYour && (response.yourDesc.length != 5 || response.yourPercentage.length != 5)) return false;
      if (apkg.isTheir && (response.theirDesc.length != 5 || response.theirPercentage.length != 5)) return false;
    } catch (err) {
      return false;
    }
    return true;
  }

  function showResponse(response, apkg) {
    response = JSON.parse(response);
    for (let i = 0; i < 5; i++) {
      if (apkg.isYour) {
        document.getElementById('your-aspect-' + i).value = response.yourPercentage[i];
        document.getElementById('your-aspect-interp-' + i).textContent = "(" + response.yourPercentage[i].toString() + "%) " + response.yourDesc[i];
      }
      if (apkg.isTheir) {
        document.getElementById('their-aspect-' + i).value = response.theirPercentage[i];
        document.getElementById('their-aspect-interp-' + i).textContent = "(" + response.theirPercentage[i].toString() + "%) " + response.theirDesc[i];
      }
      // showElementIf('your-aspect-' + i, apkg.isYour);
      // showElementIf('your-aspect-interp-' + i, apkg.isYour);
      // showElementIf('their-aspect-' + i, apkg.isTheir);
      // showElementIf('their-aspect-interp-' + i, apkg.isTheir);
    }
    showElementIf("table-result", apkg.isYour || apkg.isTheir);
  }

  async function onSubmit() {
    const apkg = collectAnswers();
    saveAnswersToStorage(apkg);
    if (!checkApkg(apkg)) return;

    const div = document.getElementById('output');
    div.textContent = "Retrieving your test results. If nothing happens after ten seconds, please check your Internet connection and submit again.";

    const response = await uploadApkg(apkg);
    if (!checkResponse(response, apkg)) {
      div.textContent = "Sorry, an error occurred when processing your request. Please [contact me](mailto:{{ site.email }}) or open an issue [here](https://github.com/intrigit/novelia.space/issues).";
      return;
    }

    div.textContent = "There has been much research on how people describe others, and five major dimensions of human personality have been found. They are often referred to as the OCEAN model of personality, because of the acronym from the names of the five dimensions. Here are your results.";
    showResponse(response, apkg);
    removeAnswersFromStorage();
    document.getElementById("btn-submit").disabled = true;
  }

  function onClick() {
    const purposeRadio = document.querySelector('input[name=purpose-radio]:checked');
    const isPurposeEvaluateYour = purposeRadio.value == "your";
    const isPurposeEvaluateTheir = purposeRadio.value == "their";
    showElementIf("purpose-evaluate", isPurposeEvaluateYour || isPurposeEvaluateTheir);
    showElementIf("purpose-evaluate-your", isPurposeEvaluateYour);
    showElementIf("purpose-evaluate-their", isPurposeEvaluateTheir);
    showElementIf("table", isPurposeEvaluateYour || isPurposeEvaluateTheir);

    showClassIf("h-your-only", isYour());
    showClassIf("h-their-only", isTheir());

    progressBarSetup();
  }

</script>