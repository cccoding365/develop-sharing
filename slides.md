---
# You can also start simply with 'default'
theme: default
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://cover.sli.dev
# some information about your slides (markdown enabled)
title: 平台与业务开发的融合
titleTemplate: "%s - DoubledConG"
info: false
# apply unocss classes to the current slide
class: text-center
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# https://sli.dev/guide/drawing
drawings:
    persist: false
# slide transition: https://sli.dev/guide/animations#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/guide/syntax#mdc-syntax
mdc: true
---

# 平台基建与业务开发的融合

了解两种开发领域，提升技术与业务能力

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-5 py-3 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    <carbon:UserAvatarFilledAlt class="inline mr-1"/>研发四部 何聪聪
  </span>
</div>

---

# 引言：平台基础设施是什么

支撑开发和运行的基础服务和工具的集合，是构建和运行业务应用的基石，为业务开发提供必要的环境和能力。

<div class="h-90 flex gap-5">
  <div class="flex flex-col justify-between">
    <v-clicks>
      <block v-motion :initial="{ y: 100 }" :enter="{ y: 0 }" v-mark="{ at: [7,11], type: 'circle' }"><img src="/Vigilante.svg" />服务抽象化</block>
      <block v-motion :initial="{ y: 100 }" :enter="{ y: 0 }"><img src="/Wind Energy.svg" />自动化工具</block>
      <block v-motion :initial="{ y: 100 }" :enter="{ y: 0 }"><img src="/Smart TV.svg" />资源管理</block>
      <block v-motion :initial="{ y: 100 }" :enter="{ y: 0 }"><img src="/Smart Care.svg" />安全性</block>
      <block v-motion :initial="{ y: 100 }" :enter="{ y: 0 }"><img src="/Environmental Monitoring.svg" />监控和日志</block>
      <block v-motion :initial="{ y: 100 }" :enter="{ y: 0 }"><img src="/Processing Power.svg" />可扩展性</block>
      <block v-motion :initial="{ y: 100 }" :enter="{ y: 0 }"><img src="/Satellite Technology.svg" />高可用性</block>
    </v-clicks>
  </div>

  <div v-click="[7,11]" class="flex-grow">

```js{1-9|11-26|28-62|64-76}{maxHeight:'360px'}
// 引入 axios 库
import axios from "axios";

// 创建 axios 实例
const http = axios.create({
	baseURL: "https://api.example.com/",
	timeout: 1000,
	headers: { "Content-Type": "application/json" },
});

// 请求拦截器
http.interceptors.request.use(
	config => {
		// 在发送请求之前做些什么
		console.log("请求发送之前，配置请求信息");
		const token = localStorage.getItem("token");
		if (token) {
			config.headers.Authorization = `Bearer ${token}`;
		}
		return config;
	},
	error => {
		// 对请求错误做些什么
		return Promise.reject(error);
	},
);

// 响应拦截器
http.interceptors.response.use(
	response => {
		// 2xx 范围内的状态码都会触发该函数
		console.log("请求响应成功，处理响应数据");
		return response;
	},
	error => {
		// 超出 2xx 范围的状态码都会触发该函数
		console.log("请求响应失败，处理错误");
		if (error.response) {
			// 服务器端返回错误状态码
			console.error(error.response.status, error.response.data);
			// 可以根据不同的HTTP状态码进行不同的错误处理
			switch (error.response.status) {
				case 401:
					// 处理未授权
					break;
				case 403:
					// 处理禁止访问
					break;
				case 404:
					// 处理未找到
					break;
				case 500:
					// 处理服务器内部错误
					break;
				default:
					// 其他错误处理
					break;
			}
		}
		return Promise.reject(error);
	},
);

// 使用封装的 http 实例发送 GET 请求
http.get("/users").then(response => {
	console.log("GET 请求成功，返回数据：", response.data);
}).catch(error => {
	console.error("GET 请求失败：", error);
});

// 使用封装的 http 实例发送 POST 请求
http.post("/users", { name: "John Doe", email: "john@example.com" }).then(response => {
	console.log("POST 请求成功，返回数据：", response.data);
}).catch(error => {
	console.error("POST 请求失败：", error);
});
```

  </div>

