---
title: Windows アプリケーション ログ | Microsoft Docs
description: ローカル システムで実行されるレポート サーバー アプリケーションによって生成されるアプリケーション ログでイベント メッセージを表示する方法について説明します。
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server
ms.topic: conceptual
helpviewer_keywords:
- Windows application logs [Reporting Services]
- logs [Reporting Services], Windows application logs
- application logs [Reporting Services]
ms.assetid: 742fd00e-aa6c-4c8a-b58f-c03c489b1699
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 5466c8a3e839a6db9438fde3ca7ce295405f3f23
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84547834"
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
  
|イベントの種類|説明|  
|----------------|-----------------|  
|Information|正常に行われた操作を表すイベント (たとえば、レポート サーバー サービスの開始時)|  
|警告|発生する可能性のある問題を示すイベント (たとえば、空きディスク容量の不足)|  
|エラー|重大な問題を表すイベント (たとえば、サービスが開始されなかった場合)|  
|成功の監査|ログオンが成功したことを表すセキュリティ イベント|  
|失敗の監査|ログインを試行して失敗したときにログに記録されるイベント|  
  
## <a name="see-also"></a>参照  
 [Reporting Services のログ ファイルとソース](../../reporting-services/report-server/reporting-services-log-files-and-sources.md)   
 [エラーとイベントのリファレンス (Reporting Services)](../../reporting-services/troubleshooting/errors-and-events-reference-reporting-services.md)  
  
  
