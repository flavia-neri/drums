<template>
    <section class="drum-container">
        <h1>BATERIA</h1>
        <div class="keys">
            <div class="key" v-for="key in keys" :key="key">
                {{key}}
            </div>
        </div>
        <div class="composition-container">
            <form>
                <input type="text" placeholder="Faça uma composição aqui...">
                <button>TOCAR</button>
            </form>
            
        </div>
        <h5>Flávia Neri</h5>
    </section>
</template>
<script>
document.title = "Bateria";
export default {
    data: function(){
        return {
            keys:['Q', 'W', 'E', 'A', 'S', 'D', 'Z', 'X', 'C'],
        }
    },
}
</script>
<style lang="scss">
    @font-face {
        font-family:'Fritlany';
        src: url('../assets/Fritlany.ttf');
    }
    .drum-container{
        display:flex;
        flex-direction:column;
        justify-content: center;
        align-items: center;
        height:100vh;
        background-color:#161616;
        h1{
            margin:0;
            padding:0;
            font-size:34px;
            color:#c9c9c9;
            letter-spacing:3px;
        }
        .keys{
            margin:30px 0;
            display:grid;
            grid-template-columns: repeat(3, 1fr);
            grid-gap: 1em;
            .key{
                display:flex;
                justify-content: center;
                align-items: center;
                width:100px;
                height:100px;
                border-radius:10px;
                border:1px solid #fff;
                color:#c9c9c9;
                font-size:30px;
                cursor:pointer;
                &:hover{
                    background-color: rgba(48,48,48,0.2);
                }
                &:active{
                    transform:scale(1.1);
                }
            }
        }
        .composition-container{
            form{
                display:flex;
                flex-direction:column;
                input, button{
                    width:320px;
                    height:40px;
                    padding-left:10px;
                    color:#c9c9c9;
                    font-size:20px;
                    border:1px solid #fff;
                    border-radius: 5px;
                    background-color:transparent;
                    text-transform:uppercase;

                    &::placeholder{
                        font-size:16px;
                        text-transform:none;
                    } 
                }
                button{
                    margin-top:15px;
                    cursor:pointer;
                    &:hover{
                        background-color: rgba(48,48,48,0.2);
                    }
                    &:active{
                        transform:scale(1.01);
                    }
                }
            }
        }
        h5{
            color:#c9c9c9;
            font-family:Fritlany;
        }
    }
</style>