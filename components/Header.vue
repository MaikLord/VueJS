<template>
  <a-layout id="components-layout-demo-custom-trigger">
    <a-layout-sider v-model="collapsed" :trigger="null" collapsible>
      <div class="logo">
        <img src="../static/Me.jpg" />
      </div>
      <a-menu theme="light" mode="inline" :default-selected-keys="['1']">
        <a-menu-item key="1">
          <a-icon type="user" />
          <span>User</span>
        </a-menu-item>
        <a-menu-item key="2">
          <a-icon type="check" />
          <span>To Do</span>
        </a-menu-item>
        <a-menu-item key="3">
          <a-icon class="exit" type="close" />
          <span>Exit</span>
        </a-menu-item>
      </a-menu>
    </a-layout-sider>
    <a-layout>
      <a-layout-header style="background: #1890ff; padding: 0">
        <a-icon
          class="trigger"
          :type="collapsed ? 'caret-right' : 'caret-left'"
          @click="() => (collapsed = !collapsed)"
        />
      </a-layout-header>
      <a-layout-content
        :style="{
          margin: '24px 16px',
          padding: '24px',
          background: '#fff',
          minHeight: '280px',
        }"
      >
        Login
        <a-form-model
          layout="inline"
          :model="formInline"
          @submit="handleSubmit"
          @submit.native.prevent
        >
          <a-form-model-item>
            <a-input v-model="formInline.user" placeholder="Username">
              <a-icon
                slot="suffix"
                type="user"
                style="color: rgba(0, 0, 0, 0.5)"
              />
            </a-input>
          </a-form-model-item>
          <a-form-model-item>
            <a-input
              v-model="formInline.password"
              type="password"
              placeholder="Password"
            >
              <a-icon
                slot="suffix"
                type="lock"
                color="red"
                style="color: rgba(0, 0, 0, 0.5)"
              />
            </a-input>
          </a-form-model-item>
          <a-form-model-item>
            <a-button
              type="primary"
              html-type="submit"
              :disabled="formInline.user === '' || formInline.password === ''"
            >
              Log in
            </a-button>
          </a-form-model-item>
        </a-form-model>
      </a-layout-content>
    </a-layout>
  </a-layout>
</template>

<script>
export default {
  data() {
    return {
      collapsed: false,
      formInline: {
        user: "",
        password: "",
      },
      methods: {
        handleSubmit(e) {
          console.log(this.formInline);
        },
      },
    };
  },
};
</script>

<style>
#components-layout-demo-custom-trigger .trigger {
  font-size: 18px;
  line-height: 64px;
  padding: 0 24px;
  cursor: pointer;
  transition: color 0.3s;
}
.ant-layout-sider-children {
  height: 100vh;
}

#components-layout-demo-custom-trigger .trigger:hover {
  color: #202020;
}

#components-layout-demo-custom-trigger .logo {
  height: fit-content;
  background: #202020;
  margin: 15px;
}
img {
  width: 100%;
  height: fit-content -10px;
  border-radius: 50%;
}
.logo {
  border-radius: 50%;
  min-height: fit-content;
}
.ant-layout-sider-children {
  background-color: #fff;
}
.ul {
  background-color: #101010;
}
.anticon-menu-unfold {
  color: #fff;
}
.anticon-menu-fold {
  color: #fff;
}
.exit {
  color: red;
}
.anticon-caret-right {
  color: white;
}
.anticon-caret-left {
  color: white;
}
</style>