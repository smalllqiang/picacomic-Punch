# 哔咔签到

- **每天通过 GitHub Actions 定时运行**
- **.NET 10 LTS**
- **支持多个账号**

## 使用说明

### 1. 检查仓库设置

在 `Settings` → `Actions` → `General` → `Workflow permissions` 中选择 **Read and write permissions**，以便自保活工作流使用 `GITHUB_TOKEN` 提交更新时间。

同时确认仓库未被归档；归档状态可在 `Settings` → `General` → `Danger Zone` 中检查。

### 2. Fork 项目并配置账号

点击项目右上角的 **Fork**。在 Fork 后的仓库中依次打开：

`Settings` → `Secrets and variables` → `Actions` → `New repository secret`

添加以下 Repository secret：

- Name：`ACCOUNTS`
- Value：`username1,password1|username2,password2...`

多个账号之间使用 `|` 分隔，每个账号的用户名和密码使用 `,` 分隔。不要把账号密码直接写入代码或工作流。

![配置 Secret](asset/1.png)

![填写 ACCOUNTS](asset/2.png)

### 3. 启用 GitHub Actions

打开仓库上方的 **Actions**。第一次使用时，可能需要点击 **I understand my workflows, go ahead and enable them**。

### 4. 触发运行

工作流会按设定时间自动运行。推送除 `README.md` 和 `.gitignore` 之外的文件时，也会触发运行。

如需通过网页提交来触发，可以修改 `Program.cs` 并提交：

![打开 Program.cs](asset/3.png)

![提交修改](asset/4.png)

### 5. 查看结果

打开 **Actions**，选择对应的工作流运行记录查看日志：

![查看 Actions](asset/5.png)

![查看运行记录](asset/6.png)

![查看运行日志](asset/7.png)

## 运行环境

- GitHub Actions：`ubuntu-latest`
- .NET SDK：`10.0.x`
- 定时任务：每天运行一次

## 注意事项

- 凭据通过 GitHub Actions Repository secrets 注入。
- 自保活工作流每 30 天更新一次仓库，避免定时任务因长期无活动而被停用。

## API

[picacomic-api](https://github.com/FirmianaMarsili/picacomic-api)
