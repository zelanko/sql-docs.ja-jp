---
title: WMI Provider for Server Events のクラスとプロパティ |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- event classes [WMI]
- WMI Provider for Server Events, events listed
- classes [WMI]
ms.assetid: e2916cd7-a3ed-41e6-97b4-2ee060754cbe
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: eaa82b6f8b7f4a1abc8e43e16eee87ad2513bdb1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68039187"
---
# <a name="wmi-provider-for-server-events-classes-and-properties"></a>WMI Provider for Server Events のクラスとプロパティ
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  次に示すサーバー イベントは、WMI Provider for Server Events のプログラミング モデルを構成しています。 プロバイダーに対する WQL クエリの実行によってクエリを実行できるイベントには、2 つの主なカテゴリがあります。 その 2 つとは、データ定義言語 (DDL) イベントおよびトレース イベントです。 また、QUEUE_ACTIVATION および BROKER_QUEUE_DISABLED の Service Broker イベントも照会することができます。 次のツリー ダイアグラムの包含的な性質に注意してください。 たとえば、DDL_ASSEMBLY_EVENTS イベントには、ALTER_ASSEMBLY、CREATE_ASSEMBLY、および DROP_ASSEMBLY イベントが含まれています。 同様に、TRC_FULL_TEXT イベントには、FT_CRAWL_ABORTED、FT_CRAWL_STARTED、および FT_CRAWL_STOPPED イベントが含まれています。 ALL_EVENTS は、すべての DDL イベント、トレース イベント、QUEUE_ACTIVATION、および BROKER_QUEUE_DISABLED をカバーします。  
  
 イベントまたはイベント グループから照会できるプロパティについては、イベント スキーマを参照してください。 既定では、イベントのスキーマは次のディレクトリにインストールされます。[!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]Tools\Binn\schemas\sqlserver\2006\11\events\events.xsd。  
  
 発行されたイベント スキーマを参照する代わりに、 [ https://schemas.microsoft.com/sqlserver](https://go.microsoft.com/fwlink/?linkid=43100)します。  
  
 たとえば、ALTER_DATABASE イベントを示しながら、学習をその親イベントが DDL_SERVER_LEVEL_EVENTS、そのプロパティが**TSQLCommand**と**DatabaseName**します。 イベントは、プロパティも継承**SQLInstance**、 **PostTime**、 **ComputerName**、 **SPID**、および**LoginName**. イベントには、子イベントはありません。  
  
> [!NOTE]  
>  DDL と同様の操作を実行するシステム ストアド プロシージャもイベント通知を起動できます。 イベント通知はテストして、実行されているシステム ストアド プロシージャに応答するかどうか、確認してください。 たとえば、CREATE TYPE ステートメントと**sp_addtype**両方のストアド プロシージャが、CREATE_TYPE イベントで作成されるイベント通知が起動されます。 詳細については、次を参照してください。[DDL イベント](../../relational-databases/triggers/ddl-events.md)します。  
  
 **データ定義言語イベントおよびイベント グループ**  
  
 ![WMI Provider for Server イベントのイベント ツリー](../../relational-databases/wmi-provider-server-events/media/sql-wmi-ddl-events-ktm.gif "WMI Provider for Server イベントのイベント ツリー")  
  
 **トレース イベントとイベント グループ**  
  
 ![トレース イベントおよびイベント グループ](../../relational-databases/wmi-provider-server-events/media/sql-wmi-trc-all-events.gif "トレース イベントおよびイベント グループ")  
  
## <a name="see-also"></a>参照  
 [WMI Provider for Server Events の概念](../../relational-databases/wmi-provider-server-events/wmi-provider-for-server-events-concepts.md)   
 [WMI Provider for Server Events と WQL の使用](../../relational-databases/wmi-provider-server-events/using-wql-with-the-wmi-provider-for-server-events.md)  
  
  
