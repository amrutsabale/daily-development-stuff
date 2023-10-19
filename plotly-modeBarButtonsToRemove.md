ref: https://plotly.com/javascript/configuration-options/#remove-modebar-buttons
`````
import Plotly from 'plotly.js-cartesian-dist-min';
import React from 'react';
import createPlotlyComponent from 'react-plotly.js/factory';
const Plot = createPlotlyComponent(Plotly);

export const MyPlot = ({
  chartData,
  notChartMsg,
}) => {
  return (
    <>
      {chartData ? (
        <Plot
          {...chartData}
          layout={{
            ...chartData.layout,
            autosize: true,
            width: undefined,
            height: undefined,
          }}
          useResizeHandler={true}
          style={{ maxWidth: 400, maxHeight: 380, width: '100%', height: '100%' }}
          config={{
            responsive: true,
            modeBarButtonsToRemove: ['toImage', 'pan2d', 'zoom', 'resetScale2d'],
            displaylogo: false,
          }}
        />
      ) : (
        <Typography style={{ fontSize: 16 }}>{notChartMsg}</Typography>
      )}
    </>
  );
};

`````
