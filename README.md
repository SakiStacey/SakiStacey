- 👋 Hi, I’m @SakiStacey
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
SakiStacey/SakiStacey is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
<!DOCTYPE html>
<html>
<head>
  <title>Fake Name Generator</title>
  <style>
    body {
      font-family: Arial, sans-serif;
    }

    .container {
      max-width: 400px;
      margin: 0 auto;
      padding: 20px;
    }

    h1 {
      text-align: center;
    }

    label {
      display: block;
      margin-bottom: 10px;
    }

    input[type="radio"] {
      margin-right: 5px;
    }

    button {
      display: block;
      margin: 20px auto;
      padding: 10px 20px;
      background-color: #4CAF50;
      color: #fff;
      border: none;
      border-radius: 4px;
      cursor: pointer;
    }

    .result-container {
      margin-top: 20px;
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
    }

    .name-box {
      width: calc(33.33% - 20px);
      margin-bottom: 10px;
      padding: 10px;
      border: 1px solid #ccc;
      background-color: #f7f7f7;
      box-shadow: 2px 2px 4px rgba(0, 0, 0, 0.2);
    }

    .name {
      text-align: center;
    }

    .copy-button {
      display: block;
      margin-top: 10px;
      width: 100%;
      padding: 5px 10px;
      background-color: #4CAF50;
      color: #fff;
      border: none;
      border-radius: 4px;
      cursor: pointer;
      box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.2);
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Fake Name Generator</h1>
    <form id="nameForm">
      <label>
        <input type="radio" name="gender" value="male" checked> Male
      </label>
      <label>
        <input type="radio" name="gender" value="female"> Female
      </label>
      <button type="submit">Generate Names</button>
    </form>
    <div id="resultContainer" class="result-container"></div>
  </div>

  <script>
    const nameForm = document.getElementById('nameForm');
    const resultContainer = document.getElementById('resultContainer');

    nameForm.addEventListener('submit', function (event) {
      event.preventDefault();

      const gender = document.querySelector('input[name="gender"]:checked').value;

      generateNames(gender);
    });

    function generateNames(gender) {
      const maleNames = [
        'John Doe',
        'Michael Smith',
        'Robert Johnson',
        'David Williams',
        'James Brown',
        'William Davis',
        'Joseph Miller',
        'Charles Wilson',
        'Thomas Anderson',
        'Daniel Clark',
        'Brian Martinez',
        'Christopher Lee'
      ];

      const femaleNames = [
        'Mary Johnson',
        'Jennifer Davis',
        'Linda Wilson',
        'Patricia Anderson',
        'Susan Thompson',
        'Jessica Martinez',
        'Sarah Lee',
        'Karen Rodriguez',
        'Nancy Thomas',
        'Lisa Lopez',
        'Betty Taylor',
        'Elizabeth Scott'
      ];

      let names = [];

  if (gender === 'male') {
    names = maleNames;
  } else {
    names = femaleNames;
  }

  shuffleArray(names);

  showResults(names.slice(0, 12));
}

function shuffleArray(array) {
  for (let i = array.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1));
    [array[i], array[j]] = [array[j], array[i]];
  }
}

function showResults(names) {
  resultContainer.innerHTML = '';

  for (let i = 0; i < names.length; i++) {
    const nameBox = document.createElement('div');
    nameBox.classList.add('name-box');

    const nameElement = document.createElement('div');
    nameElement.classList.add('name');
    nameElement.textContent = names[i];
    nameBox.appendChild(nameElement);

    const copyButton = document.createElement('button');
    copyButton.classList.add('copy-button');
    copyButton.textContent = 'Copy';
    nameBox.appendChild(copyButton);

    copyButton.addEventListener('click', function () {
      copyToClipboard(names[i]);
    });

    resultContainer.appendChild(nameBox);
  }
}

function copyToClipboard(text) {
  const textarea = document.createElement('textarea');
  textarea.value = text;
  document.body.appendChild(textarea);
  textarea.select();
  document.execCommand('copy');
  document.body.removeChild(textarea);
  alert('Copied to clipboard: ' + text);
}
  </script>
</body>
</html>
