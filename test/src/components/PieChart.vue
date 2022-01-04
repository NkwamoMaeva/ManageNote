<script>
import { Pie } from "vue-chartjs";

export default {
  extends: Pie,
  props: ['notes'],
  data: () =>{
    return{
      names: [],
      values: []
    }
  },
  mounted() {
      console.log(this.notes)
    this.notes.forEach(item => {
        this.names.push(item.name)
        this.values.push(item.note)
    });
    this.renderChart(
      {
        labels: this.names,
        datasets: [
          {
            data: this.values,
            backgroundColor: [
              "#A3A0FB",
              "#55D8FE",
              "#00D8FF",
              "#FF8373",
              "#FFDA83",
            ],
          },
        ],
      },
      {
        responsive: true,
        maintainAspectRatio: false,
        legend: {
          display: true,
          position: "right",
          labels: {
            usePointStyle: true,
          },
        },
        cutoutPercentage: 60,
      }
    );
  }
};
</script>
