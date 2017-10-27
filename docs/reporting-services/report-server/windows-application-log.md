---
title: "Windows アプリケーション ログ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows application logs [Reporting Services]
- logs [Reporting Services], Windows application logs
- application logs [Reporting Services]
ms.assetid: 742fd00e-aa6c-4c8a-b58f-c03c489b1699
caps.latest.revision: 32
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: d8e1716d9e81043992e5c92f260835cda7742972
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="windows-application-log"></a>Windows アプリケーション ログ
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] では、イベント メッセージが Windows アプリケーション ログに書き込まれます。 アプリケーション ログに書き込まれたメッセージ情報を使用して、ローカル システムで実行されているレポート サーバー アプリケーションで生成されたイベントを確認できます。  
  
## <a name="viewing-report-server-events"></a>レポート サーバーのイベントの表示  
 イベント ビューアーを使用すると、ログ ファイルの表示およびログ ファイルに含まれるメッセージのフィルター処理を実行できます。 イベント メッセージの詳細については、「 [エラーとイベントのリファレンス (Reporting Services)](../../reporting-services/troubleshooting/errors-and-events-reference-reporting-services.md)」を参照してください。 Windows アプリケーション ログおよびイベント ビューアーの詳細については、Windows の製品マニュアルを参照してください。  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] には、次の 3 つのイベント ソースがあります。  
  
-   レポート サーバー (レポート サーバー Windows サービス)  
  
-   レポート マネージャー  
  
-   スケジュールおよび配信のプロセッサ  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] には、レポート サーバーのアプリケーション イベントのログ記録を無効にしたり、ログに記録するイベントを制御する方法が用意されていません。 レポート サーバーのイベントのログ記録について記述しているスキーマは固定されています。 スキーマを拡張して、カスタム イベントをサポートすることはできません。  
  
 次の表では、レポート サーバーがアプリケーション イベント ログに書き込むイベントの種類を説明します。  
  
|イベントの種類|Description|  
|----------------|-----------------|  
|情報|正常に行われた操作を表すイベント (たとえば、レポート サーバー サービスの開始時)|  
|警告|発生する可能性のある問題を示すイベント (たとえば、空きディスク容量の不足)|  
|[エラー]|重大な問題を表すイベント (たとえば、サービスが開始されなかった場合)|  
|成功の監査|ログオンが成功したことを表すセキュリティ イベント|  
|失敗の監査|ログインを試行して失敗したときにログに記録されるイベント|  
  
## <a name="see-also"></a>参照  
 [Reporting Services のログ ファイルとソース](../../reporting-services/report-server/reporting-services-log-files-and-sources.md)   
 [エラーとイベントのリファレンス &#40;Reporting Services&#41;](../../reporting-services/troubleshooting/errors-and-events-reference-reporting-services.md)  
  
  

