# Example: Downloading and Embedding a Notebook

This repository demonstrates how to download and embed an Observable notebook into a web application.

You can download the tarball for any notebook by clicking **Download code** in the notebook menu. Or, if you know the URL of the notebook, you can translate it into the corresponding tarball URL and use curl from the command line. For example:

```bash
mkdir -p @d3/bar-chart
curl https://api.observablehq.com/@d3/bar-chart.tgz?v=3 | tar xvz -C @d3/bar-chart
```

You can then load your notebook and render the *chart* cell as follows:

```js
import {Runtime, Inspector} from "https://cdn.jsdelivr.net/npm/@observablehq/runtime@4/dist/runtime.js";
import define from "./@d3/bar-chart/index.js";

const runtime = new Runtime();
const main = runtime.module(define, name => {
  if (name === "chart") {
    return new Inspector(document.body.appendChild(document.createElement("DIV")));
  }
});
```

(If you prefer, you can self-host a copy of the [Observable runtime](https://github.com/observablehq/runtime) rather than loading the latest release published to npm.)

For more, see [Downloading and Embedding Notebooks](https://observablehq.com/@observablehq/downloading-and-embedding-notebooks).
