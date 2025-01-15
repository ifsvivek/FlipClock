<script>
    import { onMount, onDestroy } from "svelte";
    import "../app.css";

    let hours = "00";
    let minutes = "00";
    let seconds = "00";
    let prevHours = "00";
    let prevMinutes = "00";
    let prevSeconds = "00";
    // @ts-ignore
    let interval;

    function updateTime() {
        const now = new Date();
        prevHours = hours;
        prevMinutes = minutes;
        prevSeconds = seconds;
        hours = String(now.getHours()).padStart(2, "0");
        minutes = String(now.getMinutes()).padStart(2, "0");
        seconds = String(now.getSeconds()).padStart(2, "0");
    }

    onMount(() => {
        updateTime();
        interval = setInterval(updateTime, 1000);
    });

    onDestroy(() => {
        // @ts-ignore
        if (interval) clearInterval(interval);
    });

    // @ts-ignore
    const isFlipping = (curr, prev, idx) => curr[idx] !== prev[idx];
</script>

<div
    class="min-h-screen flex items-center justify-center bg-gradient-to-br from-purple-900 to-gray-900"
>
    <div class="p-8 rounded-3xl bg-black/20 backdrop-blur-xl border border-white/10 shadow-2xl">
        <div class="flex gap-2 sm:gap-3">
            {#each [0, 1] as i}
                <div class="relative w-12 h-16 sm:w-16 sm:h-24">
                    <div class="absolute inset-0 rounded-lg bg-gray-800/80">
                        <div class="relative w-full h-full">
                            <div
                                class="absolute w-full h-1/2 flex items-center justify-center overflow-hidden rounded-t-lg"
                            >
                                <span
                                    class="text-4xl mb-2 sm:text-5xl font-bold text-white translate-y-1/2"
                                    >{hours[i]}</span
                                >
                            </div>
                            <div
                                class="absolute bottom-0 w-full h-1/2 flex items-center justify-center overflow-hidden rounded-b-lg bg-gray-900/80"
                            >
                                <span
                                    class="text-4xl mt-2 sm:text-5xl font-bold text-white -translate-y-1/2"
                                    >{hours[i]}</span
                                >
                            </div>

                            {#if isFlipping(hours, prevHours, i)}
                                <div class="flip-card absolute inset-0">
                                    <div
                                        class="flip-top absolute w-full h-1/2 bg-gray-800/80 rounded-t-lg overflow-hidden"
                                    >
                                        <div
                                            class="absolute inset-0 flex items-center justify-center"
                                        >
                                            <span
                                                class="text-4xl mb-2 sm:text-5xl font-bold text-white translate-y-1/2"
                                                >{prevHours[i]}</span
                                            >
                                        </div>
                                    </div>
                                    <div
                                        class="flip-bottom absolute bottom-0 w-full h-1/2 bg-gray-900/80 rounded-b-lg overflow-hidden"
                                    >
                                        <div
                                            class="absolute inset-0 flex items-center justify-center"
                                        >
                                            <span
                                                class="text-4xl mt-2 sm:text-5xl font-bold text-white -translate-y-1/2"
                                                >{hours[i]}</span
                                            >
                                        </div>
                                    </div>
                                </div>
                            {/if}
                        </div>
                    </div>
                </div>
            {/each}

            <div class="flex items-center text-2xl sm:text-4xl font-bold text-white/50">:</div>

            {#each [0, 1] as i}
                <div class="relative w-12 h-16 sm:w-16 sm:h-24">
                    <div class="absolute inset-0 rounded-lg bg-gray-800/80">
                        <div class="relative w-full h-full">
                            <div
                                class="absolute w-full h-1/2 flex items-center justify-center overflow-hidden rounded-t-lg"
                            >
                                <span
                                    class="text-4xl mb-2 sm:text-5xl font-bold text-white translate-y-1/2"
                                    >{minutes[i]}</span
                                >
                            </div>
                            <div
                                class="absolute bottom-0 w-full h-1/2 flex items-center justify-center overflow-hidden rounded-b-lg bg-gray-900/80"
                            >
                                <span
                                    class="text-4xl mt-2 sm:text-5xl font-bold text-white -translate-y-1/2"
                                    >{minutes[i]}</span
                                >
                            </div>

                            {#if isFlipping(minutes, prevMinutes, i)}
                                <div class="flip-card absolute inset-0">
                                    <div
                                        class="flip-top absolute w-full h-1/2 bg-gray-800/80 rounded-t-lg overflow-hidden"
                                    >
                                        <div
                                            class="absolute inset-0 flex items-center justify-center"
                                        >
                                            <span
                                                class="text-4xl mb-2 sm:text-5xl font-bold text-white translate-y-1/2"
                                                >{prevMinutes[i]}</span
                                            >
                                        </div>
                                    </div>
                                    <div
                                        class="flip-bottom absolute bottom-0 w-full h-1/2 bg-gray-900/80 rounded-b-lg overflow-hidden"
                                    >
                                        <div
                                            class="absolute inset-0 flex items-center justify-center"
                                        >
                                            <span
                                                class="text-4xl mt-2 sm:text-5xl font-bold text-white -translate-y-1/2"
                                                >{minutes[i]}</span
                                            >
                                        </div>
                                    </div>
                                </div>
                            {/if}
                        </div>
                    </div>
                </div>
            {/each}

            <div class="flex items-center text-2xl sm:text-4xl font-bold text-white/50">:</div>

            {#each [0, 1] as i}
                <div class="relative w-12 h-16 sm:w-16 sm:h-24">
                    <div class="absolute inset-0 rounded-lg bg-gray-800/80">
                        <div class="relative w-full h-full">
                            <div
                                class="absolute w-full h-1/2 flex items-center justify-center overflow-hidden rounded-t-lg"
                            >
                                <span
                                    class="text-4xl mb-2 sm:text-5xl font-bold text-white translate-y-1/2"
                                    >{seconds[i]}</span
                                >
                            </div>
                            <div
                                class="absolute bottom-0 w-full h-1/2 flex items-center justify-center overflow-hidden rounded-b-lg bg-gray-900/80"
                            >
                                <span
                                    class="text-4xl mt-2 sm:text-5xl font-bold text-white -translate-y-1/2"
                                    >{seconds[i]}</span
                                >
                            </div>

                            {#if isFlipping(seconds, prevSeconds, i)}
                                <div class="flip-card absolute inset-0">
                                    <div
                                        class="flip-top absolute w-full h-1/2 bg-gray-800/80 rounded-t-lg overflow-hidden"
                                    >
                                        <div
                                            class="absolute inset-0 flex items-center justify-center"
                                        >
                                            <span
                                                class="text-4xl mb-2 sm:text-5xl font-bold text-white translate-y-1/2"
                                                >{prevSeconds[i]}</span
                                            >
                                        </div>
                                    </div>
                                    <div
                                        class="flip-bottom absolute bottom-0 w-full h-1/2 bg-gray-900/80 rounded-b-lg overflow-hidden"
                                    >
                                        <div
                                            class="absolute inset-0 flex items-center justify-center"
                                        >
                                            <span
                                                class="text-4xl mt-2 sm:text-5xl font-bold text-white -translate-y-1/2"
                                                >{seconds[i]}</span
                                            >
                                        </div>
                                    </div>
                                </div>
                            {/if}
                        </div>
                    </div>
                </div>
            {/each}
        </div>
    </div>
</div>

<style>
    .flip-card {
        perspective: 1000px;
    }

    .flip-top {
        transform-origin: bottom;
        animation: flipTop 0.3s ease-in;
        animation-fill-mode: forwards;
        backface-visibility: hidden;
    }

    .flip-bottom {
        transform-origin: top;
        transform: rotateX(90deg);
        animation: flipBottom 0.3s ease-out;
        animation-fill-mode: forwards;
        backface-visibility: hidden;
    }

    @keyframes flipTop {
        0% {
            transform: rotateX(0deg);
        }
        100% {
            transform: rotateX(-90deg);
        }
    }

    @keyframes flipBottom {
        0% {
            transform: rotateX(90deg);
        }
        100% {
            transform: rotateX(0deg);
        }
    }
</style>
