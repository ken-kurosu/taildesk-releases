# DokoDesk(旧名 DokoDesk)

外出先の iPhone / iPad / Mac から、自分の Mac を操作するリモートデスクトップです。
通信は [Tailscale](https://tailscale.com)(無料の VPN)を通り、iPad / iPhone と Mac が直接つながります。映像や操作が第三者のサーバーを経由することはありません。

## 必要なもの

- Apple シリコンまたは Intel の Mac(macOS 13 以降)
- iPad / iPhone(iOS 16 以降)
- Tailscale のアカウント(Google・Apple・Microsoft のアカウントで無料で作れます)

## 導入の手順(10 分ほど)

いちばん簡単なのは、**iPhone / iPad の DokoDesk を先に入れて、アプリの「はじめに」に沿って進める**方法です。Mac には iPhone からリンクを送れます。

### 1. iPhone / iPad

1. App Store で「DokoDesk」を入れます(テスト版は TestFlight の招待リンクから)。
2. DokoDesk を開くと「はじめに」が出ます。その順に進めてください(Tailscale を入れる → Mac にリンクを送る → QR を読む)。

### 2. Mac

1. iPhone から届いたリンク(または [DokoDesk のダウンロード](https://github.com/ken-kurosu/taildesk-releases/releases/latest/download/TailDeskHost.zip))をクリックします。
2. ダウンロードされた「TailDeskHost」を開き、「開いてもよいですか」で「開く」、「アプリケーションフォルダに入れて開きます」で「入れる」を押します。
3. 「DokoDesk の準備」が出ます。上から順にボタンを押すだけです。
   - Tailscale を入れてログイン(iPhone / iPad と同じアカウント)
   - 画面を映す許可・操作する許可(設定が開くので TailDeskHost のスイッチをオン)
4. 終わると QR コードが出るので、iPhone / iPad の DokoDesk で読み取れば完了です。

ログイン時の自動起動と、電源につないでいる間のスリープ防止は DokoDesk が自動で行います。

## Mac から別の Mac を操作する

自宅の Mac からオフィスの Mac を操作する、といった使い方もできます。操作する側の Mac は Apple シリコン(M1 以降)が必要です(iPad 版の DokoDesk をそのまま Mac で動かします)。

1. **操作される側の Mac** は、上の「2. Mac」の手順で DokoDesk(Mac 用)を入れておきます。
2. **操作する側の Mac** で App Store から「TestFlight」を入れ、TestFlight の招待リンクをその Mac で開いて DokoDesk をインストールします(iPhone / iPad と同じ Apple ID なら、TestFlight の一覧にもう出ています)。
3. 操作する側の Mac にも Tailscale を入れ、同じアカウントでログインします。
4. 操作される側の Mac のメニューバーの DokoDesk →「ペアリング開始…」で窓を出します。
5. 操作する側の Mac で、TestFlight から入れた **DokoDesk** を開きます(Launchpad かアプリケーションフォルダの「DokoDesk」。メニューバーに出る DokoDesk ではありません)。
6. 最初の画面の「**Mac を追加する**」を押し、4 の窓に出ている「Mac の住所」(100.x.x.x)を入れて「次へ」。続けて 12 桁の指紋と 6 桁のコードを入れて「ペアリング」を押せば完了です(Mac ではカメラで QR を読まないため、番号を入れてつなぎます)。

マウスとキーボードはそのまま操作される側の Mac に届きます。

## 料金

最初の 1 か月は無料です。その後は月額 290 円、または年額 2,400 円です。購入・解約は App Store(「設定」→ 自分の名前 →「サブスクリプション」)で行います。Mac 用の DokoDesk は無料です。

## よくあること

- **Tailscale で「管理者の承認が必要」と出る**: Tailscale の管理画面(https://login.tailscale.com/admin/machines)でその端末を承認してください。
- **QR を出しても見えない**: 最新版では QR の窓が最前面に出ます。古い版を使っている場合は更新してください。
- **Mac がスリープしているとつながりません**: 電源につないでおけば、DokoDesk がスリープを止めます(バッテリーのときは止めません)。

## 端末をなくしたとき

Mac のメニューバーの DokoDesk →「ペアリング済みの端末」から、その端末の「登録を解除」を選んでください。以後その端末からはつながりません。iPad / iPhone の DokoDesk の「はじめに」から Face ID ロックをオンにしておくと安心です。

## 安全のための設計

- Mac は Tailscale のネットワーク(100.x.x.x)からの接続しか受け付けません。
- ペアリングした端末だけが操作できます(端末ごとの証明書で相互に確かめます)。
- 通信はすべて TLS 1.3 で暗号化され、開発者のサーバーは経由しません。
- パスワード管理アプリでコピーした内容は iPad / iPhone に送りません。

## お問い合わせ

- 不具合や要望: [Issues](https://github.com/ken-kurosu/taildesk-releases/issues) に書き込んでください。
- メール: kurosu@i-kasa.com

## プライバシー

[プライバシーポリシー](PRIVACY.md)
