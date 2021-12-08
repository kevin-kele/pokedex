<template>
  <div>
    <div class="wrapper">
      <div class="card">
        <div class="card__body">
          <div class="card__head">
            <div class="main-info">
              <div class="pre-evo">
                <span class="pre-evo__badge" />
                <span class="pre-evo__badge-front" />
                <span class="pre-evo__title">Stage 2</span>
                <div class="pre-evo__img">
                  <img :src="pokemon.image">
                </div>
              </div>
              <span class="evolves-from">Evolves from Charmeleon</span>
              <span class="put-card">Put Charizard on the Stage 1 card</span>
              <h1 class="name">
                {{ pokemon.name }}
              </h1>
              <span class="hp">120 HP</span>
              <span class="energy" />
            </div>

            <div class="frame">
              <div class="frame__img" />
            </div>

            <div class="stats">
              <span v-if="pokemon.type === 'fire'">Flame Pokémon. Length: 5' 7", Weight: 200 lbs.</span>
              <span v-if="pokemon.type === 'poisson'">Poisson Pokémon. Length: 5' 7", Weight: 200 lbs.</span>
              <span v-if="pokemon.type === 'water'">Water Pokémon. Length: 5' 7", Weight: 200 lbs.</span>
              <span v-if="pokemon.type === 'bug'">Bug Pokémon. Length: 5' 7", Weight: 200 lbs.</span>
            </div>

            <ul class="attacks">
              <li class="attack pkmn-power">
                <p>
                  <strong>Pokémon Power: Energy Burn</strong> As often as you like during your turn <em>(before your attack)</em>, you may turn<br> all Energy attached to Charizard into <span class="energy inline" /> Energy for the rest of the turn.
                  This power can&rsquo;t be used if Charizard<br>is Asleep, Confused, or Paralyzed.
                </p>
              </li>
              <li class="attack">
                <div class="attack-cost">
                  <span class="energy small" />
                  <span class="energy small" />
                  <span class="energy small" />
                  <span class="energy small" />
                </div>
                <p>
                  <strong>Fire Spin</strong> Discard 2 Energy cards attached<br> to Charizard in order to use this attack.
                </p>
                <div class="attack-dmg">
                  100
                </div>
              </li>
            </ul>
            <ul class="type-info">
              <li>
                <span>weakness</span>
                <span class="energy smaller water" />
              </li>
              <li>
                <span>resistance</span>
                <span class="energy smaller fighting" /><span class="modifier">-30</span>
              </li>
              <li>
                <span>retreat cost</span>
                <span class="energy smaller colorless" />
                <span class="energy smaller colorless" />
                <span class="energy smaller colorless" />
              </li>
            </ul>
          </div>
          <div class="desc">
            <div class="desc__borderside" />
            <span class="desc__text">Spits fire that is hot enough to melt boulders. Known to unintentionally cause forest fires.&nbsp;&nbsp;&nbsp;LV. 76&nbsp;&nbsp;&nbsp;#6</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    pokemon: {
      type: Object,
      default: () => {}
    }
  }
}
</script>

<style lang='scss'>
$card-size: 60vh;
$font-size-large: $card-size * 0.06;

*, *:before,
*:after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  padding: 1em;
  font-family: 'Gill Sans', 'Gill Sans MT', 'Cabin', sans-serif;
  text-shadow: 0 0 0.05em rgba(black, 0.35);
  background: #37474F;
}

.wrapper {
  position: relative;
  width: $card-size;
  &:after {
    content: '';
    display: block;
    padding-top: $card-size * 1.397;
  }
}

