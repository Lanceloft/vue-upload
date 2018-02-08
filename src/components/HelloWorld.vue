<template>
  <div class="hello">
    <el-upload
      class="upload-demo"
      ref="upload"
      action="https://upload-z2.qiniup.com"
      :auto-upload="autoUpload"
      :on-success="handleSuccess"
      :file-list="fileList2"
      :before-upload="beforeUpload"
      :data="postData"
      list-type="picture">
      <el-button size="small" type="primary">选取图片</el-button>
    </el-upload>
    <el-button size="small" type="primary" @click="submitUpload">确认上传</el-button>
    <el-select v-model="value" placeholder="请选择">
      <el-option
        v-for="item in options"
        :key="item.value"
        :label="item.label"
        :value="item.value">
      </el-option>
    </el-select>
  </div>
</template>

<script>
export default {
  data() {
    return {
      autoUpload: false,
      fileList2: [],
      postData: {
        token: 'qG4ngbB0PgTu3ZWNlbZbIjmWPLaF4C7l0_6b_ZiS:1Lh87f5l4_kXWU9onUx8MKbKe4g=:eyJzY29wZSI6InRlc3RzcGFjZSIsImRlYWRsaW5lIjoxNTE4MTA0MTgwfQ==',
        key: ''
      },
      options: [{
        value: '1',
        label: '1',
      }, {
        value: '2',
        label: '2'
      }],
      value: '',
    };
  },

  methods: {
    submitUpload() {
      this.$refs.upload.submit();
    },

    handleSuccess(res, file) {
      console.log(res, file);
    },

    beforeUpload(file) {
      this.postData.key = this.value + '_' + file.name;
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
