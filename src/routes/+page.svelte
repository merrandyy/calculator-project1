<script lang="ts">
    import SquareRoot from "$lib/icons/squareRoot.svelte";
    import DivisionReminder from "$lib/icons/divisionReminder.svelte";
    import Minus from "$lib/icons/minus.svelte";
    import Division from "$lib/icons/Division.svelte";
    import Addition from "$lib/icons/Addition.svelte";
    import Multiply from "$lib/icons/Multiply.svelte";
    import Backspace from "$lib/icons/backspace.svelte";

    function addToEquation (value:string) {
        equation +=value;
    }

    function backspace (){
        equation=equation.substring(0,equation.length-1);
    }

    function clear (){
        equation="";
    }

    function solve (){
        equation= eval(equation);
    }
    
    let equation: string="";

</script>

<svelte:head>
    <title> calculator</title>
</svelte:head>

<div class="  bg-white w-[20rem] rounded-3xl grid grid-cols-4 gap-3 p-5 flex justify-center font-bold text-xl shadow-2xl"> 
    <div class="bg-blue-500 rounded-full col-span-4 h-[4rem] flex items-center px-4 mb-4 text-white  "> {equation} </div>
    <button on:click={() => addToEquation(" /100")} class="bg-[#f3f6fc]"> <DivisionReminder/> </button>
    <button on:click={backspace} class= "bg-[#f3f6fc] "> <Backspace /> </button>
    
    <button on:click={clear} class="bg-[#1f2b54] text-white col-span-2 w-full"> C </button>
    <button on:click={() => addToEquation("7")}> 7 </button>
    <button on:click={() => addToEquation("8")}> 8 </button>
    <button on:click={() => addToEquation("9")}> 9 </button>
    <button on:click={() => addToEquation(" - ")} class="bg-[#fd3f59] text-white "> <Minus/> </button>
    <button on:click={() => addToEquation("4")}> 4 </button>
    <button on:click={() => addToEquation("5")}> 5 </button>
    <button on:click={() => addToEquation("6")}> 6 </button>
    <button on:click={() => addToEquation(" / ")} class="bg-[#2285fd] text-white"> <Division/> </button>
    <button on:click={() => addToEquation("1")}> 1 </button>
    <button on:click={() => addToEquation("2")}> 2 </button>
    <button on:click={() => addToEquation("3")}> 3 </button>
    <!-- multiply icon -->
    <button on:click={() => addToEquation(" * ")} class="bg-[#f9c80e] text-white"> <Multiply/> </button>
    <button on:click={() => addToEquation(".")}> . </button>
    <button on:click={() => addToEquation("0")}> 0 </button>
    <button on:click={solve}> = </button>
    <button on:click={() => addToEquation(" + ")} class="bg-[#63dc74] text-white"> <Addition/> </button>
</div>



