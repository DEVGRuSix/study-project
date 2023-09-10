<!--&lt;!&ndash;<template>&ndash;&gt;-->
<!--&lt;!&ndash;<div>&ndash;&gt;-->
<!--&lt;!&ndash;  <div style="margin: 30px 20px">&ndash;&gt;-->
<!--&lt;!&ndash;    <el-steps :active="active" finish-status="success" align-center>&ndash;&gt;-->
<!--&lt;!&ndash;      <el-step title="验证电子邮件" />&ndash;&gt;-->
<!--&lt;!&ndash;      <el-step title="重新设定密码" />&ndash;&gt;-->
<!--&lt;!&ndash;    </el-steps>&ndash;&gt;-->
<!--&lt;!&ndash;  </div>&ndash;&gt;-->
<!--&lt;!&ndash;  <div>&ndash;&gt;-->
<!--&lt;!&ndash;    <transition name="el-fade-in-liner" mode="out-in">&ndash;&gt;-->
<!--&lt;!&ndash;      <div style="text-align: center;margin: 0 20px;height: 100%" v-if="active===0">&ndash;&gt;-->
<!--&lt;!&ndash;        <div style="margin-top:100px">&ndash;&gt;-->
<!--&lt;!&ndash;          <div style="font-size: 25px;font-weight: bold">重置密码</div>&ndash;&gt;-->
<!--&lt;!&ndash;          <div style="font-size: 14px;color: grey">请输入需要重置密码的电子邮件地址</div>&ndash;&gt;-->
<!--&lt;!&ndash;        </div>&ndash;&gt;-->
<!--&lt;!&ndash;        <div style="margin-top: 50px">&ndash;&gt;-->
<!--&lt;!&ndash;          <el-form :model="form" :rules="rules" @validate="onValidate" ref="formRef">&ndash;&gt;-->
<!--&lt;!&ndash;            <el-form-item prop="email">&ndash;&gt;-->
<!--&lt;!&ndash;              <el-input v-model="form.email" type="email" placeholder="电子邮件地址">&ndash;&gt;-->
<!--&lt;!&ndash;                <template #prefix>&ndash;&gt;-->
<!--&lt;!&ndash;                  <el-icon><Message /></el-icon>&ndash;&gt;-->
<!--&lt;!&ndash;                </template>&ndash;&gt;-->
<!--&lt;!&ndash;              </el-input>&ndash;&gt;-->
<!--&lt;!&ndash;            </el-form-item>&ndash;&gt;-->
<!--&lt;!&ndash;            <el-form-item prop="code">&ndash;&gt;-->
<!--&lt;!&ndash;              <el-row :gutter="10" style="width: 100%;">&ndash;&gt;-->
<!--&lt;!&ndash;                <el-col :span="17">&ndash;&gt;-->
<!--&lt;!&ndash;                  <el-input v-model="form.code" maxlength="6" type="text" placeholder="请输入验证码">&ndash;&gt;-->
<!--&lt;!&ndash;                    <template #prefix>&ndash;&gt;-->
<!--&lt;!&ndash;                      <el-icon><EditPen /></el-icon>&ndash;&gt;-->
<!--&lt;!&ndash;                    </template>&ndash;&gt;-->
<!--&lt;!&ndash;                  </el-input>&ndash;&gt;-->
<!--&lt;!&ndash;                </el-col>&ndash;&gt;-->
<!--&lt;!&ndash;                <el-col :span="5">&ndash;&gt;-->
<!--&lt;!&ndash;                  <el-button type="success" @click="validateEmail"&ndash;&gt;-->
<!--&lt;!&ndash;                             :disabled="!isEmailValid|| coldTime>0">&ndash;&gt;-->
<!--&lt;!&ndash;                    {{coldTime>0?'请稍后 '+coldTime+' 秒':'获取验证码'}}&ndash;&gt;-->
<!--&lt;!&ndash;                  </el-button>&ndash;&gt;-->
<!--&lt;!&ndash;                </el-col>&ndash;&gt;-->
<!--&lt;!&ndash;              </el-row>&ndash;&gt;-->
<!--&lt;!&ndash;            </el-form-item>&ndash;&gt;-->
<!--&lt;!&ndash;          </el-form>&ndash;&gt;-->
<!--&lt;!&ndash;        </div>&ndash;&gt;-->
<!--&lt;!&ndash;        <div style="margin-top: 70px">&ndash;&gt;-->
<!--&lt;!&ndash;          <el-button @click="startReset()" style="width: 270px;" type="danger">开始重置密码</el-button>&ndash;&gt;-->
<!--&lt;!&ndash;        </div>&ndash;&gt;-->
<!--&lt;!&ndash;      </div>&ndash;&gt;-->
<!--&lt;!&ndash;    </transition>&ndash;&gt;-->
<!--&lt;!&ndash;    <transition name="el-fade-in-liner" mode="out-in">&ndash;&gt;-->
<!--&lt;!&ndash;      <div style="text-align: center;margin: 0 20px;height: 100%" v-if="active===1">&ndash;&gt;-->
<!--&lt;!&ndash;        <div style="margin-top:80px">&ndash;&gt;-->
<!--&lt;!&ndash;          <div style="font-size: 25px;font-weight: bold">重置密码</div>&ndash;&gt;-->
<!--&lt;!&ndash;          <div style="font-size: 14px;color: grey">请填写您的新密码</div>&ndash;&gt;-->
<!--&lt;!&ndash;        </div>&ndash;&gt;-->
<!--&lt;!&ndash;        <div style="margin-top: 50px">&ndash;&gt;-->
<!--&lt;!&ndash;          <el-form :model="form" :rules="rules" @validate="onValidate" ref="formRef">&ndash;&gt;-->
<!--&lt;!&ndash;            <el-form-item prop="password">&ndash;&gt;-->
<!--&lt;!&ndash;              <el-input v-model="form.password" maxlength="16" type="password" placeholder="新密码">&ndash;&gt;-->
<!--&lt;!&ndash;                <template #prefix>&ndash;&gt;-->
<!--&lt;!&ndash;                  <el-icon><Lock /></el-icon>&ndash;&gt;-->
<!--&lt;!&ndash;                </template>&ndash;&gt;-->
<!--&lt;!&ndash;              </el-input>&ndash;&gt;-->
<!--&lt;!&ndash;            </el-form-item>&ndash;&gt;-->
<!--&lt;!&ndash;            <el-form-item prop="password_repeat">&ndash;&gt;-->
<!--&lt;!&ndash;              <el-input v-model="form.password_repeat" maxlength="16" type="password" placeholder="重复新密码">&ndash;&gt;-->
<!--&lt;!&ndash;                <template #prefix>&ndash;&gt;-->
<!--&lt;!&ndash;                  <el-icon><Lock /></el-icon>&ndash;&gt;-->
<!--&lt;!&ndash;                </template>&ndash;&gt;-->
<!--&lt;!&ndash;              </el-input>&ndash;&gt;-->
<!--&lt;!&ndash;            </el-form-item>&ndash;&gt;-->
<!--&lt;!&ndash;          </el-form>&ndash;&gt;-->
<!--&lt;!&ndash;        </div>&ndash;&gt;-->
<!--&lt;!&ndash;        <div style="margin-top: 70px">&ndash;&gt;-->
<!--&lt;!&ndash;          <el-button @click="doReset()" style="width: 270px;" type="danger">立即重置密码</el-button>&ndash;&gt;-->
<!--&lt;!&ndash;        </div>&ndash;&gt;-->
<!--&lt;!&ndash;      </div>&ndash;&gt;-->
<!--&lt;!&ndash;    </transition>&ndash;&gt;-->
<!--&lt;!&ndash;  </div>&ndash;&gt;-->
<!--&lt;!&ndash;</div>&ndash;&gt;-->
<!--&lt;!&ndash;</template>&ndash;&gt;-->

