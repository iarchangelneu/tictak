<template>
    <div class="timer">
        <div class="timer__body">
            <div class="timer__body--day">
                <span>{{ timeLeft.days }}</span>
                <small>дней</small>
                <img src="@/assets/img/timer_bg.svg" alt="Дней" />
            </div>

            <div class="timer__body--raz">
                <span>:</span>
            </div>

            <div class="timer__body--day">
                <span>{{ timeLeft.hours }}</span>
                <small>часов</small>
                <img src="@/assets/img/timer_bg.svg" alt="Часов" />
            </div>

            <div class="timer__body--raz">
                <span>:</span>
            </div>

            <div class="timer__body--day">
                <span>{{ timeLeft.minutes }}</span>
                <small>минут</small>
                <img src="@/assets/img/timer_bg.svg" alt="Минут" />
            </div>

            <div class="timer__body--raz">
                <span>:</span>
            </div>

            <div class="timer__body--day">
                <span>{{ timeLeft.seconds }}</span>
                <small>секунд</small>
                <img src="@/assets/img/timer_bg.svg" alt="Секунд" />
            </div>
        </div>
    </div>

    <Head>
        <Title>Задай ритм настроению с TIC TAC</Title>
    </Head>
</template>

<script>
export default {
    props: {
        date_to: {
            type: String,
            default: ''
        }
    },
    data() {
        return {
            timeLeft: {
                days: 0,
                hours: 0,
                minutes: 0,
                seconds: 0
            },
            timer: null
        };
    },
    mounted() {
        this.startTimer();
    },
    methods: {
        calculateTimeLeft() {
            const targetDate = new Date(this.date_to.split('.').reverse().join('-')).getTime();
            const now = new Date().getTime();
            const difference = targetDate - now;

            if (difference > 0) {
                this.timeLeft.days = Math.floor(difference / (1000 * 60 * 60 * 24));
                this.timeLeft.hours = Math.floor((difference / (1000 * 60 * 60)) % 24);
                this.timeLeft.minutes = Math.floor((difference / (1000 * 60)) % 60);
                this.timeLeft.seconds = Math.floor((difference / 1000) % 60);
            } else {
                clearInterval(this.timer);
                this.timeLeft = { days: 0, hours: 0, minutes: 0, seconds: 0 };
            }
        },
        startTimer() {
            this.calculateTimeLeft();
            this.timer = setInterval(this.calculateTimeLeft, 1000);
        }
    },
    beforeDestroy() {
        clearInterval(this.timer);
    }
};
</script>
<style lang="scss" scoped>
.timer {
    &__body {
        display: flex;
        align-items: flex-start;
        gap: 30px;

        @media (max-width: 700px) {
            gap: 10px;
        }

        &--raz {
            font-weight: 800;
            font-size: 72px;
            line-height: 123%;
            text-transform: uppercase;
            text-align: center;
            color: #fff;
            font-family: var(--loos);

            @media (max-width: 700px) {
                font-size: 38px;
            }
        }

        &--day {
            display: flex;
            flex-direction: column;
            gap: 10px;
            position: relative;

            @media (max-width: 700px) {
                gap: 5px;
            }

            span {
                font-weight: 800;
                font-size: 72px;
                line-height: 123%;
                text-transform: uppercase;
                text-align: center;
                color: #fff;
                font-family: var(--loos);
                z-index: 5;
                width: 105px;


                @media (max-width: 700px) {
                    font-size: 38px;
                    width: 57px;
                }
            }

            img {
                z-index: 1;
                position: absolute;
                top: -10px;
                left: 0;

                @media (max-width: 700px) {
                    width: 80px;
                    height: 60px;

                    top: -10px;
                    left: -10px;
                }
            }

            small {
                font-weight: 400;
                font-size: 22px;
                text-align: center;
                color: #fff;
                font-family: var(--loos);

                @media (max-width: 1024px) {
                    font-size: 19px;
                }

                @media (max-width: 700px) {
                    font-size: 14px;
                    display: block;

                }
            }
        }
    }
}
</style>