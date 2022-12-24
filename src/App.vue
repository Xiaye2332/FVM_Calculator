<script setup>
import Header from "@/components/Header.vue";
import Webmain from "@/components/Webmain.vue";
import Footer from "@/components/Footer.vue"
</script>

<template>
  <div class="common-layout">
    <el-container>
      <el-header>
        <Header />
      </el-header>
      <el-divider />
      <el-main>
        <Webmain />
      </el-main>
      <el-footer>
        <Footer/>
      </el-footer>
    </el-container>
  </div>
</template>


