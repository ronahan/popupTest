<template>
  <div ref="popup" class="popup" @mousedown="startDrag" style="position: absolute;">
    <!-- 팝업 내용 -->
    Drag me around!
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const popup = ref(null);

function moveAt(x, y) {
  popup.value.style.left = x + 'px';
  popup.value.style.top = y + 'px';
}

function onMouseMove(event) {
  moveAt(event.pageX, event.pageY);
}

function onMouseUp() {
  document.removeEventListener('mousemove', onMouseMove);
  document.removeEventListener('mouseup', onMouseUp);
}

function startDrag(event) {
  const shiftX = event.clientX - popup.value.getBoundingClientRect().left;
  const shiftY = event.clientY - popup.value.getBoundingClientRect().top;

  function adjustedMouseMove(e) {
    moveAt(e.pageX - shiftX, e.pageY - shiftY);
  }

  document.addEventListener('mousemove', adjustedMouseMove);
  document.addEventListener('mouseup', () => {
    document.removeEventListener('mousemove', adjustedMouseMove);
    document.removeEventListener('mouseup', onMouseUp);
  });
}

// 드래그 앤 드롭 동작을 막는 기능
onMounted(() => {
  popup.value.ondragstart = () => false;
});

</script>

<style>
.popup {
  width: 150px;
  height: 150px;
  background-color: lightblue;
  text-align: center;
  line-height: 150px;
  border-radius: 10px;
  user-select: none;
}
</style>
