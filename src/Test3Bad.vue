<script lang="tsx">
import { defineComponent, ref } from "vue";
const sname = ref("good");
function onchange(a) {
  console.log("onchange-", a);
}
function onblur(a) {
  console.log("onblur-", a);
}
function input(a) {
  console.log("input-", a);
}
export default defineComponent({
  setup() {
    /**
     * 只要修改就会触发
     * 
     */
    const sname = ref("bad2");

    return () => (
      <>
      <h1>任意输入，两个事件都会触发</h1>
      <el-form>
        <el-form-item label="test-bad">
          <el-input v-model={sname.value} blur={onblur(sname.value)}
          input={input(sname.value)}
          change={onchange(sname.value)} />
        </el-form-item>
      </el-form>
      <h1>blur 正常， 修改时change 不会触发， 修改后失去焦点change会被触发</h1>
      <input type="text" value={sname.value} 
          onChange={()=>onchange(sname.value)} 
          onBlur={()=>onblur(sname.value)} 
           /> 
      </>
    );
  },
});
</script>
 