<!--&lt;!&ndash;<script setup>&ndash;&gt;-->
<!--&lt;!&ndash;import {reactive, ref} from "vue";&ndash;&gt;-->
<!--&lt;!&ndash;import {EditPen, Lock, Message} from "@element-plus/icons-vue";&ndash;&gt;-->
<!--&lt;!&ndash;import {post} from "@/net";&ndash;&gt;-->
<!--&lt;!&ndash;import {ElMessage} from "element-plus";&ndash;&gt;-->
<!--&lt;!&ndash;import router from "@/router";&ndash;&gt;-->

<!--&lt;!&ndash;const active = ref(0)&ndash;&gt;-->

<!--&lt;!&ndash;const form = reactive({&ndash;&gt;-->
<!--&lt;!&ndash;  email:'',&ndash;&gt;-->
<!--&lt;!&ndash;  code:'',&ndash;&gt;-->
<!--&lt;!&ndash;  password:'',&ndash;&gt;-->
<!--&lt;!&ndash;  password_repeat:''&ndash;&gt;-->
<!--&lt;!&ndash;})&ndash;&gt;-->

<!--&lt;!&ndash;const validatePassword = (rule,value,callback)=> {&ndash;&gt;-->
<!--&lt;!&ndash;  if (value === '') {&ndash;&gt;-->
<!--&lt;!&ndash;    callback(new Error('请再次输入密码'))&ndash;&gt;-->
<!--&lt;!&ndash;  } else if (value !== form.password) {&ndash;&gt;-->
<!--&lt;!&ndash;    callback(new Error('两次输入的密码不一致'))&ndash;&gt;-->
<!--&lt;!&ndash;  } else {&ndash;&gt;-->
<!--&lt;!&ndash;    callback()&ndash;&gt;-->
<!--&lt;!&ndash;  }&ndash;&gt;-->
<!--&lt;!&ndash;}&ndash;&gt;-->

