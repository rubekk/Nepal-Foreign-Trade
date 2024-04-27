<script>
    import { summaries } from "$lib/data.js";
    import { tableSummaryIndex } from "$lib/store.js";
    
    let summaryIndex= 0;

    tableSummaryIndex.subscribe(value =>{
        summaryIndex= value;
    })
</script>

<div class="summary-container">
    <div class="summary-title">Short explanation of the table</div>
    
    {summaries[summaryIndex]}
</div>

<style>
    .summary-container{
        padding: 1rem;
        text-align: justify;
        background-color: #fff;
        box-shadow: 3px 3px 3px rgb(46 128 187 / 20%);
    }
    .summary-title{
        margin-bottom: 1rem;
        font-size: 1.25rem;
        text-align: center;
        text-decoration: underline;
    }
</style>