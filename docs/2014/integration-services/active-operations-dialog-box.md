---
title: '[アクティブな操作] ダイアログボックス |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.isoperations.executions.f1
- sql12.ssis.ssms.isoperations.general.f1
ms.assetid: 5bb0fcd6-0ce9-488a-85b8-25dddaa03cda
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f930a2e6f3ce84c330a4b7292ebaaba3b2ab871e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66062221"
---
# <a name="active-operations-dialog-box"></a>[アクティブな操作] ダイアログ ボックス
  配置、検証、パッケージの実行など、** サーバー上で現在実行中の ** 操作の状態を表示するには、[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)][アクティブな操作][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ダイアログ ボックスを使用します。 このデータは、SSISDB カタログに格納されます。  
  
 関連 [!INCLUDE[tsql](../includes/tsql-md.md)] ビューの詳細については、「[catalog.operations (SSISDB データベース)](/sql/integration-services/system-views/catalog-operations-ssisdb-database)」、「[catalog.validations (SSISDB データベース)](/sql/integration-services/system-views/catalog-validations-ssisdb-database)」、「[catalog.executions (SSISDB データベース)](/sql/integration-services/system-views/catalog-executions-ssisdb-database)」を参照してください。  
  
 **どの操作を行いますか。**  
  
1.  [[アクティブな操作] ダイアログボックスを開く](#open_dialog)  
  
2.  [オプションを構成する](#options)  
  
##  <a name="open_dialog"></a>[アクティブな操作] ダイアログボックスを開く  
  
1.  
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]
  [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]を開きます。  
  
2.  Microsoft SQL Server データベース エンジンに接続します。  
  
3.  オブジェクト エクスプローラーで、 **[Integration Services]** ノードを展開します。 **[SSISDB]** を右クリックし、 **[アクティブな操作]** をクリックします。  
  
##  <a name="options"></a>オプションを構成する  
  
### <a name="options"></a>オプション  
 **Type**  
 操作の種類を指定します。 次に、**型**フィールドに使用できる値と、transact-sql `catalog.operations`ビューの [operations_type] 列の対応する値を示します。  
  
|||  
|-|-|  
|Integration Services の初期化|1 で保護されたプロセスとして起動されました|  
|操作のクリーンアップ (SQL エージェント ジョブ)|2|  
|プロジェクト バージョンのクリーンアップ (SQL エージェント ジョブ)|3|  
|プロジェクトの配置|101|  
|プロジェクトの復元|106|  
|パッケージ実行の作成および開始|200|  
|操作の停止 (検証または実行の停止)|202|  
|プロジェクトの検証|300|  
|パッケージの検証|301|  
|カタログの構成|1000|  
  
 **停止**  
 現在実行中の操作を停止する場合にクリックします。  
  
  
