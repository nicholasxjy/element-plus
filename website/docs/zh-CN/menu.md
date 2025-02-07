## NavMenu 导航菜单

为网站提供导航功能的菜单。

### 顶栏

适用广泛的基础用法。

:::demo 导航菜单默认为垂直模式，通过`mode`属性可以使导航菜单变更为水平模式。另外，在菜单中通过`sub-menu`组件可以生成二级菜单。Menu 还提供了`background-color`、`text-color`和`active-text-color`，分别用于设置菜单的背景色、菜单的文字颜色和当前激活菜单的文字颜色。

```html
<el-menu :default-active="activeIndex" class="el-menu-demo" mode="horizontal" @select="handleSelect">
  <el-menu-item index="1">处理中心</el-menu-item>
  <el-sub-menu index="2">
    <template #title>我的工作台</template>
    <el-menu-item index="2-1">选项1</el-menu-item>
    <el-menu-item index="2-2">选项2</el-menu-item>
    <el-menu-item index="2-3">选项3</el-menu-item>
    <el-sub-menu index="2-4">
      <template #title>选项4</template>
      <el-menu-item index="2-4-1">选项1</el-menu-item>
      <el-menu-item index="2-4-2">选项2</el-menu-item>
      <el-menu-item index="2-4-3">选项3</el-menu-item>
    </el-sub-menu>
  </el-sub-menu>
  <el-menu-item index="3" disabled>消息中心</el-menu-item>
  <el-menu-item index="4"><a href="https://www.ele.me" target="_blank">订单管理</a></el-menu-item>
</el-menu>
<div class="line"></div>
<el-menu
  :default-active="activeIndex2"
  class="el-menu-demo"
  mode="horizontal"
  @select="handleSelect"
  background-color="#545c64"
  text-color="#fff"
  active-text-color="#ffd04b">
  <el-menu-item index="1">处理中心</el-menu-item>
  <el-sub-menu index="2">
    <template #title>我的工作台</template>
    <el-menu-item index="2-1">选项1</el-menu-item>
    <el-menu-item index="2-2">选项2</el-menu-item>
    <el-menu-item index="2-3">选项3</el-menu-item>
    <el-sub-menu index="2-4">
      <template #title>选项4</template>
      <el-menu-item index="2-4-1">选项1</el-menu-item>
      <el-menu-item index="2-4-2">选项2</el-menu-item>
      <el-menu-item index="2-4-3">选项3</el-menu-item>
    </el-sub-menu>
  </el-sub-menu>
  <el-menu-item index="3" disabled>消息中心</el-menu-item>
  <el-menu-item index="4"><a href="https://www.ele.me" target="_blank">订单管理</a></el-menu-item>
</el-menu>

<script>
  export default {
    data() {
      return {
        activeIndex: '1',
        activeIndex2: '1'
      };
    },
    methods: {
      handleSelect(key, keyPath) {
        console.log(key, keyPath);
      }
    }
  }
</script>
<!--
<setup>

  import { defineComponent, ref } from 'vue';

  export default defineComponent({
    setup() {
      const activeIndex = ref('1');
      const activeIndex2 = ref('1');
      const handleSelect = (key, keyPath) => {
        console.log(key, keyPath);
      };
      return {
        activeIndex,
        activeIndex2,
        handleSelect,
      };
    },
  });

</setup>
-->
```
:::

### 侧栏

垂直菜单，可内嵌子菜单。

