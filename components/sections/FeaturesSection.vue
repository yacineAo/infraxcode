<template>
    <section class="flex flex-col w-full items-center gap-[50px] relative">
        <!-- From intent to action -->
        <div class="flex flex-col items-start gap-8 px-[200px] py-[130px] relative w-full translate-y-[-1rem] animate-fade-in"
            style="--animation-delay:200ms">
            <div class="flex flex-col items-start gap-4 relative w-full">
                <h2 class="relative w-fit font-semibold text-white text-[40px] whitespace-nowrap">
                    From intent to action in four steps
                </h2>
                <p class="relative max-w-[625px] font-medium text-[#ffffffb2] text-base">
                    Network work lives across terminals, scripts, tickets, and tribal
                    knowledge. <br />
                    Context gets lost, changes feel risky, and time disappears into
                    tool-hopping.
                </p>
            </div>

            <div class="flex w-full max-w-[1040px] items-start justify-between gap-6 relative">
                <!-- Left steps -->
                <div class="flex flex-col w-full max-w-[419px] items-start gap-6 relative">
                    <div v-for="(step, index) in stepsData" :key="index"
                        class="flex w-full items-start gap-6 px-6 py-4 bg-[#ffffff1a] rounded-[15px] border-none"
                        :class="step.isExpanded ? 'pt-4 pb-6' : 'opacity-80'">
                        <div class="flex items-start gap-6 p-0 w-full">
                            <div v-if="step.isExpanded" class="relative w-[125px] h-[5px] ml-[-60px] rotate-90">
                                <div class="w-[125px] flex bg-[#ffffff1a] rounded-[30px]">
                                    <div class="mt-0 w-[5.29px] h-[5px] ml-0 bg-[#574fa1] rounded-[18.75px]" />
                                </div>
                            </div>

                            <div class="flex items-start gap-6 flex-1">
                                <div
                                    class="inline-flex flex-col items-center justify-center gap-2.5 px-3.5 py-1 bg-[#ffffff1a] rounded-[5px] min-w-[37px]">
                                    <div class="font-semibold text-white text-2xl text-center">
                                        {{ step.number }}
                                    </div>
                                </div>
                                <div class="flex flex-col items-start gap-3 flex-1">
                                    <h3 class="font-semibold text-white text-2xl">{{ step.title }}</h3>
                                    <p v-if="step.isExpanded && step.description"
                                        class="font-medium text-white text-base leading-[21px]">
                                        {{ step.description }}
                                    </p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Right illustration -->
                <div class="relative w-full max-w-[597px] h-[513px] bg-[#ffffff0f] rounded-[5px]" />
            </div>
        </div>

        <!-- Discover what's next -->
        <div class="inline-flex flex-col items-center gap-16 relative translate-y-[-1rem] animate-fade-in"
            style="--animation-delay:600ms">
            <div class="w-full max-w-[591px] items-center gap-1 flex flex-col relative">
                <div class="inline-flex flex-col items-center gap-2 relative">
                    <h2 class="text-white text-[40px] font-semibold text-center">Discover what's next</h2>
                    <p class="text-[#ffffffb2] text-base text-center max-w-[472px]">
                        Lorem ipsum dolor sit amet consectetur. Sit neque ullamcorper eget
                        orci suscipit et a nullam ultrices.
                    </p>
                </div>
            </div>

            <div class="flex flex-col w-full max-w-[1040px] items-start gap-12 relative">
                <div v-for="(feature, index) in upcomingFeaturesData" :key="index"
                    class="flex items-center gap-6 pt-12 pb-10 px-10 w-full bg-[#ffffff0d] rounded-[5px] border-none relative overflow-hidden">
                    <div class="flex flex-col w-full max-w-[608px] items-center gap-6 z-10">
                        <h3 class="text-white text-[32px] font-semibold text-center">{{ feature.title }}</h3>
                        <p class="text-center text-xl">
                            <span class="font-semibold text-white">{{ feature.description.split(':')[0] }}:</span>
                            <span class="font-semibold text-[#ffffffcc]">{{ feature.description.split(':')[1] }}</span>
                        </p>
                        <button
                            class="flex w-[196px] items-center justify-center gap-2.5 px-6 py-3 rounded-[5px] bg-[linear-gradient(153deg,rgba(87,79,161,1)_0%,rgba(204,160,202,1)_100%)] hover:opacity-90 transition-opacity">
                            <img src="https://c.animaapp.com/mhalnqzadLBG4i/img/vector.svg" alt="icon"
                                class="w-[13px] h-[13px]" />
                            <span class="font-bold text-white text-base">{{ feature.votes }}</span>
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script setup>
const stepsData = [
    {
        number: "1",
        title: "Insert a prompt",
        description:
            "Tell Diverz what you want: run a check, make a config change, or debug an issue. Plain language, no syntax wrangling.",
        isExpanded: true,
    },
    {
        number: "2",
        title: "Diverz gets context and shares execution plan",
        description: "",
        isExpanded: false,
    },
    {
        number: "3",
        title: "Approve or refine",
        description: "",
        isExpanded: false,
    },
    {
        number: "4",
        title: "Execute and report",
        description: "",
        isExpanded: false,
    },
];

const upcomingFeaturesData = [
    {
        title: "Workflow studio",
        description:
            "Visual runbook builder: compose CLI/API/script steps with conditions and loops, gate via pre/post checks and the twin, version in Git, schedule or event-trigger runs, and observe execution end-to-end",
        votes: "220 voted",
    },
    {
        title: "Change-impact simulator",
        description:
            "High-fidelity AI twin for devices and topologies: stage change plans, compare route/ACL diffs, detect blast radius, and export rollback bundles before any production commit",
        votes: "220 voted",
    },
];
</script>

<style scoped>
.animate-fade-in {
    animation: fadeIn 0.8s ease forwards;
}

@keyframes fadeIn {
    to {
        opacity: 1;
        transform: translateY(0);
    }
}
</style>
