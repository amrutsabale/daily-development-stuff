## Customizing the `plotly.js` bundle

By default, the `Plot` component exported by this library loads a precompiled version of all of `plotly.js`, so `plotly.js` must be installed as a peer dependency. This bundle is around 6Mb unminified, and minifies to just over 2Mb.

If you do not wish to use this version of `plotly.js`, e.g. if you want to use a [different precompiled bundle](https://github.com/plotly/plotly.js/blob/master/dist/README.md#partial-bundles) or if your wish to [assemble you own customized bundle](https://github.com/plotly/plotly.js/blob/master/CUSTOM_BUNDLE.md), or if you wish to load `plotly.js` [from a CDN](https://github.com/plotly/plotly.js#use-the-plotlyjs-cdn-hosted-by-fastly), you can skip the installation of as a peer dependency (and ignore the resulting warning) and use the `createPlotComponent` method to get a `Plot` component, instead of importing it:

````javascript
// simplest method: uses precompiled complete bundle from `plotly.js`
import Plot from 'react-plotly.js';

or

// customizable method: use your own `Plotly` object
import Plotly from 'plotly.js-cartesian-dist-min';
import createPlotlyComponent from 'react-plotly.js/factory';
const Plot = createPlotlyComponent(Plotly);
````

https://www.npmjs.com/package/plotly.js-cartesian-dist-min
````
yarn add plotly.js-cartesian-dist-min
````

As plotly.js package bundle size is 8MB we can use partial bundles packages based on our charts requirements
https://github.com/plotly/plotly.js/tree/master/dist#bundle-information

ref: https://github.com/plotly/plotly.js/tree/master/dist
