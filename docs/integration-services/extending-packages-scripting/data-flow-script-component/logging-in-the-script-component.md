---
title: "スクリプト コンポーネントでのログ記録 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Script component [Integration Services], logging
ms.assetid: 17c19787-379e-43fe-9107-e36e17ecda53
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 410a2472399574753d67a44b93437b1698c8b086
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="logging-in-the-script-component"></a>スクリプト コンポーネントでのログ記録
  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] パッケージのログ記録を使用すると、実行の進行状況、結果、問題点などに関する詳細な情報を、定義済みのイベントまたはユーザー定義のメッセージとして保存し、後で分析することができます。 スクリプト コンポーネントを使用できます、<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A>のメソッド、 **ScriptMain**ユーザー定義データを記録するクラス。 ログ記録が有効になっている場合、 **ScriptComponentLogEntry**のログオン イベントが選択されている、**詳細**のタブ、 **SSIS ログの構成**ダイアログ ボックスで、1 回の呼び出し、<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A>メソッドは、データ フロー タスク用に構成されているすべてのログ プロバイダーに、イベント情報を格納します。  
  
 ログ記録の簡単な例を次に示します。  
  
 `Dim bt(0) As Byte`  
  
 `Me.Log("Test Log Event", _`  
  
 `0, _`  
  
 `bt)`  
  
> [!NOTE]  
>  ログ記録はスクリプト コンポーネントから直接実行できますが、ログ記録ではなくイベントを実装することを検討する必要があります。 イベントを使用すると、イベント メッセージのログ記録を有効にできるだけでなく、既定またはユーザー定義のイベント ハンドラーによってイベントに応答することができます。  
  
 ログ記録の詳細については、次を参照してください。 [Integration Services & #40 です。SSIS &#41;ログ記録](../../../integration-services/performance/integration-services-ssis-logging.md)です。  
  
## <a name="see-also"></a>参照  
 [Integration Services & #40 です。SSIS &#41;ログ記録](../../../integration-services/performance/integration-services-ssis-logging.md)  
  
  

