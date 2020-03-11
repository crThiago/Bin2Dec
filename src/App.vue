<template>
    <div id="app" class="content">
        <div class="box">
            <h1>Bin2Dec</h1>
            <input type="text"  v-model="bin" placeholder="Binary">
            <button :disabled="!validateBin" :class="!validateBin ? 'error' : 'success'" @click="convertBin2Dec()">Convert</button>
            <p v-show="dec" class="result">Result: {{ dec }}</p>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            bin: "",
            dec: ""
        }
    },
    methods: {
        convertBin2Dec() {

            const splitBin = this.bin.split('').reverse();
            
            this.dec = 0
            splitBin.forEach((element, index) => {
                this.dec += element * Math.pow(2, index)
            })
            return this.dec
        }
    },
    computed: {
        validateBin() {
            return /^[01]+$/.test(this.bin)
        }
    }
}
</script>

<style>
.content {
    display: flex;
    height: 100vh;
    align-items: center;
    justify-content: center;
}
.box {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-between;

    max-width: 300px;
    min-width: 290px;
    padding: 30px;
    height: 300px;
    border-radius: 6px;
    border: 2px solid #3e3e3e;
}
h1 {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    font-size: 3em;
    color: #3e3e3e;
}
input {
    height: 20px;
    border: none;
    border-bottom: #3e3e3e solid 1px;
    font-size: 1.4em;
    padding: 10px;
    outline: none;
}
button {
    margin: top;
    background: transparent;
    border: 1px solid #3e3e3e;
    border-radius: 6px;
    font-size: 1.3em;
    font-weight: 700;
    padding: 15px 30px;
}

button.error {
    border: 1px solid #EA4335;
    color: #EA4335;
    cursor: not-allowed;
}

button.success {
    border: 1px solid #4285F4;
    color: #4285F4;
    cursor: pointer;
}

.result {
    font-size: 1.4em;
    font-weight: 800;
}

</style>