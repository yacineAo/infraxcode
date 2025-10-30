<template>
    <section class="flex flex-col w-full items-center gap-8 md:gap-[50px] relative">
        <!-- From intent to action -->
        <div class="flex flex-col items-start gap-4 md:gap-8 px-4 sm:px-8 md:px-16 lg:px-[200px] py-8 md:py-16 lg:py-[130px] relative w-full translate-y-[-1rem] animate-fade-in"
            style="--animation-delay:200ms">
            <div class="flex flex-col items-start gap-4 relative w-full">
                <h2 class="font-semibold text-white text-2xl sm:text-3xl lg:text-[40px] font-display leading-tight">
                    From intent to action in four steps
                </h2>
                <p
                    class="max-w-full sm:max-w-[625px] font-medium text-[#ffffffb2] text-sm sm:text-base leading-relaxed">
                    Network work lives across terminals, scripts, tickets, and tribal
                    knowledge.
                    <br class="hidden sm:block" />
                    Context gets lost, changes feel risky, and time disappears into
                    tool-hopping.
                </p>
            </div>
            <div class="flex flex-col lg:flex-row w-full items-start gap-4 md:gap-6 relative">
                <div
                    class="flex flex-col w-full lg:max-w-[619px] items-start gap-4 md:gap-6 relative order-2 lg:order-1">
                    <div v-for="(step, index) in stepsData" :key="index"
                        class="flex w-full items-start gap-4 md:gap-6 px-4 md:px-6 py-3 md:py-4 rounded-[15px] border-none cursor-pointer "
                        :class="step.isExpanded ? 'pt-3 md:pt-4 pb-5 md:pb-6 bg-[#ffffff1a]' : 'opacity-80'"
                        @click="toggleExpansion(index)">
                        <div class="flex items-center gap-4 md:gap-6 p-0 w-full">
                            <div v-if="step.isExpanded"
                                class="relative w-[80px] md:w-[125px] h-[5px] ml-[-40px] md:ml-[-60px] rotate-90">
                                <div class="w-[80px] md:w-[125px] flex bg-[#ffffff1a] rounded-[30px]">
                                    <div class="mt-0 w-[5.29px] h-[5px] ml-0 bg-[#574fa1] rounded-[18.75px]" />
                                </div>
                            </div>

                            <div class="flex items-start gap-4 md:gap-6 flex-1">
                                <div
                                    class="inline-flex flex-col items-center justify-center gap-2 px-2 md:px-3.5 py-1 bg-[#ffffff1a] rounded-[5px] min-w-[32px] md:min-w-[37px]">
                                    <div class="font-semibold text-white text-xl md:text-2xl text-center">
                                        {{ step.number }}
                                    </div>
                                </div>
                                <div class="flex flex-col items-start gap-2 md:gap-3 flex-1">
                                    <h3 class="font-semibold text-white text-xl md:text-2xl font-display">{{ step.title
                                        }}</h3>
                                    <p v-if="step.isExpanded && step.description"
                                        class="font-medium text-white text-sm md:text-base leading-[18px] md:leading-[21px]">
                                        {{ step.description }}
                                    </p>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                <div
                    class="relative flex-1 h-48 md:h-64 lg:h-[513px] bg-[#ffffff0f] rounded-[5px] order-1 lg:order-2 mx-auto lg:mx-0">
                </div>
            </div>
        </div>

        <!-- Developer-Grade Productivity -->
        <ProductivityFeatures />

        <!-- Discover what's next -->
        <section class="px-4 sm:px-8 md:px-16 lg:px-[200px] py-16 md:py-[100px] relative w-full">
            <div class="inline-flex w-full flex-col items-center gap-8 md:gap-16 relative translate-y-[-1rem] animate-fade-in"
                style="--animation-delay:600ms">
                <div class=" w-full items-center gap-1 flex flex-col relative">
                    <div class="inline-flex flex-col items-center gap-2 relative">
                        <h2
                            class="relative max-w-[404px] font-semibold text-white text-3xl sm:text-4xl lg:text-[40px] text-center font-display">
                            Discover what's next</h2>
                        <p class="relative max-w-[472px] font-medium text-[#ffffffb2] text-sm sm:text-base text-center">
                            Lorem ipsum dolor sit amet consectetur. Sit neque ullamcorper eget
                            orci suscipit et a nullam ultrices
                        </p>
                    </div>
                </div>
                <div class=" flex flex-col w-full items-start gap-8 md:gap-12 relative">
                    <div v-for="(feature, index) in upcomingFeatures" :key="index"
                        class="flex flex-col items-center gap-4 md:gap-6 pt-8 md:pt-12 pb-8 md:pb-10 px-6 md:px-10 w-full bg-[#ffffff0d] rounded-[5px] border-none relative overflow-hidden">
                        <div class="flex flex-col w-full md:w-[608px] items-center gap-4 md:gap-6 z-10">
                            <h3 class="font-semibold text-white text-2xl md:text-[32px] text-center font-display">{{
                                feature.title }}</h3>
                            <p
                                class="font-semibold text-[#ffffffcc] text-lg md:text-xl text-center leading-[24px] md:leading-[27px]">
                                {{ feature.description }}
                            </p>
                        </div>
                        <button
                            class="flex w-[196px] items-center justify-center gap-2.5 px-6 py-3 rounded-[5px] bg-[linear-gradient(153deg,rgba(87,79,161,1)_0%,rgba(204,160,202,1)_100%)] hover:opacity-90 transition-opacity h-auto">
                            <svg width="13" height="13" viewBox="0 0 13 13" fill="none"
                                xmlns="http://www.w3.org/2000/svg">
                                <path
                                    d="M12.6876 6.06609L8.1532 4.8468L6.93391 0.312417C6.90762 0.222286 6.85281 0.143114 6.7777 0.0867824C6.70259 0.030451 6.61124 0 6.51736 0C6.42347 0 6.33212 0.030451 6.25701 0.0867824C6.1819 0.143114 6.12709 0.222286 6.1008 0.312417L4.8468 4.8468L0.312417 6.06609C0.222286 6.09238 0.143114 6.14719 0.0867824 6.2223C0.030451 6.29741 0 6.38876 0 6.48264C0 6.57653 0.030451 6.66788 0.0867824 6.74299C0.143114 6.8181 0.222286 6.87291 0.312417 6.8992L4.8468 8.13585L6.06609 12.6876C6.09238 12.7777 6.14719 12.8569 6.2223 12.9132C6.29741 12.9695 6.38876 13 6.48264 13C6.57653 13 6.66788 12.9695 6.74299 12.9132C6.8181 12.8569 6.87291 12.7777 6.8992 12.6876L8.13585 8.1532L12.6876 6.93391C12.7777 6.90762 12.8569 6.85281 12.9132 6.7777C12.9695 6.70259 13 6.61124 13 6.51736C13 6.42347 12.9695 6.33212 12.9132 6.25701C12.8569 6.1819 12.7777 6.12709 12.6876 6.1008V6.06609Z"
                                    fill="white" />
                            </svg>
                            <span class="font-bold text-white text-base text-center whitespace-nowrap">
                                {{ feature.votes }}
                            </span>
                        </button>
                        <div
                            class="absolute -top-3 left-[400px] md:left-[625px] w-[300px] md:w-[415px] h-[300px] md:h-[415px] bg-[#574fa1] rounded-[207.5px] blur-[300px]" />
                        <img :class="['absolute', index === 0 ? 'top-[229px]' : 'top-[215px]']" left-[300px]
                            md:left-[409px] class="w-2 h-2" alt="Vector"
                            src="https://c.animaapp.com/mhc1z55wRcb3W7/img/vector.svg" />
                        <img class="absolute top-[213px] left-[400px] md:left-[606px] w-[7px] h-[7px]" alt="Vector"
                            src="https://c.animaapp.com/mhc1z55wRcb3W7/img/vector.svg" />
                        <img class="absolute top-64 left-[400px] md:left-[625px] w-1.5 h-1.5" alt="Vector"
                            src="https://c.animaapp.com/mhc1z55wRcb3W7/img/vector.svg" />
                        <img class="absolute top-[213px] left-[300px] md:left-[465px] w-1.5 h-1.5" alt="Vector"
                            src="https://c.animaapp.com/mhc1z55wRcb3W7/img/vector.svg" />
                        <img :class="['absolute', index === 0 ? 'top-[259px]' : 'top-64']" left-[300px] md:left-[413px]
                            class="w-1.5 h-1.5" alt="Vector"
                            src="https://c.animaapp.com/mhc1z55wRcb3W7/img/vector.svg" />
                    </div>
                </div>
            </div>
        </section>


        <!-- Built for how engineers really work -->
        <div class="flex flex-col items-start gap-8 md:gap-12 px-4 sm:px-8 md:px-16 lg:px-[200px] py-16 md:py-[100px] relative w-full translate-y-[-1rem] animate-fade-in"
            style="--animation-delay:800ms">
            <div class="items-start gap-3 w-full flex flex-col relative">
                <div class="inline-flex items-start gap-1 flex-col relative">
                    <h2
                        class="relative w-fit bg-gradient-to-r from-[#574fa1] to-[#cca0ca] bg-clip-text text-transparent font-semibold text-3xl sm:text-4xl lg:text-[40px] whitespace-nowrap font-display">
                        Diverz
                    </h2>
                    <h3
                        class="relative w-fit font-semibold text-white text-3xl sm:text-4xl lg:text-[40px] font-display">
                        Built for how engineers really work
                    </h3>
                </div>
                <p class="relative max-w-[611px] font-medium text-[#ffffffb2] text-sm sm:text-base">
                    Diverz brings the structure, speed, and context of a developer IDE
                    to <br class="hidden md:block" />
                    real-world infrastructure operations
                </p>
            </div>
            <div class="grid grid-cols-1 md:grid-cols-3  justify-center relative w-full gap-5 ">
                <div v-for="(feature, index) in engineerFeatures" :key="index"
                    class="inline-flex flex-col items-start gap-4 md:gap-6 relative flex-1">
                    <img class="relative w-10 h-10 md:w-12 md:h-12" :alt="`Icon ${index + 1}`" :src="feature.icon" />
                    <div class="inline-flex items-start gap-3 flex-col relative">
                        <div class="inline-flex items-start gap-1 flex-col relative">
                            <h4 class="relative w-fit font-bold text-white text-xl md:text-2xl font-display">{{
                                feature.title }}</h4>
                            <p class="relative w-[260px] font-semibold text-[#ffffff8c] text-base md:text-lg">{{
                                feature.subtitle }}</p>
                        </div>
                        <p class="relative w-[260px] font-medium text-[#ffffffb2] text-sm sm:text-base">{{
                            feature.description }}</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- Testimonial -->
        <div class="flex flex-col items-center gap-6 md:gap-10 px-4 sm:px-8 md:px-16 lg:px-[200px] py-12 md:py-20 relative w-full translate-y-[-1rem] animate-fade-in"
            style="--animation-delay:1000ms">
            <div
                class="flex flex-col max-w-[880px] items-start gap-8 md:gap-12 px-8 md:px-20 py-8 md:py-12 relative rounded-[5px] bg-[linear-gradient(180deg,rgba(255,255,255,0.08)_0%,rgba(255,255,255,0)_100%)] border-none w-full">
                <img class="relative" alt="Frame"
                    src="https://c.animaapp.com/mhc1z55wRcb3W7/img/frame-1000004528.svg" />
                <div class="flex flex-col items-start gap-6 md:gap-10 relative w-full mt-8 md:mt-12">
                    <Transition name="fade" mode="out-in">
                        <blockquote :key="currentSlide"
                            class="relative font-medium text-white text-2xl md:text-[32px] font-display">
                            {{ testimonials[currentSlide].quote }}
                        </blockquote>
                    </Transition>
                    <div class="flex items-center justify-between relative w-full">
                        <Transition name="fade" mode="out-in">
                            <p :key="currentSlide"
                                class="relative w-fit font-semibold text-[#ffffffb2] text-lg md:text-xl whitespace-nowrap">
                                {{ testimonials[currentSlide].attribution }}
                            </p>
                        </Transition>
                        <div class="inline-flex items-center gap-1.5 relative">
                            <div v-for="(slide, index) in testimonialSlides" :key="index"
                                class="relative w-2.5 h-2.5 rounded-[5px] bg-white transition-all duration-300 ease-in-out transform"
                                :class="slide.isActive ? 'bg-[#cca0ca] scale-110' : 'opacity-50 scale-100'" />
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Join our alpha programme -->
        <div id="contact"
            class="flex flex-col items-center gap-10 px-[200px] py-[100px] relative w-full translate-y-[-1rem] animate-fade-in"
            style="--animation-delay:1200ms">
            <div
                class="flex flex-col w-full max-w-[670px] items-center gap-8 px-12 py-10 relative bg-[#ffffff14] rounded-[5px] border-none before:content-[''] before:absolute before:inset-0 before:p-0.5 before:rounded-[5px] before:[background:linear-gradient(221deg,rgba(255,255,255,1)_0%,rgba(255,255,255,0)_100%)] before:[-webkit-mask:linear-gradient(#fff_0_0)_content-box,linear-gradient(#fff_0_0)] before:[-webkit-mask-composite:xor] before:[mask-composite:exclude] before:z-[1] before:pointer-events-none">
                <div class="p-0 w-full">
                    <div class="flex flex-col items-center gap-3 relative w-full">
                        <h2
                            class="text-[40px] relative w-fit font-semibold text-white text-center tracking-[0] leading-[normal] whitespace-nowrap font-display">
                            Join our alpha programme
                        </h2>
                        <p
                            class="relative max-w-[476px] font-medium text-[#ffffffb2] text-base text-center tracking-[0] leading-[normal]">
                            We are inviting people to join us as early alpha users to help
                            test and shape the future of Diverz
                        </p>
                    </div>
                    <form class="flex flex-col items-center gap-10 relative w-full mt-8">
                        <div class="flex flex-col items-start gap-8 relative w-full">
                            <div class="flex flex-col items-start gap-2 relative w-full">
                                <label
                                    class="relative font-semibold text-white text-sm tracking-[0] leading-5 font-display">
                                    Full name
                                </label>
                                <input type="text" placeholder="Enter your full name"
                                    class="flex items-center gap-2.5 px-3 py-2.5 relative w-full rounded-lg border-[1.5px] border-solid border-[#ffffff4c] bg-transparent font-medium text-[#ffffffa6] text-base placeholder:text-[#ffffffa6] font-display" />
                            </div>
                            <div class="flex flex-col items-start gap-2 relative w-full">
                                <label
                                    class="relative font-semibold text-white text-sm tracking-[0] leading-5 font-display">
                                    Email
                                </label>
                                <input type="email" placeholder="Enter your email address"
                                    class="flex items-center gap-2.5 px-3 py-2.5 relative w-full rounded-lg border-[1.5px] border-solid border-[#ffffff4c] bg-transparent font-medium text-[#ffffffa6] text-base placeholder:text-[#ffffffa6] font-display" />
                            </div>
                            <div class="flex flex-col items-start gap-2 relative w-full">
                                <label
                                    class="relative font-semibold text-white text-sm tracking-[0] leading-5 font-display">
                                    Role
                                </label>
                                <div
                                    class="flex items-center gap-2.5 px-3 py-2.5 relative w-full rounded-lg border-[1.5px] border-solid border-[#ffffff4c]">
                                    <input type="text" placeholder="Enter your role"
                                        class="relative flex-1 border-none bg-transparent p-0 font-medium text-[#ffffffa6] text-base placeholder:text-[#ffffffa6] focus-visible:ring-0 focus-visible:ring-offset-0 font-display" />
                                    <img class="relative w-[21px] h-[21px]" alt="Arrow down"
                                        src="https://c.animaapp.com/mhc1z55wRcb3W7/img/arrow-down.svg" />
                                </div>
                            </div>
                        </div>
                        <button
                            class="flex w-[161px] h-auto items-center justify-center gap-2.5 px-6 py-3 relative bg-[#574fa1] rounded-[10px] hover:bg-[#574fa1]/90 transition-colors">
                            <span
                                class="relative w-fit font-medium text-white text-base text-center tracking-[0] leading-[normal] whitespace-nowrap font-display">
                                Submit
                            </span>
                        </button>
                    </form>
                </div>
            </div>
        </div>
        <!-- FAQ -->
        <div class="flex flex-col max-w-[772px] items-center gap-8 md:gap-14 relative translate-y-[-1rem] animate-fade-in w-full"
            style="--animation-delay:1400ms">
            <div class="flex flex-col items-center gap-3 relative w-full">
                <h2
                    class="relative max-w-[546px] bg-gradient-to-r from-[#574fa1] to-[#cca0ca] bg-clip-text text-transparent font-semibold text-3xl sm:text-4xl lg:text-[40px] text-center font-display">
                    Frequently asked questions
                </h2>
                <p class="relative font-medium text-[#ffffffb2] text-sm sm:text-base text-center">
                    Find quick answers to common questions about Diverz
                </p>
            </div>

            <div class="flex flex-col items-center gap-6 md:gap-10 relative w-full">
                <div class="flex flex-col w-full relative">
                    <div class="flex flex-wrap items-center gap-2 md:gap-4 relative w-full bg-transparent h-auto p-0">
                        <button v-for="(category, index) in faqs" :key="index" @click="selectCategory(index)"
                            class="flex items-center justify-center gap-2.5 px-4 py-3 flex-1 rounded-[5px] transition-colors min-w-[100px]"
                            :class="selectedCategoryIndex === index ? 'bg-white text-black' : 'bg-[#ffffff1a] text-white'">
                            <span class="font-medium text-sm md:text-base text-center whitespace-nowrap">
                                {{ category.label }}
                            </span>
                        </button>
                    </div>
                </div>

                <div class="flex flex-col items-start gap-6 md:gap-[37px] relative w-full">
                    <div v-for="(item, index) in faqItems" :key="index"
                        class="flex flex-col w-full items-start pt-2.5 pb-6 px-2.5 relative"
                        :class="index < faqItems.length - 1 ? 'border-b-[1.5px] border-[#ffffff66]' : ''">
                        <button class="flex w-full items-start justify-between hover:no-underline pr-4"
                            @click="toggleFaq(index)">
                            <span
                                class="relative w-fit font-medium text-white text-sm md:text-base text-left leading-normal">
                                {{ item.question }}
                            </span>
                            <img src="https://c.animaapp.com/mhc1z55wRcb3W7/img/group-7.png"
                                class="relative w-[18px] h-[18px] flex-shrink-0 transition-transform duration-300"
                                :class="item.isExpanded ? 'rotate-180' : 'rotate-0'" alt="Toggle" />
                        </button>
                        <transition name="fade">
                            <div v-if="item.answer && item.isExpanded"
                                class="relative max-w-[472px] font-medium text-white text-sm md:text-base leading-normal pt-2 mt-2">
                                {{ item.answer }}
                            </div>
                        </transition>
                    </div>
                </div>
            </div>
        </div>

        <div
            class="absolute top-[4590px] left-[50%] -translate-x-1/2 w-[541px] h-[621px] bg-[#574fa1] rounded-[260.5px] blur-[355px] pointer-events-none md:left-[690px] md:translate-x-0" />
   
   </section>