</div>

<style>
  block {
    @apply py-2
  }
  img {
    @apply h-7 inline mr-1 
  }
</style>

---

# 为什么需要建设平台基础设施

提供稳定、可靠、安全的环境，帮助开发者专注于业务逻辑的实现，加速产品从概念到市场的转化过程。

<div class="flex gap-3">
  <ol class="flex flex-col justify-between">
    <v-clicks>
      <li v-motion :initial="{ y: 100 }" :enter="{ y: 0 }">提高开发效率</li>
      <li v-motion :initial="{ y: 100 }" :enter="{ y: 0 }">降低技术门槛</li>
      <li v-motion :initial="{ y: 100 }" :enter="{ y: 0 }">促进团队协作</li>
      <li v-motion :initial="{ y: 100 }" :enter="{ y: 0 }">加快迭代速度</li>
      <li v-motion :initial="{ y: 100 }" :enter="{ y: 0 }">增强系统可靠性</li>
      <li v-motion :initial="{ y: 100 }" :enter="{ y: 0 }">保障数据安全</li>
      <li v-motion :initial="{ y: 100 }" :enter="{ y: 0 }">支持业务创新</li>
      <li v-motion :initial="{ y: 100 }" :enter="{ y: 0 }">优化用户体验</li>
    </v-clicks>
  </ol>

  <div class="h-90 flex-grow flex justify-center items-center relative">
    <block v-click="[1,2]" v-motion :initial="{ y: 100 }" :enter="{ y: 0 }">
      <img src="/calendar.svg" />
      <div class="text-3xl">提高开发效率</div>
      <div class="text-gray-400">提供标准化的开发流程和自动化工具，减少重复性工作，能够更快地完成业务开发</div>
    </block>
    <block v-click="[2,3]" v-motion :initial="{ y: 100 }" :enter="{ y: 0 }">
      <img src="/draw.svg" />
      <div class="text-3xl">降低技术门槛</div>
      <div class="text-gray-400">抽象化底层技术细节，即使不具备深厚的系统知识，也能够快速上手并开发应用</div>
    </block>
    <block v-click="[3,4]" v-motion :initial="{ y: 100 }" :enter="{ y: 0 }">
      <img src="/group.svg" />
      <div class="text-3xl">促进团队协作</div>
      <div class="text-gray-400">提供版本控制、代码审查等工具，支持团队协作，提高代码质量和开发效率</div>
    </block>
    <block v-click="[4,5]" v-motion :initial="{ y: 100 }" :enter="{ y: 0 }">
      <img src="/checklist.svg" />
      <div class="text-3xl">加快迭代速度</div>
      <div class="text-gray-400">自动化的测试和部署流程，使得新功能和修复可以快速地发布到生产环境</div>
    </block>
    <block v-click="[5,6]" v-motion :initial="{ y: 100 }" :enter="{ y: 0 }">
      <img src="/shield.svg" />
      <div class="text-3xl">增强系统可靠性</div>
      <div class="text-gray-400">通过监控和日志分析，及时发现并解决问题，减少系统的故障时间</div>
    </block>
    <block v-click="[6,7]" v-motion :initial="{ y: 100 }" :enter="{ y: 0 }">
      <img src="/files-and-folders.svg" />
      <div class="text-3xl">保障数据安全</div>
      <div class="text-gray-400">提供安全机制，保护用户数据和业务逻辑不被未授权访问或破坏</div>
    </block>
    <block v-click="[7,8]" v-motion :initial="{ y: 100 }" :enter="{ y: 0 }">
      <img src="/search.svg" />
      <div class="text-3xl">支持业务创新</div>
      <div class="text-gray-400">提供灵活的基础设施，支持快速试错和迭代，鼓励创新和实验性的业务尝试</div>
    </block>
    <block v-click="[8]" v-motion :initial="{ y: 100 }" :enter="{ y: 0 }">
      <img src="/telegram.svg" />
      <div class="text-3xl">优化用户体验</div>
      <div class="text-gray-400">通过性能监控和优化，确保应用的响应速度和稳定性，提供更好的用户体验</div>
    </block>
  </div>
