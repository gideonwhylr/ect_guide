## Code Preview

[cinwell website](https://cinwell.com ':include :type=iframe width=100% height=400px')


```html
/*vue*/


<desc>
Hello `world`
* a
* b
</desc>


<template>
    <div>
        <div className='wrapper'>

        <iframe src="https://cinwell.com"></iframe>


        <div id = "result-template"> 
        hello</div> 


        {{anotherVariable}}

        <div class="card">
            <div class="card-body">
                <h1 class = "text-primary"> A test! </h1>
                <p> Another test! </p>
            </div>
        </div>


            <div>
                <p>author: {{globalVariable}}</p>
                <button :style="style" @click="onClick">test</button>
            </div>
        </div>
    </div>


</template>



<script>
    export default {
        data() {
            return {
                globalVariable,
                anotherVariable, 
                style: {
                    color: 'blue'
                }
            }
        },


        methods: {
            onClick() {
                alert('author: ' + this.globalVariable)
                this.style.color = 'red'
            }
        }



    }
</script>

<script src="http://yext-sitescdn-assets.s3-website-us-east-1.amazonaws.com/ect/bundle.js"></script>











```
