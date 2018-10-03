---
title: rsInternalError - Reporting Services エラー | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rsInternalError
ms.assetid: 52613d52-fc78-4870-93f0-7d393ab9c335
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: a48d105a0b90a460459f0aaa7c282534658210e5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48076502"
---
# <a name="rsinternalerror---reporting-services-error"></a>rsInternalError - Reporting Services エラー
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|イベント ID|rsInternalError|  
|イベント ソース|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings|  
|コンポーネント|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|メッセージ テキスト|レポート サーバーで内部エラーが発生しました。 詳細については、エラー ログを参照してください。|  
  
## <a name="explanation"></a>説明  
 これは一般的なエラー メッセージです。多くの場合、このメッセージの後に詳細を示す説明的なエラーが含まれます。  
  
 内部エラーが発生するのはまれです。 このエラーが発生した場合は、レポート サーバーのトレース ログで詳細情報を確認できます。 さらに、このエラーが発生したコンピューターで、ローカル管理者として処理を実行している場合は、呼び出し履歴で詳細情報を確認できます。  
  
## <a name="user-action"></a>ユーザーの操作  
 このメッセージの具体的な原因を特定するには、\Microsoft SQL Server\MSRS12.\<instancename >\Reporting Services\LogFiles にある、レポート サーバーのログ ファイルを確認します。 詳細については、「[Reporting Services のログ ファイルとソース](../report-server/reporting-services-log-files-and-sources.md)」を参照してください。  
  
 呼び出し履歴を表示するには、エラーが発生したページを右クリックし、 **[ソースの表示]** をクリックします。 呼び出し履歴を表示するには、エラーが発生したコンピューターの管理者権限が必要です。  
  
 入手できる情報が他にない場合は、再度要求してください。  
  
## <a name="internal-only"></a>内部使用のみ  
  
## <a name="see-also"></a>参照  
 [レポート サーバー サービスの開始と停止](../report-server/start-and-stop-the-report-server-service.md)  
  
  
