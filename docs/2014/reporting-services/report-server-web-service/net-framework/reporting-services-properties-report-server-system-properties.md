---
title: レポート サーバー システムのプロパティ | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- report servers [Reporting Services], properties
- system-specific properties [Reporting Services]
ms.assetid: cd874117-00e5-4ae6-8629-eb9ba9f40478
caps.latest.revision: 55
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 79fb5e55f54a07f8b3a770f39b3c738a59dab16e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36166019"
---
# <a name="report-server-system-properties"></a>レポート サーバーのシステム プロパティ
  次のシステム プロパティ名は予約されています。 同じ名前のユーザー定義プロパティは作成できません。 Web サービス メソッドを使用すると、これらのプロパティの多くの読み取りや修正ができます。  
  
## <a name="properties"></a>[プロパティ]  
  
|プロパティ|説明|  
|--------------|-----------------|  
|SiteName|ユーザー インターフェイスに表示されるレポート サーバー サイトの名前。 既定値は `Microsoft Report Server` です。 このプロパティには空の文字列を指定できます。 最大長は 8,000 文字です。|  
|SystemSnapshotLimit|レポートに格納されるスナップショットの最大数。 有効な値は`-1`を通じて`2`、`147`、`483`、`647`です。 値が場合`-1`スナップショットの制限はありません。|  
|SystemReportTimeout|レポート サーバー名前空間で管理されているすべてのレポートの既定のレポート処理タイムアウト値 (秒単位)。 この値はレポート レベルでオーバーライドできます。 このプロパティを設定すると、レポート サーバーは指定された時間が経過した後、レポートの処理を停止しようとします。 有効な値は`-1`を通じて`2`、`147`、`483`、`647`です。 値に `-1` を設定すると、名前空間内のレポートが処理中にタイムアウトしません。 既定値は `1800` です。|  
|UseSessionCookies|レポート サーバーがクライアント ブラウザーとの通信時にセッションクッキーを使用する必要があるかどうかを指定します。 既定値は `true` です。|  
|SessionTimeout|セッションがアクティブな状態になっている期間 (秒単位)。 既定値は `600` です。|  
|EnableMyReports|個人用レポート機能が有効になっているかどうかを指定します。 値`true`機能が有効になっていることを示します。|  
|MyReportsRole|ユーザーの個人用レポート フォルダーに、セキュリティ ポリシーを作成する際に使用するロールの名前。 既定値は `My Reports Role` です。|  
|EnableExecutionLogging|レポート実行のログ記録が有効になっているかどうかを示します。 既定値は `true` です。|  
|ExecutionLogDaysKept|レポート実行情報を実行ログに保持する日数。 このプロパティの有効な値`0`を通じて`2`、`147`、`483`、`647`です。 値が `0` の場合、エントリは実行ログ テーブルから削除されません。 既定値は `60` です。|  
|SnapshotCompression|スナップショットの圧縮方法を定義します。 既定値は `SQL` です。 有効な値は次のとおりです。<br /><br /> `SQL` = スナップショットは、レポート サーバー データベースへの格納時に圧縮されます。 これは現在の動作です。<br /><br /> **なし** = スナップショットは圧縮されません。<br /><br /> `All` = すべてのストレージ オプションのスナップショットが圧縮されます。このオプションには、レポート サーバー データベースやファイル システムが含まれます。|  
|EnableClientPrinting|レポート サーバーからのダウンロードに RSClientPrint ActiveX コントロールが使用可能かどうかを示します。 有効な値は`true`と`false`です。 既定値は `true` です。 このコントロールに必要な追加設定に関する詳細については、「 [Reporting Services のクライアント側印刷機能の有効化と無効化](../../report-server/enable-and-disable-client-side-printing-for-reporting-services.md)」を参照してください。|  
|EnableIntegratedSecurity|統合セキュリティをレポート データ ソース接続でサポートするかどうかを決定します。 既定値は `True` です。 有効な値は次のとおりです。<br /><br /> `True` = 統合セキュリティが有効になります。<br /><br /> `False` = 統合セキュリティが有効になりません。 統合セキュリティを使用するように構成されているレポート データ ソースは実行されません。|  
|EnableRemoteErrors|リモート コンピューターからレポートを要求したユーザーに返されるエラー メッセージに、外部エラー情報 (レポート データ ソースに関するエラー情報など) を含めます。 有効な値は`true`と`false`です。 既定値は `false` です。 詳細については、「[リモート エラーの有効化 (Reporting Services)](../../report-server/enable-remote-errors-reporting-services.md)」を参照してください。|  
  
## <a name="see-also"></a>参照  
 <xref:ReportService2010.ReportingService2010.GetSystemProperties%2A>   
 <xref:ReportService2010.ReportingService2010.SetSystemProperties%2A>   
 [Web サービスと .NET Framework を使用してのアプリケーションの構築](building-applications-using-the-web-service-and-the-net-framework.md)   
 [レポート サーバー Web サービス](../report-server-web-service.md)   
 [テクニカル リファレンス (SSRS)](../../technical-reference-ssrs.md)  
  
  