<script>
    import SquareRoot from "$lib/icons/squareRoot.svelte";
    import DivisionReminder from "$lib/icons/DivisionReminder.svelte";
    import Minus from "$lib/icons/Minus.svelte";
    import Division from "$lib/icons/Division.svelte";
    import Addition from "$lib/icons/Addition.svelte";
    import Multiply from "$lib/icons/Multiply.svelte";
</script>

<svelte:head>
    <title> calculator</title>
</svelte:head>

<div class="  bg-white w-[20rem] rounded-3xl grid grid-cols-4 gap-3 p-5 flex justify-center font-bold text-xl shadow-2xl"> 
    <div class="bg-blue-500 rounded-full col-span-4 h-[4rem] flex items-center px-4 mb-4 text-white  "> 122</div>
    <button class="bg-[#f3f6fc]"> <DivisionReminder/> </button>
    <button class="bg-[#f3f6fc]"> <SquareRoot /> </button>
    <button class="bg-[#f3f6fc]"> CE </button>
    <button class="bg-[#1f2b54] text-white"> C </button>
    <button> 7 </button>
    <button> 8 </button>
    <button> 9 </button>
    <button class="bg-[#fd3f59] text-white "> <Minus/> </button>
    <button> 4 </button>
    <button> 5 </button>
    <button> 6 </button>
    <button class="bg-[#2285fd] text-white"> <Division/> </button>
    <button> 1 </button>
    <button> 2 </button>
    <button> 3 </button>
    <!-- multiply icon -->
    <button class="bg-[#f9c80e] text-white"> <Multiply/> </button>
    <button> . </button>
    <button> 0 </button>
    <button> = </button>
    <button class="bg-[#63dc74] text-white"> <Addition/> </button>
</div>



