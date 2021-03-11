<template>
  <div class="header">
    <i class="fa fa-check-square-o" aria-hidden="true"></i>
    <span>Checklist</span>
  </div>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style>
.fa-check-square-o {
  font-size: 20px;
  margin: 0 10px 0 0;
  color: rgb(73, 73, 73);
}
.header {
  padding: 10px;
}
span {
  font-size: 16px;
  font-weight: 600;
  color: rgb(73, 73, 73);
}
</style>