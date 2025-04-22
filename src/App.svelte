<script lang="ts">
  import { onMount } from 'svelte';
  import content from './content.json';

const text_list: string[] = content?.en?.under_text_list || [];
let text: String;

function animation(timeout: number) {
  let length = text_list.length;
  let random = Math.round(Math.random() * length);
  text = text_list[random];
  animate_text(timeout, length, random)
}

function animate_text(timeout: number, length: number, current_number: number) {
  if (current_number < length - 1) {
    current_number++;
  } else {
    current_number = 0;
  }
  console.log(current_number)
  text = text_list[current_number]
  setTimeout(() => {
    animate_text(timeout, length, current_number);
  }, timeout);
}


onMount(() => {
  animation(5000);
});

</script>

<div class="flex flex-col drop-shadow-main">
  <div class="text-text dark:text-dark-text text-4xl font-bold">Moritz Kuttesch</div>
  <div class="text-text dark:text-dark-text text-2xl font-bold">{text}</div>
</div>