.card {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  border-radius: $card-size * 0.0316;
  background-color: #ffe50a;
  background-image: linear-gradient(to top, #ffe50a, #ffea3d 70%, #ffe50a);
  box-shadow: 0 $card-size*0.005 $card-size*0.005 rgba(black, 0.5);
  //filter: blur($card-size * 0.0008);
  transform: rotate(-3deg) translate(5%, 2%)
}

.card__body {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  margin: $card-size * 0.0528;
  background-image: url(https://i.imgur.com/x7L9qpC.png);
  background-size: cover;
  z-index: 1;
}

.card__head {
  padding: 0 5.063%;
}

.main-info {
  position: relative;
  height: $card-size * 0.1055;
  &:after {
    content: '';
    display: block;
    position: absolute;
    top: 40%;
    left: 0;
    width: 100%;
    height: 4%;
    background: linear-gradient(90deg, transparent, #cf9401 2%, #f9d51e, #ffff7a, #f9d51e, #cf9401 98%, transparent);
  }
  .energy {
    position: absolute;
    bottom: 0;
    right: 0;
    bottom: $card-size * 0.005;
    z-index: 1;
  }
}

$pre-evo-size: $card-size * 0.1371;
.pre-evo {
  position: absolute;
  left: -1.15%;
  top: 35%;
  z-index: 10;
  transform: rotate(45deg);
  > .pre-evo__badge {
    position: relative;
    display: block;
    width: $pre-evo-size;
    height: $pre-evo-size;
    background: linear-gradient(to top, #d9a81f, #fefe8e 30%, #dcb212);
    //
    &:before,
    &:after {
      content: '';
      display: block;
      position: absolute;
      z-index: -1;
      top: 0;
      left: 0;
      width: $pre-evo-size;
      height: $pre-evo-size;
      background: linear-gradient(-45deg, #bf7c11, #e5be1b, #fff260);
    }
    &:before {
      transform: rotate(15deg);
    }
    &:after {
      transform: rotate(-15deg);
      //background: linear-gradient(45deg, #bf7c11, #e5be1b, #fff260);
    }
  }
}

$badge-front-size: $card-size * 0.171;
.pre-evo__badge-front {
  display: block;
  position: absolute;
  top: -13%;
  left: -13%;
  overflow: hidden;
  width: $badge-front-size;
  height: $badge-front-size;
  transform: rotate(-15deg) skew(30deg) scaleY(0.8666);
  background: transparent;
  &:before {
    display: block;
    content: '';
    position: absolute;
    right: 6.7%;
    bottom: 0;
    left: 6.7%;
    top: 0;
    transform: scaleY(1.155) skewX(-30deg) rotate(30deg);
    background: linear-gradient(to top, #d9a81f, #fefe8e, #c67a17, #d9a81f);
  }
  &:after {

  }
}
.pre-evo__img {
  position: absolute;
  top: 14%;
  left: 7%;
  width: $card-size * 0.122;
  height: $card-size * 0.108;
  padding: $card-size*0.007 $card-size*0.015;
  background: linear-gradient(to right, #858E89, #C6C7BF, #858E89);
  transform: rotate(-45deg);

  > img {
    display: block;
    width: 100%;
  }
}
.pre-evo__title {
  display: block;
  position: absolute;
  top: 3%;
  left: -22%;
  font-size: $card-size * 0.028;
  text-transform: uppercase;
  font-weight: 600;
  text-shadow: 0 0 $card-size*0.001 black;
  transform: rotate(-45deg) scale(0.85, 1);
}

.name,
.hp,
.evolves-from,
.put-card {
  position: absolute;
  bottom: 0;
  line-height: 1;
}
.evolves-from {
  top: 13%;
  left: 15%;
  bottom: auto;
  font-size: $card-size * 0.024;
  letter-spacing: 0.025em;
  font-style: italic;
  font-weight: 600;
}
.put-card {
  bottom: auto;
  top: 13%;
  right: 0;
  z-index: 1;
  font-size: $card-size * 0.024;
  letter-spacing: 0.025em;
}
.name {
  font-size: $font-size-large;
  font-weight: 700;
  left: $card-size * 0.165;
  transform: scaleX(0.8);
  transform-origin: left;
}
.hp {
  //right: $card-size * 0.0717;
  right: 9%;
  bottom: 3%;
  margin-left: auto;
  letter-spacing: -0.05em;
  font-weight: 600;
  font-size: $card-size * 0.055;
  color: #ff0000;
  text-shadow: 0 0 0.05em rgba(#ff0000, 0.15);
  transform: scale(0.92, 1);
  transform-origin: right;
}

.frame {
  position: relative;
  width: 100%;
  height: $card-size * 0.5805;
  margin-bottom: $card-size * 0.0105;
  //background-color: #f3ce27;
  background-image: linear-gradient(45deg, #cf9401, #f9d51e, #ffff7a, #f9d51e, #ffff7a, #cf9401);
  box-shadow: $card-size*0.0105 $card-size*0.0105 $card-size*0.0253 $card-size*0.0042 rgba(black, 0.75);
  &:after,
  &:before{
    content: '';
    display: block;
    position: absolute;
    top: 0;
    height: 3.5%;
    width: 5%;

  }
  &:before {
    left: 1.2%;
    background: linear-gradient(to right, rgba(#aa6007, 0.5), transparent);
    transform: skew(45deg);
  }
  &:after {
    right: 1.2%;
    background: linear-gradient(to left, rgba(#aa6007, 0.5), transparent);
    transform: skew(-45deg);
  }
}
.frame__img {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  margin: 2.388%;
  background: url(https://i.imgur.com/8rDxLr3.jpg);
  background-size: cover;
  &:after,
  &:before{
    content: '';
    display: block;
    position: absolute;
    bottom: -3.6%;
    height: 3.6%;
    width: 5%;
  }
  &:before {
    left: -1.25%;
    background: linear-gradient(to right, rgba(#aa6007, 0.5), transparent);
    transform: skew(-45deg);
  }
  &:after {
    right: -1.25%;
    background: linear-gradient(to left, rgba(#aa6007, 0.5), transparent);
    transform: skew(45deg);
  }
}

.stats {
  position: relative;
  line-height: $card-size * 0.0421;
  margin: 0 $card-size*0.04;
  text-align: center;
  background-image: linear-gradient(to top, #fff85d, #fbde02 10%, #ba7500 80%, #fbde02 100%);
  &:after {
    content: '';
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    margin: 0.3% 0 0;
    background: linear-gradient(90deg, transparent, #cf9401 2%, #f9d51e, #ffff7a, #f9d51e, #cf9401 98%, transparent);
    //filter: blur($card-size * 0.004)
  }
  > span {
    position: relative;
    font-size: $card-size * 0.031;
    font-weight: 600;
    letter-spacing: 0.022em;
    font-style: italic;
    z-index: 1;
  }
}

.energy {
  position: relative;
  display: inline-block;
  border-radius: 100px;
  width: $card-size * 0.0654;
  height: $card-size * 0.0654;
  background: radial-gradient(#fdaeba 40%, #f84c20, #c8340e 100%);
  &:after {
    content: '';
    position: absolute;
    display: block;
    top: 14%;
    left: 2%;
    width: 50%;
    height: 25%;
    border-radius: 50%;
    transform: rotate(-45deg);
    background: linear-gradient(rgba(white, 0.8) 50%, transparent);
  }

  &.small {
    width: $card-size * 0.054;
    height: $card-size * 0.054;
  }

  &.smaller {
    width: $card-size * 0.045;
    height: $card-size * 0.045;
  }

  &.inline {
    vertical-align: top;
    width: $card-size * 0.035;
    height: $card-size * 0.035;
    margin: 0 $card-size * 0.004;
  }

  &.water {
    filter: hue-rotate(200deg);
  }

  &.fighting {
    filter: hue-rotate(40deg) brightness(67%) contrast(180%);
  }

  &.colorless {
    filter: grayscale(100%) brightness(120%) contrast(120%)
  }
}

.desc {
  position: absolute;
  bottom: $card-size * 0.0274;
  left: $card-size * 0.04;
  width: $card-size * 0.8143;
  height: $card-size * 0.0801;
  z-index: 1;
  &:before,
  &:after {
    content: '';
    position: absolute;
    display: block;
    height: $card-size*0.00422;
    left: 0;
    right: 0;
  }
  &:before {
    top: 0;
    background: linear-gradient(to right, #ffd234, #ffef64, #f8d130, #efb303, #a36009);
  }
  &:after {
    bottom: 0;
    background: linear-gradient(to right, #a36009, #efb303, #f8d130, #ffef64, #ffd234);
  }
}
.desc__borderside {
  &:before,
  &:after {
    content: '';
    position: absolute;
    display: block;
    width: $card-size*0.00422;
    bottom: 0;
    top: 0;
    z-index: -1;
  }
  &:before {
    left: 0;
    background: linear-gradient(to top, #a07700, #b08409);
  }
  &:after {
    right: 0;
    background: linear-gradient(to bottom, #a07700, #b08409);
  }
}
.desc__text {
  padding: $card-size*0.0127 $card-size*0.0253;
  font-size: $card-size * 0.029;
  font-weight: 600;
  letter-spacing: 0.022em;
  font-style: italic;
  line-height: 1;
  display: block;
}

.attacks {
  list-style: none;
  padding: 0;
  margin: 0;
  margin-top: $card-size*0.02;
  font-size: $card-size * 0.031;
}
.attack {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-top: $card-size*0.015;
  border-bottom: $card-size*0.00422 solid black;

  &.pkmn-power {
    padding: 0 $card-size*0.04;

    strong {
      font-size: inherit;
      color: #5A5A7E;
    }
  }

  strong {
    display: inline-block;
    transform-origin: left;
    font-size: $font-size-large*0.55;
  }

  p {
    margin-bottom: $card-size*0.02;
  }
}

.attack-cost {
  margin-bottom: $card-size*0.006;
  max-width: $card-size*0.12;
}

.attack-dmg {
  font-size: $font-size-large;
}

.type-info {
  margin-top: -0.2%;
  height: $card-size*0.08;
  display: flex;
  justify-content: space-between;
  text-align: center;
  list-style: none;

  span {
    display: block;
    font-size: $card-size * 0.029;
    font-weight: 600;
    letter-spacing: 0.022em;
  }

  .energy,
  .modifier {
    display: inline-block;
    vertical-align: middle;
    //margin-top: -$card-size * 0.025;
  }

  .modifier {
    margin-left: 10%;
  }
}

.footer {
  position: absolute;
  bottom: 0.35%;
  left: 1%;
  right: 1%;
  display: flex;
  justify-content: space-between;
  font-size: $card-size * 0.018;
}
</style>
