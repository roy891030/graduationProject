<template>

    <b-container>
        <b-row align-v="center">
            <div v-show="select==='a'">
                <svg-l v-b-tooltip.hover.v-warning.html="pKinder" class="person"></svg-l>
                <svg-flower v-b-tooltip.hover.v-success.html="bKinder" class="right"></svg-flower>
                <svg-flower v-b-tooltip.hover.v-success.html="bKinder" class="right-1"></svg-flower>
                <svg-flag v-b-tooltip.hover.v-primary.html="fKinder" class="left"></svg-flag>
            </div>

            <div v-show="select === 'b'">
                <svg-l v-b-tooltip.hover.v-warning.html="pScooter" class="person"></svg-l>
                <svg-bag v-b-tooltip.hover.v-success.html="bScooter" class="right"></svg-bag>
                <svg-flag v-b-tooltip.hover.v-primary.html="fScooter" class="left"></svg-flag>
            </div>

            <div v-show="select === 'c'">
                <svg-l v-b-tooltip.hover.v-warning.html="pGym" class="person"></svg-l>
                <svg-bag v-b-tooltip.hover.v-success.html="bGym" class="right" width="80%"></svg-bag>
                <svg-flag v-b-tooltip.hover.v-primary.html="fGym" class="left"></svg-flag>
            </div>

        </b-row>


    </b-container>

</template>

<script>
import * as d3 from 'd3';



export default {
    props: ['jobType','select','range' ],

    data(){
        return{
            bNum:"2",
            pKinder: { title: 'person <em>幼兒園</em>' },
            bKinder: { title: 'flower <em>幼兒園</em>' },
            fKinder: { title: 'flag <em>幼兒園</em>' },
            pScooter: { title: 'person <em>機車行</em>' },
            bScooter: { title: 'bag <em>機車行</em>' },
            fScooter: { title: 'flag <em>機車行</em>' },
            pGym: { title: 'person <em>健身房</em>' },
            bGym: { title: 'bag <em>健身房</em>' },
            fGym: { title: 'flag <em>健身房</em>' },
            roy: "cool",
        }

    },
    methods:{
        }
    }

function getRandom(min, max) {
    return Math.floor(Math.random() * (max - min + 1)) + min;
};

customElements.define("svg-bag", class extends HTMLElement {
    connectedCallback() {
        setTimeout(() => { // make sure inner DOM is parsed
            this.innerHTML = `<svg  width="55" version="1.1" id="eS1ABtXM7fO1" shape-rendering="geometricPrecision" text-rendering="geometricPrecision"
	 xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" viewBox="0 0 81.1 124.6"
	 style="enable-background:new 0 0 81.1 124.6;" xml:space="preserve">
<style type="text/css">
	.st0{fill:#FFFFFF;stroke:#000000;stroke-width:4;}
	.st2{display:inline;fill:#1C00C9;stroke:#000000;stroke-width:4;}
	.st3{display:inline;fill:#FFD700;stroke:#000000;stroke-width:4;}
	.st4{fill:#AF0AFF;stroke:#000000;stroke-width:4;}
	.st5{fill:#F0FF35;stroke:#000000;stroke-width:4;}
	.st6{fill:#391FFF;stroke:#000000;stroke-width:4;}
	.st7{fill:none;stroke:#000000;stroke-width:4;stroke-linecap:round;stroke-linejoin:round;}
</style>
<path  v-show="bNum===1" class="st0" d="M7.8,31.5h65.5c3.2,0,5.8,2.2,5.8,4.9v81.3c0,2.7-2.6,4.9-5.8,4.9H7.8c-3.2,0-5.8-2.2-5.8-4.9V36.4
	C2,33.7,4.6,31.5,7.8,31.5L7.8,31.5z"/>
<g v-show="bNum===2" style="display: contents;"  class="st1">
	<path class="st2" d="M7.8,78.2h65.5c3.2,0,5.8,1.1,5.8,2.4v39.6c0,1.3-2.6,2.4-5.8,2.4H7.8c-3.2,0-5.8-1.1-5.8-2.4V80.6
		C2,79.3,4.6,78.2,7.8,78.2L7.8,78.2z"/>
	<path class="st3" d="M7.8,32.7h65.5c3.2,0,5.8,1.1,5.8,2.4v39.6c0,1.3-2.6,2.4-5.8,2.4H7.8C4.6,77.1,2,76,2,74.7V35.1
		C2,33.8,4.6,32.7,7.8,32.7L7.8,32.7z"/>
</g>
<g v-show="bNum===3" >
	<path class="st4" d="M7.8,31.5h65.5c3.2,0,5.8,0.7,5.8,1.6V60c0,0.9-2.6,1.6-5.8,1.6H7.8C4.6,61.6,2,60.8,2,60V33.1
		C2,32.2,4.6,31.5,7.8,31.5L7.8,31.5z"/>
	<path class="st5" d="M7.8,62.3h65.5c3.2,0,5.8,0.7,5.8,1.6v26.2c0,0.9-2.6,1.6-5.8,1.6H7.8C4.6,91.7,2,91,2,90.1V63.9
		C2,63,4.6,62.3,7.8,62.3L7.8,62.3z"/>
	<path class="st6" d="M7.8,93.2h65.5c3.2,0,5.8,0.7,5.8,1.6V121c0,0.9-2.6,1.6-5.8,1.6H7.8c-3.2,0-5.8-0.7-5.8-1.6V94.8
		C2,93.9,4.6,93.2,7.8,93.2L7.8,93.2z"/>
</g>
<path class="st7" d="M21.2,31.7c0,0,9.8-30.2,18.5-29.7s19.7,29.7,19.7,29.7"/>
</svg>`;
        });
    }
})


