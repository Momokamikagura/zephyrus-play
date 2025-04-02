# zephyrus-play

function runAegis(transLang) {
    const target = document.getElementById('mainText');

    transLang.actions.forEach(action => {
        if (action.display) {
            if (target) {
                target.innerText = action.display;
                target.classList.add('fade-in');
            }
        } else if (action.speak) {
            const dialogueBox = document.createElement('div');
            dialogueBox.className = 'agent-dialogue';
            dialogueBox.innerText = `${action.agent}：${action.speak}`;
            document.body.appendChild(dialogueBox);
        } else if (action.playSound) {
            const audio = new Audio(`assets/sounds/${action.playSound}.mp3`);
            audio.play().catch(err => console.error("再生失敗:", err));
        }
    });
}
