<template>
    <div>
        <div v-if="people.length + 1 > 2 && !top2">
            <div v-if="selected" style="position: fixed; width: 100vw; height: 100vh; top: 0; left: 0; z-index: -1" :class="['funny-back', selected.color]"></div>
            <Start v-if="show" @click="click"></Start>
            <div v-if="!selected" style="color: white; font-size: 100px;">
                {{text}}
            </div>
            <div v-if="selected" style="background: white; font-size: 100px; padding: 30px 50px; text-align:center">
                <div style="text-align:center; font-size: 50px">{{people.length + 1}}</div>
                {{selected.name}}

                <div style="padding-top: 30px" v-if="people.length > 2">
                    <Start @click="click"></Start>
                </div>

                <div style="padding-top: 30px" v-if="people.length == 2">
                    <Next @click="next"></Next>
                </div>
            </div>
        </div>
        <div v-if="top2">
            <div style="background: white; font-size: 60px; padding: 30px 50px; text-align:center; display: inline-block; margin: 0 10px; width: 40`vw; vertical-align: middle">
                <div v-if="selected" style="position: fixed; width: 100vw; height: 100vh; top: 0; left: 0; z-index: -1" class="funny-back2"></div>
                {{people[0].name}}
            </div>
            <div style="background: white; font-size: 60px; padding: 30px 50px; text-align:center; display: inline-block; margin: 0 10px; width: 40`vw; vertical-align: middle">
                <div v-if="selected" style="position: fixed; width: 100vw; height: 100vh; top: 0; left: 0; z-index: -1" class="funny-back2"></div>
                {{people[1].name}}
            </div>
        </div>
    </div>
</template>

<script>
// @ is an alias to /src
import Start from '@/components/Start.vue'
import Next from '@/components/Next.vue'

export default {
    name: 'home',
    components: {
        Start,
        Next
    },
    data () {
        return {
            show: true,
            stop: false,
            text: '',
            top2: false,
            people: [
                { name: 'Azim', color: 'grey' },
                { name: 'Husna', color: 'grey' },
                { name: 'Kamal', color: 'grey' },
                { name: 'Farhana', color: 'grey' },
                { name: 'Helmi', color: 'grey' },
                { name: 'Ammar', color: 'grey' },
                { name: 'Hilmi', color: 'grey' },
                { name: 'Nizul', color: 'grey' },
                { name: 'Shakawi', color: 'red' },
                { name: 'Marcus', color: 'red' },
                { name: 'Fadhil', color: 'red' },
                { name: 'Hakim', color: 'red' },
                { name: 'Kamal Nor', color: 'red' },
                { name: 'Ikhsan', color: 'red' },
                { name: 'Fatin', color: 'red' },
                { name: 'Amy', color: 'red' },
                { name: 'Ariza', color: 'red' },
                { name: 'Wan Irfan', color: 'green' },
                { name: 'Rushamir', color: 'green' },
                { name: 'Nazli', color: 'green' },
                { name: 'Firdaus', color: 'green' },
                { name: 'Safian', color: 'green' },
                { name: 'Azrul', color: 'green' },
                { name: 'Farihin', color: 'green' },
                { name: 'Anuar', color: 'green' },
                { name: 'Nor Husna', color: 'green' },
                { name: 'Azmir', color: 'black' },
                { name: 'Angeline', color: 'black' },
                { name: 'Asya', color: 'black' },
                { name: 'Farah', color: 'black' },
                { name: 'Ayunni', color: 'black' },
                { name: 'Aimi', color: 'black' },
                { name: 'Huda', color: 'black' },
                { name: 'Ayman', color: 'black' },
                { name: 'Hambali', color: 'black' },
                { name: 'Isman', color: 'purple' },
                { name: 'Lili', color: 'purple' },
                { name: 'Rosni', color: 'purple' },
                { name: 'Azam', color: 'purple' },
                { name: 'Bryan', color: 'purple' },
                { name: 'Reshma', color: 'purple' },
                { name: 'Ming Joon', color: 'purple' },
                { name: 'Hakim', color: 'purple' },
                { name: 'Elisa', color: 'purple' }
            ],
            selected: null
        }
    },
    methods: {
        click () {
            this.show = false
            this.text = this.people[0].name
            this.stop = false
            this.randomize(500, 0, 2)
            this.selected = null
        },
        next () {
            this.top2 = true
        },
        randomize (timeout, num, selected) {
            setTimeout(() => {
                if (!this.stop) {
                    this.text = this.people[(num) % this.people.length].name
                    this.randomize(timeout - 50 < 100 ? 100 : timeout - 50, num + 1, selected)
                } else {
                    this.selected = this.people[num % this.people.length]
                    this.people.splice(num % this.people.length, 1)
                    localStorage.setItem('people', JSON.stringify(this.people))
                }
            }, timeout)
        }
    },
    mounted () {
        this.$nextTick(() => {
            console.log(localStorage.getItem('people'))
            if (!localStorage.getItem('people')) {
                localStorage.setItem('people', JSON.stringify(this.people))
            } else {
                this.people = JSON.parse(localStorage.getItem('people'))
            }
            document.body.onkeyup = (e) => {
                if (e.keyCode === 32) {
                    this.stop = true
                }
            }
        })
    }
}
</script>

