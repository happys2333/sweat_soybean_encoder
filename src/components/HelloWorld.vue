<template>
  <el-container>
    <el-header>
      <h1>😅 流汗黄豆编码器---一款让您快速无语的编码器</h1>
    </el-header>
    <el-main>
  <el-container>
    <el-row>
  <el-input
      v-model="e"
      maxlength="50"
      placeholder="输入原始文本"
      show-word-limit
      type="text"
  ></el-input>
  <el-button type="success" round @click="encode">😅一起流汗吧(编码)</el-button>
  <el-button type="success" round @click="decode">😄擦汗了(解码)</el-button>
  <el-input
      v-model="d"
      :rows="20"
      type="textarea"
      placeholder="输入黄豆文本"
  ></el-input>
    </el-row>
  </el-container>
    </el-main>
  </el-container>
</template>

<script>

export default {
  name: 'HelloWorld',
  data(){
    return{
      t:"😅",
      f:"😄",
      block:"💧",
      e:"",
      d:""
    }
  },
  methods:{
    str_to_bin(str){
      var result = [];
      var list = str.split("");
      for(var i=0;i<list.length;i++){
        if(i !== 0){
          result.push("b");
        }
        var item = list[i];
        var binaryStr = item.charCodeAt().toString(2);
        result.push(binaryStr);
      }
      return result.join("");
    },
    bin_to_str(str){
      var result = [];
      var list = str.split("b");
      for(var i=0;i<list.length;i++){
        var item = list[i];
        var asciiCode = parseInt(item,2);
        var charValue = String.fromCharCode(asciiCode);
        result.push(charValue);
      }
      return result.join("");
    },
    bin_to_face(str){
      let result = ""
      for(let c of str){
        if (c === "0"){
          result += this.f
        }else if (c === "1"){
          result += this.t
        }else {
          result += this.block
        }
      }
      return result
    },
    face_to_bin(face){
      let result = ""
      for(let c of face){
        if (c === this.f){
          result += "0"
        }else if (c === this.t){
          result += "1"
        }else {
          result += "b"
        }
      }
      return result
    },
    encode(){
      let text = this.e
      let bin = this.str_to_bin(text)
      this.d = this.bin_to_face(bin)
    },
    decode(){
      let face = this.d
      let bin = this.face_to_bin(face)
      this.e = this.bin_to_str(bin)
    }
  }
}
</script>
