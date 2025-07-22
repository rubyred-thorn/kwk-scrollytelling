<script>
    import * as Highcharts from "highcharts";
    import "highcharts/modules/exporting";
    import { Chart } from "@highcharts/svelte";
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";

    let options = {
        title: {
        text: 'Degree Attainment by Race/Ethnicity',
        },

        yAxis: {
            title: {
            text: 'Attainment Rate'
            }
        },

        xAxis: {
            accessibility: {
                rangeDescription: 'Range: 2011 to 2023'
            }
        },

        plotOptions: {
            series: {
                label: {
                connectorAllowed: false
                },
                pointStart: 2011
            }
        },

        series: [{
            name: 'Asian',
            data: [
            50.8, 51.9, 53.9, 52.7, 54.4, 56.4, 55.4,
            57.1, 58.6, 61.7, 61.9, 60.2, 62.9
            ]
        }, {
            name: 'White',
            data: [
            34.0, 34.5, 35.2, 35.6, 36.2, 37.3,
            38.1, 38.8, 40.1, 41.3, 41.9, 41.8, 42.3
            ]
        }, {
            name: 'Black',
            data: [
            20.2, 21.4, 22.0, 22.8, 22.9, 23.5,
            24.3, 25.6, 26.3, 27.9, 28.3, 27.9, 29.0
            ]
        }]

    };
</script>

<div>
    <Scroller layout="right">
        {#snippet sticky()}
            <div class="chart">
                <Chart {options} highcharts={Highcharts} />
            </div>
            <p>
                Data and graph courtesy of <a href="https://blackwealthdata.org/explore/education">BWDC</a>
            </p>
            <p>
                This graph charts the degree attainment rate of different ethnicities
                in the US from 2011 to 2023. While there's a general increasing trend,
                there's a significant and concerning gap between the rates of Asian and White 
                students versus that of Black and Hispanic students.
            </p>
            <p>
                However, when it comes to high school degree attainment, the rate for
                Black students are higher than for an undergraduate degree. Similarly,
                while the rate for Hispanic students is low, it's higher than the rate
                for a Bachelor's degree.
            </p>
            <p>
                While there isn't a direct reason, the education gap shows strong
                correlation with the racial wealth gap. A student's financial position
                can <a href="https://www.ihep.org/publication/breaking-the-cycle/">shape their
                decision to enroll in college</a>, which is in turn influenced by family wealth.
                Moreover, while other factors can influence the outcome, there's a strong link 
                between generational wealth and college enrollment.
            </p>
        {/snippet}

        {#snippet scrolly()}
            <ArticleText>
                <strong>Welcome</strong> to a deep dive into the connection between education and the racial wealth gap!
            </ArticleText>

            <ArticleText>
                What do you notice about this graph? Is the color off? Hmmm. What is it telling us?
                <br /> <br />
                Hint: It has to do with gaps
            </ArticleText>

            <ArticleText>
                The graph on your left is a small representation of reality: the education gap.
                Minority students show much lower rates of degree attainment compared to their White, and even Asian, peers.
                Research shows that there's a strong correlation between the barriers in education and in wealth.
            </ArticleText>

            <ArticleText>
                Think about it: rising expenses, exorbitant tuition, and the countless smaller expenses that comes
                with student life. You need money to pay that, and while scholarships can help lessen the financial burden,
                it's rare for more than a few students to receive a substantial amount of gift aid. Moreover, the college application process itself is another hurdle to overcome. It creates a disadvantage for minority and low-income students, and halts he journey of a bright mind.
            </ArticleText>
        {/snippet}
    </Scroller>
</div>

<style>
    .chart {
        width: 90%;
        margin: 0px auto;
    }
</style>