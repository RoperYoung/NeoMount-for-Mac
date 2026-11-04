# 安全与隐私 / Security & Privacy

## Mac App Store 版本 / Mac App Store edition

Mac App Store 版本使用 Apple App Sandbox，并通过 App Store 更新，不包含 Sparkle，也不向 GitHub 检查或下载更新。连接设置、加密凭据和 SFTP 主机信任记录保存在该版本的本机应用容器中；网络磁盘挂载到应用有权访问的私有目录，仍可通过“在访达中打开”访问。导入导出文件仅在用户通过系统文件面板选择后访问。独立安装版与商店版的数据目录不同：可先从原版导出配置再导入商店版，密码需重新填写。点击帮助、隐私或其他外部网页链接时，网页服务会收到普通浏览请求信息。

The Mac App Store edition uses Apple App Sandbox and receives updates through the App Store. It does not include Sparkle or contact GitHub to check for or download updates. Connection settings, encrypted credentials, and SFTP host-trust records stay in its local app container. Network drives mount in an app-accessible private directory and can be opened in Finder. Import and export access only files selected through the system file picker. The direct-download and store editions have separate data directories: export settings from the original app and import them into the store edition, then enter passwords again. Opening help, privacy, or other external web links sends normal browser request information to the destination website.

The updater details below apply only to the direct-download edition. Both editions have no NeoMount cloud account, advertising, or usage analytics.

以下更新器说明仅适用于独立安装版。两个版本均不提供 NeoMount 云端账号，不包含广告或使用行为统计。

## 独立安装版与更新 / Direct-download distribution and updates

请从 [RoperYoung/NeoMount-for-Mac Releases](https://github.com/RoperYoung/NeoMount-for-Mac/releases) 下载。正式发布的应用及 DMG 均使用 Developer ID 签名，并分别提交 Apple 公证、装订票据。签名主体为 Chengdu Zubuchuhu Education Technology Co., Ltd.，Team ID 为 `VD443NUPB6`。

Download from the releases linked above. Both the app and DMG are Developer ID signed, independently notarized and stapled. The signing identity is Chengdu Zubuchuhu Education Technology Co., Ltd., Team ID `VD443NUPB6`.

Sparkle checks a signed appcast on GitHub, verifies the Ed25519 signature of each update and validates the code signature before installation. Automatic checks can be turned off in Preferences. Installation requires user interaction; an occupied FTP/SFTP mount can prevent the app from quitting for an update.

更新使用 Sparkle，更新列表与安装包均有签名。自动检查可关闭；安装前由用户确认。FTP/SFTP 磁盘仍被占用时，应用可能暂停退出和更新，先关闭相关文件即可。

## 本机数据 / Local data

独立安装版的连接信息保存在当前用户的 `~/Library/Application Support/NeoMount`，密码使用 CryptoKit AES-GCM 加密，目录和文件限制为当前用户访问。解密密钥也保存在本机同一用户目录内；这可避免密码直接写入普通配置，但无法抵御已经控制该 macOS 账户的程序。导出配置不包含密码。

In the direct-download edition, connection settings are stored in the current user’s `~/Library/Application Support/NeoMount` folder. Passwords are encrypted using CryptoKit AES-GCM with user-restricted file permissions. The decryption key is stored locally in the same user’s data directory. This keeps plaintext passwords out of ordinary configuration files, but does not protect against software that already controls that macOS account. Configuration exports exclude passwords.

NeoMount does not operate a cloud account service, collect usage analytics or include ad tracking. In the direct-download edition, network requests go to configured servers, GitHub for updates, and the usual macOS services used for mounting and trust checks. GitHub receives ordinary request information such as the client IP address when checking or downloading updates. Sparkle system profiling is disabled.

NeoMount 没有云端账号、使用统计或广告追踪。独立安装版联网用于你设置的服务器、GitHub 更新和 macOS 挂载及信任检查。更新请求会让 GitHub 收到正常请求信息（例如 IP 地址）；Sparkle 的系统信息上报已关闭。

## 连接保护 / Connections

HTTPS uses normal certificate validation. SFTP fingerprints must be explicitly trusted on first connection and are checked on subsequent connections; changed keys stop the connection. The FTP/SFTP helper listens only on a random loopback port with randomly generated authentication. FTP remains an unencrypted protocol. NeoMount does not bypass certificate errors or force-unmount busy disks.

HTTPS 保持证书校验；SFTP 首次连接确认指纹，后续校验已保存指纹。FTP/SFTP 桥接仅监听随机本机回环端口，并使用随机认证信息。FTP 仍是明文协议。应用不会绕过证书错误或强制卸载忙碌磁盘。

## 问题反馈 / Reporting

普通问题请在 Issues 中反馈，并移除密码、账号、真实服务器地址及私人文件路径。安全问题也请先只描述影响与复现条件，不要公开凭据或可直接攻击他人系统的细节。

For support, open an issue after removing credentials, private addresses and file paths. For security reports, begin with the impact and reproduction conditions; do not post secrets or details that directly expose someone else’s system.
