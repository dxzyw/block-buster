# 使用固定的平台和 Python 基础镜像
FROM python:3.10-alpine AS builder

# 设置工作目录
WORKDIR /app

# 复制依赖文件并安装
COPY requirements.txt /app
RUN pip3 install -r requirements.txt

# 复制应用代码
COPY . /app

# 配置容器启动命令
ENTRYPOINT ["python3"]
CMD ["app.py"]

# 开发环境配置阶段
FROM builder as dev-envs

# 更新并安装必要工具
RUN apk update && apk add git

# 添加用户和用户组
RUN addgroup -S docker && adduser -S --shell /bin/bash --ingroup docker vscode

# 复制其他工具（例如 Docker CLI 等），可根据需求调整或删除
COPY --from=gloursdocker/docker / /

