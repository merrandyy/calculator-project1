<script lang="ts">
    import SquareRoot from "$lib/icons/squareRoot.svelte";
    import DivisionReminder from "$lib/icons/divisionReminder.svelte";
    import Minus from "$lib/icons/minus.svelte";
    import Division from "$lib/icons/division.svelte";
    import Addition from "$lib/icons/addition.svelte";
    import Multiply from "$lib/icons/multiply.svelte";
    import Backspace from "$lib/icons/backspace.svelte";
    import {onMount} from "svelte";

    function addToEquation (value:string) {
        equation +=value;
    }

    function backspace (){
        switch (equation.substring(equation.length-3, equation.length)) {
            case ' * ':
            case ' = ':
            case ' / ':
            case ' - ':
                equation = equation.substring(0, equation.length-3);
                break;
            default:
                equation = equation.substring(0, equation.length-1);
        }
    }

    function clear (){
        equation="";
    }
    

    function solve (){
        try {
            let answer=eval(equation);
            if(answer==undefined) throw SyntaxError;

            equation= answer;
    } catch (error) { 
        let output = document.getElementById('output');
        output?.classList.add('bg-red-500');
        setTimeout(() => {
            output?.classList.remove('bg-red-500');
        },500);
    }}

    let equation: string="";

    function onKeyDown(e:KeyboardEvent){
            new Audio('/click.mp3').play();
        let button =document.getElementById(e.key)
        button?.click();
        button?.focus();
        setTimeout(() => {
            //@ts-ignore
            document.activeElement?.blur()},100)
    }

    onMount(() => {
        let allButtons = document.getElementsByTagName('button');
        for (let i = 0; i < allButtons.length; i++) {
            allButtons[i].addEventListener('click', () => {
                new Audio('/click.wav').play();
            });
        }
    });

    

</script>


<svelte:head>
    <title> calculator</title>
</svelte:head>

<svelte:window on:keydown|preventDefault={onKeyDown}/>

<div class="  bg-white w-[20rem] rounded-3xl grid grid-cols-4 gap-3 p-5 flex justify-center font-bold text-xl shadow-2xl"> 
    <div id="output" class="bg-blue-500 overflow-auto rounded-full col-span-4 h-[4rem] flex items-center px-4 mb-4 text-white transition-all"> {equation} </div>
    <button on:click={() => addToEquation(" /100")} class="bg-[#f3f6fc]"> <DivisionReminder/> </button>
    <button on:click={backspace} class= "bg-[#f3f6fc] "> <Backspace /> </button>
    
    <button on:click={clear} class="bg-[#1f2b54] text-white col-span-2 w-full"> C </button>
    <button id="7" on:click={() => addToEquation("7")}> 7 </button>
    <button id="8" on:click={() => addToEquation("8")}> 8 </button>
    <button id="9" on:click={() => addToEquation("9")}> 9 </button>
    <button id="-" on:click={() => addToEquation(" - ")} class="bg-[#fd3f59] text-white "> <Minus/> </button>
    <button id="4" on:click={() => addToEquation("4")}> 4 </button>
    <button id="5" on:click={() => addToEquation("5")}> 5 </button>
    <button id="6" on:click={() => addToEquation("6")}> 6 </button>
    <button id="/" on:click={() => addToEquation(" / ")} class="bg-[#2285fd] text-white"> <Division/> </button>
    <button id="1" on:click={() => addToEquation("1")}> 1 </button>
    <button id="2" on:click={() => addToEquation("2")}> 2 </button>
    <button id="3" on:click={() => addToEquation("3")}> 3 </button>
    <button id="*" on:click={() => addToEquation(" * ")} class="bg-[#f9c80e] text-white"> <Multiply/> </button>
    <button id="." on:click={() => addToEquation(".")}> . </button>
    <button id="0" on:click={() => addToEquation("0")}> 0 </button>
    <button id="=" on:click={solve}> = </button>
    <button id="+" on:click={() => addToEquation(" + ")} class="bg-[#63dc74] text-white"> <Addition/> </button>
</div>