</div>

<style>
  img {
    @apply h-40 
  }
  block {
    @apply flex flex-col items-center gap-5 absolute
  }
</style>

---

# 〇、基础设施的关键组成

不仅提高开发效率，还保证代码质量和应用性能，为开发者提供了一个高效、稳定和可扩展的工作环境。

<div class="mt-10 grid grid-cols-3 text-center">
  <v-clicks>
    <div v-motion :initial="{ y: 100 }" :enter="{ y: 0 }" class="p-5">
      <img src="/git-icon.svg" />
      <img src="/commitizen.svg" />
      <img src="/gitlab.svg" />
      <div>分支管理和提交规范</div>
    </div>
    <div v-motion :initial="{ y: 100 }" :enter="{ y: 0 }" class="p-5">
      <img src="/vue.svg" />
      <img src="/react.svg" />
      <div>前端框架和界面库</div>
    </div>
    <div v-motion :initial="{ y: 100 }" :enter="{ y: 0 }" class="p-5">
      <img src="/webpack.svg" />
      <img src="/vitejs.svg" />
      <img src="/rollupjs.svg" />
      <div>构建工具和打包器</div>
    </div>
    <div v-motion :initial="{ y: 100 }" :enter="{ y: 0 }" class="p-5">
      <img src="/element.svg" />
      <img src="/ant-design.svg" />
      <img src="/unocss.svg" />
      <div>UI组件库和样式管理</div>
    </div>
    <div v-motion :initial="{ y: 100 }" :enter="{ y: 0 }" class="p-5">
      <img src="/chrome.svg" />
      <img src="/chartjs.svg" />
      <img src="/lighthouse.svg" />
      <div>前端监控和性能优化</div>
    </div>
    <div v-motion :initial="{ y: 100 }" :enter="{ y: 0 }" class="p-5">
      <img src="/visual-studio-code.svg" />
      <img src="/eslint.svg" />
      <img src="/typescript-icon.svg" />
      <div>开发环境和代码规范</div>
    </div>
    <div v-motion :initial="{ y: 100 }" :enter="{ y: 0 }" class="p-5">
      <img src="/nodejs-icon-alt.svg" />
      <img src="/npm-icon.svg" />
      <img src="/lodash.svg" />
      <div>工具库及工程化</div>
    </div>
     <div v-motion :initial="{ y: 100 }" :enter="{ y: 0 }" class="p-5">
      <img src="/nginx.svg" />
      <img src="/jenkins.svg" />
      <div>服务器和集成/部署(CI/CD)</div>
    </div>
    </v-clicks>
    <div v-after v-motion :initial="{ x: 100 }" :enter="{ x: 0 }" class="p-5">
      <img src="/more.svg" />
      <div>
        <carbon:overflow-menu-horizontal class="text-2xl"/>
      </div>
    </div>
</div>

<style>
img {
  @apply h-12 mx-1 inline mb-3 hover:scale-120
}
</style>

---

# 一、业务开发的提效点

使得业务开发者可以专注于实现业务逻辑，而不是底层的基础设施和通用功能，从而显著提高开发效率。

