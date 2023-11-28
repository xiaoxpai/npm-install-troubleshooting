
# [问题描述] 当我在网上的克隆一个项目到本地，进行npm install项目构建依赖时，报错
```bash
D:\src\first-app-lesson-00>npm install
npm ERR! code ERESOLVE
npm ERR! ERESOLVE unable to resolve dependency tree
npm ERR!
npm ERR! While resolving: angular.io-example@0.0.0
npm ERR! Found: @angular/common@17.0.0
npm ERR! node_modules/@angular/common
npm ERR!   @angular/common@"17.0.0" from the root project
npm ERR!
npm ERR! Could not resolve dependency:
npm ERR! peer @angular/common@"^16.0.0" from angular-in-memory-web-api@0.16.0
npm ERR! node_modules/angular-in-memory-web-api
npm ERR!   angular-in-memory-web-api@"~0.16.0" from the root project
npm ERR!
npm ERR! Fix the upstream dependency conflict, or retry
npm ERR! this command with --force or --legacy-peer-deps
npm ERR! to accept an incorrect (and potentially broken) dependency resolution.
npm ERR!
npm ERR!
npm ERR! For a full report see:
npm ERR! C:\Users\Administrator\AppData\Local\npm-cache\_logs\2023-11-28T13_38_44_136Z-eresolve-report.txt

npm ERR! A complete log of this run can be found in: C:\Users\Administrator\AppData\Local\npm-cache\_logs\2023-11-28T13_38_44_136Z-debug-0.log
```

 # [解决方案]
 
 这个错误是由于在解析项目的依赖关系时发生了冲突导致的。根据错误信息，发现了一个依赖冲突：

```
Could not resolve dependency:
peer @angular/common@"^16.0.0" from angular-in-memory-web-api@0.16.0
```

这意味着 `angular-in-memory-web-api@0.16.0` 依赖于 `@angular/common` 的版本 `^16.0.0`，但是你的项目中已经安装了 `@angular/common` 的版本 `17.0.0`。

解决这个问题有几种方法：

1. **更新依赖版本：** 如果 `angular-in-memory-web-api` 已经有了与 `@angular/common@17.0.0` 兼容的更新版本，你可以尝试将其更新到最新版本。可以通过编辑项目的 `package.json` 文件并将 `angular-in-memory-web-api` 的版本更新为兼容的版本，然后再次运行 `npm install`。

2. **使用 `--force` 参数：** 在运行 `npm install` 命令时，你可以尝试使用 `--force` 参数来强制解析依赖关系。例如：

   ```
   npm install --force
   ```

   这将忽略依赖冲突并继续安装依赖项。但请注意，这可能导致依赖关系不一致或潜在的错误。

3. **使用 `--legacy-peer-deps` 参数：** 如果你使用的是较新版本的 npm（例如 7.x），可以尝试使用 `--legacy-peer-deps` 参数来使用旧的依赖解析算法。例如：

   ```
   npm install --legacy-peer-deps
   ```

   这将使用旧的算法解析依赖关系，可能会解决依赖冲突的问题。


   ---






   日期：2023年11月28日
   坐标：shenzhen
 
