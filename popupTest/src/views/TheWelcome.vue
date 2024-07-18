<script setup>
import WelcomeItem from './WelcomeItem.vue'
import DocumentationIcon from './icons/IconDocumentation.vue'
import ToolingIcon from './icons/IconTooling.vue'
import EcosystemIcon from './icons/IconEcosystem.vue'
import CommunityIcon from './icons/IconCommunity.vue'
import SupportIcon from './icons/IconSupport.vue'
</script>
<template>
  <div>
    <section class="main">
      <button type="button" class="openPopup">팝업</button>
    </section>
    <div class="modalPortal">
      <div class="modalWrap">
        <div class="modalContent">
          <div class="title">
            <p>팝업의 타이틀영역</p>
            <a href="#" title="팝업닫기" role="button"><span class="blind">본문으로돌아가기</span></a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="sass">
.modalPortal 
  position: fixed
  inset: 0px
  background-color: rgba(30, 30, 30, 0.8)
  backdrop-filter: blur(5px)
  display: flex
  justify-content: center
  align-items: center
  z-index: 9999


.moadalWrap 
  position: absolute
  inset: unset
  border: none
  background: transparent
  overflow: hidden
  border-radius: 12px
  outline: none
  padding: 0px
  width: auto
  height: auto
  margin: 0px
  max-width: 100%
  max-height: 100vh


span 
  &.blind 
    opacity: 0
    z-index: -9999

</style>
