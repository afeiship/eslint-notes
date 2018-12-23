# 用 husky 和 lint-staged 构建超溜的代码检查工作流

- https://zhuanlan.zhihu.com/p/27094880

> 具备基本工程素养的同学都会注重编码规范，而代码风格检查（Code Linting，简称 Lint）是保障代码规范一致性的重要手段，你的工作流中有 Lint 环节么？有的话你用的爽么？你在团队中推广过 Lint，但是大家都不买账？究竟是为啥？

## Lint 是什么？

> 探讨怎么做之前，我们很有必要给 Lint 来个清晰、准确的定义，wikipedia 的定义如下：

In computer programming, lint is a Unix utility that flags some suspicious and non-portable constructs (likely to be bugs) in C language source code; generically, lint or a linter is any tool that flags suspicious usage in software written in any computer language. The term lint-like behavior is sometimes applied to the process of flagging suspicious language usage. Lint-like tools generally perform static analysis of source code.

## 一句话讲明白：

简单来说，`Lint` 就是对代码做静态分析，并试图找出潜在问题的工具，实战中我们也用 `Lint` 来指使用工具的过程。

## 为什么要 Lint？

> 使用 Lint 会有什么好处呢？在我看来至少具有如下 3 点：

- 更少的 Bug，剑桥大学的研究发现，全世界每年因为软 Bug 造成的经济损失约 3120 亿美金；
- 更高的开发效率，工程师平均会花掉 50% 的工作时间定位和解决各种 Bug，其中不乏那些显而易见的低级错误，而 Lint 很容易发现低级的、显而易见的错误；
- 更高的可读性，代码可读性的首要因子是“表面文章”，表面上看起来乱糟糟的代码通常更难读懂；
- 可以毫不客气的说，如果你不做 Lint，就是在浪费自己的时间，浪费公司的资源。既然做 Lint 的预期效果很好？该怎么做呢？

## 传统 line + ci

> 提交后 Lint：反馈链条太长？
> 说到怎么做，多数人会自然而然的想到各种 Lint 工具，目前社区中针对各种语言都开发了 Lint 工具，前端能用到的就有大把：ESLint、Standard、SCSSLint、JSONLint、HTMLHint 等。GitHub 官方出品的 Lint 工具列表 也是个非常不错的参考。

### 传统的方式：

很多同学选择在持续集成阶段（后文用 CI 代称）做 Lint，比如使用远程的 Git Hooks 来触发。但是从实际的经历来看，这种做法的反馈链条通常如下：

```
代码提交 --> 发现问题(远程) --> 修复问题 --> 重新提交 --> 通过检查(远程)
```

### 传统方式的问题：

整个过程可能会浪费掉你不少时间，毕竟 CI 过程通常不仅是在做 Lint，如果你是那种不知道自己时间每天都去哪儿了的工程师，可以反思下自己或者团队的工作流是否是这样。并且，请相信我，你不是少数人。

你有没有这样的经历：吭哧吭哧写了几天代码，各种验收都通过了，最后被 CI 拒绝，竟是因为你的代码中少加了一个逗号，这时候心情简直崩溃到无法形容：

## CI 以及远程 lint 的问题：

> 只在 CI 流程做 Lint 的缺点也是显而易见的：

- Lint 在整个开发工作流中的反馈链条太长，浪费时间、注意力和资源，最致命的；
- CI 流程搭建成本比较高，即使有各种 CI 服务，步骤也还是比较繁琐；

首先，安装依赖：

```shell
npm install -D husky
yarn add --dev husky
```

然后修改 package.json，增加配置：

```json
{
  "scripts": {
    "precommit": "eslint src/**/*.js"
  }
}
```

最后尝试 Git 提交，你就会很快收到反馈：

```shell
git commit -m "Keep calm and commit"
```

但是在遗留代码仓库上工作的同学很快会遇到新的问题，开启 Lint 初期，你可能会面临成千上万的 Lint Error 需要修复。部分同学对下面这个图可能并不陌生：只改了文件 A，但是文件 B、C、D 中也有大量错误。

## 只 Lint 改动的

> 如果把 Lint 挪到本地，并且每次提交只检查本次提交所修改的文件，上面的痛点就都解决了。Feedly 的工程师 Andrey Okonetchnikov 开发的 lint-staged 就是基于这个想法，其中 staged 是 Git 里面的概念，指待提交区，使用 git commit -a，或者先 git add 然后 git commit 的时候，你的修改代码都会经过待提交区。

## lint-staged 用法如下：

首先，安装依赖：

```shell
npm install -D lint-staged
yarn add --dev lint-staged
```

然后，修改 package.json 配置：

```json
{
  "scripts": {
    "precommit": "lint-staged"
  },
  "lint-staged": {
    "src/**/*.js": "eslint"
  }
}
```