:::demo 通过`el-menu-item-group`组件可以实现菜单进行分组，分组名可以通过`title`属性直接设定，也可以通过具名 slot 来设定。
```html
<el-row class="tac">
  <el-col :span="12">
    <h5>默认颜色</h5>
    <el-menu
      default-active="2"
      class="el-menu-vertical-demo"
      @open="handleOpen"
      @close="handleClose">
      <el-sub-menu index="1">
        <template #title>
          <i class="el-icon-location"></i>
          <span>导航一</span>
        </template>
        <el-menu-item-group>
          <template #title>分组一</template>
          <el-menu-item index="1-1">选项1</el-menu-item>
          <el-menu-item index="1-2">选项2</el-menu-item>
        </el-menu-item-group>
        <el-menu-item-group title="分组2">
          <el-menu-item index="1-3">选项3</el-menu-item>
        </el-menu-item-group>
        <el-sub-menu index="1-4">
          <template #title>选项4</template>
          <el-menu-item index="1-4-1">选项1</el-menu-item>
        </el-sub-menu>
      </el-sub-menu>
      <el-menu-item index="2">
        <i class="el-icon-menu"></i>
        <template #title>导航二</template>
      </el-menu-item>
      <el-menu-item index="3" disabled>
        <i class="el-icon-document"></i>
        <template #title>导航三</template>
      </el-menu-item>
      <el-menu-item index="4">
        <i class="el-icon-setting"></i>
        <template #title>导航四</template>
      </el-menu-item>
    </el-menu>
  </el-col>
  <el-col :span="12">
    <h5>自定义颜色</h5>
    <el-menu
      :uniqueOpened="true"
      default-active="2"
      class="el-menu-vertical-demo"
      @open="handleOpen"
      @close="handleClose"
      background-color="#545c64"
      text-color="#fff"
      active-text-color="#ffd04b">
      <el-sub-menu index="1">
        <template #title>
          <i class="el-icon-location"></i>
          <span>导航一</span>
        </template>
        <el-menu-item-group>
          <template #title>分组一</template>
          <el-menu-item index="1-1">选项1</el-menu-item>
          <el-menu-item index="1-2">选项2</el-menu-item>
        </el-menu-item-group>
        <el-menu-item-group title="分组2">
          <el-menu-item index="1-3">选项3</el-menu-item>
        </el-menu-item-group>
        <el-sub-menu index="1-4">
          <template #title>选项4</template>
          <el-menu-item index="1-4-1">选项1</el-menu-item>
        </el-sub-menu>
      </el-sub-menu>
      <el-menu-item index="2">
        <i class="el-icon-menu"></i>
        <template #title>导航二</template>
      </el-menu-item>
      <el-menu-item index="3" disabled>
        <i class="el-icon-document"></i>
        <template #title>导航三</template>
      </el-menu-item>
      <el-menu-item index="4">
        <i class="el-icon-setting"></i>
        <template #title>导航四</template>
      </el-menu-item>
      <el-sub-menu index="5">
        <template #title>
          <i class="el-icon-location"></i>
          <span>导航一</span>
        </template>
        <el-menu-item-group>
          <template #title>分组一</template>
          <el-menu-item index="5-1">选项1</el-menu-item>
          <el-menu-item index="5-2">选项2</el-menu-item>
        </el-menu-item-group>
        <el-menu-item-group title="分组2">
          <el-menu-item index="5-3">选项3</el-menu-item>
        </el-menu-item-group>
      </el-sub-menu>
    </el-menu>
  </el-col>
</el-row>

<script>
  export default {
    methods: {
      handleOpen(key, keyPath) {
        console.log(key, keyPath);
      },
      handleClose(key, keyPath) {
        console.log(key, keyPath);
      }
    }
  }
</script>
<!--
<setup>

  import { defineComponent } from 'vue';

  export default defineComponent({
    setup() {
      const handleOpen = (key, keyPath) => {
        console.log(key, keyPath);
      };
      const handleClose = (key, keyPath) => {
        console.log(key, keyPath);
      };
      return {
        handleOpen,
        handleClose,
      };
    },
  });

</setup>
-->
```
:::

### 折叠

:::demo
```html
<el-radio-group v-model="isCollapse" style="margin-bottom: 20px;">
  <el-radio-button :label="false">展开</el-radio-button>
  <el-radio-button :label="true">收起</el-radio-button>
</el-radio-group>
<el-menu default-active="1-4-1" class="el-menu-vertical-demo" @open="handleOpen" @close="handleClose" :collapse="isCollapse">
  <el-sub-menu index="1">
    <template #title>
      <i class="el-icon-location"></i>
      <span>导航一</span>
    </template>
    <el-menu-item-group>
      <template #title>分组一</template>
      <el-menu-item index="1-1">选项1</el-menu-item>
      <el-menu-item index="1-2">选项2</el-menu-item>
    </el-menu-item-group>
    <el-menu-item-group title="分组2">
      <el-menu-item index="1-3">选项3</el-menu-item>
    </el-menu-item-group>
    <el-sub-menu index="1-4">
      <template #title>选项4</template>
      <el-menu-item index="1-4-1">选项1</el-menu-item>
    </el-sub-menu>
  </el-sub-menu>
  <el-menu-item index="2">
    <i class="el-icon-menu"></i>
    <template #title>导航二</template>
  </el-menu-item>
  <el-menu-item index="3" disabled>
    <i class="el-icon-document"></i>
    <template #title>导航三</template>
  </el-menu-item>
  <el-menu-item index="4">
    <i class="el-icon-setting"></i>
    <template #title>导航四</template>
  </el-menu-item>
</el-menu>

<style>
  .el-menu-vertical-demo:not(.el-menu--collapse) {
    width: 200px;
    min-height: 400px;
  }
</style>

<script>
  export default {
    data() {
      return {
        isCollapse: true
      };
    },
    methods: {
      handleOpen(key, keyPath) {
        console.log(key, keyPath);
      },
      handleClose(key, keyPath) {
        console.log(key, keyPath);
      }
    }
  }
</script>
<!--
<setup>

  import { defineComponent, ref } from 'vue';

  export default defineComponent({
    setup() {
      const isCollapse = ref(true);
      const handleOpen = (key, keyPath) => {
        console.log(key, keyPath);
      };
      const handleClose = (key, keyPath) => {
        console.log(key, keyPath);
      };
      return {
        isCollapse,
        handleOpen,
        handleClose,
      };
    },
  });

</setup>
-->
```
:::

