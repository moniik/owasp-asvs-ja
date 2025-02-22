# 付録 A: 用語集

- **アドレス空間配置のランダム化** (Address Space Layout Randomization, ASLR) – メモリ破壊バグの悪用をより困難にする手法です。
- **許可リスト** (Allow list) – 許可されたデータまたは操作のリストです。例えば、入力の検証を実行できる文字のリストです。
- **アプリケーションセキュリティ** (Application Security) – アプリケーションレベルのセキュリティは基礎となるオペレーティングシステムや接続されるネットワークにフォーカスするのではなく、開放型システム間相互接続参照モデル (OSIモデル) のアプリケーション層を構成するコンポーネントの分析にフォーカスします。
- **アプリケーションセキュリティ検証** (Application Security Verification) – OWASP ASVS に対するアプリケーションの技術的評価です。
- **アプリケーションセキュリティ検証報告書** (Application Security Verification Report) – 対象とするアプリケーションの検証者が作成した全体的な結果と分析をまとめた報告書です。
- **認証** (Authentication) – アプリケーションユーザの申請IDを検証します。
- **自動検証** (Automated Verification) – 脆弱性シグネチャを使用して問題を発見する自動ツール (動的分析ツール、静的解析ツール、のいずれかもしくはその両方) を使用する検証です。
- **ブラックボックステスト** (Black Box Testing) – アプリケーションの機能を内部構造や動作に頼らすに検査するソフトウェアテストの手法です。
- **コンポーネント** (Component) – 自己完結型のコード単位です。他のコンポーネントと通信するディスクやネットワークに関連するインタフェースを持ちます。
- **クロスサイトスクリプティング** (Cross-Site Scripting, XSS) – クライアント側のスクリプトをコンテンツに流入することを可能にする、Web アプリケーションで典型的に見られるセキュリティ脆弱性です。
- **暗号モジュール** (Cryptographic Module) – 暗号アルゴリズムを実装し、暗号鍵を生成するハードウェア、ソフトウェア、ファームウェアです。
- **共通脆弱性タイプ一覧** (Common Weakness Enumeration, CWE) - コミュニティにより開発された一般的なソフトウェアセキュリティ脆弱性のリストです。これは共通言語、ソフトウェアセキュリティツールのものさし、および脆弱性識別、緩和、予防のためのベースラインとして機能します。
- **設計検証** (Design Verification) – アプリケーションのセキュリティアーキテクチャの技術的評価です。
- **動的アプリケーションセキュリティテスト** (Dynamic Application Security Testing, DAST) – 実行状態のアプリケーションのセキュリティ脆弱性を示す条件を検出するように設計されたテスト技法です。
- **動的検証** (Dynamic Verification) – 脆弱性シグネチャを使用してアプリケーションの実行中に問題を発見する自動ツールを使用する検証です。
- **ファイド** (Fast IDentity Online, FIDO) - バイオメトリクス、トラステッドプラットフォームモジュール (Trusted Platform Module, TPM) 、USB セキュリティトークンなど、さまざまな認証方式を使用できるようにする一連の認証標準です。
- **グローバル一意識別子** (Globally Unique Identifier, GUID) – ソフトウェアで識別子として使用される一意の参照番号です。
- **ハイパーテキスト転送プロトコル** (Hyper Text Transfer Protocol, HTTP) – 分散、協調、ハイパーメディア情報システムのためのアプリケーションプロトコルです。World Wide Web のためのデータ通信の基盤です。
- **ハードコードされた鍵** (Hardcoded Keys) – コード、コメント、ファイルなどファイルシステムに格納されている暗号鍵です。
- **ハードウェアセキュリティモジュール** (Hardware Security Module, HSM) - 暗号化鍵とその他のシークレットを保護された方法で保存できるハードウェアコンポーネントです。
- **Hibernate クエリ言語** (Hibernate Query Language, HQL) - Hibernate ORM ライブラリで使用される SQL と似た外観のクエリ言語です。
- **入力バリデーション** (Input Validation) – 信頼できないユーザ入力の正規化およびバリデーションです。
- **悪性コード** (Malicious Code) – 開発中にアプリケーションに導入された、アプリケーションの意図されたセキュリティポリシーを迂回する、アプリケーションの所有者に知られていないコードです。ウイルスやワームなどのマルウェアと同じではありません。
- **マルウェア** (Malware) – アプリケーションユーザや管理者に知られることなく実行時にアプリケーションに導入される実行可能コードです。
- **オープンウェブアプリケーションセキュリティプロジェクト** (Open Web Application Security Project, OWASP) – アプリケーションソフトウェアのセキュリティを強化することにフォーカスする世界規模のフリーでオープンなコミュニティーです。私たちの使命はアプリケーションのセキュリティを「可視化」することで、人々や組織がアプリケーションのセキュリティリスクについて意思決定を下せるようにすることです。参照：[http://www.owasp.org/](http://www.owasp.org/)
- **ワンタイムパスワード** (One-time Password, OTP) - 一度だけ使用するために一意に生成されるパスワードです。
- **オブジェクトリレーショナルマッピング** (Object-relational Mapping, ORM) - アプリケーション互換オブジェクトモデルを使用して、アプリケーションプログラム内でリレーショナル/テーブルベースのデータベースを参照および照会できるようにするために使用されるシステムです。
- **パスワードベース鍵導出関数2** (Password-Based Key Derivation Function 2, PBKDF2) - 入力テキスト (パスワードなど) および追加のランダムソルト値から強力な暗号鍵を作成するために使用される特殊な一方向アルゴリズムです。元のパスワードの代わりに結果の値が保存されている場合には、パスワードをオフラインで解読することが困難になります。
- **個人識別情報** (Personally Identifiable Information, PII) – 一人の人間を識別、接触、探索するため、あるいはコンテキストの個人を特定するために、それ自身または他の情報と共に使用することができる情報です。
- **位置独立実行形式** (Position-independent executable, PIE) – 一次メモリのどこかに配置され、絶対アドレスに関係なく適切に実行される、マシンコードの本体です。
- **公開鍵基盤** (Public Key Infrastructure, PKI) – 公開鍵をエンティティのそれぞれのアイデンティティにバインドする仕組みです。バインディングは認証局 (Certificate Authority, CA) における証明書の登録および発行のプロセスによって確立されます。
- **公衆交換電話網** (Public Switched Telephone Network, PSTN) - 固定電話と携帯電話の両方を含む従来の電話網です。
- **依存パーティ** (Relying Party, RP) - 一般的には別の認証プロバイダに対して認証されたユーザに依存するアプリケーションです。アプリケーションは認証プロバイダが提供するある種のトークンまたは一連の署名済みアサーションに依存して、ユーザが本人であることを信頼します。
- **静的アプリケーションセキュリティテスト** (Static Application Security Testing, SAST) – コーディングや設計条件のセキュリティ上の脆弱性を示すため、アプリケーションコード、バイトコード、バイナリを解析するように設計された一連の技法です。SASTソリューションはアプリケーションを非稼動状態で「内側から」分析します。
- **ソフトウェア開発ライフサイクル** (Software Development Lifecycle, SDLC) – 初期要件からデプロイメントおよび保守に至るまでのソフトウェア開発における段階的なプロセスです。
- **セキュリティアーキテクチャ** (Security Architecture) – アプリケーション設計の抽象概念です。セキュリティ管理策がどこでどのように使用されているかを特定し説明します。また、ユーザとアプリケーションの両方のデータの場所と機密性を特定し説明します。
- **セキュリティ設定** (Security Configuration) – セキュリティ管理の使用方法に影響を与えるアプリケーションの実行時設定です。
- **セキュリティ管理** (Security Control) – (アクセス制御チェックなどの) セキュリティチェックを実行する、もしくは (監査記録の生成などの) 呼び出されたときにセキュリティ効果をもたらす、機能やコンポーネントです。
- **サーバサイドリクエストフォージェリ** (Server-side Request Forgery, SSRF) - サーバで実行されるコードがデータを読み取りまたは送信する URL を提供または変更することにより、さーばーの機能を悪用して内部リソースを読み取りまたは更新する攻撃です。
- **シングルサインオン認証** (Single Sign-on Authentication, SSO) – ユーザがひとつのアプリケーションにログインするとき、他のアプリケーションに再認証の必要なく自動的にログインするものです。例えば、Google にログインすると、YouTube, Google Docs, Gmail などの他の Google サービスにアクセスする際に、自動的にログインします。
- **SQL インジェクション** (SQL Injection, SQLi) – 悪意のあるSQL文がエントリポイントに挿入される、データ駆動型アプリケーションの攻撃に使用されるコードインジェクション手法です。
- **スケーラブルベクターグラフィックス** (Scalable Vector Graphics, SVG) - 。
- **タイムベース OTP** (Time-based OTP) - OTP を生成する手法で、現在の時刻がパスワードを生成するアルゴリズムの一部として機能します。
- **脅威モデリング** (Threat Modeling) – 脅威エージェント、セキュリティゾーン、セキュリティ管理、重要な技術的およびビジネス的資産を特定することにより、より洗練されたセキュリティアーキテクチャを開発することからなる手法です。
- **トランスポート層セキュリティ** (Transport Layer Security, TLS) – ネットワーク上の通信セキュリティを提供する暗号プロトコルです。
- **トラステッドプラットフォームモジュール** (Trusted Platform Module, TPM) - 通常はマザーボードなどのより大きなハードウェアコンポーネントに接続され、そのシステムの「信頼の基点 (Root of Trust)」として機能する HSM の一種です。
- **二要素認証** (Two-factor authentication, 2FA) - アカウントログインに第二レベルの認証を追加します。
- **ユニバーサルセカンドファクタ** (Universal 2nd Factor, U2F) - USB または NFC セキュリティキーを二番目の認証要素として使用できるようにするために FIDO により作成された標準の一つです。
- **URI/URL/URL フラグメント** (URI/URL/URL fragments) – Uniform Resource Identifier は名前や Web リソースを識別するために使用される文字列です。Uniform Resource Locator は多くの場合リソースへの参照として使用されます。
- **検証者** (Verifier) – OWASP ASVS 要件に照らし合わせてアプリケーションをレビューしている人またはチームです。
- **見たままが得られる (ウィジウィグ)** (What You See Is What You Get, WYSIWYG) - レンダリングを制御するために使用されるコーディングを表示するのではなく、レンダリング時にコンテンツが実際にどのように見えるかを示すリッチコンテンツエディタのタイプです。
- **X.509 証明書** (X.509 Certificate) – 広く受け入れられている国際 X.509 公開鍵基盤 (Public Key Infrastructure, PKI) 標準を使用するデジタル証明書であり、公開鍵が証明書に含まれるユーザ、コンピュータ、サービスのIDに属することを検証します。
- **XML 外部エンティティ** (XML eXternal Entity, XXE) - 宣言されたシステム識別子を介してローカルまたはリモートコンテンツにアクセスできる XML エンティティのタイプです。これはさまざまなインジェクション攻撃につながる可能性があります。
