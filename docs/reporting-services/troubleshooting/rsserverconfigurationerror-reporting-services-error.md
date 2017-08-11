---
title: "rsServerConfigurationError - Reporting Services のエラー |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- rsServerConfigurationError
ms.assetid: 0913afc2-34b4-4713-b570-cfd5718975ac
caps.latest.revision: 12
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 78d4fd567ce57dba6d78c45a543a68725742d686
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="rsserverconfigurationerror---reporting-services-error"></a>rsServerConfigurationError - Reporting Services エラー
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|イベント ID|rsServerConfiguration|  
|イベント ソース|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings|  
|コンポーネント|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|メッセージ テキスト|レポート サーバーで構成エラーが発生しました。|  
  
## <a name="explanation"></a>説明  
 これは、レポート サーバーまたはレポート作成ツールの構成設定が無効な場合に発生する、一般的なエラーです。 通常、このエラーは、エラーの実際の原因を示す 2 番目のメッセージと共に表示されます。  
  
 考えられる原因を次に示します。  
  
-   RSReportServer.config ファイルまたは RSReportDesigner.config ファイルが見つからないか読み取ることができません。  
  
-   一方の構成ファイル内の XML 要素が見つからないか無効です。  
  
-   1 つまたは複数の XML 要素の値が見つからないか無効です。  
  
-   レジストリ設定が無効です。  
  
## <a name="user-action"></a>ユーザーの操作  
 構成ファイルを手動で編集した後にこのエラーが発生するようになった場合は、変更を破棄して以前の値を入力するか、バックアップがある場合は以前のバージョンを復元します。  
  
 付属している追加のエラー メッセージ情報を確認する、 **rsServerConfiguration**エラー、\Microsoft SQL Server\MSRS12 は、レポート サーバー トレース ログ ファイルを確認します\<。instancename > \reporting です。 詳細については、「[Reporting Services のログ ファイルとソース](../../reporting-services/report-server/reporting-services-log-files-and-sources.md)」を参照してください。  
  
## <a name="internal-only"></a>内部使用のみ  
  
## <a name="see-also"></a>参照  
 [Reporting Services 構成ファイル](../../reporting-services/report-server/reporting-services-configuration-files.md)   
 [Reporting Services の構成ファイル &#40; を変更します。RSreportserver.config &#41;](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)  
  
  
