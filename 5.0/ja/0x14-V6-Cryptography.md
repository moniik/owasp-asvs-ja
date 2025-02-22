# V6 保存時における暗号化

## 管理目標

検証対象のアプリケーションが以下の上位要件を満たすことを確認します。

* すべての暗号化モジュールはセキュアな方法で失敗し、エラーは正しく処理されています。
* 適切な乱数生成器が使用されています。
* 鍵へのアクセスはセキュアに管理されています。

## V6.1 データ分類

最も重要な資産はアプリケーションにより処理、保存、送信されるデータです。保管データのデータ保護ニーズを正しく分類するために、常にプライバシー影響評価を実施してください。

| # | 説明 | L1 | L2 | L3 | CWE |
| :---: | :--- | :---: | :---: | :---: | :---: |
| **6.1.1** | 個人識別情報 (Personally Identifiable Information, PII)、機密性の高い個人情報、EU の GDPR の対象となる可能性が高いと判断されたデータなど、規制されている個人データが保存時に暗号化されて保管されている。 | | ✓ | ✓ | 311 |
| **6.1.2** | 医療記録、医療機器の明細、匿名化されていない調査記録など、規制されている医療データが保存時に暗号化されて保管されている。 | | ✓ | ✓ | 311 |
| **6.1.3** | 金融口座、債務不履行やクレジットの履歴、税務記録、支払い履歴、受益者、匿名化されていない市場や調査記録など、規制されている金融データが保存時に暗号化されて保管されている。 | | ✓ | ✓ | 311 |

## V6.2 アルゴリズム

暗号化における近年の進歩により、以前は安全であったアルゴリズムや鍵長はもはやデータを保護するのに安全ではなく十分でもありません。したがって、アルゴリズムを変更することが可能であるべきです。

このセクションはペネトレーションテストが容易ではありませんが、L1 がほとんどの項目に含まれていなくとも、開発者はこのセクション全体を必須とみなすべきです。

| # | 説明 | L1 | L2 | L3 | CWE |
| :---: | :--- | :---: | :---: | :---: | :---: |
| **6.2.1** | すべての暗号化モジュールがセキュアに失敗し、パディングオラクル攻撃を有効にしない方法でエラーが処理される。 | ✓ | ✓ | ✓ | 310 |
| **6.2.2** | カスタムコードによる暗号化方式の代わりに、業界で実績のある、または政府が承認した暗号化アルゴリズム、モード、ライブラリが使用されている。 ([C8](https://owasp.org/www-project-proactive-controls/#div-numbering)) | | ✓ | ✓ | 327 |
| **6.2.3** | 最新のアドバイスを使用して、暗号化初期化ベクトル、暗号構成、ブロックモードがセキュアに構成されている。 | | ✓ | ✓ | 326 |
| **6.2.4** | 乱数、暗号化アルゴリズムやハッシュアルゴリズム、鍵長、ラウンド、暗号方式やモード、が暗号の破壊を防ぐためにいつでも再構成、アップグレード、交換できる。 ([C8](https://owasp.org/www-project-proactive-controls/#div-numbering)) | | ✓ | ✓ | 326 |
| **6.2.5** | 既知のセキュアではないブロックモード (ECB など) 、パディングモード (PKCS#1 v1.5 など) 、ブロックサイズの小さい暗号 (Triple-DES, Blowfish など) 、脆弱なハッシュアルゴリズム (MD5, SHA1 など) は後方互換性のために必要とされない限り使用されない。 | | ✓ | ✓ | 326 |
| **6.2.6** | ナンス、初期化ベクトル、その他の使い捨て番号を特定の暗号化鍵で複数回使用していない。生成方法は使用されているアルゴリズムに適している必要がある。 | | ✓ | ✓ | 326 |
| **6.2.7** | 暗号文が不正に変更されていないことを確認するために、暗号化されたデータが署名、認証された暗号モード、または HMAC によって認証されている。 | | | ✓ | 326 |
| **6.2.8** | 情報漏洩を防ぐために、すべての暗号化操作が一定時間であり、比較、計算、リターンの際に「短絡」操作がない。 | | | ✓ | 385 |

## V6.3 乱数値

真正疑似乱数生成 (Pseudo-random Number Generation, PRNG) を正しく実行することは非常に困難です。一般的に、システム内の優れたエントロピーソースは使い過ぎるとすぐに枯渇しますが、ランダム性の少ないソースは鍵や秘密が予測可能となる可能性があります。

| # | 説明 | L1 | L2 | L3 | CWE |
| :---: | :--- | :---: | :---: | :---: | :---: |
| **6.3.1** | 乱数値が攻撃者に推測されないことを意図している場合、すべての乱数値、ランダムファイル名、ランダム GUID、ランダム文字列は暗号モジュールの承認済みで暗号論的にセキュアな乱数生成器を使用して生成される。 | | ✓ | ✓ | 338 |
| **6.3.2** | ランダム GUID は GUID v4 アルゴリズム、および暗号論的にセキュアな疑似乱数生成器 (Cryptographically-secure Pseudo-random Number Generator, CSPRNG) を使用して作成されている。他の疑似乱数生成器を使用して作成された GUID は予測可能である可能性がある。 | | ✓ | ✓ | 338 |
| **6.3.3** | アプリケーションに大きな負荷がかかっている場合でも乱数は適切なエントロピーで作成される、またはそのような状況ではアプリケーションが適切にデグレードする。 | | | ✓ | 338 |

## V6.4 秘密管理

このセクションはペネトレーションテストが容易ではありませんが、L1 がほとんどの項目に含まれていなくとも、開発者はこのセクション全体を必須とみなすべきです。

| # | 説明 | L1 | L2 | L3 | CWE |
| :---: | :--- | :---: | :---: | :---: | :---: |
| **6.4.1** | [修正] 鍵保管庫などの秘密管理ソリューションが、サービスアカウントやサードパーティアプリケーションのクレデンシャルなどの秘密をセキュアに作成、保存、アクセス制御、破壊するために使用されている。 ([C8](https://owasp.org/www-project-proactive-controls/#div-numbering)) | | ✓ | ✓ | 798 |
| **6.4.2** | 鍵マテリアルはアプリケーションに開示されておらず、代わりに暗号操作用の保管庫などの隔離されたセキュリティモジュールを使用している。 ([C8](https://owasp.org/www-project-proactive-controls/#div-numbering)) | | ✓ | ✓ | 320 |

## 参考情報

詳しくは以下の情報を参照してください。

* [OWASP Testing Guide 4.0: Testing for weak Cryptography](https://owasp.org/www-project-web-security-testing-guide/v41/4-Web_Application_Security_Testing/09-Testing_for_Weak_Cryptography/README.html)
* [OWASP Cheat Sheet: Cryptographic Storage](https://cheatsheetseries.owasp.org/cheatsheets/Cryptographic_Storage_Cheat_Sheet.html)
* [FIPS 140-2](https://csrc.nist.gov/publications/detail/fips/140/2/final)
