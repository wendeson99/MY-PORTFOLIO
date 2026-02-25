<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Editable Portfolio</title>
  <style>
    body { font-family: sans-serif; max-width: 500px; margin: 40px auto; }
    #portfolio-item { border: 1px solid #ccc; border-radius: 8px; padding: 1.5em; margin-bottom: 20px;}
    button { padding: 10px 20px; margin: 0 10px; }
  </style>
</head>
<body>
  <div id="portfolio-item"></div>
  <div style="text-align:center;">
    <button onclick="prevItem()">Back</button>
    <button onclick="nextItem()">Next</button>
  </div>
  <script>
    // Edit your portfolio items here! Each item is an object.
    const portfolio = [
      {
        title: "Project One",
        description: "Description of Project One. What you did, tools used, outcome, etc.",
        link: "https://yourprojectlink1.com"
      },
      {
        title: "Project Two",
        description: "Description of Project Two. What you did, tools used, outcome, etc.",
        link: "https://yourprojectlink2.com"
      }
      // Add more portfolio items here
    ];

    let current = 0;
    function renderItem() {
      const { title, description, link } = portfolio[current];
      document.getElementById('portfolio-item').innerHTML = `
        <h2>${title}</h2>
        <p>${description}</p>
        ${link ? `<a href="${link}" target="_blank">View Project</a>` : ""}
        <div style="font-size:0.9em;color:#888;margin-top:1.3em;">${current+1} of ${portfolio.length}</div>
      `;
    }
    function prevItem() {
      current = (current - 1 + portfolio.length) % portfolio.length;
      renderItem();
    }
    function nextItem() {
      current = (current + 1) % portfolio.length;
      renderItem();
    }
    // Initial render
    renderItem();
  </script>
</body>
</html>
