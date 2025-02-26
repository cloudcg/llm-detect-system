# AI 文本检测系统

一个基于 Python 的 AI 文本检测系统，用于识别和分析文本内容是否由 AI 生成。

## 功能特点

- 支持多种输入方式：
  - 文件监控（支持 JSON、CSV 格式）
  - API 接口
  - WebSocket 实时推送
- 异步任务处理和队列管理
- 完善的日志记录系统
- 数据导出功能（支持 CSV、JSON、Excel）
- 实时进度显示
- 统计数据可视化
- 自动重试机制

## 系统要求

- Python 3.12
- MySQL 数据库
- 相关依赖包（见 requirements.txt）

## 配置说明

系统配置文件位于 `config/config.yml`，主要包含以下配置项：

- AI 模型配置
- 文本检测服务配置
- 数据库配置
- 文件监控配置
- 日志配置
- API 服务配置

## 快速开始

1. 克隆项目并安装依赖：
```bash
bash
git clone [项目地址]
cd [项目目录]
pip install -r requirements.txt
```
2. 配置数据库：
```bash
修改 config/config.yml 中的数据库配置
database:
host: "your_host"
port: your_port
username: "your_username"
password: "your_password"
database: "ai_detection"
```
3. 启动系统：
```bash
python src/main.py
```

## API 接口

### 1. 健康检查
`GET /health`

### 2. 单文本检测
`POST /api/check-text`
```json
Content-Type: application/json
{
"text": "要检测的文本内容",
"source": "文本来源（可选）",
"batch_id": "批次ID（可选）"
}
```
### 3. 批量检测
`POST /api/batch-check`
```json
Content-Type: application/json
{
"texts": [
{
"text": "文本1",
"source": "来源1"
},
{
"text": "文本2",
"source": "来源2"
}
]
}
```
### 4. 获取统计信息
`GET /api/statistics`
### 5. WebSocket 实时推送

## 文件监控

系统支持监控指定目录下的文件变化：
- 问题输入目录：用于生成 AI 回答
- 内容检测目录：用于检测是否为 AI 生成

支持的文件格式：
- JSON
- CSV

## 日志管理

- 支持按日期分类
- 支持日志级别过滤
- 支持日志文件轮转
- 支持异步日志处理

## 贡献者

- Chao Zhu

## 许可证

[MIT License](https://github.com/cloudcg/llm-detect-system/blob/master/LICENSE)
