<template>
  <q-page class="flex flex-center">
    <q-input outlined v-model="text" label="Pasta" />
    <q-select outlined v-model="model" :options="options" label="Impressora" />
  </q-page>
</template>

<script>
import { defineComponent } from "vue";
import { ref } from "vue";

export default defineComponent({
  name: "IndexPage",
  setup() {
    return {
      model: ref(null),
      options: ["Google", "Facebook", "Twitter", "Apple", "Oracle"],
    };
  },
  const { exec } = require('child_process');
  exec('wmic printer list brief', (err, stdout, stderr) => {
  if (err) {
    // node couldn't execute the command
    return;
  }
  // list of printers with brief details
  console.log(stdout);
  // the *entire* stdout and stderr (buffered)
  stdout=stdout.split("  ");
  var printers=[];
  j=0;
  stdout = stdout.filter(item => item);
  for (i = 0; i < stdout.length; i++)
  {
    if(stdout[i]==" \r\r\n" ||stdout[i]=="\r\r\n")
    {
       printers[j]=stdout[i+1];
       j++;
    }
  }
  // list of only printers name
  console.log(printers);
  console.log(stderr);
});
});
</script>