customElements.define("svg-flag", class extends HTMLElement {
    connectedCallback() {
        setTimeout(() => { // make sure inner DOM is parsed
            this.innerHTML = `<svg  width="66" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" id="e4fqSwYBZ6x1"
    shape-rendering="geometricPrecision" text-rendering="geometricPrecision" viewBox="0 27.13 96 182.6">
    <path d="M1,28.73c16.2,21.8,61.7-4.8,94,0v57c-26.9-18-76.2,18-94,0v-57Z" fill="#f0f0f2" stroke="#000"
        stroke-width="2" />
    <line x1="95" y1="28.13" x2="95" y2="208.73" fill="none" stroke="#000" stroke-width="2" />
</svg>`;
        });
    }
})


customElements.define("svg-flower", class extends HTMLElement {
    connectedCallback() {
        setTimeout(() => { // make sure inner DOM is parsed
            this.innerHTML = `<svg width="40"  xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" id="enJBSzQbpXc1"
    shape-rendering="geometricPrecision" text-rendering="geometricPrecision" viewBox="241.02 104.63 52.33 88.01">
    <line x1="7.002587" y1="-45.510943" x2="0.299341" y2="10.200341" transform="translate(260.154306 180.940943)"
        fill="none" stroke="#010101" stroke-width="3" />
    <ellipse rx="6.322493" ry="12.332168" transform="translate(267.189223 142.283547)" fill="#fe7d60" stroke="#000"
        stroke-width="3" />
    <ellipse rx="6.322493" ry="12.332168" transform="translate(267.189223 118.46233)" fill="#fe7d60" stroke="#000"
        stroke-width="3" />
    <ellipse rx="6.322493" ry="12.332168" transform="matrix(.707107 0.707107-.707107 0.707107 278.662722 121.839163)"
        fill="#fe7d60" stroke="#000" stroke-width="3" />
    <ellipse rx="6.322493" ry="12.332168" transform="matrix(.707107 0.707107-.707107 0.707107 258.6 139.500678)"
        fill="#fe7d60" stroke="#000" stroke-width="3" />
    <ellipse rx="6.322493" ry="12.332168" transform="matrix(-.707107 0.707107-.707107-.707107 276.996107 141.424878)"
        fill="#fe7d60" stroke="#000" stroke-width="3" />
    <ellipse rx="6.322493" ry="12.332168" transform="matrix(-.707107 0.707107-.707107-.707107 256.751726 121.839163)"
        fill="#fe7d60" stroke="#000" stroke-width="3" />
    <ellipse rx="6.322493" ry="12.332168" transform="matrix(0-1 1 0 279.521391 130.794498)" fill="#fe7d60" stroke="#000"
        stroke-width="3" />
    <ellipse rx="6.322493" ry="12.332168" transform="matrix(0 1-1 0 254.857055 129.951379)" fill="#fe7d60" stroke="#000"
        stroke-width="3" />
    <ellipse rx="12.364498" ry="12.364498" transform="translate(267.156893 130.794498)" fill="#f2e423" stroke="#000"
        stroke-width="3" />
</svg>`;
        });
    }
})

