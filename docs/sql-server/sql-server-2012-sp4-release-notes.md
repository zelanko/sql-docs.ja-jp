---
title: "SQL Server 2012 SP4 リリース ノート | Microsoft Docs"
ms.prod: sql-server
ms.prod_service: sql-non-specified
ms.service: server-general
ms.component: 
ms.technology: server-general
ms.custom: 
ms.date: 10/05/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67cb8b3e-3d82-47f4-840d-0f12a3bff565
caps.latest.revision: "0"
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 562c03dfc873adeaca8f8486f1ecb4c66c3c4d14
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="sql-server-2012-sp4-release-notes"></a>SQL Server 2012 SP4 リリース ノート
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)] このトピックは、SQL Server 2012 SP4 に含まれている機能強化をまとめたものです。 トピックでは、SP4 のインストールまたはインストールのトラブルシューティングを行う前に確認する問題についても説明します。 リリース ノートはオンラインのみで入手でき、インストール メディアには含まれていません。 このトピックは、問題が見つかったときに、定期的に更新されます。 SP4 の修正プログラムの詳細なリストについては、「[SQL Server 2012 Service Pack 4 のリリース情報](https://go.microsoft.com/fwlink/?linkid=846937)」を参照してください。  

> Service Pack 4 には、SQL Server 2012 SP3 のすべての累積的な更新プログラムが含まれます。
  
##<a name="download-pages"></a>ダウンロード ページ
次の項目は、SQL Server 2012 SP3 の主要なダウンロード パッケージへのリンクです。 システム要件と基本的なインストール手順が含まれているページをダウンロードします。
- [SQL Server 2012 SP4 の更新プログラムのインストール](https://go.microsoft.com/fwlink/?linkid=846829)
- [SQL Server 2012 SP4 Express](https://go.microsoft.com/fwlink/?linkid=846905)
- [Microsoft SQL Server 2012 SP4 Feature Pack](https://go.microsoft.com/fwlink/?linkid=846907)

##  <a name="sp4-performance-and-scale-improvements"></a>SP4 のパフォーマンスとスケーリングの改善

- **ディストリビューション エージェントのクリーンアップ プロシージャの向上**:サイズ超過のディストリビューション データベースが原因で、ブロックとデッドロックの状況が発生していました。 クリーンアップ プロシージャの向上は、これらのブロックまたはデッドロックのシナリオの一部を排除することを目的としています。 
- **動的メモリ オブジェクトのスケーリング**: 最新のハードウェア上でスケールするノードとコアの数に基づいて、動的にメモリ オブジェクトをパーティション分割します。 動的な昇格の目的は、潜在的なボトルネックを回避し、スレッド セーフ メモリ オブジェクトを自動的にパーティション分割することです。 パーティション分割されていないメモリ オブジェクトは、ノードによってパーティション分割されるように動的に昇格できます。 パーティションの数は、NUMA ノードの数と同じです。 ノードによってパーティション分割されたメモリ オブジェクトは、CPU によってパーティション分割されるようにさらに昇格することができます。この場合、パーティションの数は CPU の数と等しくなります。
- **8 TB を超えるバッファー プールの有効化**: バッファー プールの使用量に対し 128 TB の仮想アドレス空間を有効にします。
- **Change Tracking のクリーンアップ**: Change Tracking のクリーンアップのパフォーマンスと Change Tracking のサイド テーブルの効率性が向上しました。 

## <a name="sp4-supportability-and-diagnostics-improvements"></a>SP4 のサポート性と診断の向上

- **レプリケーション エージェントの完全ダンプのサポート**: 現在は、レプリケーション エージェントがハンドルされない例外に遭遇すると、既定の動作では例外の現象のミニ ダンプが作成されます。 既定の動作では、ハンドルされない例外に対する複雑なトラブルシューティング手順が必要です。 SP4 では、レプリケーション エージェントの完全ダンプの作成をサポートする新しいレジストリ キーが導入されました。
- **プラン表示 XML での診断の拡張**: プラン表示 XML は、有効なトレース フラグ、最適化された入れ子になったループ結合のメモリ部分、CPU 時間、および経過時間に関する情報を公開するために拡張されています。 
- **診断 XE および DMV 間の相関関係の改善**: クエリを一意に識別するために Query_hash と query_plan_hash フィールドが使用されます。 DMV はこれらを varbinary(8) として定義するのに対し、XEvent は UINT64 として定義します。 SQL Server に "符号なし bigint" がないため、キャストが機能しない場合があります。 この機能強化では、新しい XEvent アクション/フィルター列が導入されています。これは XE と DMV 間の関連付けクエリに役立つ INT64 として定義されている点を除き、query_hash と query_plan_hash と同等です。 
- **メモリ許可/使用状況の診断の向上**: 新しい query_memory_grant_usage XEvent (サーバー 2016 SP1 から移植)。
- **SSL ネゴシエーション手順へのプロトコル トレースの追加**: ネゴシエーションの成功/失敗のビット トレース情報 (プロトコルなど) を追加します。たとえば TLS 1.2 の展開時に接続性のシナリオをトラブルシューティングするときに役に立ちます。
- **ディストリビューション データベースの正しい互換性レベルの設定**: サービス パックをインストールすると、ディストリビューション データベースの互換性レベルが 90 に変わります。 レベルが変更されたのは、sp_vupgrade_replication ストアド プロシージャの問題によるものです。 SP はディストリビューション データベースに正しい互換性レベルが設定されるように変更されています。 
- **データベースの複製を作成する新しい DBCC コマンド**: 複製データベースは、CSS などのパワー ユーザーがスキーマとメタデータをデータなしで複製することによって、既存の運用データベースをトラブルシューティングできるように追加された、新しい DBCC コマンドです。 呼び出しは、DBCC clonedatabase (‘source_database_name’, ‘clone_database_name’) で実行されます。 複製されたデータベースは、実稼働環境では使用できません。 データベースが複製データベースの呼び出しから生成されているかどうかを確認するには、次のコマンドを使用して、DATABASEPROPERTYEX('clonedb', 'isClone') を選択します。戻り値 1 が true、0 が false です。 
- **SQL エラー ログの TempDB ファイルとファイル サイズの情報**: スタートアップ時に、TempDB データ ファイルのサイズと自動拡張が異なる場合、ファイルの数を出力し、警告をトリガーします。
- **SQL Server エラー ログの IFI サポート メッセージ**: エラー ログにデータベース ファイルの瞬時初期化の有効/無効を示します。
- **DBCC INPUTBUFFER に置き換わる新しい DMF**: DBCC INPUTBUFFER を置き換えるため、session_id をパラメーターとして受け取る新しい動的管理関数 sys.dm_input_buffer が導入されました。
- **可用性グループの読み取りルーティングの障害に対する Xevent の機能強化**: 現在、read_only_rout_fail XEvent は、ルーティング リストがあるが、リスト内のどのサーバーも接続に使用できない場合にのみ起動されます。 この機能強化には、トラブルシューティングに役立つ追加情報と、XEvent が起動するコード ポイントの拡張も含まれます。 
- **可用性グループのフェールオーバーを使用した Service Broker の処理の向上**: 現在、可用性グループのデータベースで Service Broker が有効になっていると、プライマリ レプリカで開始されたすべての Service Broker の接続は、AG フェールオーバー中に開いたままになります。 この機能強化により、AG フェールオーバー中、これらの開いたままの接続がすべて閉じられます。
- **[自動ソフト NUMA のパーティション分割](https://msdn.microsoft.com/library/ms345357(SQL.120).aspx)**: サーバー レベルでトレース フラグ 8079 が有効になっている場合、SQL 2014 SP2 で自動ソフト NUMA が導入されます。 スタートアップ時にトレース フラグ 8079 が有効になっていると、SQL Server 2014 SP2 はハードウェア レイアウトを問い合わせて、NUMA ノードあたり 8 個以上の CPU をレポートするシステムにソフト NUMA を自動的に構成します。 自動ソフト NUMA の動作は、ハイパースレッド (HT/論理プロセッサ) に対応しています。 パーティション分割と追加ノードの作成により、リスナーの数の増加、スケーリング、およびネットワークと暗号化機能の向上により、バックグラウンド処理が拡張されます。 自動ソフト NUMA を実稼働環境でオンにする前に、最初にワークロードのパフォーマンスをテストすることをお勧めします。

## <a name="see-also"></a>参照
- [SQL Server 2012 サービス更新プログラムのインストール](https://msdn.microsoft.com/library/hh479746(v=sql.110).aspx)
- [SQL Server のバージョンとエディションを識別する方法](https://support.microsoft.com/en-us/help/321185)

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]
