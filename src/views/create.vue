<template >
  <a-form :model="form" :label-col="{span:4}" :wrapper-col="{span:14}">
    <a-form-item label="选择计划的日期">
      <a-date-picker
        v-model:value="form.date"
        type="date"
        placeholder="选择计划的日期"
        style="width:100%"
      >

      </a-date-picker>
    </a-form-item>
    <section @click="onSubmit">提交</section>
  </a-form>
</template>
<script>
import {reactive,toRefs} from 'vue'
import moment from 'moment'
export default {
  setup(props,context){
    const state=reactive({
      form:{
        date:moment(Date.now()).format('YYYY-MM-DD')
      }
    })
     
     const onSubmit = ()=> {
       context.emit('handle-plan',state.form)
       console.log(state.form)
     }
    return {
      ...toRefs(state),
      onSubmit
    }
  }
}
</script>