---
title: HTML デバイス情報設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- HTML [Reporting Services], rendering
- device information settings [Reporting Services], HTML rendering
ms.assetid: f505f478-dd6d-444a-957c-34f7cfb98911
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: a415a5f735e731efe3f3ae8b282f8ce2a1ad2eba
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48155850"
---
# <a name="html-device-information-settings"></a>HTML デバイス情報設定
  次の表は、HTML 形式で表示するデバイス情報設定を示しています。  
  
> [!IMPORTANT]  
>  次の表に示す **(\*)** の付いたデバイス情報設定は非推奨になっているため、新しいアプリケーションでは使用できません。 詳細については、次を参照してください。 [SQL Server 2014 における SQL Server Reporting Services の非推奨機能](deprecated-features-in-sql-server-reporting-services-ssrs.md)します。  
  
|設定|値|  
|-------------|-----------|  
|`AccessibleTablix`|スクリーン リーダー用の追加のアクセシビリティ メタデータを使用して表示するかどうかを示します。 このパラメーターは、単純なグループ化が行われる、単純なテーブル構造またはマトリックス構造を持つレポートにのみ適用できます。 既定値は `false` です。 追加のアクセシビリティ メタデータを使用すると、「Electronic and Information Technology Accessibility Standards (電子/情報技術アクセシビリティ基準)」(Section 508 (第 508 条)) の「Web-based Intranet and Internet Information and Applications (Web ベースのイントラネットとインターネットの情報およびアプリケーション)」(1194.22) で定められている次の技術標準に準拠したレポートを表示できます。<br /><br /> (g) データ テーブルの行と列のヘッダーは、識別できるようにすること。<br /><br /> (h) データ テーブルの行または列のヘッダーの論理階層が 2 階層以上になる場合は、マークアップを使用してデータ セルとヘッダー セルを関連付けること。<br /><br /> (i) 識別および移動しやすいように、フレームにはテキストによるタイトルを付けること。<br /><br /> このパラメーターは、 [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[SPS2010](../includes/sps2010-md.md)]でサポートされていますが、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[SPS2007](../includes/sps2007-md.md)]ではサポートされていません。|  
|**ActionScript(\*)**|ドリルスルーやブックマークのクリックなどのアクション イベントが発生したときに使用する JavaScript 関数の名前を指定します。 このパラメーターを指定した場合、アクション イベントが発生すると、サーバーへのポストバックを行う代わりに、名前付き JavaScript 関数がトリガーされます。|  
|**BookmarkID**|レポート内のジャンプ先ブックマーク ID。|  
|**DocMap**|レポートドキュメント マップの表示と非表示を切り替えます。 このパラメーターの既定値は`true`します。|  
|`ExpandContent`|レポートを、水平方向のサイズを抑えたテーブル構造に収めるかどうかを示します。|  
|**FindString**|レポートの検索条件として使用する文字列。 このパラメーターの既定値は、空文字列です。|  
|**GetImage (\*)**|HTML ビューアー ユーザー インターフェイス用の特定のアイコンを取得します。|  
|`HTMLFragment`|完全な HTML ドキュメントの代わりに HTML 断片を作成するかどうかを示します。 HTML 断片には TABLE 要素のレポート コンテンツが含まれ、HTML 要素と BODY 要素は省略されます。 既定値は `false` です。 SOAP を使用して表示する、`HTMLFragment`プロパティに設定`true`画像の正しい要求に使用できるセッション情報が入った Url が作成されます。 画像はレポート サーバー データベースのアップロードされたリソースである必要があります。|  
|`ImageConsolidation`|表示するグラフ、マップ、ゲージ、およびインジケーターの画像を 1 つの大きな画像に結合するかどうかを示します。 レポートに多数のデータ視覚化用アイテムが含まれている場合、画像を結合することで、クライアント ブラウザーでのレポートのパフォーマンスが向上します。 既定値は`true`の最新のブラウザー。|  
|**JavaScript**|表示レポートで JavaScript がサポートされるかどうかを示します。 既定値は `true` です。|  
|`LinkTarget`|レポートのハイパーリンクの対象。 ウィンドウまたはフレームを対象と同様に、ウィンドウの名前を提供することで`LinkTarget` = *window_name*、使用して新しいウィンドウを対象することも`LinkTarget`_blank を = です。 他に有効な対象名には、_self、_parent、および _top があります。|  
|**OnlyVisibleStyles(\*)**|現在レンダリングされているページの共有スタイルのみが生成されることを示します。|  
|`OutlookCompat`|Outlook でレポートの外観をよくする追加のメタデータを使用して表示するかどうかを示します。 それ以外の場合、既定値は`false`します。|  
|**パラメーター**|ツール バーのパラメーター領域を表示するか非表示にするかを示します。 このパラメーターの値に設定する場合`true`ツールバーのパラメーター領域が表示されます。 このパラメーターの既定値は`true`します。|  
|`PrefixId`|使用すると`HTMLFragment`、すべてを指定したプレフィックスを追加します。`ID`作成された HTML フラグメント内の属性。|  
|**ReplacementRoot(\*)**|ReportViewer コントロールの外部に表示する場合、レポートのすべてのドリルスルー、トグル、およびブックマークのリンクの先頭に追加する文字列。 たとえば、ユーザーのクリックをカスタム ページにリダイレクトするために使用されます。|  
|**ResourceStreamRoot(\*)**|切り替えや並べ替え用の画像など、すべての画像リソースの URL の先頭に追加する文字列。|  
|**セクション**|表示するレポートのページ番号。 `0` の値は、レポートのすべてのセクションが表示されることを示します。 既定値は `1` です。|  
|**StreamRoot (\*)**|レポート サーバーが返す HTML レポートで IMG 要素の **src** 属性の値の前に付けるパス。 既定では、レポート サーバーがパスを提供します。 この設定を使用して、レポートの画像のルート パスを指定できます (たとえば、**http://\<サーバー名>/resources/companyimages**)。|  
|**StyleStream**|スタイルとスクリプトがドキュメント内ではなく、異なるストリームとして作成されるかどうかを示します。 既定値は `false` です。|  
|`Toolbar`|ツール バーを表示するか非表示にするかを示します。 このパラメーターの既定値は`true`します。 このパラメーターの値が場合`false`、(ドキュメント マップ) を除くすべての残りのオプションは無視されます。 このパラメーターを省略すると、サポートされている表示形式でツール バーが自動的に表示されます。<br /><br /> URL アクセスを使用してレポートを表示すると、レポート ビューアー ツール バーが表示されます。 ツール バーは SOAP API によっては表示されません。 ただし、`Toolbar`設定がレポートを表示する方法に影響するデバイス情報、SOAP を使用したときに`Render`メソッド。 このパラメーターの値が場合`true`レポートの最初のセクションのみが表示される HTML を表示するために SOAP を使用する場合。 値が `false` である場合、HTML レポート全体が単一の HTML ページとして表示されます。|  
|`UserAgent`|`user-agent`は HTTP 要求であると、要求を行っているブラウザーの文字列。|  
|**Zoom (\*)**|整数のパーセンテージまたは文字列定数としてのレポート ズーム値。 標準的な文字列値には `Page Width` と `Whole Page` などがあります。 Internet Explorer 5.0 よりも前の [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer および[!INCLUDE[msCoName](../includes/msconame-md.md)] 以外のすべてのブラウザーでは、このパラメーターが無視されます。 このパラメーターの既定値は`100`します。|  
|**DataVisualizationFitSizing**|Tablix 内でのデータの視覚エフェクトの調整動作を示します。 これには、グラフ、ゲージ、およびマップが含まれます。<br /><br /> 有効な値は、 **Approximate** および **Exact**です。<br /><br /> 既定値は **Approximate**です。 この設定を **rsreportserver.config** ファイルから削除すると、既定の動作は **Exact**になります。<br /><br /> **Exact** を有効にした場合は、正確なサイズを特定する処理に時間がかかることがあるため、パフォーマンスに影響する可能性があります。|  
  
## <a name="see-also"></a>参照  
 [表示拡張機能にデバイス情報設定を渡す](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [RSReportServer.Config で表示拡張機能パラメーターをカスタマイズする](customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [テクニカル リファレンス (SSRS)](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  
