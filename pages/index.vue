<template>
    <div class="tictac">
        <div class="tictac--topline"></div>

        <div class="tictac__body">

            <div class="tictac__body--top">
                <img src="@/assets/img/logo.svg" alt="Логотип" class="logo">

                <h1>
                    <span>задай ритм</span>
                    <div>
                        настроению <br> с TIC TAC
                    </div>
                </h1>

                <h2>Создавай треки и выигрывай классные призы!</h2>
            </div>

            <img src="@/assets/img/mic.svg" class="mic" alt="Микрофон">

            <div class="tictac__body--bottom">

                <Timer date_to="01.01.2025" />

                <span>Перематываем треки, осталось:</span>
            </div>

        </div>

        <div class="tictac--bottomline"></div>
    </div>
</template>
<script>
export default {
    data() {
        return {

        }
    }
}
</script>
<style lang="scss" scoped>
.tictac {
    background-image: url('@/assets/img/bgpage.png');
    background-repeat: no-repeat;
    background-size: cover;
    width: 100%;
    height: 100vh;
    display: flex;
    align-items: flex-start;
    flex-direction: column;
    justify-content: space-between;

    @media (max-width: 1024px) {
        background-image: url('@/assets/img/bgpage_tablet.png');
    }

    @media (max-width: 768px) {
        background-image: url('@/assets/img/bgpage_tablet_vert.png');
    }

    @media (max-width: 450px) {
        background-image: url('@/assets/img/bgpage_mob.png');
        background-size: 100vw 100vh;
    }

    &__body {
        padding: 20px 40px;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        width: 100%;
        height: 100%;
        position: relative;

        @media (max-width: 700px) {
            padding: 20px 15px;
        }

        .mic {
            position: absolute;
            left: 108px;
            z-index: 1;
            bottom: -50px;

            height: 24.323vw;

            @media (max-width: 1024px) {
                display: none;
            }
        }

        &--bottom {
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            gap: 10px;
            width: 100%;

            span {
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
                }
            }
        }

        &--top {
            display: flex;
            flex-direction: column;
            align-items: flex-start;
            max-width: 455px;

            .logo {
                @media (max-width: 700px) {
                    width: 52px;
                    height: 38px;
                }
            }

            h1 {
                font-weight: 800;
                font-size: 49px;
                line-height: 123%;
                text-transform: uppercase;
                color: #fff;
                font-family: var(--loos);
                margin-top: 30px;
                margin-bottom: 12px;

                @media (max-width: 1024px) {
                    font-size: 46px;
                }

                @media (max-width: 700px) {
                    font-size: 38px;
                    margin-top: 12px;
                }

                @media (max-width: 360px) {
                    font-size: 34px;
                }

                @media (max-width: 330px) {
                    font-size: 30px;
                }

                span {
                    border-radius: 64px;
                    border: 3px solid #11FB89;
                    padding: 5px 8px 0px 8px;
                    line-height: 100%;
                    font-family: var(--loos);
                }

                div {
                    margin-left: 10px;

                    &::after {
                        content: url('@/assets/img/wave.svg');

                        @media (max-width: 700px) {
                            content: url('@/assets/img/wave_small.svg');
                        }
                    }
                }
            }

            h2 {
                font-weight: 400;
                font-size: 26px;
                color: #fff;
                font-family: var(--loos);
                margin: 0;
                margin-left: 10px;

                @media (max-width: 1024px) {
                    font-size: 24px;
                }

                @media (max-width: 700px) {
                    font-size: 20px;
                }

                @media (max-width: 360px) {
                    font-size: 18px;
                }
            }
        }
    }

    &--topline {
        background: rgba(0, 0, 0, 0.4);
        width: 100%;
        height: 151px;

        @media (max-width: 1024px) {
            display: none;
        }
    }

    &--bottomline {
        background: rgba(0, 0, 0, 0.4);
        width: 100%;
        height: 92px;
        z-index: 5;

        @media (max-width: 1024px) {
            display: none;
        }
    }
}
</style>