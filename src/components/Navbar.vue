<template>
  <div class="navigation">
    <ul>
      <li class="list" ref="li1" @click="handleClick">
        <a href="#">
          <span class="icon">
            <ion-icon name="home-outline"></ion-icon>
          </span>
          <span class="text">Home</span>
        </a>
      </li>
      <li class="list" ref="li2" @click="handleClick">
        <a href="#">
          <span class="icon">
            <ion-icon name="person-outline"></ion-icon>
          </span>
          <span class="text">Profile</span>
        </a>
      </li>
      <li class="list" ref="li3" @click="handleClick">
        <a href="#">
          <span class="icon">
            <ion-icon name="chatbox-ellipses-outline"></ion-icon>
          </span>
          <span class="text">Texts</span>
        </a>
      </li>
      <li class="list" ref="li4" @click="handleClick">
        <a href="#">
          <span class="icon">
            <ion-icon name="bookmark-outline"></ion-icon>
          </span>
          <span class="text">Favorites</span>
        </a>
      </li>
      <li class="list" ref="li5" @click="handleClick">
        <a href="#">
          <span class="icon">
            <ion-icon name="settings-outline"></ion-icon>
          </span>
          <span class="text">Settings</span>
        </a>
      </li>
      <div class="shadow"></div>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Navbar",
  data() {
    return {
      isActive: false,
      elements: this.els,
    }
  },
  methods: {
    getElements() {
      let els = [this.$refs.li1, this.$refs.li2, this.$refs.li3, this.$refs.li4, this.$refs.li5]
      return els;
    },
    handleClick(e) {
      let elements = this.getElements()
      elements.forEach(el=> {
        if(el.classList.contains('active')) {
          el.classList.remove('active');
        }
      })
      switch(e.target.name) {
        case 'home-outline':
          elements[0].classList.add('active')
          break;
        case 'person-outline':
          elements[1].classList.add('active');
          break;
        case 'chatbox-ellipses-outline':
          elements[2].classList.add('active');
          break;
        case 'bookmark-outline':
          elements[3].classList.add('active');
          break;
        case 'settings-outline':
          elements[4].classList.add('active');
          break;
      }
    },
    
  },
};
</script>

<style scoped>
  .navigation {
    position: relative;
    width: 400px;
    height: 70px;
    background: #fff;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 10px;
  }

  .navigation ul {
    width: 350px;
    display: flex;
    padding-left: 0;
  }
  .navigation ul li {
    position: relative;
    list-style: none;
    width: 70px;
    height: 70px;
    z-index: 1;
  }
  .navigation ul li a {
    position: relative;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    font-weight: 500;
    text-align: center;
  }
  .navigation ul li a .icon {
    position: relative;
    display: block;
    line-height: 75px;
    font-size: 1.5em;
    text-align: center;
    color: var(--bg-color);

    transition: .5s ease;
  }
  .navigation ul li.active a .icon {
    transform: translateY(-35px);
  }
  .navigation ul li a .text {
    position: absolute;
    color: var(--bg-color);
    font-weight: 400;
    letter-spacing: 0.05em;
    font-size: 0.75em;
    opacity: 0;
    transform: translateY(25px);

    transition: .5s ease;
  }
  .navigation ul li.active a .text {
    opacity: 1;
    transform: translateY(15px);
  }
  .shadow {
    position: absolute;
    top: -60%;
    transform: translateX(-7%);
    height: 70px;
    width: 70px;
    background: #23e249;
    border-radius: 50%;
    border: 6px solid var(--bg-color);

    visibility: hidden;
    transition: transform .5s ease, visibility 0s;
    
  }
  .shadow::before {
    content: "";
    position: absolute;
    top: 51.5%;
    left: -21.5px;
    height: 20px;
    width: 20px;
    background: transparent;
    border-top-right-radius: 20px;
    box-shadow: 1px -10px 0 0 var(--bg-color);
  }
  .shadow::after {
    content: "";
    position: absolute;
    top: 51.5%;
    right: -21.5px;
    height: 20px;
    width: 20px;
    background: transparent;
    border-top-left-radius: 20px;
    box-shadow: -1px -10px 0 0 var(--bg-color);
  }

  .navigation ul li:nth-child(1).active ~ .shadow {
    visibility: visible;
    transform: translateX(calc(70px * 0) - 21.5px);
  }
  .navigation ul li:nth-child(2).active ~ .shadow {
    visibility: visible;
    transform: translateX(calc((70px * 1) - 6.5px));
  }
  .navigation ul li:nth-child(3).active ~ .shadow {
    visibility: visible;
    transform: translateX(calc((70px * 2) - 6.5px));
  }
  .navigation ul li:nth-child(4).active ~ .shadow {
    visibility: visible;
    transform: translateX(calc((70px * 3) - 6.5px));
  }
  .navigation ul li:nth-child(5).active ~ .shadow {
    visibility: visible;
    transform: translateX(calc((70px * 4) - 6.5px));
  }
</style>
