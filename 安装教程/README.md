# Go 语言环境搭建指南（Windows / macOS / Linux）

## 1. Windows 下安装 Go

### 步骤
1. 访问官网下载 Windows 版本的 `.msi` 安装包：  
   [https://go.dev/dl/](https://go.dev/dl/)

2. 双击安装包，按提示完成安装（默认路径：`C:\Program Files\Go`）。

3. 安装完成后，打开 **命令提示符** 或 **PowerShell**，输入：
   ```powershell
   go version
```
   如果能看到版本号，说明安装成功。

4. **配置 GOPATH（可选，Go 1.11+ 可使用 Go Modules）**  
   在环境变量中添加：
   ```powershell
   setx GOPATH "C:\Users\YourUser\go"
   setx PATH "%PATH%;%GOPATH%\bin"
```

5. **测试运行**
   ```powershell
   mkdir %GOPATH%\src\hello
   cd %GOPATH%\src\hello
   notepad main.go
   ```
   在 `main.go` 中写入：
   ```go
   package main
   import "fmt"
   func main() {
       fmt.Println("Hello, Go!")
   }
   ```
   保存后运行：
   ```powershell
   go run main.go
   ```

---

## 2. macOS 下安装 Go

### 方法一：使用 Homebrew
```bash
brew install go
```

### 方法二：下载安装包
1. 访问官网下载 macOS 版本的 `.pkg` 安装包：  
   [https://go.dev/dl/](https://go.dev/dl/)

2. 双击安装包完成安装。

3. 验证安装：
   ```bash
   go version
   ```

4. **配置 GOPATH（可选）**
   ```bash
   echo 'export GOPATH=$HOME/go' >> ~/.zshrc
   echo 'export PATH=$PATH:$GOPATH/bin' >> ~/.zshrc
   source ~/.zshrc
   ```

5. **测试运行**
   ```bash
   mkdir -p $GOPATH/src/hello
   cd $GOPATH/src/hello
   cat > main.go << EOF
   package main
   import "fmt"
   func main() {
       fmt.Println("Hello, Go!")
   }
   EOF
   go run main.go
   ```

---

## 3. Linux 下安装 Go

### 步骤
1. 下载 Go 二进制包（以 1.22.5 版本为例）：
   ```bash
   wget https://go.dev/dl/go1.22.5.linux-amd64.tar.gz
   ```

2. 解压到 `/usr/local`：
   ```bash
   sudo rm -rf /usr/local/go
   sudo tar -C /usr/local -xzf go1.22.5.linux-amd64.tar.gz
   ```

3. 添加到环境变量：
   ```bash
   echo 'export PATH=$PATH:/usr/local/go/bin' >> ~/.bashrc
   source ~/.bashrc
   ```

4. 验证安装：
   ```bash
   go version
   ```

5. **测试运行**
   ```bash
   mkdir -p $HOME/go/src/hello
   cd $HOME/go/src/hello
   cat > main.go << EOF
   package main
   import "fmt"
   func main() {
       fmt.Println("Hello, Go!")
   }
   EOF
   go run main.go
   ```

---

## 4. 常见问题和解决方案

### Q1: `go: command not found`
**原因**：Go 的可执行文件路径没有加入到系统 PATH 中。  
**解决方法**：
- Windows：检查 `C:\Program Files\Go\bin` 是否在 PATH 中。
- macOS / Linux：在 `.bashrc` 或 `.zshrc` 中添加：
  ```bash
  export PATH=$PATH:/usr/local/go/bin
  ```
  然后执行 `source ~/.bashrc` 或 `source ~/.zshrc`。

### Q2: GOPATH 目录不存在或找不到包
**原因**：没有正确设置 GOPATH 或未启用 Go Modules。  
**解决方法**：
- 设置 GOPATH：
  ```bash
  export GOPATH=$HOME/go
  export PATH=$PATH:$GOPATH/bin
  ```
- 或使用 Go Modules（推荐 Go 1.11+）：
  ```bash
  go env -w GO111MODULE=on
  go env -w GOPROXY=https://goproxy.cn,direct
  ```

### Q3: 下载依赖速度慢
**原因**：默认 GOPROXY 在国内访问慢。  
**解决方法**：
```bash
go env -w GOPROXY=https://goproxy.cn,direct
```

### Q4: Windows PowerShell 提示权限不足
**原因**：PowerShell 执行策略限制。  
**解决方法**：
```powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
```
选择 Y 确认。




