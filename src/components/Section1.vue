<template>
    <section class="Component Article1" id="latest">
        <h3 class="Article1-Title Animate"> Latest projects </h3>
        <article class="Article1-Carousel Animate">
            <div class="Carousel01">
                <div class="Carousel01-Arrow1 show"></div>
                <div class="Carousel01-Arrow2 show"></div>
                <div class="Carousel01-Item1 Carousel01-Item Carousel01-Item_Initial">
                    <div class="Carousel01-ItemContent">
                        <img src="./../assets/sztosApp.jpg" alt="default1" class="Carousel01-ItemContent-Img Carousel01-ItemContent-Img1">
                    </div>
                    <div class="Carousel01-ItemText Carousel01-ItemText1 Carousel01-ItemText1_Active">
                        UI of HOME APP
                    </div>
                </div>
                <div class="Carousel01-Item2 Carousel01-Item">
                    <div class="Carousel01-ItemContent">
                        <img src="./../assets/coffee.jpg" alt="default1" class="Carousel01-ItemContent-Img Carousel01-ItemContent-Img2">
                    </div>
                    <div class="Carousel01-ItemText Carousel01-ItemText2 Carousel01-ItemText1_Notactive">
                        Coffee
                    </div>
                </div>
                <div class="Carousel01-Item3 Carousel01-Item">
                    <div class="Carousel01-ItemContent">
                        <img src="./../assets/businessCard.jpg" alt="default1" class="Carousel01-ItemContent-Img Carousel01-ItemContent-Img3">
                    </div>
                    <div class="Carousel01-ItemText Carousel01-ItemText3 Carousel01-ItemText1_Notactive">
                        BUSINESS CARD
                    </div>
                </div>
            </div>
        </article>
        <div class="Carousel01-ItemModal1">
          <div class="Carousel01-ItemModal1Exit">
            <div class="Carousel01-ItemModal1Line Carousel01-ItemModal1Line1"></div>
            <div class="Carousel01-ItemModal1Line Carousel01-ItemModal1Line2"></div>
          </div>
          <img src="./../assets/sztosApp.jpg" alt="default1" class="Carousel01-ItemModal1Img">
        </div>
        <div class="Carousel01-ItemModal2">
          <div class="Carousel01-ItemModal2Exit">
            <div class="Carousel01-ItemModal1Line Carousel01-ItemModal1Line1"></div>
            <div class="Carousel01-ItemModal1Line Carousel01-ItemModal1Line2"></div>
          </div>
          <img src="./../assets/coffee.jpg" alt="default1" class="Carousel01-ItemModal2Img">
        </div>
        <div class="Carousel01-ItemModal3">
          <div class="Carousel01-ItemModal3Exit">
            <div class="Carousel01-ItemModal1Line Carousel01-ItemModal1Line1"></div>
            <div class="Carousel01-ItemModal1Line Carousel01-ItemModal1Line2"></div>
          </div>
          <img src="./../assets/businessCard.jpg" alt="default1" class="Carousel01-ItemModal3Img">
        </div>
    </section>
</template>

