<template>
  <div class="hello">
    <chart @mouseover="aaa" :options="option"></chart>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      currentData:[],
      option: {
        xAxis: {
          data:['big', 'cat', 'fox','dog']
        },
        yAxis: {},
        tooltip: {
          show: true,
          trigger: 'axis',
          axisPointer: {
            type: 'cross',
            snap: true,
            axis: 'x', // y轴选项
            label: {
              // show: false,
              color: '#fff',
              backgroundColor: 'rgba(0, 0, 0, .55)'
            }
          },
          formatter: (params) => {
            console.log(params,'dsad');
            if(!this.currentData) return;
            var htmlF = '';
            params.forEach(item => {
              if(this.currentData[0] === item.data[0] && this.currentData[1]===item.data[1]){
                htmlF += `<div>
                            <h3>${item.data[0]}</h3>
                            <p>${item.data[1]}</p>
                          </div>`;
              }
              
            });
            return htmlF;
          }
        },
        series: [{
            symbolSize: 20,
            data: [
                ['big', 4.82],
                ['cat', 1.82],
                ['cat', 2.82],
                ['dog', 1.82],
                ['fox', 5.68],
                ['fox', 5.68]
            ],
            type: 'scatter'
        }]
      }
    }
  },
  methods: {
    aaa (params) {
      this.currentData = params.data;
      console.log(this.currentData)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