</template>


<script setup>
import { ref } from 'vue'
import ProductivityFeatures from './ProductivityFeatures.vue'

const stepsData = ref([
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
        description: "Tell Diverz what you want: run a check, make a config change, or debug an issue. Plain language, no syntax wrangling.",
        isExpanded: false,
    },
    {
        number: "3",
        title: "Approve or refine",
        description: "Tell Diverz what you want: run a check, make a config change, or debug an issue. Plain language, no syntax wrangling.",
        isExpanded: false,
    },
    {
        number: "4",
        title: "Execute and report",
        description: "Tell Diverz what you want: run a check, make a config change, or debug an issue. Plain language, no syntax wrangling.",
        isExpanded: false,
    },
])

const toggleExpansion = (index) => {
    stepsData.value.forEach((step, i) => {
        step.isExpanded = i === index
    })
}


const upcomingFeatures = [
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
]

const engineerFeatures = [
    {
        icon: "https://c.animaapp.com/mhc1z55wRcb3W7/img/group-10.png",
        title: "Context-aware",
        subtitle: "Tag sessions; it correlates",
        description:
            "See the whole picture across panes without copy-paste or guesswork",
    },
    {
        icon: "https://c.animaapp.com/mhc1z55wRcb3W7/img/group-11.png",
        title: "Intent-driven",
        subtitle: "Focus on the what; it plans how",
        description:
            "Diverz adapts to your role/stack to help you accomplish your tasks",
    },
    {
        icon: "https://c.animaapp.com/mhc1z55wRcb3W7/img/group-10-1.png",
        title: "Connection hub",
        subtitle: "SSH, APIs in one workspace",
        description: "All your remote protocols in a single workspace",
    },
    {
        icon: "https://c.animaapp.com/mhc1z55wRcb3W7/img/group-10-2.png",
        title: "Safety built-in",
        subtitle: "Complete control of your agents",
        description:
            "The flexibility to approve, refine, or cancel any agent tasks",
    },
    {
        icon: "https://c.animaapp.com/mhc1z55wRcb3W7/img/group-10-3.png",
        title: "Universal CLI coverage",
        subtitle: "OS & Vendor neutral",
        description:
            "Execute commands seamlessly and reliably across vendors, OS or platforms",
    },
    {
        icon: "https://c.animaapp.com/mhc1z55wRcb3W7/img/group-10-4.png",
        title: "Auditable",
        subtitle: "Evidence, automatically",
        description: "All your sessions logged for security and compliance",
    },
]

