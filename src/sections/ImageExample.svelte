<script>
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";
</script>

<div>
    <Scroller layout="right">
        {#snippet sticky()}
            <img class="together-img" src="https://github.com/rubyred-thorn/kwk-scrollytelling/blob/gh-pages/were-all-in-togehter.jpg?raw=true" alt="We're all in this together! (meme)" />
            <p>We're all in this together!</p>
        {/snippet}

        {#snippet scrolly()}
            <ArticleText>
                The best way to tackle insidious problems like this is to acknowledge it exists and steadily build each other up.
                Policymaking will change, but outside of that, there are countless other ways to change lives. From encouraging a friend
                to take a chance on that program to starting an initiative, like a scholarship or a support group, anything
                can create change.
            </ArticleText>

            <ArticleText>In the end, it's your choice.</ArticleText>
        {/snippet}
    </Scroller>
</div>

<style>
    .together-img {
        width: 75%;
        margin: 0px auto;
    }
</style>
