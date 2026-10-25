# TailDesk

外出先の iPad / iPhone から、自分の Mac を操作するリモートデスクトップです(テスト版)。
通信は [Tailscale](https://tailscale.com)(無料の VPN)を通り、iPad / iPhone と Mac が直接つながります。映像や操作が第三者のサーバーを経由することはありません。

## 必要なもの

- Apple シリコンまたは Intel の Mac(macOS 13 以降)
- iPad / iPhone(iOS 16 以降)
- Tailscale のアカウント(Google・Apple・Microsoft のアカウントで無料で作れます)

## 導入の手順(10 分ほど)

いちばん簡単なのは、**iPhone / iPad の TailDesk を先に入れて、アプリの「はじめに」に沿って進める**方法です。Mac には iPhone からリンクを送れます。

### 1. iPhone / iPad

1. 受け取った TestFlight の招待リンクを開き、TestFlight アプリから TailDesk を入れます。
2. TailDesk を開くと「はじめに」が出ます。その順に進めてください(Tailscale を入れる → Mac にリンクを送る → QR を読む)。

### 2. Mac

1. iPhone から届いたリンク(または [TailDesk のダウンロード](https://github.com/ken-kurosu/taildesk-releases/releases/latest/download/TailDeskHost.zip))をクリックします。
2. ダウンロードされた「TailDeskHost」を開き、「開いてもよいですか」で「開く」、「アプリケーションフォルダに入れて開きます」で「入れる」を押します。
3. 「TailDesk の準備」が出ます。上から順にボタンを押すだけです。
   - Tailscale を入れてログイン(iPhone / iPad と同じアカウント)
   - 画面を映す許可・操作する許可(設定が開くので TailDeskHost のスイッチをオン)
4. 終わると QR コードが出るので、iPhone / iPad の TailDesk で読み取れば完了です。

ログイン時の自動起動と、電源につないでいる間のスリープ防止は TailDesk が自動で行います。

## Mac から別の Mac を操作する

自宅の Mac からオフィスの Mac を操作する、といった使い方もできます。操作する側の Mac は Apple シリコン(M1 以降)が必要です(iPad 版の TailDesk をそのまま Mac で動かします)。

1. **操作される側の Mac** は、上の「2. Mac」の手順で TailDesk(Mac 用)を入れておきます。
2. **操作する側の Mac** で App Store から「TestFlight」を入れ、TestFlight の招待リンクをその Mac で開いて TailDesk をインストールします(iPhone / iPad と同じ Apple ID なら、TestFlight の一覧にもう出ています)。
3. 操作する側の Mac にも Tailscale を入れ、同じアカウントでログインします。
4. 操作される側の Mac のメニューバーの TailDesk →「ペアリング開始…」で窓を出します。
5. 操作する側の Mac で TailDesk を開き、右上の「+」→「手入力」で、窓に出ている「Mac の住所」(100.x.x.x)・12 桁の指紋・6 桁のコードを入れれば完了です(Mac ではカメラで QR を読まないため、手入力にします)。

マウスとキーボードはそのまま操作される側の Mac に届きます。

## よくあること

- **Tailscale で「管理者の承認が必要」と出る**: Tailscale の管理画面(https://login.tailscale.com/admin/machines)でその端末を承認してください。
- **QR を出しても見えない**: 最新版では QR の窓が最前面に出ます。古い版を使っている場合は更新してください。
- **Mac がスリープしているとつながりません**: 電源につないでおけば、TailDesk がスリープを止めます(バッテリーのときは止めません)。

## 端末をなくしたとき

Mac のメニューバーの TailDesk →「ペアリング済みの端末」から、その端末の「登録を解除」を選んでください。以後その端末からはつながりません。iPad / iPhone の TailDesk の「はじめに」から Face ID ロックをオンにしておくと安心です。

## 安全のための設計

- Mac は Tailscale のネットワーク(100.x.x.x)からの接続しか受け付けません。
- ペアリングした端末だけが操作できます(端末ごとの証明書で相互に確かめます)。
- 通信はすべて TLS 1.3 で暗号化され、開発者のサーバーは経由しません。
- パスワード管理アプリでコピーした内容は iPad / iPhone に送りません。

## プライバシー

[プライバシーポリシー](PRIVACY.md)
