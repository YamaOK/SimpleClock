<template>
  <div id="clock">
    <div id="center-point centering"></div>
    <span id="hour" class="hands"></span>
    <span id="minute" class="hands"></span>
    <span id="second" class="hands"></span>
    <span class="indicator centering" style="--nth: 1">1</span>
    <span class="indicator centering" style="--nth: 2">2</span>
    <span class="indicator centering" style="--nth: 3">3</span>
    <span class="indicator centering" style="--nth: 4">4</span>
    <span class="indicator centering" style="--nth: 5">5</span>
    <span class="indicator centering" style="--nth: 6">6</span>
    <span class="indicator centering" style="--nth: 7">7</span>
    <span class="indicator centering" style="--nth: 8">8</span>
    <span class="indicator centering" style="--nth: 9">9</span>
    <span class="indicator centering" style="--nth: 10">10</span>
    <span class="indicator centering" style="--nth: 11">11</span>
    <span class="indicator centering" style="--nth: 12">12</span>
  </div>
</template>

<script>
export default {
  name: "simpleClock",
  data: function () {
    return {
      date: new Date(),
      deg: {
        hour: "90deg",
        minute: 0,
        second: 0,
      },
    };
  },
  mounted: function () {
    setInterval(() => {
      this.date = new Date();
      let hour = document.getElementById("hour");
      let minute = document.getElementById("minute");
      let second = document.getElementById("second");
      hour.style.setProperty(
        "--deg",
        `${
          (360 / 12) * this.date.getHours() +
          (360 / 12 / 60) * this.date.getMinutes()
        }deg`
      );
      minute.style.setProperty(
        "--deg",
        `${(360 / 60) * this.date.getMinutes()}deg`
      );
      second.style.setProperty(
        "--deg",
        `${(360 / 60) * this.date.getSeconds()}deg`
      );
    }, 1000);
  },
};
</script>
<style scoped>
#clock {
  position: relative;
  width: 20em;
  height: 20em;
  background: rgb(214, 208, 208);
  border-radius: 100%;
  box-shadow: inset rgb(0, 0, 0) 5px 5px 10px, inset rgb(0, 0, 0) -5px 5px 10px;
}
#center-point {
  position: absolute;
  --diameter: 2%;
  width: var(--diameter);
  height: var(--diameter);
  background: black;
  border-radius: 100%;
}
.indicator {
  display: inline-block;
  --diameter: 90%;
  width: var(--diameter);
  height: var(--diameter);
  position: absolute;
  text-align: center;
  vertical-align: top;
  transform: rotate(calc(30deg * var(--nth)));
  font-size: 1.5em;
  text-shadow: 1px 1px 2px, -1px -1px 1px;
}
.hands {
  position: absolute;
  transform: rotate(var(--deg));
  left: calc((100% - var(--width)) / 2);
  top: calc((100% / 2) - var(--height));
  transform-origin: center bottom;
  width: var(--width);
  height: var(--height);
  background: linear-gradient(
    90deg,
    rgb(0, 0, 0),
    rgb(87, 83, 83),
    rgb(0, 0, 0)
  );
}
#hour {
  --width: 6px;
  --height: 50px;
  border-radius: 10px 10px 10px 10px;
}
#minute {
  --width: 4px;
  --height: 70px;
  border-radius: 5px 5px 10px 10px;
}
#second {
  --width: 2px;
  --height: 30%;
  border-radius: 5px 5px 10px 10px;
}
.centering {
  left: calc((100% - var(--diameter)) / 2);
  top: calc((100% - var(--diameter)) / 2);
}
</style>