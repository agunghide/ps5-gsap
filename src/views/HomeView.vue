<script lang="ts">
    import ControllerImage from '@/components/ControllerImage.vue'
    import RectangleRight from '@/components/RectangleRight.vue'
    import RectangleLeft from '@/components/RectangleLeft.vue'
    import DotsElement from '@/components/DotsElement.vue'
    import GamepadButtonsRight from '@/components/GamepadButtonsRight.vue'
    import GamepadButtonsLeft from '@/components/GamepadButtonsLeft.vue'
    import gsap from 'gsap'
    import { ScrollTrigger } from "gsap/ScrollTrigger";

    gsap.registerPlugin(ScrollTrigger);
    export default {
        setup() {
            function scroll() {
                const body = gsap.timeline({
                    scrollTrigger: {
                        trigger: "body",
                        start: "top top",
                        end: "bottom top",
                        scrub: true,
                        pin: true,
                    }
                })

                body
                    .from("#controller-image", { scale : 0.9 })
                    .from("#left-rectangle", {y: 0})
                    .from("#right-rectangle", {y: 0})
                    .from("#section1", {y: 0})
                    .from("#section2", {y: innerHeight, opacity: 0})
                    .from("#section3", {y: innerHeight, opacity: 0})
                    .to("#section1", {opacity: 0, ease: "power1.out"})
                    .to("#section1", {display: "none"}, ">")
                    .to("#controller-image", { y :-innerHeight + 110, scale : 0.9 }, ">-0.6")
                    .to("#gamepad-buttons-right", {opacity: 0}, "<")
                    .to("#gamepad-buttons-left", {x: -300, opacity: 0}, "<")
                    .to("#left-rectangle", {y: -500, ease: "power1.out"}, "<")
                    .to("#right-rectangle", {y: -500, ease: "power1.out"}, "<")
                    .to("#dots-element-middle-right", {y: 250, x: 30}, "<")
                    .to("#section2", {y: 0, opacity: 1, duration: 0.5}, ">")
                    .to("#controller-image", {y : -innerHeight + 110, scale: 0.8, ease: "power1.in"}, ">+1.3")
                    .to("#section2", {opacity: 0, ease: "power1.out", duration: 0.4}, "<")
                    .to("#section2", {display: "none"}, "<+0.2")
                    .to("#section3", {opacity: 1, ease: "power1.in", duration: 0.3}, ">-0.9")
            }
            return {
                scroll
            }
        },
        components: {
            ControllerImage,
            RectangleRight,
            RectangleLeft,
            DotsElement,
            GamepadButtonsRight,
            GamepadButtonsLeft
        },
        mounted() {
            this.scroll();
        }
    }
</script>

<template>
    <div id="container" class="bg-gray-[#747474]">
        <div class="h-full">
            <RectangleLeft id="left-rectangle" class="absolute top-0 left-0 drop-shadow-2xl" />
            <RectangleRight id="right-rectangle" class="absolute top-0 right-0 drop-shadow-2xl" />

            <DotsElement id="dots-element-right" class="absolute top-32 -right-20 drop-shadow-2xl"/>
            <DotsElement id="dots-element-middle-right" class="absolute top-64 right-96 drop-shadow-2xl"/>
            <DotsElement id="dots-element-middle-left" class="absolute top-28 left-96 drop-shadow-2xl"/>
            <DotsElement id="dots-element-left" class="absolute bottom-32 -left-16 drop-shadow-2xl"/>
            
            <GamepadButtonsRight id="gamepad-buttons-right" class="absolute bottom-14 -right-20 drop-shadow-2xl"/>
            <GamepadButtonsLeft id="gamepad-buttons-left" class="absolute -bottom-2 -left-4 drop-shadow-2xl"/>

            <ControllerImage id="controller-image" class="absolute top-full left-1/2 -translate-x-1/2 -translate-y-[55%] scale-90"/>
        </div>
        <section id="section1" class="h-screen text-center py-24 space-y-14">
            <h2 class="text-black font-bold text-5xl max-w-[450px] mx-auto leading-tight tracking-wide">
                Are You Ready To Play The Game?
            </h2>
            <p class="text-gray-500 text-xl font-semibold">
                The next generations of players begin with Playstation 5
            </p>
            <p class="text-accent text-lg font-bold">
                DISCOVER
            </p>
        </section>
        <section id="section2" class="h-screen text-center py-14">
            <p class="text-gray-500 text-lg font-semibold mb-4">
                The Future of gaming in yout palm
            </p>
            <h1 class="text-black font-bold text-5xl mx-auto mb-8 leading-tight tracking-wide">
                Playstation 5 DualShock
            </h1>
        </section>
        <section id="section3" class="h-screen">
            <div class="text-center py-14">
                <p class="text-gray-500 text-lg font-semibold mb-4">
                    Evolve Your Experience Around
                </p>
                <h2 class="text-black font-bold text-5xl mx-auto mb-8 leading-tight tracking-wide">
                    Latest Technologies
                </h2>
            </div>
            <div class="flex justify-between container mx-auto">
                <div class="tooltips left">
                    <div class="tooltip-item-container -right-8">
                        <div class="tooltip-item">Ergonomic Design</div>
                    </div>
                    <div class="tooltip-item-container">
                        <div class="tooltip-item">Longer Battery Service</div>
                    </div>
                    <div class="tooltip-item-container -right-8">
                        <div class="tooltip-item">Wireless Charging</div>
                    </div>
                </div>
                <div class="tooltips">
                    <div class="tooltip-item-container -left-8">
                        <div class="tooltip-item">Two-tone Design</div>
                    </div>
                    <div class="tooltip-item-container">
                        <div class="tooltip-item">3D Audio</div>
                    </div>
                    <div class="tooltip-item-container -left-8">
                        <div class="tooltip-item">Additional Trigger</div>
                    </div>
                </div>
            </div>
        </section>
    </div>
</template>

<style scoped>
    .tooltips {
        @apply flex flex-col space-y-24;
    }
    .tooltip-item-container {
        z-index: 1;
        width: 219px;
        height: 45px;

        background: #FFFFFF;
        box-shadow: 0px 0px 2px rgba(0, 0, 0, 0.25);
        border-radius: 100px 46px 44px 0px;
        @apply flex justify-center items-center relative;
    }

    .tooltips.left .tooltip-item-container {
        border-radius: 46px 100px 0px 44px;
    }

    .tooltip-item::before {
        content: '';
        z-index: -1;
        width: 217.4px;
        height: 42.78px;

        box-shadow: 0px 0px 3px rgba(0, 0, 0, 0.25);
        border-radius: inherit;
        background: linear-gradient(180deg, rgba(4,41,173,1) 0%, rgba(173,4,166,1) 100%);
        @apply absolute;
    }

    .tooltip-item {
        content: '';
        width: 213.4px;
        height: 39.78px;
        box-shadow: 0px 0px 3px rgba(0, 0, 0, 0.25);
        border-radius: inherit;
        background: rgb(231, 242, 255);
        @apply flex justify-center items-center relative -right-1 text-accent;
    }
    .tooltips.left .tooltip-item {
        @apply -left-1;
    }
</style>