# 監査と認証

## ASVS 認証と認証マークに対する OWASP の見解

OWASP はベンダ中立の非営利組織であり、現在、ベンダ、検証者、ソフトウェアの認証は行っていません。

そのような保証の表明、認証マーク、認証はいずれも OWASP によって公式に検査、登録、認証されたものではありません。そのような見解に依存している組織は ASVS 認証を主張する第三者や認証マークについて、その信頼性に注意する必要があります。

これは、OWASP の公式な認証であると主張しない限り、組織がこのような保証サービスを提供することを妨げるものではありません。

## 認証機関のためのガイダンス

アプリケーションセキュリティ検証標準はアプリケーションのオープンブック検証として使用できます。特にレベル 2 とレベル 3 の検証には、設計者や開発者、プロジェクト文書、ソースコード、(役割ごとにひとつ以上のアカウントへのアクセスを含む) テストシステムへの認証されたアクセスといった、主要リソースへのオープンで自由なアクセスを含みます。

歴史上、ペネトレーションテストとソースコードレビューは「例外による」問題を含んでいました。つまり、不合格のテストのみが最終レポートに示されます。認証機関は (特に SSO 認証などの主要コンポーネントがスコープ外の場合) 検証のスコープ、合格および不合格のテストを含む検証結果の要約、不合格のテストへの解決法の明確な指示をレポートに含める必要があります。

特定の検証要件はテスト中のアプリケーションに適用されない場合があります。例えば、クライアント実装なしで顧客にステートレスサービス層 API を提供する場合、V3 セッション管理の要件の多くは直接適用されません。そのような場合、認証機関は依然として ASVS の完全な順守を主張することができますが、そのような除外された検証要件が適用されない理由を明確にレポートに示さなければなりません。

詳細な調書、スクリーンショットやムービー、問題を確実かつ繰り返し利用するためのスクリプト、傍受したプロキシログなどのテストの電子記録、クリーンアップリストなどの関連メモを保持することは標準的な業界の慣行と考えられます。そして、最も疑わしい開発者の発見の証拠として本当に役に立ちます。単にツールを実行して不合格を報告するだけでは十分ではありません。認証レベルのすべての問題がテストされ、余すところなくテストされている十分な証跡を (まったく) 提供していません。異議申し立てがあった場合に備えて、それぞれすべての検証要件が実際にテストされたことを実証するのに十分な証跡が必要となります。

### テスト手法

認証機関は適切なテスト手法を自由に選択できますが、レポートに記載する必要があります。

テスト対象のアプリケーションと検証要件に応じて、結果に均一な信頼性を得るためにさまざまなテスト手法を使用できます。例えば、アプリケーションの入力検証メカニズムの有効性を妥当性確認するには、手動ペネトレーションテストで分析するかソースコード解析を用います。

#### 自動セキュリティテストツールの役割

自動ペネトレーションテストツールの使用は、できるだけ多くの範囲をカバーするために推奨されています。

自動ペネトレーションテストツールだけを使用して ASVS 検証を完全に完了することはできません。レベル 1 の要件の大部分は自動テストを使用して実行できますが、要件全体の大半は自動ペネトレーションテストには適していません。

アプリケーションセキュリティ業界が成熟するにつれて、自動テストと手動テストの境界があいまいになっていることに注意してください。自動ツールは専門家により手動で調整されることが多く、手動テスト担当者はさまざまな自動テストツールを活用することがよくあります。

#### ペネトレーションテストの役割

バージョン 4.0 では、ソースコード、ドキュメント、開発者にアクセスすることなくレベル 1 を完全にペネトレーションテストできるようにしました。OWASP Top 10 2017 A10 に準拠するための必要な二つのログ記録の項目は、OWASP Top 10 2017 の場合と同様に、インタビュー、スクリーンショット、その他の証跡収集が必要になります。しかし、必要な情報にアクセスせずにテストすることは、ソースのレビュー、脅威の特定、管理策の欠如、そしてより短期間での十分なテスト実行の可能性を見逃すため、セキュリティ検証の理想的な方法ではありません。

可能であれば、開発者、ドキュメント、コードへのアクセス、および本番用ではないデータでのテストアプリケーションへのアクセスが、レベル 2 またはレベル 3 アセスメントを実行する際に必要です。これらのレベルで行われるペネトレーションテストには、「ハイブリッドレビュー」や「ハイブリッドペネトレーションテスト」と呼ぶ、このレベルのアクセスが必要です。