const testimonials = [
    {
        quote: "Diverz brings the structure, speed, and context of a developer IDE to real-world network operations",
        attribution: "Senior Network Engineer, Fintech"
    },
    {
        quote: "Transformed our NetOps workflow overnight with seamless automation and context-aware tools.",
        attribution: "DevOps Lead, Telecom"
    },
    {
        quote: "The AI assistant is a game-changer for config management and troubleshooting.",
        attribution: "Network Architect, Enterprise"
    },
    {
        quote: "Seamless integration with our existing tools—finally, developer-grade speed in NetOps.",
        attribution: "IT Director, Cloud Provider"
    },
    {
        quote: "Automation that's safe, explainable, and vendor-correct—revolutionizing our operations.",
        attribution: "Security Engineer, Bank"
    }
]

const currentSlide = ref(0)

const testimonialSlides = computed(() =>
    testimonials.map((slide, index) => ({
        ...slide,
        isActive: index === currentSlide.value
    }))
)

const faqs = [
    {
        label: "Pricing",
        faqItems: [
            {
                question: "What is Diverz?",
                answer:
                    "Lorem ipsum dolor sit amet consectetur. Sit neque ullamcorper eget orci suscipit et a nullam ultrices",
                isExpanded: true,
            },
            {
                question: "Who can use Diverz?",
                answer: "",
                isExpanded: false,
            },
            {
                question:
                    "How is Diverz different from tools like GNS3, EVE-NG, or legacy CLIs?",
                answer: "",
                isExpanded: false,
            },
            {
                question: "Which vendors and devices does Diverz support?",
                answer: "",
                isExpanded: false,
            },
            {
                question: "Can Diverz generate and translate configs automatically?",
                answer: "",
                isExpanded: false,
            },
            {
                question: "How does Diverz handle troubleshooting across multiple devices?",
                answer: "",
                isExpanded: false,
            },
            {
                question: "Is Diverz available as both cloud and on-prem deployment?",
                answer: "",
                isExpanded: false,
            },
            {
                question: "Is Diverz free to use, and what's included in the free plan?",
                answer: "",
                isExpanded: false,
            },
        ]
    },
    {
        label: "Category 1", faqItems: [
            {
                question: "What is Diverz?",
                answer:
                    "category 1 Lorem ipsum dolor sit amet consectetur. Sit neque ullamcorper eget orci suscipit et a nullam ultrices",
                isExpanded: true,
            },
            {
                question: "Who can use Diverz?",
                answer: "",
                isExpanded: false,
            },
            {
                question:
                    "How is Diverz different from tools like GNS3, EVE-NG, or legacy CLIs?",
                answer: "",
                isExpanded: false,
            },
            {
                question: "Which vendors and devices does Diverz support?",
                answer: "",
                isExpanded: false,
            },
            {
                question: "Can Diverz generate and translate configs automatically?",
                answer: "",
                isExpanded: false,
            },
            {
                question: "How does Diverz handle troubleshooting across multiple devices?",
                answer: "",
                isExpanded: false,
            },
            {
                question: "Is Diverz available as both cloud and on-prem deployment?",
                answer: "",
                isExpanded: false,
            },
            {
                question: "Is Diverz free to use, and what's included in the free plan?",
                answer: "",
                isExpanded: false,
            },
        ]
    },
    {
        label: "Category 2", faqItems: [
            {
                question: "What is Diverz?",
                answer:
                    "Lorem ipsum dolor sit amet consectetur. Sit neque ullamcorper eget orci suscipit et a nullam ultrices",
                isExpanded: true,
            },
            {
                question: "Who can use Diverz?",
                answer: "",
                isExpanded: false,
            },
            {
                question:
                    "How is Diverz different from tools like GNS3, EVE-NG, or legacy CLIs?",
                answer: "",
                isExpanded: false,
            },
            {
                question: "Which vendors and devices does Diverz support?",
                answer: "",
                isExpanded: false,
            },
            {
                question: "Can Diverz generate and translate configs automatically?",
                answer: "",
                isExpanded: false,
            },
            {
                question: "How does Diverz handle troubleshooting across multiple devices?",
                answer: "",
                isExpanded: false,
            },
            {
                question: "Is Diverz available as both cloud and on-prem deployment?",
                answer: "",
                isExpanded: false,
            },
            {
                question: "Is Diverz free to use, and what's included in the free plan?",
                answer: "",
                isExpanded: false,
            },
        ]
    }
]

const selectedCategoryIndex = ref(0)
const faqItems = ref([...faqs[selectedCategoryIndex.value].faqItems])

const selectCategory = (index) => {
    selectedCategoryIndex.value = index
    faqItems.value = faqs[index].faqItems.map((item, i) => ({
        ...item,
        isExpanded: i === 0,
    }))
}

const toggleFaq = (index) => {
    faqItems.value = faqItems.value.map((item, i) => ({
        ...item,
        isExpanded: i === index ? !item.isExpanded : false,
    }))
}

let interval = null

onMounted(() => {
    interval = setInterval(() => {
        currentSlide.value = (currentSlide.value + 1) % testimonials.length
    }, 5000)
})

onUnmounted(() => {
    clearInterval(interval)
})
</script>

<style scoped>
.animate-fade-in {
    animation: fadeIn 0.8s ease forwards;
}

@keyframes fadeIn {
    from {
        opacity: 0;
        transform: translateY(-1rem);
    }

    to {
        opacity: 1;
        transform: translateY(0);
    }
}

.font-display {
    font-family: 'Inter Display', sans-serif;
}
</style>