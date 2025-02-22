# V14 構成

## 管理目標

検証対象のアプリケーションが以下を備えていることを確認します。

* セキュアで、再現性があり、自動化されたビルド環境。
* 古くなったコンポーネントやセキュアでないコンポーネントがアプリケーションに含まれないような、堅牢なサードパーティライブラリ、依存関係、構成管理。

箱から出してすぐのアプリケーションの構成はインターネット上で安全であるべきです。つまり、そのままで安全な構成であるということです。

## V14.1 ビルドとデプロイ

ビルドパイプラインはリピート可能なセキュリティの基盤です。セキュアではないものが発見されるたびに、ソースコード、ビルド、またはデプロイメントスクリプトで解決され、自動的にテストされます。既知のセキュリティ問題が本番環境にデプロイされることを防ぐために、ビルドを警告または中断する自動セキュリティおよび依存関係チェックを備えたビルドパイプラインの使用を強くお勧めします。手動で不規則に実行された手順は回避できないセキュリティ上の誤りに直接つながります。

業界が DevSecOps モデルに移行するにつれて、「既知の良好な」状態を達成するために、デプロイメントと構成の継続的な可用性と完全性を確保することが重要です。これまで、システムがハックされた場合、それ以上の侵入が行われていないことを証明するのに数日から数か月かかりました。今日では、ソフトウェア定義のインフラストラクチャ、ダウンタイムゼロでの迅速な A/B デプロイメント、自動コンテナ化ビルドの出現により、危殆化されたシステムに代わる「既知の良好な」代替品を自動的かつ継続的に構築、堅牢化、デプロイできます。

従来のモデルがまだ存在している場合は、手動で手順を実行してその構成を堅牢化およびバックアップし、危殆化されたシステムをタイムリーに完全性が高く危殆化されていないシステムに迅速に置き換えることができる必要があります。

このセクションに準拠するには自動ビルドシステムと、ビルドおよびデプロイメントスクリプトへのアクセスが必要です。

| # | 説明 | L1 | L2 | L3 | CWE |
| :---: | :--- | :---: | :---: | :---: | :---: |
| **14.1.1** | アプリケーションのビルドおよびデプロイメントプロセスが、CI / CD 自動化、自動構成管理、自動デプロイメントスクリプトなど、セキュアでリピート可能な方法で実行されている。 | | ✓ | ✓ | |
| **14.1.2** | スタックのランダム化、データ実行防止など、利用可能なすべてのバッファオーバーフロー保護および警告を有効にし、安全ではないポインタ、メモリ、書式文字列、整数、文字列操作が見つかった場合にはビルドを中止するようにコンパイラフラグを設定している。 | | ✓ | ✓ | 120 |
| **14.1.3** | [修正] すべてのサードパーティ製品、ライブラリ、フレームワーク、サービスにおいて、それぞれの推奨事項に従って、設定の堅牢化が実行されている。 | | ✓ | ✓ | 16 |
| **14.1.4** | アプリケーション、構成、およびすべての依存関係が、文書化およびテストされた Runbook から作成された自動デプロイメントスクリプトを使用して遅延なく再デプロイできること、またはバックアップからタイムリーにリストアできる。 | | ✓ | ✓ | |
| **14.1.5** | 改竄を検出するために、許可された管理者がすべてのセキュリティ関連構成の完全性を検証できる。 | | | ✓ | |
| **14.1.6** | [14.2.2 から移動] すべての不要な機能、ドキュメント、サンプルアプリケーション、構成が削除されている。 | ✓ | ✓ | ✓ | 1002 |
| **14.1.7** | [追加] 本番環境にテストコードが含まれていない。 | | ✓ | ✓ | 489 |

## V14.2 依存関係

依存関係管理はあらゆる種類のアプリケーションを安全に運用するために不可欠です。古い依存関係やセキュアでない依存関係で最新に保てないことが、これまでで最大かつ最高となる攻撃の根本原因です。

注意: レベル 1 では、14.2.1 順守はより正確なビルド時の静的コード解析や依存関係解析よりも、クライアント側および他のライブラリやコンポーネントの監視や検出に関連します。これらのより正確なテクニックは、必要に応じてインタビューにより発見可能です。

