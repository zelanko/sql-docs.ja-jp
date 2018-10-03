---
title: テーブルのプロパティ ダイアログ ボックス (SSAS - テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.ssmsimbi.TableProperties.f1
ms.assetid: 77571ccd-bdba-4e07-af55-465509dc6a33
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 783bd1ba103e97e442e61891138090198a5cdd0f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48104492"
---
# <a name="table-properties-dialog-box-ssas---tabular"></a>[テーブルのプロパティ] ダイアログ ボックス (SSAS - テーブル)
  テーブル モデル データベースでテーブルのプロパティを表示するには、 **の** [テーブルのプロパティ] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ダイアログ ボックスを使用します。 すべてのプロパティは読み取り専用です。  
  
 **[テーブルのプロパティ]** ダイアログ ボックスを表示するには、オブジェクト エクスプローラーでテーブルを右クリックして **[プロパティ]** をクリックします。  
  
## <a name="options"></a>および  
  
|項目|定義|  
|----------|----------------|  
|**名前**|テーブルの名前を表示します。|  
|**ID**|テーブルの識別子を表示します。|  
|**[説明]**|テーブルの説明を表示します。|  
|**[タイムスタンプの作成]**|テーブルが作成された日時を表示します。|  
|**[スキーマの最終更新]**|テーブルのメタデータが最後に更新された日時を表示します。|  
|**State**|テーブルの処理状態を表示します。 このプロパティの値の詳細については、次を参照してください。<xref:Microsoft.AnalysisServices.ProcessableMajorObject.State%2A>します。|  
|**最後に処理されました。**|テーブルが最後に処理された日時を表示します。|  
|**現在のストレージ モード**|テーブルの現在のストレージ モードを表示します。 ストレージ モードはデータベース レベルで設定され、すべてのテーブルで継承されます。 テーブル レベルで異なるストレージ モードを使用することはできません。 有効な値は、InMemory (既定値)、InMemoryWithDirectQuery、DirectQuery、DirectQueryWithinMemory です。|  
  
  
