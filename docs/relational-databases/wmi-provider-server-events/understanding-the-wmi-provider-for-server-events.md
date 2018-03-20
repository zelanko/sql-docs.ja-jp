---
title: "WMI Provider for Server Events を理解する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: wmi
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- architecture [WMI]
- SQL Server Agent [WMI]
- WMI Provider for Server Events, about WMI Provider for Server Events
ms.assetid: 8fd7bd18-76d0-4b28-8fee-8ad861441ab2
caps.latest.revision: 
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a7f710e54927b01ddcbdf0bb7890d992087bc51f
ms.sourcegitcommit: 0d904c23663cebafc48609671156c5ccd8521315
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2018
---
# <a name="understanding-the-wmi-provider-for-server-events"></a>WMI Provider for Server Events について
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  WMI Provider for Server Events を使用すれば、Windows Management Instrumentation (WMI) を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のイベントを監視できます。 このプロバイダーは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を WMI マネージ オブジェクトに変えることによって機能します。 このプロバイダーを使用することにより、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でイベント通知を生成できるイベントはすべて、WMI で利用できるようになります。 さらに、WMI と連動する管理アプリケーションとして、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントがそのイベントに応答できるので、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントで対応できるイベントのスコープが以前のリリースより広くなります。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントなどの管理アプリケーションは、WQL (WMI Query Language) ステートメントを実行することで WMI Provider for Server Events を使用して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] イベントにアクセスすることができます。 WQL は、WMI 特有の拡張機能を複数持つ、構造化照会言語 (SQL) の単純化されたサブセットです。 WQL を使用した場合、アプリケーションは特定のデータベースまたはデータベース オブジェクトに対してイベントの種類を取得します。 WMI Provider for Server Events は、クエリをイベント通知に変換し、対象データベース内のイベント通知を効率的に作成します。 イベント通知の動作の詳細については[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を参照してください[WMI Provider for Server Events の概念](http://technet.microsoft.com/library/ms180560.aspx)です。 クエリ可能なイベントは、「 [WMI Provider for Server Events のクラスとプロパティ](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-classes-and-properties.md)です。  
  
 定義済みの対象のサービスには、メッセージはメッセージを送信するイベント通知をトリガーするイベントの発生時に**msdb**という**SQL/Notifications/ProcessWMIEventProviderNotification/v1.0**. サービスがイベントを定義済みでキューに配置**msdb**という**WMIEventProviderNotificationQueue**です。 (サービスもキューも、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に最初に接続する際にプロバイダーによって動的に作成されます)。プロバイダーは、このキューからイベント データを読み取り、それをマネージ オブジェクト形式 (MOF) に変換してからアプリケーションに返します。 次の図に、このプロセスを示します。  
  
 ![WMI Provider for Server Events のフロー ダイアグラム](../../relational-databases/wmi-provider-server-events/media/wmi-provider-functional-spec.gif "WMI Provider for Server Events のフロー図")  
  
 たとえば、次の WQL クエリについて考えてみます。  
  
```  
SELECT * FROM DDL_DATABASE_LEVEL_EVENTS  
WHERE DatabaseName = 'AdventureWorks'  
```  
  
 このクエリに応答して、WMI Provider for Server Events は、対象データベース内に同等のイベント通知を作成します。  
  
```  
USE AdventureWorks ;  
GO  
CREATE EVENT NOTIFICATION SQLWEP_76CF38C1_18BB_42DD_A7DC_C8820155B0E9  
    ON DATABASE  
    WITH FAN_IN  
    FOR DDL_DATABASE_LEVEL_EVENTS  
    TO SERVICE  
        'SQL/Notifications/ProcessWMIEventProviderNotification/v1.0',   
        'A7E5521A-1CA6-4741-865D-826F804E5135';  
GO  
```  
  
 この例では、`SQLWEP_76CF38C1_18BB_42DD_A7DC_C8820155B0E9` は、プレフィックス `SQLWEP_` と GUID から構成される [!INCLUDE[tsql](../../includes/tsql-md.md)] 識別子です。 `SQLWEP` は、各識別子に対して新しい GUID を作成します。 値`A7E5521A-1CA6-4741-865D-826F804E5135`で、`TO SERVICE`句内の broker インスタンスを識別する GUID では、 **msdb**データベース。  
  
 WQL を使用する方法の詳細については、次を参照してください。 [WMI Provider for Server Events と WQL を使用して](http://technet.microsoft.com/library/ms180524\(v=sql.105\).aspx)です。  
  
 管理アプリケーションは、プロバイダーによって定義された WMI 名前空間に接続することで、WMI Provider for Server Events を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにダイレクトします。 Windows WMI サービスは、この名前空間をプロバイダー DLL である Sqlwep.dll にマップし、これをメモリに読み込みます。 プロバイダーは、サーバー イベント用の各インスタンスの WMI 名前空間を管理する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、形式は次です: \\ \\.\\*ルート*\Microsoft\SqlServer\ServerEvents\\*instance_name*ここで、 *instance_name*既定では MSSQLSERVER です。 インスタンスの WMI 名前空間に接続する方法について[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を参照してください[WMI Provider for Server Events と WQL を使用して](http://technet.microsoft.com/library/ms180524\(v=sql.105\).aspx)です。  
  
 プロバイダー DLL である Sqlwep.dll は、サーバー上にある [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの数にかかわらず、サーバーのオペレーティング システムの WMI ホスト サービスに一度だけ読み込まれます。  
  
 例については、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] for Server Events, WMI プロバイダーを使用するエージェント管理アプリケーションを参照してください[サンプル: を作成する SQL Server エージェント警告を使用して、WMI Provider for Server Events](http://technet.microsoft.com/library/ms186385.aspx)です。 マネージ コードのサーバー イベントの WMI プロバイダーを使用する管理アプリケーションの例は、次を参照してください。[サンプル: WMI イベント プロバイダーを使用してマネージ コードで](http://technet.microsoft.com/library/ms179315.aspx)です。 WMI に関する詳細についてはまた、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK。  
  
## <a name="see-also"></a>参照  
 [WMI Provider for Server Events の概念](http://technet.microsoft.com/library/ms180560.aspx)  
  
  
