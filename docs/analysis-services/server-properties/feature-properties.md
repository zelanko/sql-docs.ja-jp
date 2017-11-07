---
title: "フィーチャーのプロパティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQMSupportEnabled property
- ComUdfEnabled property
- LinkToOtherInstanceEnabled property
- ManagedCodeEnabled property
- ConnStringEncryptionEnabled property
- LinkFromOtherInstanceEnabled property
- LinkInsideInstanceEnabled property
- UseCachedPageAllocators property
ms.assetid: a34d046a-6562-4d98-b827-37cebc6d77b4
caps.latest.revision: 21
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 5249b93411e921ba98f23ccd99fe4d3ea475a6ce
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="feature-properties"></a>機能プロパティ
  機能プロパティは、製品の機能に関連しており、そのほとんどが詳細プロパティです。サーバー インスタンス間のリンクを制御するプロパティが含まれます。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、次の表に示すサーバー プロパティがサポートされています。 その他のサーバー プロパティとその設定方法の詳細については、「 [Analysis Services のサーバー プロパティ](../../analysis-services/server-properties/server-properties-in-analysis-services.md)」を参照してください。  
  
 **適用対象:** 多次元サーバー モードのみ  
  
## <a name="properties"></a>プロパティ  
  
|プロパティ|既定値|Description|  
|--------------|-------------|-----------------|  
|**ManagedCodeEnabled**|1|CLR ストレージ手順が有効かどうかを示す、ブール型プロパティです。|  
|**LinkInsideInstanceEnabled**|1|リンク オブジェクトを同じサーバー インスタンス内で作成できるかどうかを示す、ブール型プロパティです。|  
|**LinkToOtherInstanceEnabled**|0|リモート サーバー上のオブジェクトにリンクできるかどうかを示す、ブール型プロパティです。|  
|**LinkFromOtherInstanceEnabled**|0|他のサーバー インスタンスからオブジェクトにリンクできるかどうかを示す、ブール型プロパティです。|  
|**ConnStringEncryptionEnabled**|1|接続文字列がサーバー構成ファイル内で暗号化されているかどうかを示す、ブール型プロパティです。|  
|**UseCachedPageAllocators**|0|キャッシュ ページ アロケーターが有効かどうかを示す、ブール型プロパティです。|  
|**ComUdfEnabled**|0|COM オブジェクトとして定義されているユーザー定義関数が有効かどうかを示す、ブール型プロパティです。|  
|**SQMSupportEnabled**|1|エラー レポートおよび機能の使用状況レポートが [!INCLUDE[msCoName](../../includes/msconame-md.md)] に自動的に送信されるかどうかを示す、ブール型プロパティです。|  
|**ResourceMonitoringEnabled**|1|内部リソース監視カウンターが有効かどうかを示す、ブール型プロパティです。 既定では、このプロパティは有効です。 有効である場合、このプロパティは、カウンターが CPU、メモリ、および I/O アクティビティに関する使用状況データを収集できるようにします。<br /><br /> 内部リソース監視カウンターは、リソース使用状況について報告する動的管理ビュー (DMV) によって使用されます。 このプロパティを無効にすると、DMV クエリは引き続き実行されますが、結果セットは無効になります。 このプロパティに依存するのは、次のような DMV です。<br /><br /> **DISCOVER_OBJECT_ACTIVITY**<br /><br /> **DISCOVER_COMMAND_OBJECTS**<br /><br /> **DISCOVER_SESSIONS** (SESSION_READS、SESSION_WRITES、SESSION_CPU_TIME_MS の場合)<br /><br /> <br /><br /> 注: NUMA アーキテクチャを使用するマルチコア システムでは、このプロパティを無効にすると、特にマルチユーザーのワークロードが高い場合に、クエリのパフォーマンスを向上させることができます。 このプロパティを変更したためにクエリのパフォーマンスが向上したかどうかを判断するには、比較テストを実行する必要があります。 キャッシュの消去、一般的な間違いの回避など、比較テストの実行に関するベスト プラクティスについては、「 [SQL Server 2008 R2 Analysis Services 操作ガイド](http://go.microsoft.com/fwlink/?LinkID=225539)」を参照してください。|  
  
## <a name="see-also"></a>参照  
 [Analysis Services のサーバー プロパティ](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Analysis Services インスタンスのサーバー モードの決定](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)   
 [動的管理ビュー (DMV) を使用した Analysis Services の監視](../../analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)  
  
  