### Menu Attribute
| 参数                | 说明                                                                                | 类型    | 可选值                | 默认值   |
| ------------------- | ----------------------------------------------------------------------------------- | ------- | --------------------- | -------- |
| mode                | 模式                                                                                | string  | horizontal / vertical | vertical |
| collapse            | 是否水平折叠收起菜单（仅在 mode 为 vertical 时可用）                                | boolean | —                     | false    |
| background-color    | 菜单的背景色（仅支持 hex 格式）                                                     | string  | —                     | #ffffff  |
| text-color          | 菜单的文字颜色（仅支持 hex 格式）                                                   | string  | —                     | #303133  |
| active-text-color   | 当前激活菜单的文字颜色（仅支持 hex 格式）                                           | string  | —                     | #409EFF  |
| default-active      | 当前激活菜单的 index                                                                | string  | —                     | —        |
| default-openeds     | 当前打开的 sub-menu 的 index 的数组                                                 | Array   | —                     | —        |
| unique-opened       | 是否只保持一个子菜单的展开                                                          | boolean | —                     | false    |
| menu-trigger        | 子菜单打开的触发方式(只在 mode 为 horizontal 时有效)                                | string  | hover / click         | hover    |
| router              | 是否使用 vue-router 的模式，启用该模式会在激活导航时以 index 作为 path 进行路由跳转 | boolean | —                     | false    |
| collapse-transition | 是否开启折叠动画                                                                    | boolean | —                     | true     |

### Menu Methods
| 方法名称 | 说明                | 参数                                |
| -------- | ------------------- | ----------------------------------- |
| open     | 展开指定的 sub-menu | index: 需要打开的 sub-menu 的 index |
| close    | 收起指定的 sub-menu | index: 需要收起的 sub-menu 的 index |

### Menu Events
| 事件名称 | 说明                | 回调参数                                                                   |
| -------- | ------------------- | -------------------------------------------------------------------------- |
| select   | 菜单激活回调        | index: 选中菜单项的 index, indexPath: 选中菜单项的 index path, item: 选中菜单项, routeResult: vue-router 的返回值（如果 router 为 true）              |
| open     | sub-menu 展开的回调 | index: 打开的 sub-menu 的 index, indexPath: 打开的 sub-menu 的 index path |
| close    | sub-menu 收起的回调 | index: 收起的 sub-menu 的 index, indexPath: 收起的 sub-menu 的 index path |

### SubMenu Attribute
| 参数                  | 说明                                                                     | 类型        | 可选值 | 默认值                                 |
| --------------------- | ------------------------------------------------------------------------ | ----------- | ------ | -------------------------------------- |
| index                 | 唯一标志                                                                 | string/null | —      | null                                   |
| popper-class          | 弹出菜单的自定义类名                                                     | string      | —      | —                                      |
| show-timeout          | 展开 sub-menu 的延时                                                     | number      | —      | 300                                    |
| hide-timeout          | 收起 sub-menu 的延时                                                     | number      | —      | 300                                    |
| disabled              | 是否禁用                                                                 | boolean     | —      | false                                  |
| popper-append-to-body | 是否将弹出菜单插入至 body 元素。在菜单的定位出现问题时，可尝试修改该属性 | boolean     | —      | 一级子菜单：true / 非一级子菜单：false |

### Menu-Item Attribute
| 参数     | 说明                | 类型    | 可选值 | 默认值 |
| -------- | ------------------- | ------- | ------ | ------ |
| index    | 唯一标志            | string  | —      | —      |
| route    | Vue Router 路径对象 | Object  | —      | —      |
| disabled | 是否禁用            | boolean | —      | false  |

### Menu-Group Attribute
| 参数  | 说明     | 类型   | 可选值 | 默认值 |
| ----- | -------- | ------ | ------ | ------ |
| title | 分组标题 | string | —      | —      |
