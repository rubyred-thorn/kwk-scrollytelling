<script>
    import * as Highcharts from "highcharts";
    import "highcharts/modules/exporting";
    import { Chart } from "@highcharts/svelte";
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";

    const series = [
        {
            name: "White",
            data: [
                [2007, 245000],
                [2010, 177000],
                [2013, 181000],
                [2016, 216000],
                [2019, 219000],
                [2022, 284000],
            ],
            color: "#8427c9",
        },
        {
            name: "Other",
            data: [
                [2007, 87000],
                [2010, 58000],
                [2013, 52000],
                [2016, 80000],
                [2019, 86000],
                [2022, 132000],
            ],
            color: "#ff99fc",
        },
        {
            name: "Black",
            data: [
                [2007, 30000],
                [2010, 22000],
                [2013, 17000],
                [2016, 21000],
                [2019, 28000],
                [2022, 44000],
            ],
            color: "#4096fa",
        },
        {
            name: "Hispanic",
            data: [
                [2007, 30000],
                [2010, 23000],
                [2013, 18000],
                [2016, 26000],
                [2019, 42000],
                [2022, 62000],
            ],
            color: "#4096fa",
        },
        {
            name: "All",
            data: [
                [2007, 173000],
                [2010, 105000],
                [2013, 104000],
                [2016, 120000],
                [2019, 141000],
                [2022, 193000],
            ],
            color: "#4096fa",
        },
    ];

    let chart;
    let fifthSeriesVisible = false;

    let options = {
        chart: {
            type: "spline",
            backgroundColor: "#e3ff00",
            borderColor: "#007052",
            borderWidth: 5,
            borderRadius: 20,
        },
        title: {
            text: "Median Total Net Worth for Households, by Race/Ethnicity",
        },
        subtitle: {
            text: "Nationwide, 2007-2022",
        },
        series: [series[0], series[1], series[2], series[3]],
    };

    function toggleFifthSeries() {
        const existingSeries = chart.series.find((s) => s.name === "All");

        if (existingSeries) {
            existingSeries.remove();
            fifthSeriesVisible = false;
        } else {
            chart.addSeries(series[4]);
            fifthSeriesVisible = true;
        }
    }
</script>

<div>
    <Scroller layout="left">
        {#snippet sticky()}
            <div class="chart">
                <Chart bind:chart {options} highcharts={Highcharts} />
            </div>
            <button on:click={toggleFifthSeries} class="toggle-button">
                {fifthSeriesVisible ? "Remove All" : "Add All"}
            </button>
            <div>
                <p>
                    The chart above shows the median net worth of various households from the early 2000s to
                    2022. Similar to the data on education, there's a noticeable gap in median net worth
                    in minorities, which is below the median national new worth. Fortunately, trends show that
                    Hispanic and Black households, among other minorities, are growing in wealth and progressing.
                    The rise happens soon after the COVID pandemic, and it's likely this growth correlates to
                    the many changes in the job industry and entrepreneurship.
                </p>
                <p>
                    We can't conclude that it's a cause-and-effect relationship; however, there is
                    a strong relationship between these two factors and the way they influence the opportunities
                    and education a person can hope to achieve to.
                </p>
            </div>
        {/snippet}

        {#snippet scrolly()}
            <ArticleText>
                The problems minorities face seem insurmountable. Why bother worrying about it?
            </ArticleText>

            <ArticleText>
                Being a minority doesn't make a person any less human. They deserve the same chances
                and a voice at the table; they should be able to hold their head high
                and not drag around a weight they can't control.
            </ArticleText>

            <ArticleText>
                Numbers tell us what we need to focus on. Now it's our job to figure out what we can do about it.
            </ArticleText>
        {/snippet}
    </Scroller>
</div>

<style>
    .chart {
        width: 90%;
        margin: 0px auto;
    }

    .toggle-button {
        margin: 20px;
        padding: 20px;
        color: #007052;
        background-color: #0bd956;
        border: solid 2px #007052;
        border-radius: 16px;
        font-size: large;
        cursor: pointer;
        transition: all 0.2s ease;
        box-shadow: 0 4px 0 #007052;
    }

    .toggle-button:active {
        transform: translateY(2px);
        box-shadow: 0 2px 0 #007052;
    }
</style>
