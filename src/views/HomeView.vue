<script lang="ts">
    import ControllerImage from '@/components/ControllerImage.vue'
    import gsap from 'gsap'
    import { ScrollTrigger } from "gsap/ScrollTrigger";

    gsap.registerPlugin(ScrollTrigger);
    export default {
        setup() {
            function scroll() {
                // const section1 = gsap.timeline({
                //     scrollTrigger: {
                //         trigger: "#section1",
                //         start: "center center",
                //         // end: "bottom top",
                //         markers: true,
                //         end: () => "+=500",
                //         scrub: true,
                //         pin: true,
                //     },
                //     // paused: true,
                // })

                // section1
                //     .from('#text', {opacity: 1, y: 0})
                //     .from("#controller-image", { y : 0 })
                //     .to('#text', {opacity: 0, y: 0, ease: "power1.in"})
                //     .to("#controller-image", { y : innerHeight/2})

                // const section2 = gsap.timeline({
                //     scrollTrigger: {
                //         trigger: "#section2",
                //         start: "center center",
                //         end: "bottom top",
                //         // markers: true,
                //         // end: "+=300",
                //         scrub: true,
                //         pin: true,
                //     }
                // })

                // section2
                //     .from('#section2', {opacity: 1, y: 0})
                //     .from("#controller-image", { y : innerHeight/2 })
                //     .to('#section2', {opacity: 0, y: 0, ease: "power1.in"})
                    // .to("#controller-image", { y : 500 })

                const body = gsap.timeline({
                    scrollTrigger: {
                        trigger: "body",
                        start: "center center",
                        end: "bottom top",
                        // markers: true,
                        // end: "+=700",
                        scrub: true,
                        pin: true,
                    }
                })

                body
                    .from("#controller-image", { scale : 0.9 })
                    .from("#section1", {y: 0})
                    .from("#section2", {y: innerHeight, opacity: 0})
                    .to("#section1", {y: 0, opacity: 0, display: "none", ease: "power1.out", duration: 0.4})
                    .to("#controller-image", { y :-innerHeight + 110, scale : 0.9 }, ">-0.3")
                    .to("#section2", {y: 0, opacity: 1})
                    .to("#controller-image", {y : -innerHeight + 110, scale: 0.8, ease: "power1.in"})
                    .to("#section2", {opacity: 0}, "<")
            }
            return {
                scroll
            }
        },
        components: {
            ControllerImage
        },
        mounted() {
            this.scroll();
        }
    }
</script>

<template>
        <!-- <section id="section1" class="h-[calc(100vh-10vh)] ">
            <div id="text" class="text-center py-24">
                <h1 class="text-black font-bold text-5xl max-w-[450px] mx-auto mb-8 leading-tight">
                    Are You Ready To Play The Game
                </h1>
                <p class="text-gray-500 text-lg">
                    The next generations of players begin with Play Station 5
                </p>
            </div>
        </section>
        
        <section id="section2" class="text-5xl font-bold h-screen bg-blue-400">
            Tes Data
        </section> -->
    <div class="h-full">
        <ControllerImage id="controller-image" class="absolute top-full left-1/2 -translate-x-1/2 -translate-y-1/2 scale-90"/>
    </div>
    <section id="section1" class="h-screen">
        <div id="text" class="text-center py-24">
            <h1 class="text-black font-bold text-5xl max-w-[450px] mx-auto mb-8 leading-tight tracking-wide">
                Are You Ready To Play The Game
            </h1>
            <p class="text-gray-500 text-lg font-semibold mb-8">
                The next generations of players begin with Play Station 5
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

</template>