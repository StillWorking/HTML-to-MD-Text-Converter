<script>
  import showdown from "showdown";
  import { parse } from "node-html-parser";
  const converter = new showdown.Converter();
  let text = "";
  $: root = parse(text);
  $: md = converter.makeMarkdown(text);
</script>

<style>
  main {
    text-align: center;
    padding: 0.5em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #24235a;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
  .html-editor {
    width: 100%;
    display: flex;
    align-items: flex-start;
    justify-content: space-evenly;
  }
  .html-editor__left-panel,
  .html-editor__center-panel,
  .html-editor__right-panel {
    width: 33%;
    border: solid 1px black;
    height: 70vh;
  }
  .html-editor__right-panel {
    overflow: auto;
  }
  .html-editor__source {
    border: none;
    width: 100%;
    height: 100%;
  }
  .html-editor__source:focus {
    outline: none;
  }
  #container {
    width: 100%;
    text-align: center;
  }

  #left {
    float: left;
    width: 100px;
    font-size: 1.25em;
    font-weight: 150;
  }

  #center {
    display: inline-block;
    margin: 0 auto;
    width: 100px;
    font-size: 1.25em;
    font-weight: 150;
  }

  #right {
    float: right;
    width: 100px;
    font-size: 1.25em;
    font-weight: 150;
  }
</style>

<main>
  <h1>HTML to Markdown/Text Converter</h1>
  <div id="container">
    <div id="left">HTML</div>
    <div id="center">Markdown</div>
    <div id="right">Regular Text</div>
  </div>
  <div class="html-editor">

    <div class="html-editor__left-panel">
      <textarea bind:value={text} class="html-editor__source" />
    </div>

    <div class="html-editor__center-panel">
      <div class="text__output">
        {@html md}
      </div>
    </div>

    <div class="html-editor__right-panel">
      <div class="html__output">
        {@html root}
      </div>
    </div>
  </div>
  <footer>
    <p>
      Created by Taha Sheikh using
      <a href="https://svelte.dev">Svelte</a>
      ,
      <a href="https://www.npmjs.com/package/showdown">Showdown</a>
      and
      <a href="https://www.npmjs.com/package/node-html-parser">
        node-html-parser
      </a>
    </p>
  </footer>
</main>
