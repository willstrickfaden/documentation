---
kind: documentation
title: Watchdog アラート
---

## 概要

Watchdog アラート機能は、サービス、インフラストラクチャーおよびログの異常をプロアクティブに検出します。Watchdog は監視しているすべてのテクノロジーをスキャンし、異常な動作を検出します。異常な動作が Watchdog の異常パターンの 1 つに一致する場合、Watchdog はアラートを作成します。

## アラート

### Watchdog アラートの入手先

Watchdog アラートは、Datadog サイト内の 3 つの場所に表示されます。
- [Watchdog アラートフィード][1]
- [APM ホームページ][2]
- 個別の [APM サービス詳細画面][3]

### アラートの概要

各アラート概要カードは、1 つの異常に関する情報を伝えます。

{{< img src="watchdog/alerts/alerts_overview.png" alt="sms-service の send-sms エンドポイントにおけるエラーレートの上昇を示す Watchdog アラートカードのスクリーンショット" style="width:100%;">}}

アラート概要カードには、以下の項目があります。

1. Status: 異常は、**ongoing** (継続中) または **resolved** (解決済み) のいずれかです。
2. Timeline: どのような期間に異常が発生したかを説明します。
3. Message: 異常の内容を説明します。
4. Graph: 異常を視覚的に表現します。
5. Tags: 異常の範囲が表示されます。
6. [Impact][4] (利用可能な場合): 異常がどのユーザー、ビュー、またはサービスに影響を及ぼすかを説明します。

無関係なアラートを非表示にするには、そのアラートにカーソルを合わせます。右上に表示されるフォルダーアイコンをクリックします。

### アラート詳細

アラート概要カードの任意の場所をクリックすると、アラートの詳細ペインが表示されます。

アラート概要カードの情報を繰り返すだけでなく、**Overview** タブには、以下のフィールドを 1 つ以上含めることができます。
- Expected Bounds: **Show expected bounds** チェックボックスをクリックします。グラフの色が変わり、予想される動作と異常な動作が区別されます。
- Suggested Next Steps: 異常な動作の調査およびトリアージの手順を説明します。
- Correlated dashboards: アラートに関連するダッシュボードを活用することを提案します。Datadog はダッシュボード内のどのメトリクスがアラートのインサイトに関連しているかを表示します。

**Monitors** タブには、アラートに関連付けされたモニターがリストされます。表示されるモニターにはそれぞれ、現在のアラートのメトリクスとそのスコープに含まれる関連タグがあります。

さらに、Watchdog は、異常が再び発生した場合に通知するために作成できる 1 つまたは複数のモニターを提案します。これらのモニターはまだ存在しないため、テーブルにはステータスが **suggested** と表示されています。**Enable Monitor** をクリックして、組織に提案されたモニターを有効にします。一連のアイコンがポップアップ表示され、新しいモニターを開く、編集する、複製する、ミュートする、または削除することができます。

## フィルターアラート

Watchdog アラートフィードの絞り込みには、タイムレンジ、検索バー、ファセットを使用できます。

### タイムレンジ

右上のタイムレンジセレクターを使用して、指定したタイムレンジのアラートを表示します。過去 13 か月までのアラートを表示できます

### 検索バー

**Filter alerts** 検索ボックスにテキストを入力すると、アラートのタイトルを検索できます。

### ファセット

Watchdog アラートフィードの左側には、以下の検索ファセットがあります。対応するボックスにチェックを入れると、アラートをファセットで絞り込むことができます。

| すべてのアラートグループ    | 説明                                                           |
|---------------------|-----------------------------------------------------------------------|
| アラートカテゴリ      | すべての `apm`、`infrastructure` または `logs` アラートを表示。                |
| アラートタイプ          | APM やインフラストラクチャーインテグレーションのメトリクスを使用してアラートを選択します。  |
| APM プライマリタグ     | 表示するアラートのある[定義済み APM プライマリタグ][6]。              |
| 環境         | 表示するアラートのある環境。`env` タグの詳細については、[統合サービスタグ付け][5]を参照してください。                                                                                          |
| サービス             | 表示するアラートのあるサービス。`service` タグの詳細については、[統合サービスタグ付け][5]を参照してください。                                                                                          |

| ロググループ      | 説明                                                           |
|-----------------|-----------------------------------------------------------------------|
| ログ異常の種類| この種類のログ異常のみ表示します。サポートされている種類は、新しいログパターンと、既存のログパターンの増加です。                                                                                 |
| ログのソース      | このソースからのログを含むアラートのみ表示します。                 |
| ログのステータス      | このログステータスのログを含むアラートのみ表示します。               |



## アーカイブされたアラートの管理

Watchdog アラートのサイドパネルで、右上のフォルダーアイコンをクリックしてアーカイブします。アーカイブすると、フィードだけでなく、ホームページなど Datadog サイトの他の場所からもアラートが非表示になります。アラートがアーカイブされると、関連するサービスやリソースの横に Watchdog のピンクの双眼鏡アイコンが表示されなくなります。

アーカイブされたアラートを見るには、[Watchdog アラートフィード][1]の左上の "Show N archived alerts" のチェックボックスオプションを選択します。このオプションは、少なくとも 1 つのアラートがアーカイブされている場合にのみ利用可能です。また、各アラートを誰がいつアーカイブしたかを確認したり、アーカイブされたアラートをフィードに復元したりすることができます。

**注**: アーカイブ後であっても、Watchdog はサービスやリソースに関連する問題にフラグを立てます。

[1]: https://app.datadoghq.com/watchdog
[2]: https://app.datadoghq.com/apm/home
[3]: /ja/tracing/services/service_page/
[4]: /ja/watchdog/impact_analysis/
[5]: /ja/getting_started/tagging/unified_service_tagging/
[6]: /ja/tracing/guide/setting_primary_tags_to_scope/