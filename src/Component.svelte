<script>
  import { getContext } from 'svelte';
  import { Bar } from 'svelte-chartjs';

  /* import { Bar } from 'svelte-chartjs'; */
  import 'chart.js/auto';

  export let data;
  export let options;

  const default_options = {
    responsive: true,
    scales: {
      y: {
        beginAtZero: true
      }
    }
  }
  
  const { styleable } = getContext("sdk");
  const component = getContext("component");
</script>

<div use:styleable={$component.styles}>
  <Bar data={ typeof data === 'string' ? JSON.parse(data) : data } options={Object.assign(default_options, typeof options === 'string' ? JSON.parse(options) : options)} />
</div>
