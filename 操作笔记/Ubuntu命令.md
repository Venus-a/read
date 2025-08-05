# Ubuntu命令

## 常见命令

ls cd 

ls -a查看所有文件，包含隐藏文件

touch 创建新文件

mkdir 创建目录

rm 删除文件

cp 复制文件

cp -r 复制目录

mv 

nvidia-smi 查看显卡型号

## **一、软件包管理**

1. **更新软件源**

   ```bash
   sudo apt update        # 更新软件列表
   ```

2. **安装/卸载软件**

   ```bash
   sudo apt install package_name  # 安装
   sudo apt remove package_name   # 卸载（保留配置）
   sudo apt purge package_name    # 完全卸载
   ```

3. **搜索软件**

   ```bash
   apt search keyword    # 搜索软件包
   ```

4. **升级系统**

   ```bash
   sudo apt upgrade      # 升级已安装包
   sudo apt dist-upgrade # 智能处理依赖
   ```

## **二、系统监控与管理**

1. **查看进程**

   ```bash
   top                  # 动态进程监控
   htop                 # 增强版top（需安装）
   ps aux | grep nginx  # 查找特定进程
   ```

2. **终止进程**

   ```bash
   kill PID             # 结束进程（PID为进程号）
   kill -9 PID          # 强制结束
   ```

3. **磁盘空间检查**

   ```bash
   df -h                # 查看磁盘使用情况
   du -sh /path         # 统计目录大小
   ```

4. **系统信息**

   ```bash
   uname -a             # 内核版本
   lsb_release -a       # 发行版信息
   free -h              # 内存使用
   ```

## **三、网络操作**

1. **检查网络**

   ```bash
   ping google.com      # 测试连通性
   ifconfig 或 ip a     # 查看IP地址（需安装 net-tools）
   ```

2. **远程连接**

   ```bash
   ssh user@host_ip     # SSH远程登录
   scp file.txt user@host_ip:/path  # 远程复制
   ```

3. **下载文件**

   ```bash
   wget https://example.com/file.zip
   curl -O https://example.com/file.zip
   ```

## **四、权限管理**

1. **修改文件权限**

   ```bash
   chmod 755 script.sh  # 设置权限（rwxr-xr-x）
   chmod +x script.sh   # 添加执行权限
   ```

2. **修改文件所有者**

   ```bash
   sudo chown user:group file.txt
   ```

3. **提权操作**

   ```bash
   sudo command         # 以管理员身份执行
   sudo -i              # 切换到root用户
   ```

## **五、文本处理**

1. **查看文件内容**

   ```bash
   cat file.txt         # 显示全部内容
   less file.txt        # 分页查看（可搜索）
   head -n 10 file.txt  # 显示前10行
   tail -f log.txt      # 实时追踪日志
   ```

2. **文本搜索**

   ```bash
   grep "text" file.txt       # 搜索关键词
   grep -r "text" /path       # 递归搜索目录
   ```

3. **编辑文本**

   ```bash
   nano file.txt        # 简单编辑器
   vim file.txt         # 高级编辑器
   ```

## **六、压缩与解压**

```bash
# .tar 文件
tar -cvf archive.tar /dir   # 压缩
tar -xvf archive.tar        # 解压

# .gz 文件
gzip file                  # 压缩为 .gz
gunzip file.gz             # 解压

# .zip 文件
zip archive.zip file       # 压缩
unzip archive.zip          # 解压
```

## **七、系统服务管理（Systemd）**

```bash
sudo systemctl start nginx    # 启动服务
sudo systemctl stop nginx     # 停止服务
sudo systemctl restart nginx  # 重启服务
sudo systemctl status nginx   # 查看状态
sudo systemctl enable nginx   # 开机自启
```

## **八、实用快捷键（桌面版）**

- `Ctrl+Alt+T`：打开终端
- `Alt+Tab`：切换窗口
- `Super` (Win键)：显示活动概览
- `Ctrl+Q`：关闭当前应用窗口
- `Ctrl+Alt+Del`：打开系统监视器

## **九、常见问题解决**

1. **忘记root密码**：

   - 重启系统 → 长按 `Shift` 进入GRUB菜单 → 选择恢复模式 → 重置密码。

2. **磁盘空间不足**：

   - 使用 `ncdu` (需安装) 扫描大文件：

     ```bash
     sudo apt install ncdu
     ncdu /
     ```

3. **开机进入命令行**：

   ```bash
   startx        # 尝试启动图形界面
   sudo systemctl start gdm3 # 或 lightdm（根据显示管理器）
   ```