<!--&lt;!&ndash;const rules = {&ndash;&gt;-->
<!--&lt;!&ndash;  email:[&ndash;&gt;-->
<!--&lt;!&ndash;    {required:true,message: '请输入电子邮件地址',trigger: 'blur'},&ndash;&gt;-->
<!--&lt;!&ndash;    {type:'email', message: '请输入合法的电子邮件地址',trigger:['blur','change']}&ndash;&gt;-->
<!--&lt;!&ndash;  ],&ndash;&gt;-->
<!--&lt;!&ndash;  code:[&ndash;&gt;-->
<!--&lt;!&ndash;    {required:true,message: '请输入获取的验证码',trigger: 'blur'},&ndash;&gt;-->
<!--&lt;!&ndash;  ],&ndash;&gt;-->
<!--&lt;!&ndash;  password:[&ndash;&gt;-->
<!--&lt;!&ndash;    {required:true,message: '请输入密码',trigger: 'blur'},&ndash;&gt;-->
<!--&lt;!&ndash;    {min:6,max:16,message:'密码长度必须在6-16个字符之间',trigger:['blur','change']},&ndash;&gt;-->
<!--&lt;!&ndash;  ],&ndash;&gt;-->
<!--&lt;!&ndash;  password_repeat:[&ndash;&gt;-->
<!--&lt;!&ndash;    { validator: validatePassword,trigger:['blur','change']},&ndash;&gt;-->
<!--&lt;!&ndash;  ],&ndash;&gt;-->
<!--&lt;!&ndash;}&ndash;&gt;-->

<!--&lt;!&ndash;const formRef = ref()&ndash;&gt;-->
<!--&lt;!&ndash;const isEmailValid = ref(false)&ndash;&gt;-->
<!--&lt;!&ndash;const coldTime = ref(0)&ndash;&gt;-->

<!--&lt;!&ndash;const onValidate=(prop,isValid)=>{&ndash;&gt;-->
<!--&lt;!&ndash;  if (prop === 'email')&ndash;&gt;-->
<!--&lt;!&ndash;    isEmailValid.value = isValid&ndash;&gt;-->
<!--&lt;!&ndash;}&ndash;&gt;-->

