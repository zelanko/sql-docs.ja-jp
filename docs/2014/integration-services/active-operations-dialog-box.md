---
title: アクティブな操作 ダイアログ ボックス |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.isoperations.executions.f1
- sql12.ssis.ssms.isoperations.general.f1
ms.assetid: 5bb0fcd6-0ce9-488a-85b8-25dddaa03cda
caps.latest.revision: 7
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b3c9105d6649443d8ec2d3425f86d609dfe6a2b3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37151123"
---
# <a name="active-operations-dialog-box"></a>[アクティブな操作] ダイアログ ボックス
  配置、検証、パッケージの実行など、 **サーバー上で現在実行中の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 操作の状態を表示するには、**[アクティブな操作][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ダイアログ ボックスを使用します。 このデータは、SSISDB カタログに格納されます。  
  
 関連 [!INCLUDE[tsql](../includes/tsql-md.md)] ビューの詳細については、「[catalog.operations (SSISDB データベース)](/sql/integration-services/system-views/catalog-operations-ssisdb-database)」、「[catalog.validations (SSISDB データベース)](/sql/integration-services/system-views/catalog-validations-ssisdb-database)」、「[catalog.executions (SSISDB データベース)](/sql/integration-services/system-views/catalog-executions-ssisdb-database)」を参照してください。  
  
 **目的に合ったトピックをクリックしてください**  
  
1.  [アクティブな操作 ダイアログ ボックスを開く](#open_dialog)  
  
2.  [オプションの構成](#options)  
  
##  <a name="open_dialog"></a> [アクティブな操作] ダイアログ ボックスを開く  
  
1.  開いている[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]します。  
  
2.  Microsoft SQL Server データベース エンジンに接続します。  
  
3.  オブジェクト エクスプローラーで、 **[Integration Services]** ノードを展開します。 **[SSISDB]** を右クリックし、 **[アクティブな操作]** をクリックします。  
  
##  <a name="options"></a> オプションの構成  
  
### <a name="options"></a>および  
 **型**  
 操作の種類を指定します。 可能な値を次に、**型**フィールドと、TRANSACT-SQL の operations_type 列に対応する値`catalog.operations`ビュー。  
  
|||  
|-|-|  
|Integration Services の初期化|1|  
|操作のクリーンアップ (SQL エージェント ジョブ)|2|  
|プロジェクト バージョンのクリーンアップ (SQL エージェント ジョブ)|3|  
|プロジェクトの配置|101|  
|プロジェクトの復元|106|  
|パッケージ実行の作成および開始|200|  
|操作の停止 (検証または実行の停止)|202|  
|プロジェクトの検証|300|  
|パッケージの検証|301|  
|カタログの構成|1000|  
  
 **[停止]**  
 現在実行中の操作を停止する場合にクリックします。  
  
  
