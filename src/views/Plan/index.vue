<template >
  <div>
    <Create></Create>
  </div>
</template>
<script>
import Create from "../create";
export default {
  components: {
    Create,
  },
  setup() {
    const handlePlan = (plan) => {
      console.log(plan);
    };
    return {handlePlan};
  },
};
</script>