# TailDesk

外出先の iPad / iPhone から、自分の Mac を操作するリモートデスクトップです(テスト版)。
通信は [Tailscale](https://tailscale.com)(無料の VPN)を通り、iPad / iPhone と Mac が直接つながります。映像や操作が第三者のサーバーを経由することはありません。

## 必要なもの

- Apple シリコンまたは Intel の Mac(macOS 13 以降)
- iPad / iPhone(iOS 16 以降)
- Tailscale のアカウント(Google・Apple・Microsoft のアカウントで無料で作れます)

## 導入の手順(10 分ほど)

### 1. Mac

1. [Tailscale for Mac](https://tailscale.com/download/mac) を入れてログインし、接続をオンにします。
2. このページの [Releases](../../releases/latest) から `TailDeskHost-x.y.z.zip` をダウンロードして開き、`TailDeskHost.app` を「アプリケーション」フォルダに移します。
3. TailDeskHost を開くと「TailDesk を使う準備」が出ます。表示に沿って次を行います。
   - **画面収録**: 「許可する」→ システム設定で TailDeskHost をオン → 「再起動」
   - **アクセシビリティ**: 「許可する」→ システム設定で TailDeskHost をオン(進まないときは「再起動」)
   - **ログイン時に自動で起動**: 「オンにする」
4. メニューバーに TailDesk のアイコンが出ていれば準備完了です。

### 2. iPad / iPhone

1. 受け取った TestFlight の招待リンクを開き、TestFlight アプリから TailDesk を入れます。
2. App Store から [Tailscale](https://apps.apple.com/app/tailscale/id1470499037) を入れ、**Mac と同じアカウント**でログインして接続をオンにします。
3. TailDesk を開くと「はじめに」のチェックリストが出ます。Tailscale につながると自動でチェックが付きます。

### 3. つなぐ

1. Mac のメニューバーの TailDesk から「ペアリング開始…」を選ぶと QR コードが出ます。
2. iPad / iPhone の TailDesk で「＋」→「QR を読む」で読み取り、Mac に出ている 6 桁のコードを入力します。
3. 次からはアプリを開くだけで前回の Mac につながります(自宅など別の場所からでもつながります)。

## よくあること

- **Tailscale で「管理者の承認が必要」と出る**: Tailscale の管理画面(https://login.tailscale.com/admin/machines)でその端末を承認してください。
- **QR を出しても見えない**: 最新版では QR の窓が最前面に出ます。古い版を使っている場合は更新してください。
- **Mac がスリープしているとつながりません**: 電源につなぎ、スリープしない設定にしてください(システム設定 → バッテリー → オプション、または Amphetamine などのアプリ)。

## 端末をなくしたとき

Mac のメニューバーの TailDesk →「ペアリング済みの端末」から、その端末の「登録を解除」を選んでください。以後その端末からはつながりません。iPad / iPhone の TailDesk の「はじめに」から Face ID ロックをオンにしておくと安心です。

## 安全のための設計

- Mac は Tailscale のネットワーク(100.x.x.x)からの接続しか受け付けません。
- ペアリングした端末だけが操作できます(端末ごとの証明書で相互に確かめます)。
- 通信はすべて TLS 1.3 で暗号化され、開発者のサーバーは経由しません。
- パスワード管理アプリでコピーした内容は iPad / iPhone に送りません。

## プライバシー

[プライバシーポリシー](PRIVACY.md)
