---
title: "レポート サーバー アイテムのプロパティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- report servers [Reporting Services], properties
- item-specific properties [Reporting Services]
- report items [Reporting Services], properties
- items [Reporting Services], properties
ms.assetid: 21edec6d-9897-48fb-8c75-182305b1dbdb
caps.latest.revision: 43
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: ae7f1a99b09e4c8fc5f2483e9aa360cce83da2df
ms.contentlocale: ja-jp
ms.lasthandoff: 08/12/2017

---
# <a name="reporting-services-properties---report-server-item-properties"></a>Reporting Services のプロパティ - レポート サーバー アイテムのプロパティ
  アイテム プロパティは、レポート サーバー データベースのアイテムに固有のプロパティです。 アイテム プロパティには、レポート、リンク レポート、フォルダー、リソース、モデル、データ ソースなどがあります。  
  
 次のアイテム プロパティ名は予約されています。 同じ名前のユーザー定義プロパティは作成できません。 レポート サーバー Web サービス メソッドを使用すると、これらのプロパティの多くを読み取ったり、修正したりできます。  
  
## <a name="item-properties"></a>アイテム プロパティ  
 次のプロパティは、レポート サーバー データベースのすべてのアイテムに適用されます。  
  
|プロパティ|Description|  
|--------------|-----------------|  
|**作成者**|レポート サーバー データベースへアイテムを最初に追加したユーザーの名前。|  
|**CreationDate**|アイテムがレポート サーバー データベースに追加された日付と時刻。|  
|**説明**|アイテムの説明。|  
|**[非表示]**|ユーザーがアイテムを表示および使用できるかどうかを示す値。|  
|**ID**|レポート サーバー データベースのアイテムの ID。|  
|**ModifiedBy**|レポート サーバー データベースのアイテムを最後に変更したユーザーの名前。|  
|**ModifiedDate**|ユーザーがアイテムを最後に変更した日付と時刻。|  
|**名**|レポート サーバー データベースのアイテムの名前。|  
|**パス**|アイテムの完全なパス名です。 レポート サーバー データベースのアイテムのパスの長さは最大 260 字です。|  
|**サイズ**|レポート サーバー データベースのアイテムのサイズ (バイト単位)。|  
|**種類**|レポート サーバー データベースのアイテムの種類。|  
|**VirtualPath**|レポート サーバー データベースのアイテムの仮想パス。 <xref:ReportService2010.CatalogItem.VirtualPath%2A> プロパティの値は、ユーザーがそのアイテムを表示するときに使用するパスです。 たとえば、report1 というレポートがユーザーの個人的な My Reports フォルダー内にある場合、仮想パスは /My Reports となります。 アイテムの実際のパスは /Users/username/My Reports です。|  
  
## <a name="folder-properties"></a>フォルダー プロパティ  
 これまで説明したアイテム プロパティの他に、次のプロパティがレポート サーバー データベースのフォルダーに適用されます。  
  
|プロパティ|Description|  
|--------------|-----------------|  
|**予約済み**|フォルダーの <xref:ReportService2010.ReportingService2010.GetProperties%2A> メソッドが返す値は、レポート サーバーによって予約されています。 予約されたフォルダーには Users、My Reports、および / が含まれています。 予約されたフォルダーは、変更も削除もできません。|  
  
## <a name="report-properties"></a>レポート プロパティ  
 これまで説明したアイテム プロパティの他に、次のプロパティがレポート サーバー データベースのレポートに適用されます。  
  
|プロパティ|Description|  
|--------------|-----------------|  
|**言語**|レポートで使用される言語。 値は、Internet Engineering Task Force (IETF) RFC1766 仕様で定義されている言語コードです。 先頭の 2 文字は基本言語を指定します。 ハイフンで区切られた 2 番目の部分は、言語のバリエーションや方言を指定します。 レポート定義の **Body**要素に関連付けられた **Style** 要素に値が指定されていない場合は、既定値がレポート サーバーの言語になります。|  
|**ReportProcessingTimeout**|各レポートのタイムアウト値 (秒単位)。 この値を設定すると、指定した時間が経過した時点でレポートの処理が中止されます。 有効値は **-1** ～ **2**、**147**、**483**、**647**です。 値が場合**-1**レポートが処理中にタイムアウトをしません。 値が場合**null**、システム プロパティの値**ReportProcessingTimeout**レポート処理のタイムアウトのために使用します。 既定値は**null**です。 詳細については、「[レポート サーバーのシステム プロパティ](../../../reporting-services/report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md)」を参照してください。|  
|**ExecutionDate**|レポートのスナップショットが最後に作成された日付と時刻。|  
|**CanRunUnattended**|スケジュールに基づいてレポートを自動実行できるかどうかを示す値。 このプロパティ設定されている場合**true**、レポート パラメーターの既定値が定義されていると、レポートでデータ ソースの資格情報が格納されているまたはに設定されている資格情報取得オプション**None**です。 このプロパティ設定されている場合**false**、自動実行レポートを実行するための前提条件が満たされていません。 「[自動実行アカウントを構成する &#40;SSRS 構成マネージャー&#41;](../../../reporting-services/install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)」を参照してください。|  
|**HasParameterDefaultValues**|レポートのすべてのレポート パラメーターが有効な既定値に設定されているかどうかを示す値。 値も**true**レポートがレポート パラメーターを持っていない場合。 このプロパティが **false** に設定されている場合は、1 つ以上のレポート パラメーターに有効な既定値がありません。|  
|**HasDataSourceCredentials**|レポートに関連付けられているすべてのデータ ソースの資格情報取得オプション セットが **None** または **Store** であることを示す値。 このプロパティが **false** に設定されている場合は、レポートに関連付けられているいずれかのデータ ソースの資格情報取得オプション セットが **Integrated** または **Prompt** です。|  
|**IsSnapshotExecution**|レポートがスナップショットであるかどうかを示す値。|  
|**HasScheduleReadyDataSources**|レポートのデータ ソースが、実行スケジュールをサポートするように構成されているかどうかを示す値。 このプロパティ設定されている場合**false**ユーザーがレポートをサブスクライブできません。|  
  
## <a name="resource-properties"></a>リソース プロパティ  
 これまで説明したアイテム プロパティの他に、次のプロパティがレポート サーバー データベースのリソースに適用されます。  
  
|プロパティ|Description|  
|--------------|-----------------|  
|**Mime の種類**|レポート サーバー データベースのリソースの MIME の種類。|  
  
## <a name="see-also"></a>参照  
 [Web サービスと、.NET Framework を使用してアプリケーションの構築](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [レポート サーバー Web サービス](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [テクニカル リファレンス & #40 です。SSRS &#41;](../../../reporting-services/technical-reference-ssrs.md)  
  
  
