# 安全与隐私 / Security & Privacy

## 安装包与更新 / Distribution and updates

请从 [RoperYoung/NeoMount-for-Mac Releases](https://github.com/RoperYoung/NeoMount-for-Mac/releases) 下载。正式发布的应用及 DMG 均使用 Developer ID 签名，并分别提交 Apple 公证、装订票据。签名主体为 Chengdu Zubuchuhu Education Technology Co., Ltd.，Team ID 为 `VD443NUPB6`。

Download from the releases linked above. Both the app and DMG are Developer ID signed, independently notarized and stapled. The signing identity is Chengdu Zubuchuhu Education Technology Co., Ltd., Team ID `VD443NUPB6`.

Sparkle checks a signed appcast on GitHub, verifies the Ed25519 signature of each update and validates the code signature before installation. Automatic checks can be turned off in Preferences. Installation requires user interaction; an occupied FTP/SFTP mount can prevent the app from quitting for an update.

更新使用 Sparkle，更新列表与安装包均有签名。自动检查可关闭；安装前由用户确认。FTP/SFTP 磁盘仍被占用时，应用可能暂停退出和更新，先关闭相关文件即可。

## 本机数据 / Local data

连接信息保存在当前用户的 `~/Library/Application Support/NeoMount`，密码使用 CryptoKit AES-GCM 加密，目录和文件限制为当前用户访问。解密密钥也保存在本机同一用户目录内；这可避免密码直接写入普通配置，但无法抵御已经控制该 macOS 账户的程序。导出配置不包含密码。

Connection settings are stored in the current user’s `~/Library/Application Support/NeoMount` folder. Passwords are encrypted using CryptoKit AES-GCM with user-restricted file permissions. The decryption key is stored locally in the same user’s data directory. This keeps plaintext passwords out of ordinary configuration files, but does not protect against software that already controls that macOS account. Configuration exports exclude passwords.

NeoMount does not operate a cloud account service, collect usage analytics or include ad tracking. Network requests go to configured servers, GitHub for updates, and the usual macOS services used for mounting and trust checks. GitHub receives ordinary request information such as the client IP address when checking or downloading updates. Sparkle system profiling is disabled.

NeoMount 没有云端账号、使用统计或广告追踪。联网用于你设置的服务器、GitHub 更新和 macOS 挂载及信任检查。更新请求会让 GitHub 收到正常请求信息（例如 IP 地址）；Sparkle 的系统信息上报已关闭。

## 连接保护 / Connections

HTTPS uses normal certificate validation. SFTP fingerprints must be explicitly trusted on first connection and are checked on subsequent connections; changed keys stop the connection. The FTP/SFTP helper listens only on a random loopback port with randomly generated authentication. FTP remains an unencrypted protocol. NeoMount does not bypass certificate errors or force-unmount busy disks.

HTTPS 保持证书校验；SFTP 首次连接确认指纹，后续校验已保存指纹。FTP/SFTP 桥接仅监听随机本机回环端口，并使用随机认证信息。FTP 仍是明文协议。应用不会绕过证书错误或强制卸载忙碌磁盘。

## 问题反馈 / Reporting

普通问题请在 Issues 中反馈，并移除密码、账号、真实服务器地址及私人文件路径。安全问题也请先只描述影响与复现条件，不要公开凭据或可直接攻击他人系统的细节。

For support, open an issue after removing credentials, private addresses and file paths. For security reports, begin with the impact and reproduction conditions; do not post secrets or details that directly expose someone else’s system.
