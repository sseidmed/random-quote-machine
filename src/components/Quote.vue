<template>
    <div class="card" :style="{ 'background-color': color}">
        
        
            <p>{{quote}}</p>
            <p v-show="author" class="author">-{{ author }}</p>
        
        <button @click="getQuote">Get a new quote</button>
    </div>

</template>

<script>
    export default {
        name: 'Quote',
        data() {
            return {
                quote: '',
                author: '',
                colors: [
                    '#297afb',
                    '#2898fb',
                    '#01d8fd',
                    '#ff0000',
                    '#a92323',
                    '#00c36f',
                    '#ffb3cb',
                    ],
                color: ''
            }
        },
        methods: {
            async getQuote() {
                await fetch("https://type.fit/api/quotes")
                    .then((response) => {
                        return response.json();
                    })
                    .then((data) => {
                        this.quote = data[Math.floor(Math.random() * data.length)].text
                        this.author = data[Math.floor(Math.random() * data.length)].author
                        this.color = this.colors[Math.floor(Math.random() * this.colors.length)]
                        console.log(this.quote);
                    });
            }
        }
    }
</script>

<style scoped>
.card {
    max-width: 500px;
    margin: 120px auto;
    padding: 20px;
    border-radius: 5px;
}
button:hover{
    transform: scale(1.1);
  }

button{
    border-radius: 5px;
    border: 1px solid #212a21;
    background-color: #0d1f0c;
    padding: 8px 15px;
    outline: none;
    font-size: 14px;
    font-weight: 700;
    color: #fff;
    cursor: pointer;
    transition: all 0.3s ease;
  }
  
button:hover{
    background-color: #222422;
  }

.author {
    margin-left: 70%;
}
</style>