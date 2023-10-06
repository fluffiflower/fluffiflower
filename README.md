<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Typewriter Effect</title>
</head>
<body>
    <div class="typewriter">
        <h1></h1>
    </div>

    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inconsolata:wght@200&display=swap');
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
            background-color: #f0f0f0;
        }
        
        .typewriter {
            overflow: hidden;
            white-space: nowrap;
            border-right: 3px solid #333;
            font-size: 36px;
            font-family: 'Inconsolata', monospace;
            padding-right: 10px; /* Create space for the cursor */
            animation: blink-caret 0.75s step-end infinite;
            animation: rotation-start 5s infinite;
            animation: rotation 5s infinite;
        } 
        
        @keyframes blink-caret {
            from,
            to {
                border-color: transparent;
            }
            50% {
                border-color: #333;
            }
        }
        
        
        @keyframes rotation {
            50% {
                transform: rotate(5deg);
            }
        }
    </style>
    
    <script>
    function typewriterEffect() {
      const texts = ["You matter", "Everyone loves you!", "I care about you", "I wish all this words we're true..", "You know.. sometimes i want some attention too!", "Huh, hi there?", "Woah this getting really out of hand", "I dont really care tbh", "💀", "🗿"];
      let textIndex = 0;
      let charIndex = 0;
      let isTyping = true;
      const speed = 50;
      const typewriter = document.querySelector('.typewriter h1');
      function typeOrErase() {
          const currentText = texts[textIndex];
  
          if (isTyping) {
              if (charIndex < currentText.length) {
                  typewriter.textContent += currentText.charAt(charIndex);
                  charIndex++;
                  setTimeout(typeOrErase, speed);
              } else {
                  // Finished typing, start erasing
                  isTyping = false;
                  setTimeout(typeOrErase, 1000); // Pause before erasing
              }
          } else {
              if (charIndex > 0) {
                  typewriter.textContent = currentText.substring(0, charIndex - 1);
                  charIndex--;
                  setTimeout(typeOrErase, speed / 2); // Erasing is faster
              } else {
                  // Finished erasing, move to the next text
                  isTyping = true;
                  textIndex = toString(texts[Math.random() * 3])
                  setTimeout(typeOrErase, 1000); // Pause before typing the next text
              }
          }
      }
  
      // Start the typing/erasing effect
      typeOrErase();
}

// Call the typewriter effect function
typewriterEffect();

    </script>
</body>
</html>
