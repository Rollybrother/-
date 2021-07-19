# -
지정된 키를 누르면 소리가 납니다
<script>
  playSound = e
    const audio = document.querySelector(`audio[data-key="${e.keyCode}"]`); //소리
    const key = document.querySelector(`li[data-key="${e.keyCode}"]`); //키
    
    if (audio) { //
      audio.currentTime = 0; //  
      audio.play(); // 
      key.classList.add("playing"); 
    }
  };

  removeTransition = e => { // 
    if (e.propertyName === "transform") 
      e.target.classList.remove("playing"); 
    }
  };

  window.addEventListener("keydown", playSound); 

  const pianoElList = document.querySelectorAll("li"); 

  pianoElList.forEach(el => { 
    el.addEventListener("transitionend", removeTransition); 

  });
</script>