<!--&lt;!&ndash;const validateEmail = ()=>{&ndash;&gt;-->
<!--&lt;!&ndash;  coldTime.value=60&ndash;&gt;-->
<!--&lt;!&ndash;  post('/api/auth/valid-reset-email',{&ndash;&gt;-->
<!--&lt;!&ndash;    email: form.email&ndash;&gt;-->
<!--&lt;!&ndash;  },(message) => {&ndash;&gt;-->
<!--&lt;!&ndash;    const successMessage = message||"已发送验证邮件，请查收"&ndash;&gt;-->
<!--&lt;!&ndash;    ElMessage.success(successMessage)&ndash;&gt;-->
<!--&lt;!&ndash;    setInterval(()=>coldTime.value&#45;&#45;,1000)&ndash;&gt;-->
<!--&lt;!&ndash;  },(message) =>{&ndash;&gt;-->
<!--&lt;!&ndash;    ElMessage.warning(message)&ndash;&gt;-->
<!--&lt;!&ndash;    coldTime.value = 0&ndash;&gt;-->
<!--&lt;!&ndash;  })&ndash;&gt;-->
<!--&lt;!&ndash;}&ndash;&gt;-->

<!--&lt;!&ndash;const startReset = () => {&ndash;&gt;-->
<!--&lt;!&ndash;  formRef.value.validate((isValid) =>{&ndash;&gt;-->
<!--&lt;!&ndash;    if(isValid){&ndash;&gt;-->
<!--&lt;!&ndash;      post('/api/auth/start-reset', {&ndash;&gt;-->
<!--&lt;!&ndash;        email: form.email,&ndash;&gt;-->
<!--&lt;!&ndash;        code: form.code&ndash;&gt;-->
<!--&lt;!&ndash;      },() => {&ndash;&gt;-->
<!--&lt;!&ndash;        active.value++&ndash;&gt;-->
<!--&lt;!&ndash;      })&ndash;&gt;-->
<!--&lt;!&ndash;    } else {&ndash;&gt;-->
<!--&lt;!&ndash;      ElMessage.warning('请填写电子邮件地址和验证码')&ndash;&gt;-->
<!--&lt;!&ndash;    }&ndash;&gt;-->
<!--&lt;!&ndash;  })&ndash;&gt;-->
<!--&lt;!&ndash;}&ndash;&gt;-->

<!--&lt;!&ndash;const doReset = () =>{&ndash;&gt;-->
<!--&lt;!&ndash;  formRef.value.validate((isValid) =>{&ndash;&gt;-->
<!--&lt;!&ndash;    if(isValid){&ndash;&gt;-->
<!--&lt;!&ndash;      post('/api/auth/do-reset', {&ndash;&gt;-->
<!--&lt;!&ndash;        password: form.password&ndash;&gt;-->
<!--&lt;!&ndash;      },() => {&ndash;&gt;-->
<!--&lt;!&ndash;        ElMessage.success('密码重置成功')&ndash;&gt;-->
<!--&lt;!&ndash;        router.push('/')&ndash;&gt;-->
<!--&lt;!&ndash;      })&ndash;&gt;-->
<!--&lt;!&ndash;    } else {&ndash;&gt;-->
<!--&lt;!&ndash;      ElMessage.warning('请填写新的密码')&ndash;&gt;-->
<!--&lt;!&ndash;    }&ndash;&gt;-->
<!--&lt;!&ndash;  })&ndash;&gt;-->
<!--&lt;!&ndash;}&ndash;&gt;-->

<!--&lt;!&ndash;</script>&ndash;&gt;-->

<!--&lt;!&ndash;<style scoped>&ndash;&gt;-->

<!--&lt;!&ndash;</style>&ndash;&gt;-->

<!--<template>-->
<!--  <div>-->
<!--    <div style="margin: 30px 20px">-->
<!--      <el-steps :active="active" finish-status="success" align-center>-->
<!--        <el-step title="验证电子邮件" />-->
<!--        <el-step title="重新设定密码" />-->
<!--      </el-steps>-->
<!--    </div>-->
<!--    <transition name="el-fade-in-linear" mode="out-in">-->
<!--      <div style="text-align: center;margin: 0 20px;height: 100%" v-if="active === 0">-->
<!--        <div style="margin-top: 80px">-->
<!--          <div style="font-size: 25px;font-weight: bold">重置密码</div>-->
<!--          <div style="font-size: 14px;color: grey">请输入需要重置密码的电子邮件地址</div>-->
<!--        </div>-->
<!--        <div style="margin-top: 50px">-->
<!--          <el-form :model="form" :rules="rules" @validate="onValidate" ref="formRef">-->
<!--            <el-form-item prop="email">-->
<!--              <el-input v-model="form.email" type="email" placeholder="电子邮件地址">-->
<!--                <template #prefix>-->
<!--                  <el-icon><Message /></el-icon>-->
<!--                </template>-->
<!--              </el-input>-->
<!--            </el-form-item>-->
<!--            <el-form-item prop="code">-->
<!--              <el-row :gutter="10" style="width: 100%">-->
<!--                <el-col :span="17">-->
<!--                  <el-input v-model="form.code" :maxlength="6" type="text" placeholder="请输入验证码">-->
<!--                    <template #prefix>-->
<!--                      <el-icon><EditPen /></el-icon>-->
<!--                    </template>-->
<!--                  </el-input>-->
<!--                </el-col>-->
<!--                <el-col :span="5">-->
<!--                  <el-button type="success" @click="validateEmail"-->
<!--                             :disabled="!isEmailValid || coldTime > 0">-->
<!--                    {{coldTime > 0 ? '请稍后 ' + coldTime + ' 秒' : '获取验证码'}}-->
<!--                  </el-button>-->
<!--                </el-col>-->
<!--              </el-row>-->
<!--            </el-form-item>-->
<!--          </el-form>-->
<!--        </div>-->
<!--        <div style="margin-top: 70px">-->
<!--          <el-button @click="startReset()" style="width: 270px;" type="danger" plain>开始重置密码</el-button>-->
<!--        </div>-->
<!--      </div>-->
<!--    </transition>-->
<!--    <transition name="el-fade-in-linear" mode="out-in">-->
<!--      <div style="text-align: center;margin: 0 20px;height: 100%" v-if="active === 1">-->
<!--        <div style="margin-top: 80px">-->
<!--          <div style="font-size: 25px;font-weight: bold">重置密码</div>-->
<!--          <div style="font-size: 14px;color: grey">请填写您的新密码，务必牢记，防止丢失</div>-->
<!--        </div>-->
<!--        <div style="margin-top: 50px">-->
<!--          <el-form :model="form" :rules="rules" @validate="onValidate" ref="formRef">-->
<!--            <el-form-item prop="password">-->
<!--              <el-input v-model="form.password" :maxlength="16" type="password" placeholder="新密码">-->
<!--                <template #prefix>-->
<!--                  <el-icon><Lock /></el-icon>-->
<!--                </template>-->
<!--              </el-input>-->
<!--            </el-form-item>-->
<!--            <el-form-item prop="password_repeat">-->
<!--              <el-input v-model="form.password_repeat" :maxlength="16" type="password" placeholder="重复新密码">-->
<!--                <template #prefix>-->
<!--                  <el-icon><Lock /></el-icon>-->
<!--                </template>-->
<!--              </el-input>-->
<!--            </el-form-item>-->
<!--          </el-form>-->
<!--        </div>-->
<!--        <div style="margin-top: 70px">-->
<!--          <el-button @click="doReset()" style="width: 270px;" type="danger" plain>立即重置密码</el-button>-->
<!--        </div>-->
<!--      </div>-->
<!--    </transition>-->
<!--  </div>-->
<!--</template>-->

<!--<script setup>-->
<!--import {reactive, ref} from "vue";-->
<!--import {EditPen, Lock, Message} from "@element-plus/icons-vue";-->
<!--import {post} from "@/net";-->
<!--import {ElMessage} from "element-plus";-->
<!--import router from "@/router";-->

<!--const active = ref(0)-->

<!--const form = reactive({-->
<!--  email: '',-->
<!--  code: '',-->
<!--  password: '',-->
<!--  password_repeat: '',-->
<!--})-->

<!--const validatePassword = (rule, value, callback) => {-->
<!--  if (value === '') {-->
<!--    callback(new Error('请再次输入密码'))-->
<!--  } else if (value !== form.password) {-->
<!--    callback(new Error("两次输入的密码不一致"))-->
<!--  } else {-->
<!--    callback()-->
<!--  }-->
<!--}-->

<!--const rules = {-->
<!--  email: [-->
<!--    { required: true, message: '请输入邮件地址', trigger: 'blur' },-->
<!--    {type: 'email', message: '请输入合法的电子邮件地址', trigger: ['blur', 'change']}-->
<!--  ],-->
<!--  code: [-->
<!--    { required: true, message: '请输入获取的验证码', trigger: 'blur' },-->
<!--  ],-->
<!--  password: [-->
<!--    { required: true, message: '请输入密码', trigger: 'blur' },-->
<!--    { min: 6, max: 16, message: '密码的长度必须在6-16个字符之间', trigger: ['blur', 'change'] }-->
<!--  ],-->
<!--  password_repeat: [-->
<!--    { validator: validatePassword, trigger: ['blur', 'change'] },-->
<!--  ],-->
<!--}-->

<!--const formRef = ref()-->
<!--const isEmailValid = ref(false)-->
<!--const coldTime = ref(0)-->

<!--const onValidate = (prop, isValid) => {-->
<!--  if(prop === 'email')-->
<!--    isEmailValid.value = isValid-->
<!--}-->

<!--const validateEmail = () => {-->
<!--  coldTime.value = 60-->
<!--  post('/api/auth/valid-reset-email', {-->
<!--    email: form.email-->
<!--  }, (message) => {-->
<!--    ElMessage.success(message)-->
<!--    setInterval(() => coldTime.value&#45;&#45;, 1000)-->
<!--  }, (message) => {-->
<!--    ElMessage.warning(message)-->
<!--    coldTime.value = 0-->
<!--  })-->
<!--}-->

<!--const startReset = () => {-->
<!--  formRef.value.validate((isValid) => {-->
<!--    if(isValid) {-->
<!--      post('/api/auth/start-reset', {-->
<!--        email: form.email,-->
<!--        code: form.code-->
<!--      }, () => {-->
<!--        active.value++-->
<!--      })-->
<!--    } else {-->
<!--      ElMessage.warning('请填写电子邮件地址和验证码')-->
<!--    }-->
<!--  })-->
<!--}-->

<!--const doReset = () => {-->
<!--  formRef.value.validate((isValid) => {-->
<!--    if(isValid) {-->
<!--      post('/api/auth/do-reset', {-->
<!--        password: form.password-->
<!--      }, (message) => {-->
<!--        ElMessage.success(message)-->
<!--        router.push('/')-->
<!--      })-->
<!--    } else {-->
<!--      ElMessage.warning('请填写新的密码')-->
<!--    }-->
<!--  })-->
<!--}-->

<!--</script>-->

<!--<style scoped>-->

<!--</style>-->
<template>
  <div>
    <div style="margin: 30px 20px">
      <el-steps :active="active" finish-status="success" align-center>
        <el-step title="验证电子邮件" />
        <el-step title="重新设定密码" />
      </el-steps>
    </div>
    <transition name="el-fade-in-linear" mode="out-in">
      <div style="text-align: center;margin: 0 20px;height: 100%" v-if="active === 0">
        <div style="margin-top: 80px">
          <div style="font-size: 25px;font-weight: bold">重置密码</div>
          <div style="font-size: 14px;color: grey">请输入需要重置密码的电子邮件地址</div>
        </div>
        <div style="margin-top: 50px">
          <el-form :model="form" :rules="rules" @validate="onValidate" ref="formRef">
            <el-form-item prop="email">
              <el-input v-model="form.email" type="email" placeholder="电子邮件地址">
                <template #prefix>
                  <el-icon><Message /></el-icon>
                </template>
              </el-input>
            </el-form-item>
            <el-form-item prop="code">
              <el-row :gutter="10" style="width: 100%">
                <el-col :span="17">
                  <el-input v-model="form.code" :maxlength="6" type="text" placeholder="请输入验证码">
                    <template #prefix>
                      <el-icon><EditPen /></el-icon>
                    </template>
                  </el-input>
                </el-col>
                <el-col :span="5">
                  <el-button type="success" @click="validateEmail"
                             :disabled="!isEmailValid || coldTime > 0">
                    {{coldTime > 0 ? '请稍后 ' + coldTime + ' 秒' : '获取验证码'}}
                  </el-button>
                </el-col>
              </el-row>
            </el-form-item>
          </el-form>
        </div>
        <div style="margin-top: 70px">
          <el-button @click="startReset()" style="width: 270px;" type="danger" plain>开始重置密码</el-button>
        </div>
      </div>
    </transition>
    <transition name="el-fade-in-linear" mode="out-in">
      <div style="text-align: center;margin: 0 20px;height: 100%" v-if="active === 1">
        <div style="margin-top: 80px">
          <div style="font-size: 25px;font-weight: bold">重置密码</div>
          <div style="font-size: 14px;color: grey">请填写您的新密码，务必牢记，防止丢失</div>
        </div>
        <div style="margin-top: 50px">
          <el-form :model="form" :rules="rules" @validate="onValidate" ref="formRef">
            <el-form-item prop="password">
              <el-input v-model="form.password" :maxlength="16" type="password" placeholder="新密码">
                <template #prefix>
                  <el-icon><Lock /></el-icon>
                </template>
              </el-input>
            </el-form-item>
            <el-form-item prop="password_repeat">
              <el-input v-model="form.password_repeat" :maxlength="16" type="password" placeholder="重复新密码">
                <template #prefix>
                  <el-icon><Lock /></el-icon>
                </template>
              </el-input>
            </el-form-item>
          </el-form>
        </div>
        <div style="margin-top: 70px">
          <el-button @click="doReset()" style="width: 270px;" type="danger" plain>立即重置密码</el-button>
        </div>
      </div>
    </transition>
  </div>
</template>

<script setup>
import {reactive, ref} from "vue";
import {EditPen, Lock, Message} from "@element-plus/icons-vue";
import {post} from "@/net";
import {ElMessage} from "element-plus";
import router from "@/router";

const active = ref(0)

const form = reactive({
  email: '',
  code: '',
  password: '',
  password_repeat: '',
})

const validatePassword = (rule, value, callback) => {
  if (value === '') {
    callback(new Error('请再次输入密码'))
  } else if (value !== form.password) {
    callback(new Error("两次输入的密码不一致"))
  } else {
    callback()
  }
}

const rules = {
  email: [
    { required: true, message: '请输入邮件地址', trigger: 'blur' },
    {type: 'email', message: '请输入合法的电子邮件地址', trigger: ['blur', 'change']}
  ],
  code: [
    { required: true, message: '请输入获取的验证码', trigger: 'blur' },
  ],
  password: [
    { required: true, message: '请输入密码', trigger: 'blur' },
    { min: 6, max: 16, message: '密码的长度必须在6-16个字符之间', trigger: ['blur', 'change'] }
  ],
  password_repeat: [
    { validator: validatePassword, trigger: ['blur', 'change'] },
  ],
}

const formRef = ref()
const isEmailValid = ref(false)
const coldTime = ref(0)

const onValidate = (prop, isValid) => {
  if(prop === 'email')
    isEmailValid.value = isValid
}

const validateEmail = () => {
  coldTime.value = 60
  post('/api/auth/valid-reset-email', {
    email: form.email
  }, (message) => {
    ElMessage.success(message)
    setInterval(() => coldTime.value--, 1000)
  }, (message) => {
    ElMessage.warning(message)
    coldTime.value = 0
  })
}

const startReset = () => {
  formRef.value.validate((isValid) => {
    if(isValid) {
      post('/api/auth/start-reset', {
        email: form.email,
        code: form.code
      }, () => {
        active.value++
      })
    } else {
      ElMessage.warning('请填写电子邮件地址和验证码')
    }
  })
}

const doReset = () => {
  formRef.value.validate((isValid) => {
    if(isValid) {
      post('/api/auth/do-reset', {
        password: form.password
      }, (message) => {
        ElMessage.success(message)
        router.push('/')
      })
    } else {
      ElMessage.warning('请填写新的密码')
    }
  })
}

</script>

<style scoped>

</style>