<style>
.funny-back {
  background-color: #757575;
  background-image: linear-gradient(
      45deg,
      #BDBDBD 25%,
      transparent 25%,
      transparent 75%,
      #BDBDBD 75%,
      #BDBDBD
    ),
    linear-gradient(
      -45deg,
      #BDBDBD 25%,
      transparent 25%,
      transparent 75%,
      #BDBDBD 75%,
      #BDBDBD
    );
  background-size: 60px 60px;
  background-position: 0 0;
  animation: slide 4s infinite linear;
}

.funny-back.black {
  background-color: #616161;
  background-image: linear-gradient(
      45deg,
      #212121 25%,
      transparent 25%,
      transparent 75%,
      #212121 75%,
      #212121
    ),
    linear-gradient(
      -45deg,
      #212121 25%,
      transparent 25%,
      transparent 75%,
      #212121 75%,
      #212121
    );
}

.funny-back.purple {
  background-color: #7E57C2;
  background-image: linear-gradient(
      45deg,
      #5E35B1 25%,
      transparent 25%,
      transparent 75%,
      #5E35B1 75%,
      #5E35B1
    ),
    linear-gradient(
      -45deg,
      #5E35B1 25%,
      transparent 25%,
      transparent 75%,
      #5E35B1 75%,
      #5E35B1
    );
}

.funny-back.red {
  background-color: #EF5350;
  background-image: linear-gradient(
      45deg,
      #B71C1C 25%,
      transparent 25%,
      transparent 75%,
      #B71C1C 75%,
      #B71C1C
    ),
    linear-gradient(
      -45deg,
      #B71C1C 25%,
      transparent 25%,
      transparent 75%,
      #B71C1C 75%,
      #B71C1C
    );
}

.funny-back.green {
  background-color: #00897B;
  background-image: linear-gradient(
      45deg,
      #004D40 25%,
      transparent 25%,
      transparent 75%,
      #004D40 75%,
      #004D40
    ),
    linear-gradient(
      -45deg,
      #004D40 25%,
      transparent 25%,
      transparent 75%,
      #004D40 75%,
      #004D40
    );
}

@keyframes slide {
  from {
    background-position: 0 0;
  }

  to {
    background-position: -120px 60px;
  }
}

.funny-back2 {
  background-color: #3F51B5;
  background-image: linear-gradient(
      45deg,
      #283593 25%,
      transparent 25%,
      transparent 75%,
      #283593 75%,
      #283593
    ),
    linear-gradient(
      -45deg,
      #283593 25%,
      transparent 25%,
      transparent 75%,
      #283593 75%,
      #283593
    );
  background-size: 60px 60px;
  background-position: 0 0;
  animation: slide 4s infinite linear;
}
</style>
