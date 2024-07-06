# Text-to-Voice Converter 🎤📝

Welcome to the Text-to-Voice Converter project! This tool allows you to convert text to speech effortlessly using JavaScript and the Web Speech API. Let's turn your text into voice! 🎉

## Features ✨

- Convert any text input to speech 🔊
- Supports multiple languages and voices 🌐
- User-friendly interface 🖥️

## Table of Contents 📑

- [Installation](#installation)
- [Usage](#usage)
- [Configuration](#configuration)
- [Code Overview](#code-overview)
- [Contributing](#contributing)
- [License](#license)

## Installation 🚀

Get started by cloning the repository:

```bash
git clone https://github.com/yourusername/text-to-voice-converter.git
```

Navigate to the project directory:

```bash
cd text-to-voice-converter
```

Open `index.html` in your preferred web browser. 🌍

## Usage 🛠️

1. Open `index.html` in your web browser. 🌐
2. Enter the text you want to convert to speech in the input box. ✍️
3. Select your desired voice and language from the dropdown menus. 🌏
4. Click the "Speak" button to hear the text. 🗣️

## Configuration ⚙️

### Voice and Language 🌎

The Web Speech API provides various voices and languages. These can be selected from the dropdown menus provided in the interface.

## Code Overview 💻

The core functionality is implemented in `main.js`:

### `main.js`

```javascript
// Select elements from the DOM
const textInput = document.getElementById('text-input');
const voiceSelect = document.getElementById('voice-select');
const speakButton = document.getElementById('speak-button');

// Initialize speech synthesis
const synth = window.speechSynthesis;
let voices = [];

// Populate voice options
function populateVoices() {
    voices = synth.getVoices();
    voiceSelect.innerHTML = '';
    voices.forEach(voice => {
        const option = document.createElement('option');
        option.textContent = `${voice.name} (${voice.lang})`;
        option.setAttribute('data-lang', voice.lang);
        option.setAttribute('data-name', voice.name);
        voiceSelect.appendChild(option);
    });
}

populateVoices();
if (synth.onvoiceschanged !== undefined) {
    synth.onvoiceschanged = populateVoices;
}

// Speak text
function speak() {
    if (synth.speaking) {
        console.error('Already speaking...');
        return;
    }
    if (textInput.value !== '') {
        const utterThis = new SpeechSynthesisUtterance(textInput.value);
        const selectedOption = voiceSelect.selectedOptions[0].getAttribute('data-name');
        voices.forEach(voice => {
            if (voice.name === selectedOption) {
                utterThis.voice = voice;
            }
        });
        synth.speak(utterThis);
    }
}

speakButton.addEventListener('click', speak);
```

## Contributing 🤝

Contributions are welcome! If you have suggestions for improvements or find a bug, please open an issue or submit a pull request. Let's make this project better together! 🌟

1. Fork the repository. 🍴
2. Create your feature branch (`git checkout -b feature/AmazingFeature`). 🌿
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`). 📦
4. Push to the branch (`git push origin feature/AmazingFeature`). 🚀
5. Open a pull request. 🔄

## License 📜

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

---

Feel free to reach out if you have any questions or need further assistance! Happy coding! 😄👩‍💻👨‍💻