customElements.define("svg-l", class extends HTMLElement {
    connectedCallback() {
        setTimeout(() => { // make sure inner DOM is parsed
            //max r=70
            //min r= -33

            let r = getRandom(-20, 70);
            let x = 205.1 - r;
            let y = 23.3 + r;
            this.innerHTML = `<svg width="130" version="1.1" id="enPHxEQtrXM1" text-rendering="geometricPrecision" shape-rendering="geometricPrecision"
    xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
    viewBox="0 0 193.4 303" style="enable-background:new 0 0 193.4 303;" xml:space="preserve">
    <style type="text/css">
        .st0p {
            fill: #E8BA00;
            stroke: #0F0707;
            stroke-width: 5;
        }

        .st1p {
            fill: #FFD767;
            stroke: #230707;
            stroke-width: 3.66;
            stroke-miterlimit: 4.58;
        }

        .st2p {
            fill: #153832;
            stroke: #FFFFFF;
        }

        .st3p {
            fill: #F0F0F2;
            stroke: #070404;
            stroke-width: 3;
        }

        .st4p {
            fill: #FFD767;
            stroke: #000000;
            stroke-width: 4;
            stroke-linecap: round;
            stroke-linejoin: round;
        }

        .st5p {
            fill: #FFFFFF;
            stroke: #000000;
            stroke-width: 4;
            stroke-linecap: round;
            stroke-linejoin: round;
        }

        .st6p {
            fill: #FFD767;
            stroke: #000000;
            stroke-width: 3;
        }

        .st7p {
            fill: #FFD767;
            stroke: #000000;
            stroke-width: 3;
            stroke-linecap: round;
            stroke-linejoin: round;
        }

        .st8p {
            fill: none;
            stroke: #CC2A09;
            stroke-width: 3;
            stroke-linecap: round;
            stroke-linejoin: round;
        }

        .st9p {
            fill: #94BEFF;
            stroke: #000000;
            stroke-width: 4;
        }
    </style>
    <ellipse class="st0p" cx="88.2" cy="256.4" rx="85.7" ry="44.1" />
    <circle class="st1p" cx="86.3" cy="76.8" r="48.6" />
    <circle class="st2p" cx="103.2" cy="83.3" r="6.4" />
    <circle class="st2p" cx="71.4" cy="83.3" r="6.4" />
    <path class="st3p" d="M33.4,56.3c25.4,22.4,86,17.5,105.4-5C70.7-25.1,65.4,5,61.8,20.8S31,47.7,33.4,56.3z" />
    <path class="st4p" d="M73.1,230.5c18.6-8.5,10,36-0.6,36.3C53.3,269.4,54,248.7,73.1,230.5L73.1,230.5z" />
    <path class="st4p" d="M95.7,231.7c20.9-8.2,17,35.2,5,35.5C78.5,265.2,99.4,235.3,95.7,231.7L95.7,231.7z" />
    <path class="st5p" d="M40.3,135.7l0.3,93.3c0,6.5,5.3,11.7,11.8,11.7l0,0h66.3c6.4,0,11.7-5.2,11.8-11.6l0.9-94.1" />
    <path class="st6p" d="M39.3,167.2c-9.5,11.8-28-0.5-30.3-22.7C2,139,13.4,124.4,39.3,167.2z" />
    <path class="st7p" d="M132.6,166.4c25.3,32.3,75.1,11.9,54.4-0.8C170,172.4,135.2,156.8,132.6,166.4L132.6,166.4z" />
    <path class="st8p" d="M67.3,99.5c6.2,17.3,31.4,17.9,38,0" />
    <path class="st9p" d="M40.3,${x}l0.3,${y}c0,6.5,5.3,11.7,11.8,11.7l0,0h66.3c6.4,0,11.7-5.2,11.8-11.6l0.9-${y}" />
</svg>`;
        });
    }
})

</script>

<style scoped>





@keyframes example {
    0% {
    top: 140px;
    }
    50% {
    top: 110px;
    transform: rotate(-10deg)
    }
    100% {
    top: 140px;
    }
}



@keyframes example2 {
    0% {
    top: 170px;
    left: 180px;

    }

    50% {
    top: 150px;
    left: 190px;
    transform: rotate(45deg)

    }

    100% {
    top: 170px;
    left: 180px;
    }
}

svg.liquid{
    position:absolute;

}

.left{
    position: absolute;
    width: 130px;
    height: 130px;
            left: 10px;
    animation-name: example;
    
    animation-duration: 2s;
    animation-iteration-count: 1000000;
}



.person{
    position: absolute;
    top:140px;
    left:100px;
    width:30%;
}


.right{
position: absolute;
    animation-name: example2;
    animation-duration: 2s;
    animation-iteration-count: 1000000;
    width: 80px;
    height: 80px;
}
.right-1 {
    position: absolute;
    animation-name: example2;
    animation-duration: 2s;
    animation-iteration-count: 1000000;
    width: 80px;
    height: 80px;
}

</style>