<div class="flex justify-center h-90 place-content-center flex-wrap gap-5">
  <v-clicks>
    <block v-motion :initial="{ y: 50 }" :enter="{ y: 0 }">标准化开发框架</block>
    <block v-motion :initial="{ y: 50 }" :enter="{ y: 0 }">模块化和组件库</block>
    <block v-motion :initial="{ y: 50 }" :enter="{ y: 0 }">自动化构建和部署工具</block>
    <block v-motion :initial="{ y: 50 }" :enter="{ y: 0 }">统一的认证和授权服务</block>
    <block v-motion :initial="{ y: 50 }" :enter="{ y: 0 }">数据管理服务</block>
    <block v-motion :initial="{ y: 50 }" :enter="{ y: 0 }">开发工具和模板</block>
    <block v-motion :initial="{ y: 50 }" :enter="{ y: 0 }">API Gateway</block>
    <block v-motion :initial="{ y: 50 }" :enter="{ y: 0 }">监控和日志服务</block>
    <block v-motion :initial="{ y: 50 }" :enter="{ y: 0 }">配置集中管理</block>
    <block v-motion :initial="{ y: 50 }" :enter="{ y: 0 }">微服务架构</block>
    <block v-motion :initial="{ y: 50 }" :enter="{ y: 0 }">开发指南和文档</block>
    <block v-motion :initial="{ y: 50 }" :enter="{ y: 0 }">低代码和无代码平台</block>
  </v-clicks>
</div>

<style>
  block {
    @apply border flex p-5 rounded-2xl
  }
</style>

---

# 二、平台基建与业务开发的异同点 Difference

平台基础设施建设和业务开发是软件开发中的两个重要领域，它们有各自的特点、目标和工作方式

<div class="h-90 flex justify-center items-center relative">
  <block v-click="[1,2]">
    <div class="flex" v-motion :initial="{ y: 50 }" :enter="{ y: 0 }">
      <span class="bg-blue-900">工具、服务</span>
      <span class="bg-red-900">特定业务</span>
    </div>
    <div class="absolute right-5 -top-10">开发范围</div>
  </block>
  <block v-click="[2,3]">
    <div class="flex" v-motion :initial="{ y: 50 }" :enter="{ y: 0 }">
      <span class="bg-blue-900">广泛</span>
      <span class="bg-red-900">特定</span>
    </div>
    <div class="absolute right-5 -top-10">技术栈</div>
  </block>
  <block v-click="[3,4]">
    <div class="flex">
      <span class="bg-blue-900">抽象</span>
      <span class="bg-red-900">具体</span>
    </div>
    <div class="absolute right-5 -top-10">抽象层次</div>
  </block>
  <block v-click="[4,5]">
    <div class="flex">
      <span class="bg-blue-900">高度复用</span>
      <span class="bg-red-900">一次性</span>
    </div>
    <div class="absolute right-5 -top-10">复用性</div>
  </block>
  <block v-click="[5,6]">
    <div class="flex">
      <span class="bg-blue-900">较长</span>
      <span class="bg-red-900">较短</span>
    </div>
    <div class="absolute right-5 -top-10">开发周期</div>
  </block>
  <block v-click="[6,7]">
    <div class="flex">
      <span class="bg-blue-900">可维护性<br />可扩展性</span>
      <span class="bg-red-900">快速迭代</span>
    </div>
    <div class="absolute right-5 -top-10">稳定与创新</div>
  </block>
  <block v-click="[7,8]">
    <div class="flex">
      <span class="bg-blue-900">面向开发者</span>
      <span class="bg-red-900">面向最终用户</span>
    </div>
    <div class="absolute right-5 -top-10">用户界面</div>
  </block>
</div>

<style>
  block {
    @apply border flex p-7 rounded-2xl absolute
  }
  span {
    @apply size-50 rounded-full flex justify-center items-center text-3xl mx-1 text-center
  }
</style>

---

# 续：平台基建与业务开发的异同点 Similarity

平台基建和业务开发是软件开发中两个重要领域，它们有各自的特点、目标和工作方式，但也存在共通之处。

