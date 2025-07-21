# 🎓 BlueLink - 大学生向け時間割シェアアプリ

![BlueLink](https://img.shields.io/badge/BlueLink-時間割シェア-blue)
![Version](https://img.shields.io/badge/version-3.0-green)
![Status](https://img.shields.io/badge/status-完全動作-success)

## 📱 アプリ概要

**BlueLink**は、大学生が友達の授業状況を一目で確認できるWebアプリです。

**「今、友達は授業中？空いてる？」**
そんな疑問を瞬時に解決します！

## ✨ 主な機能

### 🔐 ユーザー機能
- ✅ ユーザー登録・ログイン
- ✅ プロフィール管理・編集

### 📅 時間割機能
- ✅ 時間割の登録・編集・削除
- ✅ 授業詳細（教室、教授名）
- ✅ リアルタイム保存

### 👥 友達機能
- ✅ 友達検索・追加
- ✅ 友達申請の送信・承認・拒否
- ✅ QRコードによる友達追加
- ✅ 友達の現在の授業状況をリアルタイム表示

### 💬 メッセージ機能
- ✅ 友達とのチャット
- ✅ リアルタイムメッセージ

## 🛠️ 技術構成

### フロントエンド
- **React** + **Vite**
- **Tailwind CSS**
- **Lucide React**

### バックエンド
- **Flask** (Python)
- **SQLite** (データベース)
- **Flask-SQLAlchemy**
- **Flask-CORS**

## 🚀 使い方

### 1. ローカル実行

#### バックエンド起動
```bash
cd "timetable-api 6"
pip install -r requirements.txt
python src/main.py
```

#### フロントエンド起動
```bash
cd timetable-share
npm install
npm run dev
```

### 2. アクセス
- フロントエンド: http://localhost:5173
- バックエンド: http://localhost:5001

### 3. 開発環境の設定

#### 必要な環境
- **Python**: 3.8以上
- **Node.js**: 16以上
- **npm**: 8以上

#### 初回セットアップ
1. リポジトリをクローン
2. バックエンドの依存関係をインストール
3. フロントエンドの依存関係をインストール
4. データベースが自動作成される

#### トラブルシューティング
- **ポート5001が使用中**: macOSのAirPlay Receiverを無効化するか、`main.py`でポート番号を変更
- **依存関係エラー**: `date-fns`と`react-day-picker`のバージョン互換性を確認
- **データベースエラー**: `instance`ディレクトリの権限を確認
- **プロキシエラー**: `vite.config.js`のプロキシ設定を確認

## 📁 プロジェクト構造

```
bluelink-app/
├── timetable-api 6/        # バックエンド
│   ├── instance/
│   │   └── timetable.db    # SQLiteデータベース
│   ├── src/
│   │   ├── main.py         # メインアプリ
│   │   ├── models/         # データベースモデル
│   │   │   ├── user.py     # ユーザーモデル
│   │   │   ├── timetable.py # 時間割モデル
│   │   │   ├── friend.py   # 友達関係モデル
│   │   │   ├── message.py  # メッセージモデル
│   │   │   └── profile.py  # プロフィールモデル
│   │   └── routes/         # APIルート
│   │       ├── auth.py     # 認証API
│   │       ├── user.py     # ユーザーAPI
│   │       ├── timetable.py # 時間割API
│   │       ├── friends.py  # 友達API
│   │       ├── messages.py # メッセージAPI
│   │       ├── profiles.py # プロフィールAPI
│   │       └── qr.py       # QRコードAPI
│   └── requirements.txt    # Python依存関係
├── timetable-share/        # フロントエンド
│   ├── src/
│   │   ├── components/     # Reactコンポーネント
│   │   └── App.jsx         # メインアプリ
│   └── package.json        # Node.js依存関係
└── README.md               # このファイル
```

## 🎯 使用手順

### 1. アカウント作成
1. アプリにアクセス
2. 新規登録でアカウント作成

### 2. 時間割登録
1. 「マイ時間割」で授業を追加
2. 授業名、教室、教授名を入力

### 3. 友達追加
1. 「友達検索」でユーザー検索
2. 友達申請を送信
3. QRコードでも追加可能

### 4. 授業状況確認
1. ダッシュボードで友達の状況確認
2. 🔴授業中 / 🟢空き時間 をリアルタイム表示

## 📊 システム仕様

- **対応人数**: 100人程度
- **データベース**: SQLite
- **認証**: セッション認証
- **デザイン**: レスポンシブ対応

### データベーステーブル
- **users**: ユーザー情報（UUID主キー）
- **timetables**: 時間割データ
- **friends**: 友達関係（申請・承認システム）
- **messages**: チャットメッセージ
- **profiles**: プロフィール詳細情報
- **conversations**: 会話履歴

## 🔒 セキュリティ

- **パスワードハッシュ化**: Werkzeugの`scrypt`アルゴリズムを使用
- **セッション管理**: Flask組み込みセッション機能
- **SQLインジェクション対策**: SQLAlchemyのORM使用
- **CORS設定**: 適切なクロスオリジン設定
- **UUID主キー**: 推測困難なユーザーID

### パスワードセキュリティ
- 平文保存なし（ハッシュ値のみ保存）
- ソルト付きハッシュ化
- 安全な比較関数使用

## 🚀 今後の予定

### セキュリティ強化
- [ ] JWT認証の導入
- [ ] 2要素認証（2FA）
- [ ] API レート制限

### 機能拡張
- [ ] プッシュ通知
- [ ] リマインダー機能
- [ ] グループチャット
- [ ] 授業評価システム
- [ ] 出席管理機能

### インフラ改善
- [ ] PostgreSQL移行
- [ ] Redis キャッシュ
- [ ] Docker対応
- [ ] モバイルアプリ化（React Native）

## 📄 ライセンス

MIT License

---

**BlueLink** - 友達の授業状況を一目で確認 🎓

