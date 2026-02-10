---
slug: web3-security-checklist
title: Web3 安全检查清单
authors: [autosec]
tags: [whitehat-spotlight]
date: 2026-02-10T10:00
image: https://images.unsplash.com/photo-1639762681485-074b7f938ba0?w=1200&h=630&fit=crop
---

## 一、智能合约安全
- 使用 **OpenZeppelin** 等成熟库，避免重复造轮子
- 遵循 **Checks → Effects → Interactions** 模式，防止重入攻击
- 使用 Solidity ≥ 0.8.x，避免整数溢出
- 关键函数必须做 **权限控制（Ownable / AccessControl）**
- 上线前必须进行 **第三方安全审计**

---

## 二、私钥与资产安全
- 私钥绝不写入代码或提交到 Git
- 管理员权限使用 **多签钱包（Safe）**
- 大额资产建议使用 **硬件钱包**

---

## 三、前端与交互安全
- 明确展示交易内容，避免用户误签名
- 校验合约地址，防止钓鱼网站
- RPC 接口需限流与鉴权

---

## 四、部署与运维
- 主网部署前先在测试网充分验证
- 合约参数初始化后尽量 **不可修改**
- 监控异常交易与合约事件

---

## 五、核心原则
> 在 Web3 中：  
> **代码即法律，错误不可撤销。安全优先于一切。**