<div class="h-90 flex justify-between items-center text-center">
  <v-clicks>
    <block v-motion :initial="{ y: 200 }" :enter="{ y: 0 }"> 
      <img src="/Strategy and goal.svg" /> 
      <div>目标导向</div>
    </block>
    <block v-motion :initial="{ y: 200 }" :enter="{ y: 0 }"> 
    <img src="/Feedback .svg" /> 
      <div>用户中心</div> 
    </block>
    <block v-motion :initial="{ y: 200 }" :enter="{ y: 0 }"> 
      <img src="/Launch.svg" /> 
      <div>技术驱动</div> 
    </block>
    <block v-motion :initial="{ y: 200 }" :enter="{ y: 0 }"> 
      <img src="/Business solutions .svg" /> 
      <div>团队合作</div> 
    </block>
    <block v-motion :initial="{ y: 200 }" :enter="{ y: 0 }"> 
      <img src="/Progress graph.svg" /> 
      <div>迭代过程</div> 
    </block>
    <block v-motion :initial="{ y: 200 }" :enter="{ y: 0 }"> 
      <img src="/Web security.svg" /> 
      <div>质量保证</div> 
    </block>
  </v-clicks>
</div>

<style>
  block {
    @apply px-3 py-7 border rounded-xl
  }

  img {
    @apply h-25 mb-5
  }
</style>

---

# 三、开发人员的技术栈与能力

通过在平台基础设施建设和业务开发领域的工作，积累宝贵的技术能力和软技能。

<div class="flex h-90 gap-10">
  <div class="flex-1 p-5 flex-col flex">
    <div v-click v-motion :initial="{ x: -200 }" :enter="{ x: 0 }" class="text-center text-xl mb-3">平台基建</div>
    <div class="flex flex-col flex-1 justify-between">
      <v-clicks>
        <block v-motion :initial="{ y: 200 }" :enter="{ y: 0 }"><img src="/technology.svg" />深入理解前端架构</block>
        <block v-motion :initial="{ y: 200 }" :enter="{ y: 0 }"><img src="/puzzle.svg" />模块化和组件化设计</block>
        <block v-motion :initial="{ y: 200 }" :enter="{ y: 0 }"><img src="/settings.svg" />API设计和开发</block>
        <block v-motion :initial="{ y: 200 }" :enter="{ y: 0 }"><img src="/stats.svg" />性能优化</block>
        <block v-motion :initial="{ y: 200 }" :enter="{ y: 0 }"><img src="/network.svg" />跨团队协作</block>
        <block v-motion :initial="{ y: 200 }" :enter="{ y: 0 }"><img src="/teamwork.svg" />系统思维</block>
      </v-clicks>
    </div>
  </div>
  <div class="flex-1 p-5 flex-col flex">
    <div v-click v-motion :initial="{ x: -200 }" :enter="{ x: 0 }" class="text-center text-xl mb-3">业务开发</div>
    <div class="flex flex-1 flex-col justify-between">
      <v-clicks>
        <block v-motion :initial="{ y: 200 }" :enter="{ y: 0 }"><img src="/timetable.svg" />快速迭代能力</block>
        <block v-motion :initial="{ y: 200 }" :enter="{ y: 0 }"><img src="/speech.svg" />业务理解</block>
        <block v-motion :initial="{ y: 200 }" :enter="{ y: 0 }"><img src="/palette.svg" />用户界面设计</block>
        <block v-motion :initial="{ y: 200 }" :enter="{ y: 0 }"><img src="/startup.svg" />前端技术栈专长</block>
        <block v-motion :initial="{ y: 200 }" :enter="{ y: 0 }"><img src="/stats-1.svg" />项目管理</block>
        <block v-motion :initial="{ y: 200 }" :enter="{ y: 0 }"><img src="/sample-tube.svg" />测试和调试</block>
      </v-clicks>
    </div>
  </div>
</div>

<style>
  img {
    @apply inline h-7
  }
  block {
    @apply flex items-center gap-3
  }

