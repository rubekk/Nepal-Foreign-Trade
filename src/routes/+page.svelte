<script>
    import "./app.css";
    import Chart from "../components/Chart.svelte";
    import Table from "../components/Table.svelte";
    import WorldMap from "../components/WorldMap.svelte";
    import CustomMap from "../components/CustomMap.svelte";
    import Share from "../components/Share.svelte";
</script>

<div class="container">
    <div class="header">
        <h1 class="main-title">Nepal Foreign Trade Statistics</h1>
        <h3 class="sub-title">Based on First Nine(Shrawan-Chaitra) of FY 2080/81 (Mid July 2023 to Mid April 2024)</h3>
    </div>

    <div class="note">Note: All import and export values are in 1000 (thousands)</div>

    <div class="total-container">
        <div class="chart">
            <Chart />
        </div>

        <div class="text">
            <div class="box">
                <div class="box-num">121312312</div>
                <div class="box-text">Total import</div>
            </div>
            <div class="box">
                <div class="box-num">121312312</div>
                <div class="box-text">Total export</div>
            </div>
            <div class="box">
                <div class="box-num">91.11</div>
                <div class="box-text">Import percentage</div>
            </div>
            <div class="box">
                <div class="box-num">8.89</div>
                <div class="box-text">Export percentage</div>
            </div>
            <div class="box">
                <div class="box-num">10.24</div>
                <div class="box-text">Import to Export ratio</div>
            </div>
        </div>
    </div>

    <div class="share-container top">
        <Share />
    </div>

    <div class="table-container">
        <Table />
    </div>
    
    <div class="worldmap-container">
        <WorldMap />
    </div>

    <div class="custommap-container">
        <CustomMap />
    </div>

    <div class="share-container">
        <Share />
    </div>

    <div class="info">
        Above tables are based on the data of ASYCUDA world System obtained form 29 major Customs Offices. They exclude  imports and exports that occur through the custom points where ASYCUDA world system is not implemented. Information are preliminary and subject to revise on annual trade Statistics.
    </div>
</div>

<style>
    .container{
        margin: 2rem auto;
        width: var(--width);
        flex-direction: column;
    }
    .header{
        margin-bottom: 2rem;
        padding: 1rem;
        width: 100%;
        text-align: center;
        background-color: #fff;
        border: 1px solid var(--blue);
    }
    .main-title{
        margin-bottom: 1rem;
    }
    .sub-title{
        color: #797979;
        font-size: 1.25rem;
        font-style: italic;
    }
    .note{
        margin-bottom: 2rem;
        padding: .5rem;
        font-style: italic;
        color: #fff;
        background-color: var(--red);
    }
    .total-container{
        margin: auto;
        padding: 2rem;
        width: 100%;
        background-color: #afa8a8;
        border-radius: 3px;
    }
    .chart{
        width: 350px;
    }
    .box{
        margin: .5rem;
        width: 200px;
        height: 60px;
        text-align: center;
        background-color: var(--green);
        border-radius: 5px;
        flex-direction: column;
    }
    .box-num{
        font-weight: bold;
        font-style: italic;
        color: #fff;
    }
    .box-text{
        font-size: .9rem;
    }
    .share-container, .table-container, .worldmap-container, .custommap-container, .info{
        width: 100%;
        margin-top: 2rem;
    }
    .info{
        font-size: .8rem;
        font-style: italic;
        background-color: #fff;
    }
</style>