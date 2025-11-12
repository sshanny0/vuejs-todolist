<template>
<label
    class="group flex items-center p-4 px-6 my-3 bg-white rounded-xl shadow-[0_2px_8px_rgba(0,0,0,0.06)] transition-all duration-300 ease-[cubic-bezier(0.4,0,0.2,1)] cursor-pointer relative overflow-hidden hover:-translate-y-0.5 hover:shadow-[0_4px_12px_rgba(0,0,0,0.1)] before:content-[''] before:absolute before:left-0 before:top-0 before:h-full before:w-1 before:bg-[#667eea] before:opacity-0 before:transition-opacity before:duration-300 hover:before:opacity-100"
  >
    <input type="checkbox" :checked="isChecked" @change="emit('update')" class="hidden" />
    <!-- We can put any element to this slot -->
    <span
      class="w-[22px] h-[22px] border-2 rounded-md mr-4 relative transition-all duration-200 shrink-0 flex items-center justify-center"
      :class="
        isChecked
          ? 'bg-[#667eea] border-[#667eea] after:content-[\'✓\'] after:text-white after:text-sm after:font-bold'
          : 'border-[#ddd] group-hover:border-[#667eea]'
      "
    ></span>
    <span
      class="flex-1 text-left text-base transition-all duration-300 mr-4"
      :class="isChecked ? 'line-through text-[#a0aec0]' : 'text-[#2d3748]'"
    >
      <slot></slot>
    </span>
  </label>
</template>

<script setup lang="ts">
// // options api
// import { defineComponent } from 'vue'

// export default defineComponent({
//   name: 'TaskComponent',
//     props: {
//       isChecked: {
//         type: Boolean,
//         required: false,
//         default: false
//       }
//     }
//   }
// )

const emit = defineEmits(['update'])

// composition api
defineProps<{
  isChecked: boolean | false
}>()

</script>
<!-- <style scoped>
label {
  display: flex;
  align-items: center;
  padding: 1rem 1.5rem;
  margin: 0.75rem 0;
  background: white;
  border-radius: 17px;
  transition: 0 2px 8px #0000000f;
  cursor: pointer;
  position: relative;
  overflow: hidden;
}

label::before {
  content: '';
  position: absolute;
  left: 0;
  top: 0;
  height: 100%;
  width: 4px;
  background: #667eea;
  opacity: 0;
  transition: opacity 0.3s ease;
}

label:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

label:hover::before {
  opacity: 1;
}

input[type='checkbox'] {
  display: none;
}

.checkbox-custom {
  width: 22px;
  height: 22px;
  border: 2px solid #ddd;
  border-radius: 6px;
  margin-right: 1rem;
  position: relative;
  transition: all 0.2s ease;
  flex-shrink: 0;
}

label:hover .checkbox-custom {
  border-color: #667eea;
}

.checked .checkbox-custom {
  background: #667eea;
  border-color: #667eea;
}

.checked .checkbox-custom::after {
  content: '✓';
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: white;
  font-size: 14px;
  font-weight: bold;
}

.todo-text {
  flex: 1;
  text-align: left;
  color: #2d3748;
  font-size: 1rem;
  transition: all 0.3s ease;
  margin-right: 1rem;
}

.checked .todo-text {
  text-decoration: line-through;
  color: #a0aec0;
}
</style> -->