| # | 説明 | L1 | L2 | L3 | CWE |
| :---: | :--- | :---: | :---: | :---: | :---: |
| **14.2.1** | できれば依存関係チェッカーをビルド時またはコンパイル時に使用して、すべてのコンポーネントが最新である。 ([C2](https://owasp.org/www-project-proactive-controls/#div-numbering)) | ✓ | ✓ | ✓ | 1026 |
| **14.2.2** | [14.1.6 へ移動] | | | | |
| **14.2.3** | JavaScript ライブラリ、CSS 、Web フォントなどのアプリケーション資産がコンテンツ配信ネットワーク (Content Delivery Network, CDN) や外部のプロバイダで外部的にホストされている場合には、サブリソース完全性 (Subresource Integrity, SRI) を使用して資産の完全性を確認している。 | ✓ | ✓ | ✓ | 829 |
| **14.2.4** | サードパーティコンポーネントは事前定義済みで信頼でき、継続的に保守されているリポジトリから取得している。 ([C2](https://owasp.org/www-project-proactive-controls/#div-numbering)) | | ✓ | ✓ | 829 |
| **14.2.5** | 使用しているすべてのサードパーティライブラリのソフトウェア部品表 (SBOM) が保守されている。 ([C2](https://owasp.org/www-project-proactive-controls/#div-numbering)) | | ✓ | ✓ | |
| **14.2.6** | アプリケーションに必要な動作のみを開示するためにサードパーティライブラリをサンドボックス化またはカプセル化することでアタックサーフェスが減少している。 ([C2](https://owasp.org/www-project-proactive-controls/#div-numbering)) | | ✓ | ✓ | 265 |
| **14.2.7** | [追加] サードパーティコンポーネントが内部で所有および開発されたアプリケーションとは別に供給されている。 | ✓ | ✓ | ✓ | 441 |


注: 特定の言語およびパッケージマネージャには、複数の要素 (groupId や artifactId など) を使用してパッケージを識別することを要求するエコシステムがあります。これによりビルドプロセスでリソースをより具体的に識別できるようになります。そうでない場合、パッケージマネージャは含まれているリポジトリまたはミラーの順で動作します。検索順を具体的に示すには、パッケージマネージャに相談してください。


## V14.3 意図しないセキュリティ開示

デバッグコンソールなどの一般的な攻撃からの保護、クロスサイトスクリプティング (Cross-site Scripting, XSS) およびリモートファイルインクルージョン (Remote File Inclusion, RFI) 攻撃に対するハードルの引き上げ、そして多くのペネトレーションテストレポートの歓迎されない品質証明である厄介な情報露見「脆弱性」を排除するために、プロダクションの設定を堅牢化すべきです。これらの問題の多くは重大なリスクとみなされることはめったにありませんが、それらは他の脆弱性と連鎖しています。これらの問題がデフォルトで現れなければ、それはほとんどの攻撃が成功する前にハードルを引き上げます。

| # | 説明 | L1 | L2 | L3 | CWE |
| :---: | :--- | :---: | :---: | :---: | :---: |
| **14.3.1** | [削除, 7.4.1 と重複] | | | | |
| **14.3.2** | デバッグ機能、開発者コンソール、意図しないセキュリティ開示を排除するために、Web またはアプリケーションサーバおよびアプリケーションフレームワークのデバッグモードが本番環境で無効になっている。 | ✓ | ✓ | ✓ | 497 |
| **14.3.3** | HTTP ヘッダまたは HTTP レスポンスの一部がシステムコンポーネントの詳細なバージョン情報を開示していない。 | ✓ | ✓ | ✓ | 200 |
| **14.3.4** | [追加, 4.3.2 から分割] 明確に必要でない限りディレクトリ参照が無効化されている。 | ✓ | ✓ | ✓ | 548 |
| **14.3.5** | [追加, 4.3.2 から分割] アプリケーションは Thumbs.db, .DS_Store, .git, .svn フォルダなどのファイルやディレクトリメタデータの漏洩や開示を許していない。 | ✓ | ✓ | ✓ | |
| **14.3.6** | [12.5.1 から移動] 意図しない情報漏洩やソースコード漏洩を防ぐために、Web 層が特定のファイル拡張子を持つファイルのみを処理するように設定されている。例えば、バックアップファイル (.bak など) 、一時作業ファイル (.swp など) 、圧縮ファイル (.zip, .tar.gz など) やエディタで一般的に使用されるその他の拡張子は、必要でない限りブロックする。 | ✓ | ✓ | ✓ | 552 |

## V14.4 HTTP セキュリティヘッダ

| # | 説明 | L1 | L2 | L3 | CWE |
| :---: | :--- | :---: | :---: | :---: | :---: |
| **14.4.1** | すべての HTTP レスポンスに Content-Type ヘッダが含まれている。またコンテンツタイプが text/*, /+xml および application/xml の場合には安全な文字セット (UTF-8, ISO-8859-1 など) を指定する。コンテンツは提供された Content-Type ヘッダと一致する必要がある。 | ✓ | ✓ | ✓ | 173 |
| **14.4.2** | [削除] | | | | |
| **14.4.3** | HTML, DOM, JSON, JavaScript インジェクション脆弱性などの XSS 攻撃に対する影響を軽減するのに役立つコンテンツセキュリティポリシー (Content Security Policy, CSP) レスポンスヘッダが設定されている。 | ✓ | ✓ | ✓ | 1021 |
| **14.4.4** | すべてのレスポンスに X-Content-Type-Options: nosniff ヘッダが含まれている。 | ✓ | ✓ | ✓ | 116 |
| **14.4.5** | [修正] Strict-Transport-Security ヘッダが、Strict-Transport-Security: max-age=31536000; includeSubdomains のように、すべてのレスポンスとすべてのサブドメインに含まれている。 | ✓ | ✓ | ✓ | 523 |
| **14.4.6** | URL 内の機密情報が Referer ヘッダを介して信頼できない関係者に公開されないように、適切な Referrer-Policy ヘッダが含まれている。 | ✓ | ✓ | ✓ | 116 |
| **14.4.7** | Web アプリケーションのコンテンツはデフォルトでサードパーティのサイトに埋め込むことができない、および適切な Content-Security-Policy: frame-ancestors と X-Frame-Options レスポンスヘッダを使用して必要な場所でのみ正規のリソースの埋め込みが許可されている。 | ✓ | ✓ | ✓ | 1021 |
| **14.4.8** | [追加, 14.5.3 から分割] クロスオリジンリソース共有 (CORS) Access-Control-Allow-Origin ヘッダが信頼できるオリジンの厳密な許可リストを使用している。 "Access-Control-Allow-Origin: *" を使用する必要がある場合、レスポンスに機密情報が含まれていない。 | ✓ | ✓ | ✓ | 183 |


## V14.5 HTTP リクエストヘッダバリデーション

| # | 説明 | L1 | L2 | L3 | CWE |
| :---: | :--- | :---: | :---: | :---: | :---: |
| **14.5.1** | [修正] アプリケーションサーバが、アプリケーションや API によって使用されている HTTP メソッド (preflight リクエスト時の OPTIONS を含む) のみを受け入れる。 | ✓ | ✓ | ✓ | 749 |
| **14.5.2** | Origin ヘッダは攻撃者によって簡単に変更される可能性があるため、提供された Origin ヘッダが認証またはアクセス制御判定に使用されていない。 | ✓ | ✓ | ✓ | 346 |
| **14.5.3** | [修正, 14.4.8 へ分割] Origin ヘッダが目的のクロスオリジンリソース共有 (CORS) ポリシーを満たすために、許可されたオリジンの定義済みリストに対して妥当性確認されている。 | ✓ | ✓ | ✓ | 346 |
| **14.5.4** | 信頼できるプロキシまたは SSO デバイスにより追加されたベアラトークンなどの HTTP ヘッダがアプリケーションにより認証されている。 | | ✓ | ✓ | 306 |
| **14.5.5** | [追加] HEAD, OPTIONS, TRACE, または GET verb を使用する HTTP リクエストがバックエンドデータ構造を変更することや、状態変更アクションを実行することがない。これらのリクエストは安全なメソッドであるため、副作用を持つべきではない。 | ✓ | ✓ | ✓ | 650 |
| **14.5.6** | [追加] インフラストラクチャが RFC2616 に準拠しており、Transfer-Encoding ヘッダフィールドも存在する場合には Content-Length ヘッダフィールドを無視している。 | | ✓ | ✓ | 444 |
| **14.5.5** | [追加] アプリケーションが依存する HTTP セキュリティ機能をサポートしていない古いブラウザを使用しているユーザーに対して、Web アプリケーションが警告を発している。古いブラウザのリストは定期的に見直して更新する必要がある。 | | | ✓ | 1104 |

## V14.6 HTTP/2

| # | 説明 | L1 | L2 | L3 | CWE |
| :---: | :--- | :---: | :---: | :---: | :---: |
| **14.6.1** | [追加] Content-Length リクエストヘッダの値がビルトインのメカニズムを使用して計算された長さと一致している。 | ✓ | ✓ | ✓ | 400 |
| **14.6.2** | [追加] すべての Transfer-Encoding ヘッダがメッセージから削除されるか、リクエストが完全にブロックされている。 | ✓ | ✓ | ✓ | |
| **14.6.3** | [追加] フル CRLF (\r\n) シーケンスは HTTP/2 ヘッダ内で無効化されている。 | ✓ | ✓ | ✓ | 113 |

## 参考情報

詳しくは以下の情報を参照してください。

* [OWASP Web Security Testing Guide 4.1: Testing for HTTP Verb Tampering]( https://owasp.org/www-project-web-security-testing-guide/v41/4-Web_Application_Security_Testing/07-Input_Validation_Testing/03-Testing_for_HTTP_Verb_Tampering.html)
* [Content Security Policy Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Content_Security_Policy_Cheat_Sheet.html)
* [Exploiting CORS misconfiguration for BitCoins and Bounties](https://portswigger.net/blog/exploiting-cors-misconfigurations-for-bitcoins-and-bounties)
* [OWASP Web Security Testing Guide 4.1: Configuration and Deployment Management Testing](https://owasp.org/www-project-web-security-testing-guide/v41/4-Web_Application_Security_Testing/02-Configuration_and_Deployment_Management_Testing/README.html)
* [Sandboxing third party components](https://cheatsheetseries.owasp.org/cheatsheets/Third_Party_Javascript_Management_Cheat_Sheet.html#sandboxing-content)
* [Defining multiple repositories in maven](https://maven.apache.org/guides/mini/guide-multiple-repositories.html)
* [Software Component Verification Standard V2 L1-3 requirements](https://github.com/OWASP/Software-Component-Verification-Standard/blob/master/en/0x11-V2-Software_Bill_of_Materials.md)
