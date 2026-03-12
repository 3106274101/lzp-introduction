<template>
  <section class="experience-box">
    <a-steps :current="2">
      <template #progressDot="{ index, status, prefixCls}">
        <a-popover>
          <template #content>
            <span>详细经历以简历为准哦</span>
          </template>
          <span :class="`${prefixCls}-icon-dot`"/>
        </a-popover>
      </template>
      <!-- 修改subTitle宽度  -->
      <a-step title="2020 - 2022"  subTitle="天古信息科技有限公司" description="参与前端开发工作" />
      <a-step title="2022 - 2023" subTitle="上海透景生命科技股份有限公司" description="前端开发工作"/>
      <a-step title="2023 - 当前" subTitle="浙江浙商互联信息科技有限公司" description="担任前端主要负责人"/>
      <a-step title="当前 - 未来" description="静待机缘"/>
    </a-steps>
  </section>
</template>

<script setup>

</script>

<style lang="scss">
.experience-box {
  padding: 3rem 2rem;
  width: 100%;
  //.ant-steps-item-subtitle {
  //  filter: blur(1.5px);
  //}
}

// .ant-steps-item-subtitle {
//   width: 180px;
// }
// .ant-steps-item-description {
//  width: 180px;
// }
</style>
