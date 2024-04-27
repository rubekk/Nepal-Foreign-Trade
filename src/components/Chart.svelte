<script>
    import { onMount } from "svelte";
    import Chart from "chart.js/auto";

    let chartValues = [1167369808, 113946007];
	let chartLabels = ['Import', 'Export'];
	let ctx, chartCanvas;

    onMount(async () => {
        ctx = chartCanvas.getContext('2d');
        
        new Chart(ctx, {
            type: 'pie',
            data: {
                labels: chartLabels,
                datasets: [{
                    label: 'Revenue',
                    backgroundColor: [
                        'rgb(243, 72, 103)',
                        'rgb(0, 89, 255)'
                    ],
                    borderColor: 'rgb(255, 255, 255)',
                    hoverOffset: 1,
                    data: chartValues
                }]
            },
            options: {
                plugins: {
                    title: {
                        display: false
                    },
                    tooltip: {
                        enabled: false
                    },
                    legend: {
                        display: false
                    }
                }
            },
            plugins: [displayTooltip]
		})
	});

    const displayTooltip={
        id: 'displayTooltip',
        afterDraw(chart, args, options){
            const { ctx }= chart;
            ctx.save();

            chart.data.datasets.forEach((dataset,i)=>{
                chart.getDatasetMeta(0).data.forEach((dataPoint,index)=>{
                    const { x, y } = dataPoint.tooltipPosition();
                    const text = Array.from(dataset.data)[index];
                    const textWidth = ctx.measureText(text).width;
                    const textHeight = 24;

                    ctx.fillStyle='rgba(0, 0, 0, 0.5)';
                    ctx.fillRect(x-((textWidth/2)+5),(y-(textHeight/2)), textWidth+10, textHeight);
                    ctx.font = '14px Arial';
                    ctx.fillStyle = 'white';
                    ctx.fillText(text,x-textWidth/2,y+4);
                    ctx.restore();
                })
            })
        }
    }
</script>

<div class="chart-container">    
    <div class="chart-title">Import Export Chart</div>
    <div class="chart">
        <canvas bind:this={chartCanvas}></canvas>
    </div>
    <div class="chart-legend">
        {#each chartLabels as data, i}
        <li>
            <div class={`legend-color lc-${i+1}`}></div>
            {data}
        </li>
        {/each}
    </div>
</div>

<style>
    .chart-container{
        flex-direction: column;
    }
    .chart-title{
        font-size: 1.25rem;
        font-weight: bold;
        color: #fff;
    }
    .chart{
        margin: 1rem 0;
        width: 275px;
        height: 275px;
    }
    canvas{
        width: 100%;
        height: 100%;
    }
    .chart-legend{
        display: flex;
        gap: 1.5rem;
    }
    .legend-color{
        margin-right: .25rem;
        width: 15px;
        height: 15px;
        border-radius: 50%;
    }
    .lc-1{
        background-color: rgb(255, 99, 132);
    }
    .lc-2{
        background-color: rgb(54, 162, 235);
    }
</style>