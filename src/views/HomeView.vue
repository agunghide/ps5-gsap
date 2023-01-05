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
                        start: "center center",
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
                    .to("#section1", {y: 0, opacity: 0, display: "none", ease: "power1.out", duration: 0.4})
                    .to("#controller-image", { y :-innerHeight + 110, scale : 0.9 }, ">-0.2")
                    .to("#left-rectangle", {y: -500}, "<+0.1")
                    .to("#right-rectangle", {y: -500}, "<")
                    .to("#dots-element-middle-right", {y: 250, x: 30}, "<")
                    .to("#gamepad-buttons-right", {opacity: 0}, "<+0.2")
                    .to("#gamepad-buttons-left", {x: -300, opacity: 0}, "<")
                    .to("#section2", {y: 0, opacity: 1})
                    .to("#controller-image", {y : -innerHeight + 110, scale: 0.8, ease: "power1.in"})
                    .to("#section2", {opacity: 0}, "<")
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
    <div class="bg-gray-[#747474]">
        <div class="h-full">
            <RectangleLeft id="left-rectangle" class="absolute top-0 left-0 drop-shadow-2xl" />
            <RectangleRight id="right-rectangle" class="absolute top-0 right-0 drop-shadow-2xl" />

            <DotsElement id="dots-element-right" class="absolute top-32 -right-20 drop-shadow-2xl"/>
            <DotsElement id="dots-element-middle-right" class="absolute top-64 right-96 drop-shadow-2xl"/>
            <DotsElement id="dots-element-middle-left" class="absolute top-28 left-96 drop-shadow-2xl"/>
            <DotsElement id="dots-element-left" class="absolute bottom-32 -left-16 drop-shadow-2xl"/>
            
            <GamepadButtonsRight id="gamepad-buttons-right" class="absolute bottom-14 -right-20 drop-shadow-2xl"/>
            <GamepadButtonsLeft id="gamepad-buttons-left" class="absolute -bottom-2 -left-4 drop-shadow-2xl"/>

            <ControllerImage id="controller-image" class="absolute top-full left-1/2 -translate-x-1/2 -translate-y-1/2 scale-90"/>
        </div>
        <section id="section1" class="h-screen">
            <div id="text" class="text-center py-24">
                <h1 class="text-black font-bold text-5xl max-w-[450px] mx-auto mb-8 leading-tight tracking-wide">
                    Are You Ready To Play The Game?
                </h1>
                <p class="text-gray-500 text-xl font-semibold mb-8">
                    The next generations of players begin with Playstation 5
                </p>
                <p class="text-accent text-lg font-bold">
                    DISCOVER
                </p>
            </div>
        </section>
        <section id="section2" class="h-screen">
            <div id="text" class="text-center py-14">
                <p class="text-gray-500 text-lg font-semibold mb-4">
                    The Future of gaming in yout palm
                </p>
                <h1 class="text-black font-bold text-5xl mx-auto mb-8 leading-tight tracking-wide">
                    Playstation 5 DualShock
                </h1>
            </div>
        </section>
    </div>
</template>