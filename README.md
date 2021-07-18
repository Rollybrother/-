# -
지정된 키를 누르면 소리가 납니다
<script>
  playSound = e => { //생소하게 보일수도 있으나 화살표 함수 es6문법 (키가 눌렸을때 함수)
    const audio = document.querySelector(`audio[data-key="${e.keyCode}"]`); //소리
    const key = document.querySelector(`li[data-key="${e.keyCode}"]`); //키
    
    if (audio) { //오디오라면
      audio.currentTime = 0; //이전 오디오가 끝나지 않으면 새로운 오디오가 재생되지 않는것을 처리하는것      
      audio.play(); // 오디오를 출력한다.
      key.classList.add("playing"); //key의 새로운 클래스를 추가한다.
      //이유는 눌렀을때 css가 눌린 디자인을 보여주기위함. 
    }
  };

  removeTransition = e => { // (키를 뗐을때 함수)
    if (e.propertyName === "transform") { //e의 속성이 트랜스폼과 같다면
      e.target.classList.remove("playing"); // 눌린 디자인을 제거해준다. 원복느낌css을 주기위함
    }
  };

  window.addEventListener("keydown", playSound); // 함수 키가눌렸을때 playsound

  const pianoElList = document.querySelectorAll("li"); // li속성을 가진 리스트들을 정의

  pianoElList.forEach(el => { // 키가눌려 css의 트랜지션 효과가 생길때 
    el.addEventListener("transitionend", removeTransition); // transition상태가 되면 removeTransition 함수를 실행시켜라.

  });
</script>