<script>
export default {
  name: 'Section1',
  mounted() {
    this.carousel01();
    this.Modal1();
    this.Modal2();
    this.Modal3();
  },
  methods: {
    carousel01() {
      const itemClassName = '.Carousel01-Item';
      const items = document.querySelectorAll(itemClassName);
      const totalItems = items.length;
      let slide1 = 0;
      const text1 = document.querySelector('.Carousel01-ItemText1');
      const text2 = document.querySelector('.Carousel01-ItemText2');
      const text3 = document.querySelector('.Carousel01-ItemText3');
      let moving = true;
      items[0].classList.remove('Carousel01-Item_Initial');
      // Set classes
      function setInitialClasses() {
        // Targets the previous, current, and next items
        // This assumes there are at least three items.
        console.log(totalItems);
        items[totalItems - 1].classList.add('Carousel01-Item_Prev');
        items[0].classList.add('Carousel01-Item_Active');
        items[1].classList.add('Carousel01-Item_Next');
      }
      function disableInteraction() {
        // Set 'moving' to true for the same duration as our transition.
        // (0.5s = 500ms)
        moving = true;
        // setTimeout runs its function once after the given time
        setTimeout(() => {
          moving = false;
        }, 500);
      }
      function moveCarouselTo(slide) {
        if (!moving) {
          disableInteraction();
          if ((totalItems - 1) >= 2) {
            if (slide === 0) {
              items[slide].classList.add('Carousel01-Item_Active');
              items[slide].classList.remove('Carousel01-Item_Next');
              items[slide].classList.remove('Carousel01-Item_Prev');

              items[slide + 1].classList.add('Carousel01-Item_Next');
              items[slide + 1].classList.remove('Carousel01-Item_Prev');
              items[slide + 1].classList.remove('Carousel01-Item_Active');

              items[slide + 2].classList.add('Carousel01-Item_Prev');
              items[slide + 2].classList.remove('Carousel01-Item_Active');
              items[slide + 2].classList.remove('Carousel01-Item_Next');

              // texts
              setTimeout(() => {
                text1.classList.add('Carousel01-ItemText1_Active');
                text1.classList.remove('Carousel01-ItemText1_Notactive');
              }, 500);
              text3.classList.remove('Carousel01-ItemText3_Active');
              text3.classList.add('Carousel01-ItemText3_Notactive');
              text2.classList.remove('Carousel01-ItemText2_Active');
              text2.classList.add('Carousel01-ItemText2_Notactive');
            } else if (slide === 1) {
              items[slide - 1].classList.remove('Carousel01-Item_Active');
              items[slide - 1].classList.add('Carousel01-Item_Prev');
              items[slide - 1].classList.remove('Carousel01-Item_Next');
              items[slide - 1].classList.remove('Carousel01-Item_Initial');

              items[slide].classList.add('Carousel01-Item_Active');
              items[slide].classList.remove('Carousel01-Item_Next');
              items[slide].classList.remove('Carousel01-Item_Prev');

              items[slide + 1].classList.add('Carousel01-Item_Next');
              items[slide + 1].classList.remove('Carousel01-Item_Prev');
              items[slide + 1].classList.remove('Carousel01-Item_Active');

              // text

              setTimeout(() => {
                text2.classList.add('Carousel01-ItemText2_Active');
                text2.classList.remove('Carousel01-ItemText2_Notactive');
              }, 350);
              text1.classList.remove('Carousel01-ItemText1_Active');
              text1.classList.add('Carousel01-ItemText1_Notactive');
              text3.classList.remove('Carousel01-ItemText3_Active');
              text3.classList.add('Carousel01-ItemText3_Notactive');
            } else if (slide === 2) {
              items[slide - 2].classList.add('Carousel01-Item_Next');
              items[slide - 2].classList.remove('Carousel01-Item_Prev');
              items[slide - 2].classList.remove('Carousel01-Item_Active');

              items[slide - 1].classList.add('Carousel01-Item_Prev');
              items[slide - 1].classList.remove('Carousel01-Item_Active');
              items[slide - 1].classList.remove('Carousel01-Item_Next');

              items[slide].classList.add('Carousel01-Item_Active');
              items[slide].classList.remove('Carousel01-Item_Next');
              items[slide].classList.remove('Carousel01-Item_Prev');
              // text

              setTimeout(() => {
                text3.classList.add('Carousel01-ItemText3_Active');
                text3.classList.remove('Carousel01-ItemText3_Notactive');
              }, 350);
              text2.classList.remove('Carousel01-ItemText2_Active');
              text2.classList.add('Carousel01-ItemText2_Notactive');
              text1.classList.remove('Carousel01-ItemText1_Active');
              text1.classList.add('Carousel01-ItemText1_Notactive');
            }
          } else {
            console.log('error');
          }
        }
      }
      // Next navigation handler
      function moveNext() {
        // Check if moving
        if (!moving) {
        // If it's the last slide, reset to 0, else +1
          if (slide1 === (totalItems - 1)) {
            slide1 = 0;
          } else {
            slide1 += 1;
          }
          // Move carousel to updated slide
          moveCarouselTo(slide1);
        }
      }
      // Previous navigation handler
      function movePrev() {
        console.log('move prev');
        // Check if moving
        if (!moving) {
        // If it's the first slide, set as the last slide, else -1
          if (slide1 === 0) {
            slide1 = (totalItems - 1);
          } else {
            slide1 -= 1;
          }

          // Move carousel to updated slide
          moveCarouselTo(slide1);
        }
      }
      // Set event listeners
      function setEventListeners() {
        const next = document.getElementsByClassName('Carousel01-Arrow2')[0];
        const prev = document.getElementsByClassName('Carousel01-Arrow1')[0];
        next.addEventListener('click', moveNext);
        prev.addEventListener('click', movePrev);
      }
      function initCarousel() {
        setInitialClasses();
        setEventListeners();
        // Set moving to false so that the carousel becomes interactive
        moving = false;
      }
      // make it rain
      initCarousel();
    },
    Modal1() {
      const Modal1 = document.querySelector('.Carousel01-ItemModal1');
      const Modal1Button = document.querySelector('.Carousel01-ItemContent-Img1');
      const Modal1Exit = document.querySelector('.Carousel01-ItemModal1Exit');
      function OpenModal() {
        Modal1Button.removeEventListener('click', OpenModal);
        Modal1.classList.add('Carousel01-ItemModal1_active');
        // eslint-disable-next-line
        Modal1Exit.addEventListener('click', CloseModal);
      }
      function CloseModal() {
        Modal1Exit.removeEventListener('click', CloseModal);
        Modal1Button.addEventListener('click', OpenModal);
        Modal1.classList.remove('Carousel01-ItemModal1_active');
      }
      Modal1Button.addEventListener('click', OpenModal);
    },
    Modal2() {
      const Modal2 = document.querySelector('.Carousel01-ItemModal2');
      const Modal2Button = document.querySelector('.Carousel01-ItemContent-Img2');
      const Modal2Exit = document.querySelector('.Carousel01-ItemModal2Exit');
      function OpenModal() {
        Modal2Button.removeEventListener('click', OpenModal);
        Modal2.classList.add('Carousel01-ItemModal2_active');
        // eslint-disable-next-line
        Modal2Exit.addEventListener('click', CloseModal);
      }
      function CloseModal() {
        Modal2Exit.removeEventListener('click', CloseModal);
        Modal2Button.addEventListener('click', OpenModal);
        Modal2.classList.remove('Carousel01-ItemModal2_active');
      }
      Modal2Button.addEventListener('click', OpenModal);
    },
    Modal3() {
      const Modal3 = document.querySelector('.Carousel01-ItemModal3');
      const Modal3Button = document.querySelector('.Carousel01-ItemContent-Img3');
      const Modal3Exit = document.querySelector('.Carousel01-ItemModal3Exit');
      function OpenModal() {
        Modal3Button.removeEventListener('click', OpenModal);
        Modal3.classList.add('Carousel01-ItemModal3_active');
        // eslint-disable-next-line
        Modal3Exit.addEventListener('click', CloseModal);
      }
      function CloseModal() {
        Modal3Exit.removeEventListener('click', CloseModal);
        Modal3Button.addEventListener('click', OpenModal);
        Modal3.classList.remove('Carousel01-ItemModal3_active');
      }
      Modal3Button.addEventListener('click', OpenModal);
    },
  },
};
</script>