</style>

---

# 四、融合开发的最佳实践

促进资源共享、提高开发效率、加快产品迭代速度，并最终提升用户体验。

<div class="flex flex-col gap-1 text-sm">
  <div class="flex justify-between items-center">
    <block v-click v-motion :initial="{ x: -200 }" :enter="{ x: 0 }"> <img src="/fenxi.svg" /> 需求分析与规划</block>
    <carbon:PortInput v-click class="text-3xl" />
    <block v-after v-motion :initial="{ x: -200 }" :enter="{ x: 0 }"> <img src="/huanjing.svg" /> 环境搭建与配置</block>
    <carbon:ArrowRight v-click class="text-3xl" />
    <block v-after v-motion :initial="{ x: -200 }" :enter="{ x: 0 }"> <img src="/mokuai.svg" /> 模块与组件开发</block>
    <carbon:ArrowsHorizontal v-click class="text-3xl" />
    <block v-after v-motion :initial="{ x: -200 }" :enter="{ x: 0 }"> <img src="/bianma.svg" /> 业务编码实践</block>
  </div>
  <div class="flex justify-end pr-10">
    <carbon:ArrowDown v-click class="text-3xl" />
  </div>
  <div class="flex flex-row-reverse justify-between items-center">
    <block v-after v-motion :initial="{ y: -200 }" :enter="{ y: 0 }"> <img src="/banben.svg" /> 分支版本控制</block>
    <carbon:ArrowLeft v-click class="text-3xl" />
    <block v-after v-motion :initial="{ x: 200 }" :enter="{ x: 0 }"> <img src="/bushu.svg" /> 持续集成/部署(CI/CD)</block>
    <carbon:ArrowLeft v-click class="text-3xl" />
    <block v-after v-motion :initial="{ x: 200 }" :enter="{ x: 0 }"> <img src="/youhua.svg" /> 性能监控与优化</block>
    <carbon:ArrowsHorizontal v-click class="text-3xl" />
    <block v-after v-motion :initial="{ x: 200 }" :enter="{ x: 0 }"> <img src="/liulanqi.svg" /> 跨端兼容性测试</block>
  </div>
  <div class="flex pl-15">
    <carbon:arrow-down v-click class="text-3xl" />
  </div>
  <div class="flex justify-between items-center">
    <block v-after v-motion :initial="{ y: -200 }" :enter="{ y: 0 }"> <img src="/fankui.svg" /> 用户反馈与迭代</block>
    <carbon:ArrowRight v-click class="text-3xl" />
    <block v-after v-motion :initial="{ x: -200 }" :enter="{ x: 0 }"> <img src="/wendang.svg" /> 文档与知识共享</block>
    <carbon:ArrowRight v-click class="text-3xl" />
    <block v-after v-motion :initial="{ x: -200 }" :enter="{ x: 0 }"> <img src="/zhaiwu.svg" /> 技术债务管理</block>
    <carbon:PortOutput v-click class="text-3xl" />
    <block v-after v-motion :initial="{ x: -200 }" :enter="{ x: 0 }"> <img src="/xuexi.svg" /> 总结反思成长</block>
  </div>
</div>

<style>
  block {
    @apply px-3 py-2 border rounded-xl px-5  
  }

  img {
    @apply h-12 mx-auto mb-3
  }
</style>

---

# 结语：道阻且长，行则将至

<div v-click v-motion :initial="{ y: 200 }" :enter="{ y: 0 }" class="mt-30 p-10 flex flex-col items-center justify-center rounded-md bg-dark-300">
<div class="text-2xl mb-10">“朱泙漫学屠龙于支离益，单千金之家，三年技成而无所用其巧。”</div>
<div class="self-end">————《庄子·列御寇》</div>
</div>

---
layout: end
---

# Thanks for watching{.italic}

谢谢聆听，欢迎批评指正！

<PoweredBySlidev mt-10 mx-auto />
